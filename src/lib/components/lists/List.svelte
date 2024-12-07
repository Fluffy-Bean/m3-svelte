<script lang="ts">
    import { mdiAccountOutline, mdiDragHorizontalVariant } from "@mdi/js";
    import SvgIcon from "@jamescoyle/svelte-icon";

    interface Props {
        headline: string;
        supporting?: string;
    }

    let { headline, supporting }: Props = $props();
</script>

<div class="flex flex-row h-[56px]">
    <div class="pl-4 flex justify-center items-center text-m3-on-surface-variant">
        <SvgIcon type="mdi" path={mdiAccountOutline} size={24} />
    </div>

    <div class="px-4 flex flex-col w-full justify-center items-start">
        <p class="text-m3-on-surface text-m3-size-body-large">{ headline }</p>
        {#if supporting}<p class="text-m3-size-body-medium text-m3-on-surface-variant">{ supporting }</p>{/if}
    </div>

    <div class="pr-4 flex justify-center items-center text-m3-on-surface-variant">
        <SvgIcon type="mdi" path={mdiDragHorizontalVariant} size={24} />
    </div>
</div>
