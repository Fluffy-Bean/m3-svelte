<script lang="ts">
    import {
        mdiWifi,
        mdiBrightness6,
        mdiSd,
        mdiPhoneOutline,
    } from "@mdi/js";
    import SvgIcon from "@jamescoyle/svelte-icon";

    import Card from "$lib/components/cards/Card.svelte";
    import List from "$lib/components/lists/List.svelte";
    import ListLabel from "$lib/components/lists/ListLabel.svelte";
</script>

<h1 class="text-m3-size-headline-large mb-3">Lists</h1>

<Card style={"filled"} class="mb-3">
    <div class="p-5 pb-1">
        <h2 class="text-m3-size-headline-small">Settings</h2>
        <p class="text-m3-size-body-medium">Example settings list</p>
    </div>
    <ul class="flex flex-col rounded py-2">
        <li>
            <List>
                {#snippet leading()}<SvgIcon type="mdi" path={mdiWifi} size={24} />{/snippet}
                <ListLabel type={"headline"}>Connections</ListLabel>
                <ListLabel type={"supporting"}>Wifi, Bluetooth and Hotspots</ListLabel>
            </List>
        </li>
        <li>
            <List>
                {#snippet leading()}<SvgIcon type="mdi" path={mdiBrightness6} size={24} />{/snippet}
                <ListLabel type={"headline"}>Display</ListLabel>
                <ListLabel type={"supporting"}>Brightness, Themes</ListLabel>
            </List>
        </li>
        <li>
            <List>
                {#snippet leading()}<SvgIcon type="mdi" path={mdiSd} size={24} />{/snippet}
                <ListLabel type={"headline"}>Storage</ListLabel>
                <ListLabel type={"supporting"}>58% used - 53.81 GB free</ListLabel>
            </List>
        </li>
    </ul>
</Card>

<Card style={"filled"} class="mb-3">
    <div class="p-5 pb-1">
        <h2 class="text-m3-size-headline-small">Contacts</h2>
    </div>
    <ul class="flex flex-col rounded py-2">
        <li>
            <List>
                {#snippet leading()}
                    <div class="bg-m3-tertiary text-m3-on-tertiary w-[40px] h-[40px] flex justify-center items-center rounded-full text-m3-size-body-large">B</div>
                {/snippet}
                <ListLabel type={"headline"}>Becca</ListLabel>
                {#snippet trailing()}
                    <SvgIcon type="mdi" path={mdiPhoneOutline} size={24} />
                {/snippet}
            </List>
        </li>
        <li>
            <List>
                {#snippet leading()}
                    <div class="bg-m3-tertiary text-m3-on-tertiary w-[40px] h-[40px] flex justify-center items-center rounded-full text-m3-size-body-large">M</div>
                {/snippet}
                <ListLabel type={"headline"}>Michael</ListLabel>
                {#snippet trailing()}
                    <SvgIcon type="mdi" path={mdiPhoneOutline} size={24} />
                {/snippet}
            </List>
        </li>
        <li>
            <List>
                {#snippet leading()}
                    <div class="bg-m3-tertiary text-m3-on-tertiary w-[40px] h-[40px] flex justify-center items-center rounded-full text-m3-size-body-large">K</div>
                {/snippet}
                <ListLabel type={"headline"}>Kris</ListLabel>
                {#snippet trailing()}
                    <SvgIcon type="mdi" path={mdiPhoneOutline} size={24} />
                {/snippet}
            </List>
        </li>
    </ul>
</Card>
