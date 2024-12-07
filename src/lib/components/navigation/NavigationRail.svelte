<script lang="ts">
    import type { Snippet } from 'svelte';
    import { mdiMenu } from "@mdi/js";
    import SvgIcon from "@jamescoyle/svelte-icon";

    interface Props {
        menu_callback?: () => void;
        children: Snippet;
    }

    let { menu_callback, children }: Props = $props();
</script>

<div class="w-[80px] h-full py-[12px] flex flex-col justify-start items-center gap-[12px]">
    {#if menu_callback}
        <button class="w-[56px] min-h-[56px] h-[56px] flex justify-center items-center bg-transparent border-none" onclick={menu_callback}>
            <SvgIcon type="mdi" path={mdiMenu} size={24} />
        </button>
    {/if}
    <ul class="h-full flex flex-col justify-center items-center gap-[12px]">
        {@render children()}
    </ul>
</div>
