<script>
    import SideBar from "$lib/sidebar.svelte"
    import Button from "$lib/button.svelte"
    import Link from "$lib/link.svelte"
    
    let { children } = $props();
</script>

<div class="animate-fadein animate-scrollup md:h-screen flex flex-col items-center justify-center p-5">
    <div class="bg-gradient-to-tl from-amber-400 to-fuchsia-800 rounded-lg shadow-2xl max-w-5xl w-full md:h-[650px] text-white md:overflow-hidden">
        <div class="p-2 grid grid-cols-3 gap-0 w-full md:h-full">
            <SideBar>
                <Button href="/">👤 About me</Button>
                <Button href="/projects">🛠️ Projects</Button>
                <div class="hidden md:block my-auto"></div>
                <Button href="https://github.com/UselessGhost">🐙 Github</Button>
            </SideBar>

            <div class="rounded col-span-3 md:col-span-2 p-5 md:h-full md:overflow-auto bg-gradient-to-b from-black/10 to-black/20 border border-black/10 shadow-inner flex">
                {@render children()}
            </div>
            
        </div>
    </div>

    <div class="text-xs text-white opacity-75 p-3">This page was rendered with <Link href="https://svelte.dev/">SvelteKit</Link>, <Link href="https://tailwindcss.com/">Tailwind CSS</Link> and a bit of magic. ✨</div>
</div>