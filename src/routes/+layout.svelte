<script>
	import '../app.css';
	import Header from './header.svelte';
</script>

<Header />

<div class="grid min-h-screen place-content-center">
	<slot></slot>
</div>
