<script lang="ts">
    import { twMerge as tw } from "tailwind-merge";

    interface Props {
        orientation: "horizontal" | "vertical";
        class?: string;
    }

    let {
        orientation,
        class: c,
    }: Props = $props();
</script>

{#if orientation === "horizontal"}
    <div class={tw("bg-m3-outline-variant h-[1px] w-full", c)}></div>
{:else if orientation === "vertical"}
    <div class={tw("bg-m3-outline-variant h-full w-[1px]", c)}></div>
{/if}
