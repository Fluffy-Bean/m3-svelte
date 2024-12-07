<script lang="ts">
    import { createSwitch } from '@melt-ui/svelte';

    interface Props {
        label: string;
        toggled: boolean;
    }

    let { label, toggled }: Props = $props();

    const {
        elements: { root, input },
        states: { checked },
    } = createSwitch({});

    $effect(() => { $checked = toggled; })
    $effect(() => { toggled = $checked; })
</script>

<div class="w-[52px] h-[32px]">
    <button
        class="
        group relative w-[52px] h-[32px] bg-m3-surface-container-highest rounded-full transition-all border-2 border-m3-outline
        data-[state=checked]:bg-m3-primary data-[state=checked]:border-m3-primary
        "
        aria-labelledby={label}
        {...$root} use:root
    >
        <span
            class="
            absolute top-[6px] left-[6px] bg-m3-outline rounded-full h-[16px] w-[16px] transition-all
            data-[state=checked]:left-[22px] data-[state=checked]:top-[2px] data-[state=checked]:bg-m3-on-primary data-[state=checked]:h-[24px] data-[state=checked]:w-[24px]
            "
            data-state={$checked ? "checked" : "unchecked"}
        ></span>
    </button>
    <input {...$input} use:input />
</div>
