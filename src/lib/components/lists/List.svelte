<script lang="ts">
    import type { Snippet } from "svelte";

    interface Props {
        link?: string;
        leading?: Snippet,
        body: Snippet,
        trailing?: Snippet,
    }

    let { link, leading, body, trailing }: Props = $props();
</script>

{#snippet list()}
    {#if leading}
        <div class="pl-4 flex justify-center items-center text-m3-on-surface-variant">
            {@render leading()}
        </div>
    {/if}
    <div class="px-4 py-[12px] flex flex-col w-full justify-center items-start">
        {@render body()}
    </div>
    {#if trailing}
        <div class="pr-4 flex justify-center items-center text-m3-on-surface-variant">
            {@render trailing()}
        </div>
    {/if}
{/snippet}

{#if link}
    <a href={link} class="flex flex-row min-h-[72px]">
        {@render list()}
    </a>
{:else}
    <div class="flex flex-row min-h-[72px]">
        {@render list()}
    </div>
{/if}
