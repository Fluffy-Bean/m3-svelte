<script lang="ts">
    import { createAccordion } from "@melt-ui/svelte";
    import { slide } from "svelte/transition";
    import SvgIcon from "@jamescoyle/svelte-icon";
    import { mdiMenuUp } from "@mdi/js";
    import Divider from "$lib/components/Divider.svelte";

    interface Props {
        entries: Array<{
            id: string;
            title: string;
            description: string;
        }>;
    }

    let { entries }: Props = $props();

    const {
        elements: { content, item, trigger, root },
        helpers: { isSelected },
    } = createAccordion({
        defaultValue: entries[0]?.id ?? null,
    });
</script>

<div {...root}>
    {#each entries as { id, title, description }}
        <div {...$item(id)} use:item>
            <button class="flex min-h-10 w-full flex-row items-center justify-start gap-1 bg-transparent rounded focus-visible:bg-amber-700/10 focus-visible:outline-none" {...$trigger(id)} use:trigger>
                <span class="text-sm">{title}</span>
                <span
                        class="ml-auto flex justify-center items-center transition-colors"
                        data-open={$isSelected(id)}
                >
                    <span class="transition-all data-[open=true]:-scale-y-[1]" data-open={$isSelected(id)}>
                        <SvgIcon type="mdi" path={mdiMenuUp} />
                    </span>
                </span>
            </button>
            {#if $isSelected(id)}
                <div {...$content(id)} use:content transition:slide={{ axis: "y", duration: 250 }}>
                    <div class="p-3.5 bg-black/5 rounded-lg">
                        {description}
                    </div>
                </div>
            {/if}
        </div>
    {/each}
</div>
