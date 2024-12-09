<script lang="ts">
    import {
        mdiShape,
        mdiSend,
        mdiKey,
    } from "@mdi/js";

    import Button from "$lib/components/buttons/Button.svelte";
    import Card from "$lib/components/cards/Card.svelte";
</script>

<h1 class="text-m3-size-headline-large mb-3">Buttons</h1>

<Card type={"filled"} class="mb-3 p-5">
    <div class="flex flex-row justify-start items-center gap-2 flex-wrap">
        <Button
            type={"filled"}
            orientation="right"
            icon={mdiSend}
            onclick={() => {}}
            label={"Send Message"}
        />
        <Button
            type={"tonal"}
            icon={mdiKey}
            onclick={() => {}}
            label={"Enable VPN"}
        />
        <Button
            type={"outlined"}
            icon={mdiShape}
            onclick={() => {}}
            label="Press meeee"
        />
        <Button
            type={"text"}
            onclick={() => {}}
            label={"Learn More"}
        />
    </div>
</Card>
