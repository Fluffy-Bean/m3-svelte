<script lang="ts">
    interface Props {
        label: string;
        checked?: boolean;
    }

    let { label, checked = false }: Props = $props();
</script>

<label class="flex w-full min-h-10 items-center cursor-pointer rounded focus-within:outline-none">
    <span class="text-sm">{label}</span>
    <input type="checkbox" class="sr-only peer" checked={checked} />
    <span class="
        peer ml-auto relative w-[52px] h-[32px] bg-m3-surface-container-highest rounded-full transition-all border-2 border-m3-outline
        peer-checked:bg-m3-primary peer-checked:border-m3-primary
        after:content-[''] after:absolute after:top-[6px] after:left-[6px] after:bg-m3-outline after:rounded-full after:h-[16px] after:w-[16px] after:transition-all
        peer-checked:after:left-[22px] peer-checked:after:top-[2px] peer-checked:after:bg-m3-on-primary peer-checked:after:h-[24px] peer-checked:after:w-[24px]
        "
    ></span>
</label>
