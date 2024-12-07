<script lang="ts">
	import '../app.css';

    import { page, navigating } from "$app/stores";
    import { fly } from "svelte/transition";
    import {
        mdiHome,
        mdiMenuDown,
        mdiToggleSwitchOutline,
        mdiCookieOutline,
        mdiButtonPointer,
        mdiFormatListBulletedType,
        mdiNavigationVariantOutline,
        mdiCardOutline,
    } from "@mdi/js";

    import NavigationRail from "$lib/components/navigation/NavigationRail.svelte";
    import NavigationButton from "$lib/components/navigation/NavigationButton.svelte";

	let { children } = $props();

    // Svelte reactivity is slightly weird with lists... so need to make a closure for the selected status :P
    let nav_buttons = $state([
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
            label: "Toggles",
            link: "/components/toggles",
            selected: () => { return $page.url.pathname == "/components/toggles" },
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
</script>

<div class="fixed top-0 left-0 bottom-0 z-10 bg-m3-surface-container-high">
    <NavigationRail>
        {#each nav_buttons as { icon, label, link, selected }}
            <NavigationButton
                icon={icon}
                label={label}
                link={link}
                selected={selected()}
            />
        {/each}
    </NavigationRail>
</div>

<main class="bg-m3-surface text-m3-on-surface min-h-screen relative ml-[80px]">
    <div class="p-[1px] max-w-[600px] mx-auto">
        {#key $navigating}
            <div class="m-4" out:fly={{ y: 5, duration: 150 }} in:fly={{ y: -5, duration: 150, delay: 150 }}>
                {@render children()}
            </div>
        {/key}
    </div>
</main>
