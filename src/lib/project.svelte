<script>
    let { children, image, url, tools, name, description } = $props();
</script>

<div class="shrink-0 px-8 w-full h-full bg-cover bg-center" style="background-image: url('{image}')">
    <div class="p-5 w-full bg-black/50 drop-shadow">
        <a class="text-lg font-bold {url !== null ? "underline" : ""}" href={ url } target="_blank">{ name }</a>
        <h2 class="text-xs text-white/50 mb-1">{ tools }</h2>

        <p class="text-sm">{ description }</p>
   </div>
</div>