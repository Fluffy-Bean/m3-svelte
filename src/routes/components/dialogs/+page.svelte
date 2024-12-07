<script lang="ts">
    import { mdiForumPlusOutline, mdiExclamation } from "@mdi/js";

    import Button from "$lib/components/buttons/CommonButton.svelte";
    import Card from "$lib/components/cards/Card.svelte";
    import Dialog from "$lib/components/dialogs/Dialog.svelte";

    const dialog = {
        heading: "Sample Dialog",
        supporting: "This is a sample dialog, here you can put much junk, like an annoying cookies popup!",
        open: false,
        actions: [
            {
                text: "Cool!",
                onclick: () => { dialog.open = false },
            }
        ]
    }
    const dialog_leg = {
        icon: mdiExclamation,
        heading: "Maned Wolf Jumpscare",
        supporting: `
        Look at this amazing orange creature... So majestic and fluffy.
        Did you know that their urine smells like weed? Also one of the tallest canines in the world!
        `,
        open: false,
        actions: [
            {
                text: "leg?",
                onclick: () => { alert("Maned wolfs are verrrry tall") },
            },
            {
                text: "leg!",
                onclick: () => { dialog_leg.open = false },
                style: "outlined",
            }
        ]
    }
</script>

<h1 class="text-m3-size-headline-large mb-3">Dialogs</h1>

<div class="mb-3">
    <Card style={"filled"}>
        <div class="p-5">
            <div class="flex flex-row justify-start items-center gap-2 flex-wrap">
                <Button style={"filled"} icon={mdiForumPlusOutline} text={"Open Dialog"} onclick={() => dialog.open = true} />
                <Button style={"filled"} text={"Show Leggy"} onclick={() => dialog_leg.open = true} />
            </div>

            <Dialog heading={dialog.heading} supporting={dialog.supporting} open={dialog.open} actions={dialog.actions}/>
            <Dialog heading={dialog_leg.heading} supporting={dialog_leg.supporting} icon={dialog_leg.icon} open={dialog_leg.open} actions={dialog_leg.actions}>
                <img src="/leg.jpg" alt="" class="h-80 mx-auto" />
            </Dialog>
        </div>
    </Card>
</div>
