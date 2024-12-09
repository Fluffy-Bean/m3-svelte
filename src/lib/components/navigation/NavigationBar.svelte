<script lang="ts">
    import type { Snippet } from 'svelte';
    import { twMerge as tw } from "tailwind-merge";

    interface Props {
        children: Snippet;
        class?: string;
    }

    let {
        children,
        class: c,
    }: Props = $props();
</script>

<div class={tw("bg-m3-surface w-full h-[80px] pt-[12px] pb-[16px] flex flex-row justify-evenly items-center gap-[2px] list-none", c)} role="navigation">
    {@render children()}
</div>
