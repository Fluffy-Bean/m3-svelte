<script lang="ts">
    import {
        mdiBellBadgeOutline,
        mdiShape,
    } from "@mdi/js";
    
    import Card from "$lib/components/cards/Card.svelte";
    import Chips from "$lib/components/chips/Chips.svelte";

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

<h1 class="text-m3-size-headline-large mb-3">Chips</h1>

<Card type={"filled"} class="mb-3 p-5">
    <ul class="flex flex-row flex-wrap gap-1">
        {#each chips as { text, icon }}
            <li><Chips text={text} icon={icon ?? undefined} /></li>
        {/each}
    </ul>
</Card>
