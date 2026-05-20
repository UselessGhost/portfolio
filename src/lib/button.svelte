<script>
    let { children, href, onclick } = $props();
</script>

<a href={href} onclick={onclick} class="rounded border border-white/25 hover:bg-white/25 transition w-full p-1 shadow">
    {@render children?.()}
</a>