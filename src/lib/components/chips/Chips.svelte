<script lang="ts">
    import SvgIcon from "@jamescoyle/svelte-icon";

    interface Props {
        text: string;
        icon?: string;
    }

    let { text, icon }: Props = $props();
</script>

<div class="h-8 px-4 bg-transparent text-m3-on-surface border border-m3-outline rounded-lg flex justify-center items-center gap-1">
    {#if icon}<div class="-ml-2 text-m3-primary"><SvgIcon type="mdi" path={icon} size={18} /></div>{/if}
    <p class="text-m3-size-label-large">{ text }</p>
</div>
