<script lang="ts">
    import SvgIcon from "@jamescoyle/svelte-icon";
    import { twMerge as tw } from "tailwind-merge";

    interface Props {
        type: "filled" | "tonal" | "outlined" | "text";
        orientation?: "left" | "right";
        label: string;
        icon?: string;
        onclick: () => void;
        class?: string;
    }

    let {
        type,
        orientation,
        label,
        icon,
        class: c,
        onclick,
    }: Props = $props();

    let styles = {
        filled: "bg-m3-primary text-m3-on-primary hover:bg-m3-primary focus:bg-m3-primary active:bg-m3-primary hover:shadow focus:shadow-none active:shadow-none",
        tonal: "bg-m3-secondary-container text-m3-on-secondary-container hover:shadow focus:shadow-none active:shadow-none",
        outlined: "bg-transparent border border-m3-outline text-m3-primary hover:bg-m3-primary/10 focus:bg-m3-primary/10 focus:border-m3-primary active:bg-m3-primary/15",
        text: "bg-transparent text-m3-primary hover:bg-m3-primary/10 focus:bg-m3-primary/10 active:bg-m3-primary/15",
    };
</script>

<button
    class={tw("flex justify-center items-center gap-4 h-10 px-6 rounded-full shadow-m3-shadow focus:outline-none", styles[type], c)}
    class:flex-row={orientation === "left"}
    class:flex-row-reverse={orientation === "right"}
    onclick={onclick}
>
    {#if icon}<div class="-mx-2"><SvgIcon type="mdi" path={icon} size={18} /></div>{/if}
    <span class="text-center text-m3-size-label-large">{label}</span>
</button>
