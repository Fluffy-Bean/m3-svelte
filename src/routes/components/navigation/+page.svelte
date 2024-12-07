<script lang="ts">
    import { mdiVectorSquareRemove } from "@mdi/js";
    import Card from "$lib/components/cards/Card.svelte";
    import NavigationRail from "$lib/components/navigation/NavigationRail.svelte";
    import NavigationButton from "$lib/components/navigation/NavigationButton.svelte"

    const navigation_rail = {
        menu_callback: () => { alert("Menu Callback!"); },
        options: [
            {
                icon: mdiVectorSquareRemove,
                label: "Label",
                link: "#",
                selected: true,
            },
            {
                icon: mdiVectorSquareRemove,
                label: "Label",
                link: "#",
                selected: false,
            },
            {
                icon: mdiVectorSquareRemove,
                label: "Label",
                link: "#",
                selected: false,
            },
        ]
    }
</script>

<h1 class="text-m3-size-headline-large mb-3">Navigation</h1>

<div class="mb-3">
    <Card style={"filled"}>
        <div class="p-5">
            <h1 class="text-m3-size-headline-small mb-2">Navigation Rail</h1>
            <div class="h-[700px] bg-m3-surface-container-high w-fit">
                <NavigationRail menu_callback={navigation_rail.menu_callback}>
                    {#each navigation_rail.options as { icon, label, link, selected }}
                        <NavigationButton icon={icon} label={label} link={link} selected={selected} />
                    {/each}
                </NavigationRail>
            </div>
        </div>
    </Card>
</div>
