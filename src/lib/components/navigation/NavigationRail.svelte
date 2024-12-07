<script lang="ts">
    import type { Snippet } from 'svelte';
    import { mdiMenu } from "@mdi/js";
    import SvgIcon from "@jamescoyle/svelte-icon";
    import { twMerge as tw } from "tailwind-merge";

    interface Props {
        menu_callback?: () => void;
        children: Snippet;
        class?: string;
    }

    let { menu_callback, children, class: c = "" }: Props = $props();
</script>

<div class={tw("bg-m3-surface-container-high w-[80px] h-full py-[12px] flex flex-col justify-start items-center gap-[12px] list-none", c)} role="navigation">
    {#if menu_callback}
        <button class="w-[56px] min-h-[56px] h-[56px] flex justify-center items-center bg-transparent border-none text-m3-on-surface" onclick={menu_callback}>
            <SvgIcon type="mdi" path={mdiMenu} size={24} />
        </button>
    {/if}
    <div class="h-full flex flex-col justify-center items-center gap-[12px] list-none" role="navigation">
        {@render children()}
    </div>
</div>
