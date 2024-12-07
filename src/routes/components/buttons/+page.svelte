<script lang="ts">
    import {
        mdiShape,
        mdiSend,
        mdiKey,
    } from "@mdi/js";

    import Button from "$lib/components/buttons/CommonButton.svelte";
    import Card from "$lib/components/cards/Card.svelte";
</script>

<h1 class="text-m3-size-headline-large mb-3">Buttons</h1>

<Card style={"filled"} class="mb-3 p-5">
    <div class="flex flex-row justify-start items-center gap-2 flex-wrap">
        <Button style={"filled"} icon_orientation="right" icon={mdiSend} text={"Send Message"} />
        <Button style={"tonal"} icon={mdiKey} text={"Enable VPN"} />
        <Button style={"outlined"} icon={mdiShape} />
        <Button style={"text"} text={"Learn More"} />
    </div>
</Card>
