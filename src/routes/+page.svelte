<script>
	import data from '../data/data.json';
    import 'virtual:uno.css'
	import Navbar from '$lib/components/navbar.svelte';
</script>

<Navbar />

<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>

<p class="text-4xl">Name: {data.name}</p>
<p>Age: {data.age}</p>
<p>City: {data.city}</p>
