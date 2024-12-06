<script lang="ts">
    import type { Snippet } from 'svelte';
    import { fade, scale } from "svelte/transition";
    import { quintOut } from "svelte/easing";
    import { createDialog } from "@melt-ui/svelte";
    import SvgIcon from "@jamescoyle/svelte-icon";

    import Button from "$lib/components/Button.svelte";
    import Divider from "$lib/components/Divider.svelte";

    interface Props {
        icon?: string;
        heading: string;
        subheading?: string;
        children?: Snippet;
        actions?: Array<{
            text: string;
            onclick: () => void;
            style?: "filled" | "tonal" | "outlined" | "text";
        }>;
        open: boolean;
    }

    let { open, icon, heading, subheading, actions, children }: Props = $props();

    const {
        elements: { overlay, content, title, description, portalled },
        states: { open: dialogOpen },
    } = createDialog({});

    $effect(() => { $dialogOpen = open; })
    $effect(() => { open = $dialogOpen; })
</script>

{#if $dialogOpen}
    <div class="" {...$portalled} use:portalled>
        <div class="fixed inset-0 z-50 bg-m3-scrim/30" {...$overlay} use:overlay transition:fade={{ easing: quintOut, duration: 300 }}></div>
        <div
                class="fixed left-1/2 top-1/2 z-50 -translate-x-1/2 -translate-y-1/2 rounded-3xl bg-m3-surface-container-high w-[500px] max-w-[90vw] max-h-[90vh]"
                {...$content} use:content transition:scale={{ easing: quintOut, start: 0.9, duration: 300 }}
        >
            <div class="py-4 px-6 flex flex-col justify-center items-center gap-3">
                {#if icon}<div class="text-m3-secondary"><SvgIcon type="mdi" path={icon} /></div>{/if}
                <h2 class="text-lg text-center text-m3-on-surface" {...$title} use:title>{ heading }</h2>
                {#if subheading}<p class="text-sm text-m3-on-surface-variant">{subheading}</p>{/if}
            </div>
            {#if children}
                <div class="px-6">
                    <Divider orientation="horizontal" />
                    <div class="overflow-y-auto max-h-96 py-6 text-stone-800" {...$description} use:description>
                        {@render children?.()}
                    </div>
                    <Divider orientation="horizontal" />
                </div>
            {/if}
            <div class="py-4 px-6 flex justify-end items-center gap-1" class:pt-0={!children}>
                {#if actions && actions.length > 0}
                    {#each actions as { text, onclick, style }}
                        <Button style={style ?? "text"} text={text} onclick={onclick} />
                    {/each}
                {:else}
                    <Button style={"text"} text="Close" onclick={() => open = false} />
                {/if}
            </div>
        </div>
    </div>
{/if}
