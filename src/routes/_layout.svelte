<script>
	import Nav from '../components/Nav.svelte';

	export let segment;
</script>

<style>
	main {
		margin: 40px;
		position: relative;
	}
</style>

<Nav {segment}/>

<main>
	<slot></slot>
</main>