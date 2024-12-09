<script lang="ts">
    import type { Snippet } from "svelte";
    import { twMerge as tw } from "tailwind-merge";

    interface Props {
        children: Snippet,
        type: "headline" | "supporting",
        class?: string,
    }

    let {
        children,
        type,
        class: c,
    }: Props = $props();
</script>

{#if type === "headline"}
    <p class={tw("text-m3-on-surface text-m3-size-body-large", c)}>{@render children()}</p>
{:else if type === "supporting"}
    <p class={tw("text-m3-size-body-medium text-m3-on-surface-variant", c)}>{@render children()}</p>
{/if}
