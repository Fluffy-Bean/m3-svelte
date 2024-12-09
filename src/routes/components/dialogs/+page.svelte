<script lang="ts">
    import {
        mdiForumPlusOutline,
        mdiExclamation,
        mdiShieldCrownOutline,
        mdiShieldAccountOutline,
        mdiMenuRight,
        mdiAccountOutline,
    } from "@mdi/js";
    import SvgIcon from "@jamescoyle/svelte-icon";

    import Button from "$lib/components/buttons/Button.svelte";
    import Card from "$lib/components/cards/Card.svelte";
    import Dialog from "$lib/components/dialogs/Dialog.svelte";
    import List from "$lib/components/lists/List.svelte";
    import Avatar from "$lib/components/avatar/Avatar.svelte";
    import ListLabel from "$lib/components/lists/ListLabel.svelte";

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
    const dialog_list = {
        icon: mdiAccountOutline,
        headline: "Channel Members",
        supporting: "Edit, remove, channel members here",
        open: false,
    }
    const dialog_user = {
        supporting: "Remove user \"Guest User\"?",
        open: false,
    }
</script>

<h1 class="text-m3-size-headline-large mb-3">Dialogs</h1>

<Card type={"filled"} class="mb-3 p-5">
    <div class="flex flex-row justify-start items-center gap-2 flex-wrap">
        <Button
            type={"filled"}
            icon={mdiForumPlusOutline}
            label={"Open Dialog"}
            onclick={() => { dialog.open = true }}
        />
        <Button
            type={"filled"}
            label={"Show Leggy"}
            onclick={() => { dialog_leg.open = true }}
        />
        <Button
            type={"filled"}
            label={"Dialog with other elements"}
            onclick={() => { dialog_list.open = true }}
        />
    </div>

    <Dialog
        heading={dialog.heading}
        supporting={dialog.supporting}
        open={dialog.open}
        actions={dialog.actions}
    />
    <Dialog
        heading={dialog_leg.heading}
        supporting={dialog_leg.supporting}
        icon={dialog_leg.icon}
        open={dialog_leg.open}
        actions={dialog_leg.actions}
    >
        <img src="/leg.jpg" alt="" class="h-80 mx-auto" />
    </Dialog>
    <Dialog
            icon={dialog_list.icon}
            heading={"Channel Members"}
            supporting={dialog_list.supporting}
            open={dialog_list.open}
    >
        <p class="text-m3-on-surface text-m3-size-body-large">Administrators</p>
        <ul class="flex flex-col -mx-4">
            <li>
                <List>
                    {#snippet leading()}
                        <Avatar img={""} fallback={"Y"} />
                    {/snippet}
                    <ListLabel type={"headline"} class="text-m3-on-surface">You</ListLabel>
                    <ListLabel type={"supporting"} class="text-m3-on-surface-variant">Owner</ListLabel>
                    {#snippet trailing()}
                        <SvgIcon type="mdi" path={mdiShieldCrownOutline} size={24} />
                    {/snippet}
                </List>
            </li>
            <li>
                <List>
                    {#snippet leading()}
                        <Avatar img={"/goob.png"} fallback={"G"} />
                    {/snippet}
                    <ListLabel type={"headline"} class="text-m3-on-surface">Goober</ListLabel>
                    <ListLabel type={"supporting"} class="text-m3-on-surface-variant">Administrator</ListLabel>
                    {#snippet trailing()}
                        <SvgIcon type="mdi" path={mdiShieldAccountOutline} size={24} />
                    {/snippet}
                </List>
            </li>
        </ul>

        <p class="text-m3-on-surface text-m3-size-body-large">Users</p>
        <ul class="flex flex-col -mx-4">
            <li>
                <List onclick={() => { dialog_user.open = true }}>
                    {#snippet leading()}
                        <Avatar img={""} fallback={"GU"} />
                    {/snippet}
                    <ListLabel type={"headline"} class="text-m3-on-surface">Guest User</ListLabel>
                    {#snippet trailing()}
                        <SvgIcon type="mdi" path={mdiMenuRight} size={24} />
                    {/snippet}
                </List>
            </li>
            <li>
                <List onclick={() => { dialog_user.open = true }}>
                    {#snippet leading()}
                        <Avatar img={""} fallback={"GU"} />
                    {/snippet}
                    <ListLabel type={"headline"} class="text-m3-on-surface">Guest User</ListLabel>
                    {#snippet trailing()}
                        <SvgIcon type="mdi" path={mdiMenuRight} size={24} />
                    {/snippet}
                </List>
            </li>
            <li>
                <List onclick={() => { dialog_user.open = true }}>
                    {#snippet leading()}
                        <Avatar img={""} fallback={"GU"} />
                    {/snippet}
                    <ListLabel type={"headline"} class="text-m3-on-surface">Guest User</ListLabel>
                    {#snippet trailing()}
                        <SvgIcon type="mdi" path={mdiMenuRight} size={24} />
                    {/snippet}
                </List>
            </li>
            <li>
                <List onclick={() => { dialog_user.open = true }}>
                    {#snippet leading()}
                        <Avatar img={""} fallback={"GU"} />
                    {/snippet}
                    <ListLabel type={"headline"} class="text-m3-on-surface">Guest User</ListLabel>
                    {#snippet trailing()}
                        <SvgIcon type="mdi" path={mdiMenuRight} size={24} />
                    {/snippet}
                </List>
            </li>
        </ul>
    </Dialog>
    <Dialog
        supporting={dialog_user.supporting}
        open={dialog_user.open}
    />
</Card>
