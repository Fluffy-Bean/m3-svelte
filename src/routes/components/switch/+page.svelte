<script lang="ts">
    import { mdiShieldAccountOutline, mdiMessageBadgeOutline } from "@mdi/js";
    import SvgIcon from "@jamescoyle/svelte-icon";

    import Card from "$lib/components/cards/Card.svelte";
    import Switch from "$lib/components/switches/Switch.svelte";
    import List from "$lib/components/lists/List.svelte";
    import ListLabel from "$lib/components/lists/ListLabel.svelte";

    let toggleProtectAccount = $state(false);
    let toggleMessageRequests = $state(true);
</script>

<h1 class="text-m3-size-headline-large mb-3">Switch</h1>

<Card type={"filled"} class="mb-3">
    <div class="p-5 pb-1">
        <p>An example usage of a switch could be in combination with the list element.</p>
    </div>
    <ul class="flex flex-col rounded py-2">
        <li>
            <List onclick={() => { toggleProtectAccount = !toggleProtectAccount }}>
                {#snippet leading()}
                    <SvgIcon type="mdi" path={mdiShieldAccountOutline} size={24} />
                {/snippet}
                <ListLabel type={"headline"}>
                    Protected posts
                </ListLabel>
                <ListLabel type={"supporting"}>
                    This will make your posts only viewable by people that follow you
                </ListLabel>
                {#snippet trailing()}
                    <Switch label={"Protect posts"} toggled={toggleProtectAccount} />
                {/snippet}
            </List>
        </li>
        <li>
            <List onclick={() => { toggleMessageRequests = !toggleMessageRequests }}>
                {#snippet leading()}
                    <SvgIcon type="mdi" path={mdiMessageBadgeOutline} size={24} />
                {/snippet}
                <ListLabel type={"headline"}>
                    Message Request
                </ListLabel>
                <ListLabel type={"supporting"}>
                    Allow people who dont follow you to send messages
                </ListLabel>
                {#snippet trailing()}
                    <Switch label={"Allow message requests"} toggled={toggleMessageRequests} />
                {/snippet}
            </List>
        </li>
    </ul>
</Card>
