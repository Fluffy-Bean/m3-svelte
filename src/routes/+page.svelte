<script lang="ts">
    import {
        mdiDatabaseEditOutline,
        mdiArrowCollapseDown,
        mdiForumPlusOutline,
        mdiCat,
        mdiShape,
        mdiBellBadgeOutline,
        mdiSend,
        mdiKey,
    } from "@mdi/js";

    import Dropdown from "$lib/components/Dropdown.svelte";
    import Toggle from "$lib/components/Toggle.svelte";
    import Dialog from "$lib/components/Dialog.svelte"
    import Button from "$lib/components/Button.svelte";
    import Chips from "$lib/components/Chips.svelte";
    import Card from "$lib/components/Card.svelte";

    const dropdown = [
        {
            id: "item-1",
            title: "Item 1",
            description: "Description 1",
        },
        {
            id: "item-2",
            title: "Item 2",
            description: "Description 2",
        },
        {
            id: "item-3",
            title: "Item 3",
            description: "Description 3",
        },
    ];

    const toggle = {
        label: "Example toggle",
        checked: true,
    }

    const dialog = {
        icon: mdiDatabaseEditOutline,
        heading: "Confirm changes?",
        subheading: "Changes to the database 'DO_NOT_EDIT' will be unreversible!",
        open: false,
    }
    const dialog_leg = {
        icon: mdiCat,
        heading: "Maned Wolffff",
        open: false,
        actions: [
            {
                text: "leg?",
                onclick: () => { dialog.open = true },
            },
            {
                text: "leg!",
                onclick: () => { dialog_leg.open = false },
                style: "outlined",
            }
        ]
    }

    const button = {
        icon: mdiArrowCollapseDown,
        text: "Button",
    }

    const chips = [
        {
            text: "This",
            icon: mdiShape,
        },
        {
            text: "is",
        },
        {
            text: "an example",
        },
        {
            text: "chip set",
            icon: mdiBellBadgeOutline,
        },
    ]
</script>

<div class="mb-3">
    <Card style={"filled"}>
        <div class="p-5">
            <h2 class="text-lg">Dropdown</h2>
            <Dropdown entries={dropdown} />
        </div>
    </Card>
</div>

<div class="mb-3">
    <Card style={"filled"}>
        <div class="p-5">
            <h2 class="text-lg mb-2">Toggle</h2>
            <Toggle label={toggle.label} checked={toggle.checked} />
            <Toggle label={toggle.label} checked={toggle.checked} />
            <Toggle label={toggle.label} checked={toggle.checked} />
            <Toggle label={toggle.label} checked={toggle.checked} />
            <Toggle label={toggle.label} checked={toggle.checked} />
        </div>
    </Card>
</div>

<div class="mb-3">
    <Card style={"filled"}>
        <div class="p-5">
            <h2 class="text-lg mb-2">Dialogs</h2>

            <div class="flex flex-row justify-start items-center gap-2 flex-wrap">
                <Button style={"filled"} icon={mdiForumPlusOutline} text={"Open Dialog"} onclick={() => dialog.open = true} />
                <Button style={"filled"} text={"Show Leggy"} onclick={() => dialog_leg.open = true} />
            </div>

            <Dialog heading={dialog.heading} subheading={dialog.subheading} icon={dialog.icon} open={dialog.open}></Dialog>
            <Dialog heading={dialog_leg.heading} open={dialog_leg.open} actions={dialog_leg.actions}>
                <img src="/leg.jpg" alt="" class="h-80 mx-auto" />
            </Dialog>
        </div>
    </Card>
</div>

<div class="mb-3">
    <Card style={"filled"}>
        <div class="p-5">
            <h2 class="text-lg mb-2">Buttons</h2>
            <div class="flex flex-row justify-start items-center gap-2 flex-wrap">
                <Button style={"filled"} icon_orientation="right" icon={mdiSend} text={"Send Message"} />
                <Button style={"tonal"} icon={mdiKey} text={"Enable VPN"} />
                <Button style={"outlined"} icon={mdiShape} />
                <Button style={"text"} text={"Learn More"} />
            </div>
        </div>
    </Card>
</div>

<div class="mb-3">
    <Card style={"filled"}>
        <div class="p-5">
            <h2 class="text-lg mb-2">Chips</h2>
            <Chips chips={chips} />
        </div>
    </Card>
</div>
