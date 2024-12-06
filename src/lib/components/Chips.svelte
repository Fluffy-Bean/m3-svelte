<script lang="ts">
    import SvgIcon from "@jamescoyle/svelte-icon";

    interface Props {
        chips: Array<{
            text: string;
            icon?: string;
        }>;
    }

    let { chips }: Props = $props();
</script>

<ul class="flex flex-row flex-wrap gap-1">
    {#each chips as { text, icon }}
        <li class="h-8 px-4 bg-transparent text-m3-on-surface border border-m3-outline rounded-lg flex justify-center items-center gap-1">
            {#if icon}<div class="-ml-2 text-m3-primary"><SvgIcon type="mdi" path={icon} size={18} /></div>{/if}
            <div>{ text }</div>
        </li>
    {/each}
</ul>
