<script lang="ts">
    import Card from "$lib/components/cards/Card.svelte";
    import Dropdown from "$lib/components/dropdowns/Dropdown.svelte";

    const accordions = [
        {
            id: "item-1",
            title: "Item 1",
            description: "Description 1",
        },
        {
            id: "item-2",
            title: "Item 2",
            description: "Description 2",
        },
        {
            id: "item-3",
            title: "Item 3",
            description: "Description 3",
        },
    ];
</script>

<h1 class="text-m3-size-headline-large mb-3">Accordions</h1>

<Card type={"filled"} class="mb-3 p-5">
    <Dropdown entries={accordions} />
</Card>
