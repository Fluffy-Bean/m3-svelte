<script lang="ts">
	import '../app.css';
	let { children } = $props();
</script>

<!--
<nav class="bg-stone-100 fixed top-0 left-0 w-[450px] h-screen p-3.5 border-r border-stone-200 z-10">
    <h1 class="text-right text-xl">Smelly Components</h1>
    <hr class="h-[1px] bg-stone-200 border-none my-2">
    <ul class="text-right">
        <li><a href="/" class="hover:text-amber-700 py-2 block">Dropdowns</a></li>
        <li><a href="/" class="hover:text-amber-700 py-2 block">Toggles</a></li>
        <li><a href="/" class="hover:text-amber-700 py-2 block">Dialogs</a></li>
    </ul>
</nav>
-->
<main class="bg-m3-surface text-m3-on-surface min-h-screen relative">
    <div class="bg-m3-surface-container text-m3-on-surface-container p-3.5 sticky z-10 top-0">
        <h2>Header</h2>
    </div>
    <div class="p-[1px]">
        <div class="m-4">
            {@render children()}
        </div>
    </div>
</main>
