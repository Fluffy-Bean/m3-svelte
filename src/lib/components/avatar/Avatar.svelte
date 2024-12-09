<script lang="ts">
    import { createAvatar } from '@melt-ui/svelte';
    import { twMerge as tw } from "tailwind-merge";


    interface Props {
        img: string;
        fallback: string;
        delay?: number;
        class?: string;
    }

    let {
        img,
        fallback: fb,
        delay = 0,
        class: c,
    }: Props = $props();

    const {
        elements: { image, fallback },
        states: { loadingStatus: status },
    } = createAvatar({
        src: img,
        delayMs: delay,
    });
</script>

<div
    class={tw("flex w-[40px] h-[40px] items-center justify-center rounded-full overflow-hidden bg-m3-primary", c)}
    class:bg-transparent={$status === "loaded"}
>
    <img
        alt="Avatar"
        class="h-full w-full"
        {...$image} use:image
    />
    <span
        class="text-m3-on-primary text-m3-size-body-large"
        {...$fallback} use:fallback
    >
        {fb}
    </span>
</div>
