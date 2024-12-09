<script lang="ts">
    import type { Snippet } from "svelte";

    interface Props {
        leading?: Snippet,
        children: Snippet,
        trailing?: Snippet,
        link?: string;
        onclick?: () => void;
    }

    let {
        link,
        onclick,
        leading,
        children,
        trailing,
    }: Props = $props();
</script>

{#snippet list()}
    {#if leading}
        <div class="pl-4 flex justify-center items-center text-m3-on-surface-variant">
            {@render leading()}
        </div>
    {/if}
    <div class="px-4 py-[12px] flex flex-col w-full justify-center items-start text-left">
        {@render children()}
    </div>
    {#if trailing}
        <div class="pr-4 flex justify-center items-center text-m3-on-surface-variant">
            {@render trailing()}
        </div>
    {/if}
{/snippet}

{#if link}
    <a href={link} class="flex flex-row min-h-[72px] w-full">
        {@render list()}
    </a>
{:else if onclick}
    <button class="flex flex-row min-h-[72px] w-full" onclick={onclick}>
        {@render list()}
    </button>
{:else}
    <div class="flex flex-row min-h-[72px] w-full">
        {@render list()}
    </div>
{/if}
