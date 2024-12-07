<script lang="ts">
    import Card from "$lib/components/cards/Card.svelte";
    import List from "$lib/components/lists/List.svelte";
</script>

<h1 class="text-m3-size-headline-large mb-3">Lists</h1>

<div class="mb-3">
    <Card style={"filled"}>
        <ul class="flex flex-col rounded py-2">
            <li><List headline="Headline" /></li>
            <li><List headline="Headline" supporting="Supporting Text" /></li>
            <li><List headline="Headline" /></li>
        </ul>
    </Card>
</div>
