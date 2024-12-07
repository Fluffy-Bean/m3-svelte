<script lang="ts">
	import '../app.css';

    import { page, navigating } from "$app/stores";
    import { fly } from "svelte/transition";
    import {
        mdiHome,
        mdiShapeOutline,
        mdiMenuDown,
        mdiToggleSwitchOutline,
        mdiCookieOutline,
        mdiButtonPointer,
        mdiFormatListBulletedType,
        mdiNavigationVariantOutline,
        mdiCardOutline,
        mdiCodeTags,
    } from "@mdi/js";

    import NavigationRail from "$lib/components/navigation/NavigationRail.svelte";
    import NavigationRailButton from "$lib/components/navigation/NavigationRailButton.svelte";
    import Divider from "$lib/components/dividers/Divider.svelte";
    import NavigationBar from "$lib/components/navigation/NavigationBar.svelte";
    import NavigationBarButton from "$lib/components/navigation/NavigationBarButton.svelte";

	let { children } = $props();

    let windowWidth = $state(0);

    // Svelte reactivity is slightly weird with lists... so need to make a closure for the selected status :P
    let desktop_nav = $state([
        {
            icon: mdiHome,
            label: "Home",
            link: "/",
            selected: () => { return $page.url.pathname == "/" },
        },
        {
            icon: mdiMenuDown,
            label: "Accordions",
            link: "/components/accordions",
            selected: () => { return $page.url.pathname == "/components/accordions" },
        },
        {
            icon: mdiToggleSwitchOutline,
            label: "Switch",
            link: "/components/switch",
            selected: () => { return $page.url.pathname == "/components/switch" },
        },
        {
            icon: mdiCookieOutline,
            label: "Dialogs",
            link: "/components/dialogs",
            selected: () => { return $page.url.pathname == "/components/dialogs" },
        },
        {
            icon: mdiButtonPointer,
            label: "Buttons",
            link: "/components/buttons",
            selected: () => { return $page.url.pathname == "/components/buttons" },
        },
        {
            icon: mdiFormatListBulletedType,
            label: "Lists",
            link: "/components/lists",
            selected: () => { return $page.url.pathname == "/components/lists" },
        },
        {
            icon: mdiNavigationVariantOutline,
            label: "Navigation",
            link: "/components/navigation",
            selected: () => { return $page.url.pathname == "/components/navigation" },
        },
        {
            icon: mdiCardOutline,
            label: "Chips",
            link: "/components/chips",
            selected: () => { return $page.url.pathname == "/components/chips" },
        },
    ]);

    let mobile_nav = $state([
        {
            icon: mdiHome,
            label: "Home",
            link: "/",
            selected: () => { return $page.url.pathname == "/" },
        },
        {
            icon: mdiShapeOutline,
            label: "Components",
            link: "/components",
            selected: () => { return $page.url.pathname == "/components" },
        },
        {
            icon: mdiCodeTags,
            label: "GitHub",
            link: "https://github.com/Fluffy-Bean",
            selected: () => { return false },
        },
    ]);
</script>

<svelte:window bind:innerWidth={windowWidth} />

{#if windowWidth > 660}
    <NavigationRail class="fixed top-0 left-0 bottom-0 z-10 bg-transparent" menu_callback={() => {}}>
        {#each desktop_nav as { icon, label, link, selected }}
            <NavigationRailButton
                    icon={icon}
                    label={label}
                    link={link}
                    selected={selected()}
            />
        {/each}
    </NavigationRail>
    <Divider orientation="vertical" class="fixed top-0 left-[80px] bottom-0 z-10" />
{:else if windowWidth <= 660}
    <NavigationBar class="fixed bottom-0 left-0 right-0 z-10">
        {#each mobile_nav as { icon, label, link, selected }}
            <NavigationBarButton
                    icon={icon}
                    label={label}
                    link={link}
                    selected={selected()}
            />
        {/each}
    </NavigationBar>
{/if}

<main
        class="text-m3-on-surface min-h-screen relative"
        class:ml-[80px]={windowWidth > 660}
        class:mb-[80px]={windowWidth <= 660}
>
    <div class="p-[1px] max-w-[600px] mx-auto">
        {#key $navigating}
            <div class="m-4" out:fly={{ y: 5, duration: 150 }} in:fly={{ y: -5, duration: 150, delay: 150 }}>
                {@render children()}
            </div>
        {/key}
    </div>
</main>
