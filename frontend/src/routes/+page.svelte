<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>

<script>
	/** @type {import('./$types').PageData} */
	export let data;
	console.log("data:", data);
</script>

<h1>{data.global.title}</h1>
<p>{data.global.description}</p>
