<script lang="ts">
    import SvgIcon from "@jamescoyle/svelte-icon";

    interface Props {
        icon: string;
        label: string;
        link: string;
        selected: boolean;
    }

    let {
        icon,
        label,
        link,
        selected,
    }: Props = $props();
</script>

<a class="w-full flex flex-col justify-center items-center gap-[4px]" href={link}>
        <span
            class="relative h-[32px] w-[32px] rounded-full flex items-center justify-center"
            class:bg-m3-secondary-container={selected}
            class:text-m3-on-secondary-container={selected}
            class:!w-[64px]={selected}
            class:transition-all={selected}
            class:bg-m3-transparent={!selected}
            class:text-m3-on-surface-variant={!selected}
        >
            <SvgIcon type="mdi" path={icon} size={24} />
        </span>
    <span
        class="text-m3-size-label-small"
        class:text-m3-on-surface={selected}
        class:text-m3-on-surface-variant={!selected}
    >
        {label}
    </span>
</a>
