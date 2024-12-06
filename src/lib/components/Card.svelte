<script lang="ts">
    import type { Snippet } from 'svelte';

    interface Props {
        style: "elevated" | "filled" | "outlined";
        children: Snippet;
    }

    let { style, children }: Props = $props();
</script>

<div class="rounded-2xl bg-m3-surface-container text-m3-on-surface-container">
    {@render children()}
</div>
