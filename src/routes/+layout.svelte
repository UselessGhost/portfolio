<script>	
	import './layout.css';
	//import favicon from '$lib/assets/favicon.svg';

	import Modal from "$lib/modal.svelte"

	let { children } = $props();
</script>

<svelte:head>
	<title>UselessGhost.me</title>
</svelte:head>

<Modal>
	{@render children?.()}
</Modal>