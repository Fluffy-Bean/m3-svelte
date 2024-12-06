<script lang="ts">
    interface Props {
        orientation: "horizontal" | "vertical";
    }
    let { orientation }: Props = $props();
</script>

{#if orientation === "horizontal"}
    <div class="bg-m3-outline-variant h-[1px] w-full"></div>
{:else if orientation === "vertical"}
    <div class="bg-m3-outline-variant h-full w-[1px]"></div>
{/if}
