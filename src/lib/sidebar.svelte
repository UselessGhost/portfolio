<script>
    import Header from "$lib/header.svelte";
    let { children } = $props();
</script>

<div class="p-5 flex flex-col col-span-3 md:col-span-1 overflow-auto">
    <Header />

    <div class="h-full mb-1 flex flex-col gap-1 md:text-left text-center">
        {@render children?.()}
    </div>
</div>