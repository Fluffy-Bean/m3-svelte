<script lang="ts">
    import {
        mdiButtonPointer,
        mdiCardOutline,
        mdiCookieOutline,
        mdiFormatListBulletedType,
        mdiMenuDown,
        mdiNavigationVariantOutline,
        mdiToggleSwitchOutline,
        mdiMenuRight,
    } from "@mdi/js";
    import SvgIcon from "@jamescoyle/svelte-icon";

    import Card from "$lib/components/cards/Card.svelte";
    import List from "$lib/components/lists/List.svelte";
    import ListLabel from "$lib/components/lists/ListLabel.svelte";

    const components = [
        {
            icon: mdiMenuDown,
            label: "Accordions",
            support: "Not an official component!",
            link: "/components/accordions",
        },
        {
            icon: mdiToggleSwitchOutline,
            label: "Switch",
            support: "",
            link: "/components/switch",
        },
        {
            icon: mdiCookieOutline,
            label: "Dialogs",
            support: "",
            link: "/components/dialogs",
        },
        {
            icon: mdiButtonPointer,
            label: "Buttons",
            support: "",
            link: "/components/buttons",
        },
        {
            icon: mdiFormatListBulletedType,
            label: "Lists",
            support: "Janky",
            link: "/components/lists",
        },
        {
            icon: mdiNavigationVariantOutline,
            label: "Navigation",
            support: "",
            link: "/components/navigation",
        },
        {
            icon: mdiCardOutline,
            label: "Chips",
            support: "",
            link: "/components/chips",
        },
    ]
</script>

<h1 class="text-m3-size-headline-large mb-3">Components</h1>

<Card style={"filled"} class="mb-3">
    <ul class="flex flex-col rounded py-2">
        {#each components as { icon, link, label, support }, i}
            <li>
                <List link={link}>
                    {#snippet leading()}
                        <SvgIcon type="mdi" path={icon} size={24} />
                    {/snippet}
                    <ListLabel type={"headline"}>{label}</ListLabel>
                    <ListLabel type={"supporting"}>{support}</ListLabel>
                    {#snippet trailing()}
                        <SvgIcon type="mdi" path={mdiMenuRight} size={24} />
                    {/snippet}
                </List>
            </li>
        {/each}
    </ul>
</Card>
