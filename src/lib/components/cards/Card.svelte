<script lang="ts">
    import type { Snippet } from 'svelte';
    import { twMerge as tw } from "tailwind-merge";

    interface Props {
        style: "elevated" | "filled" | "outlined";
        children: Snippet;
        class?: string;
    }

    let { style, children, class: c = "" }: Props = $props();

    let styles = {
        elevated: "bg-m3-surface-container-low text-m3-on-surface-container-low shadow-sm shadow-m3-shadow",
        filled: "bg-m3-surface-container-highest text-m3-on-surface-container-highest",
        outlined: "border border-m3-outline-variant bg-m3-surface text-m3-on-surface",
    };
</script>

<div class={tw("rounded-2xl", styles[style], c)}>
    {@render children()}
</div>
