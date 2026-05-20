<script>
    import projects from "$lib/projects"
    import Slider from "$lib/slider.svelte"
    import Project from "$lib/project.svelte"
</script>

<div class="animate-fadein drop-shadow flex flex-col gap-3 w-full h-full">
    <Slider>
        {#each projects as project}
            <Project {...project} />
        {/each}
    </Slider>
</div>