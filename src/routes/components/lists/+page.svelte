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
                {#snippet leading()}
                    <SvgIcon type="mdi" path={mdiWifi} size={24} />
                {/snippet}
                {#snippet body()}
                    <ListLabel type={"headline"} text={"Connections"} />
                    <ListLabel type={"supporting"} text={"Wifi, Bluetooth and Hotspots"} />
                {/snippet}
            </List>
        </li>
        <li>
            <List>
                {#snippet leading()}
                    <SvgIcon type="mdi" path={mdiBrightness6} size={24} />
                {/snippet}
                {#snippet body()}
                    <ListLabel type={"headline"} text={"Display"} />
                    <ListLabel type={"supporting"} text={"Brightness, Themes"} />
                {/snippet}
            </List>
        </li>
        <li>
            <List>
                {#snippet leading()}
                    <SvgIcon type="mdi" path={mdiSd} size={24} />
                {/snippet}
                {#snippet body()}
                    <ListLabel type={"headline"} text={"Storage"} />
                    <ListLabel type={"supporting"} text={"58% used - 53.81 GB free"} />
                {/snippet}
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
                    <div class="bg-m3-tertiary text-m3-on-tertiary w-[40px] h-[40px] flex justify-center items-center rounded-full text-m3-size-body-large">
                        B
                    </div>
                {/snippet}
                {#snippet body()}
                    <ListLabel type={"headline"} text={"Becca"} />
                {/snippet}
                {#snippet trailing()}
                    <SvgIcon type="mdi" path={mdiPhoneOutline} size={24} />
                {/snippet}
            </List>
        </li>
        <li>
            <List>
                {#snippet leading()}
                    <div class="bg-m3-tertiary text-m3-on-tertiary w-[40px] h-[40px] flex justify-center items-center rounded-full text-m3-size-body-large">
                        M
                    </div>
                    {/snippet}
                {#snippet body()}
                    <ListLabel type={"headline"} text={"Michael"} />
                {/snippet}
                {#snippet trailing()}
                    <SvgIcon type="mdi" path={mdiPhoneOutline} size={24} />
                {/snippet}
            </List>
        </li>
        <li>
            <List>
                {#snippet leading()}
                    <div class="bg-m3-tertiary text-m3-on-tertiary w-[40px] h-[40px] flex justify-center items-center rounded-full text-m3-size-body-large">
                        K
                    </div>
                {/snippet}
                {#snippet body()}
                    <ListLabel type={"headline"} text={"Kris"} />
                {/snippet}
                {#snippet trailing()}
                    <SvgIcon type="mdi" path={mdiPhoneOutline} size={24} />
                {/snippet}
            </List>
        </li>
    </ul>
</Card>
