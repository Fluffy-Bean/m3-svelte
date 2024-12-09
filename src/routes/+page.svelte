<script lang="ts">
    import { mdiAlertOutline } from "@mdi/js";
    import SvgIcon from "@jamescoyle/svelte-icon";

    import Card from "$lib/components/cards/Card.svelte";
    import List from "$lib/components/lists/List.svelte";
    import ListLabel from "$lib/components/lists/ListLabel.svelte";
</script>

<h1 class="text-m3-size-headline-large">M3 Svelte Components</h1>
<p class="text-m3-size-body-large mb-3">By Michał</p>

<Card type={"filled"} class="mb-3 bg-m3-error-container">
    <List>
        {#snippet leading()}
            <span class="text-m3-on-error-container"><SvgIcon type="mdi" path={mdiAlertOutline} size={24} /></span>
        {/snippet}
        <ListLabel class="text-m3-on-error-container" type="headline">
            Dragons, beware!
        </ListLabel>
        <ListLabel class="text-m3-on-error-container/80" type="supporting">
            This "Library" is still work-in-progress and very very far from complete
        </ListLabel>
    </List>
</Card>
