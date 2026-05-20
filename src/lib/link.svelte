<script>
    let { href, children } = $props();
</script>

<a href={ href } class="text-blue-600 dark:text-blue-500 hover:underline">{@render children?.()}</a>