<script lang="ts">
    import Card from "$lib/components/cards/Card.svelte";
    import Toggle from "$lib/components/toggles/Toggle.svelte";

    const toggle = {
        label: "Example toggle",
        checked: true,
    }
</script>

<h1 class="text-m3-size-headline-large mb-3">Toggles</h1>

<div class="mb-3">
    <Card style={"filled"}>
        <div class="p-5">
            <Toggle label={toggle.label} checked={toggle.checked} />
            <Toggle label={toggle.label} checked={toggle.checked} />
            <Toggle label={toggle.label} checked={toggle.checked} />
            <Toggle label={toggle.label} checked={toggle.checked} />
            <Toggle label={toggle.label} checked={toggle.checked} />
        </div>
    </Card>
</div>
