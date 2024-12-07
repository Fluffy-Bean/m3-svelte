<script lang="ts">
    import { mdiShapeOutline } from "@mdi/js";

    import Card from "$lib/components/cards/Card.svelte";
    import NavigationRail from "$lib/components/navigation/NavigationRail.svelte";
    import NavigationRailButton from "$lib/components/navigation/NavigationRailButton.svelte"
    import NavigationBar from "$lib/components/navigation/NavigationBar.svelte";
    import NavigationBarButton from "$lib/components/navigation/NavigationBarButton.svelte"

    const navigation_buttons = {
        menu_callback: () => { alert("Menu Callback!"); },
        options: [
            {
                icon: mdiShapeOutline,
                label: "Label",
                link: "#",
                selected: true,
            },
            {
                icon: mdiShapeOutline,
                label: "Label",
                link: "#",
                selected: false,
            },
            {
                icon: mdiShapeOutline,
                label: "Label",
                link: "#",
                selected: false,
            },
        ]
    }
</script>

<h1 class="text-m3-size-headline-large mb-3">Navigation</h1>

<Card style={"filled"} class="mb-3 p-5">
    <h1 class="text-m3-size-headline-small mb-2">Navigation Rail</h1>
    <div class="h-[700px] bg-m3-surface-container-high w-fit">
        <NavigationRail menu_callback={navigation_buttons.menu_callback}>
            {#each navigation_buttons.options as { icon, label, link, selected }}
                <NavigationRailButton icon={icon} label={label} link={link} selected={selected} />
            {/each}
        </NavigationRail>
    </div>
</Card>

<Card style={"filled"} class="mb-3 p-5">
    <h1 class="text-m3-size-headline-small mb-2">Navigation Bar</h1>
    <NavigationBar>
        {#each navigation_buttons.options as { icon, label, link, selected }}
            <NavigationBarButton icon={icon} label={label} link={link} selected={selected} />
        {/each}
    </NavigationBar>
</Card>
