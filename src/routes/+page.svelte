<script lang="ts">
    import { mdiAlertOutline } from "@mdi/js";
    import SvgIcon from "@jamescoyle/svelte-icon";

    import Card from "$lib/components/cards/Card.svelte";
    import List from "$lib/components/lists/List.svelte";
    import ListLabel from "$lib/components/lists/ListLabel.svelte";
</script>

<h1 class="text-m3-size-headline-large">M3 Svelte Components</h1>
<p class="text-m3-size-body-large mb-3">By Michał</p>


<Card style={"filled"} class="mb-3 bg-m3-error-container">
    <List>
        {#snippet leading()}
            <span class="text-m3-on-error-container"><SvgIcon type="mdi" path={mdiAlertOutline} size={24} /></span>
        {/snippet}
        {#snippet body()}
            <ListLabel type="headline" text={"Dragons, beware!"} class="text-m3-on-error-container" />
            <ListLabel type="supporting" text={"This \"Library\" is still work-in-progress and very very far from complete"} class="text-m3-on-error-container/80" />
        {/snippet}
    </List>
</Card>
