<script lang="ts">
    import { twMerge as tw } from "tailwind-merge";

    interface Props {
        text: string,
        type: "headline" | "supporting",
        class?: string,
    }

    let { text, type, class: c = "" }: Props = $props();
</script>

{#if type === "headline"}
    <p class={tw("text-m3-on-surface text-m3-size-body-large", c)}>{ text }</p>
{:else if type === "supporting"}
    <p class={tw("text-m3-size-body-medium text-m3-on-surface-variant", c)}>{ text }</p>
{/if}
