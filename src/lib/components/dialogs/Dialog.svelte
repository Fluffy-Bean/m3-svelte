<script lang="ts">
    import type { Snippet } from 'svelte';
    import { fade, scale } from "svelte/transition";
    import { quintOut } from "svelte/easing";
    import { createDialog } from "@melt-ui/svelte";
    import SvgIcon from "@jamescoyle/svelte-icon";

    import Button from "$lib/components/buttons/Button.svelte";

    interface Props {
        icon?: string;
        heading?: string;
        supporting: string;
        children?: Snippet;
        actions?: Array<{
            text: string;
            onclick: () => void;
            style?: "filled" | "tonal" | "outlined" | "text";
        }>;
        open: boolean;
    }

    let {
        open,
        icon,
        heading,
        supporting,
        actions,
        children,
    }: Props = $props();

    const {
        elements: { overlay, content, description, portalled },
        states: { open: dialogOpen },
    } = createDialog({});

    $effect(() => { $dialogOpen = open; })
    $effect(() => { open = $dialogOpen; })
</script>

{#if $dialogOpen}
    <div {...$portalled} use:portalled>
        <div class="fixed inset-0 z-50 bg-m3-scrim/30" {...$overlay} use:overlay transition:fade={{ easing: quintOut, duration: 300 }}></div>
        <div
                class="fixed left-1/2 top-1/2 z-50 -translate-x-1/2 -translate-y-1/2 rounded-3xl bg-m3-surface-container-high w-[500px] max-w-[90vw] max-h-[90vh]"
                {...$content} use:content transition:scale={{ easing: quintOut, start: 0.9, duration: 300 }}
        >
            <div
                    class="py-4 px-6 flex flex-col justify-center gap-2.5"
                    class:items-center={ icon } class:text-center={ icon }
                    class:items-start:={ !icon } class:text-left:={ !icon }
            >
                {#if icon}<div class="text-m3-secondary"><SvgIcon type="mdi" path={icon} /></div>{/if}
                {#if heading}<h2 class="text-m3-size-headline-small text-m3-on-surface">{ heading }</h2>{/if}
                <p class="text-m3-size-body-medium text-m3-on-surface-variant text-left mr-auto">{ supporting }</p>
            </div>
            {#if children}
                <div class="px-6 overflow-y-auto overflow-x-hidden max-h-96 text-m3-on-surface" {...$description} use:description>
                    {@render children?.()}
                </div>
            {/if}
            <div class="py-4 px-6 flex justify-end items-center gap-1" class:pt-0={!children}>
                {#if actions && actions.length > 0}
                    {#each actions as { text, onclick, style }}
                        <Button
                            type={style ?? "text"}
                            label={text}
                            onclick={onclick}
                        />
                    {/each}
                {:else}
                    <Button
                        type={"text"}
                        label="Close"
                        onclick={() => { open = false }}
                    />
                {/if}
            </div>
        </div>
    </div>
{/if}
