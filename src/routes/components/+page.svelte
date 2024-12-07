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
            support: "These dont make sound",
            link: "/components/accordions",
        },
        {
            icon: mdiToggleSwitchOutline,
            label: "Switch",
            support: "Also know as a Toggle",
            link: "/components/switch",
        },
        {
            icon: mdiCookieOutline,
            label: "Dialogs",
            support: "Cookie popups everywhere!",
            link: "/components/dialogs",
        },
        {
            icon: mdiButtonPointer,
            label: "Buttons",
            support: "Click everything",
            link: "/components/buttons",
        },
        {
            icon: mdiFormatListBulletedType,
            label: "Lists",
            support: "Show a lot of information in a pretty way",
            link: "/components/lists",
        },
        {
            icon: mdiNavigationVariantOutline,
            label: "Navigation",
            support: "Dont get lost!",
            link: "/components/navigation",
        },
        {
            icon: mdiCardOutline,
            label: "Chips",
            support: "Not edible",
            link: "/components/chips",
        },
    ]
</script>

<h1 class="text-m3-size-headline-large mb-3">Components</h1>

<Card style={"filled"} class="mb-3">
    <ul class="flex flex-col rounded py-2">
        {#each components as { icon, link, label, support }}
            <li>
                <List link={link}>
                    {#snippet leading()}
                        <SvgIcon type="mdi" path={icon} size={24} />
                    {/snippet}
                    {#snippet body()}
                        <ListLabel type={"headline"} text={label} />
                        <ListLabel type={"supporting"} text={support} />
                    {/snippet}
                    {#snippet trailing()}
                        <SvgIcon type="mdi" path={mdiMenuRight} size={24} />
                    {/snippet}
                </List>
            </li>
        {/each}
    </ul>
</Card>
