# 300 - Prepare SvelteKit to use Directus

Create a new file called ```+page.js``` in the directory ```frontend/src/routes/```. This file's load function will be responsible to fetch the data on the client and on the server during Server Side Rendering.

```
/** @type {import('./$types').PageLoad} */
import getDirectusInstance from '$lib/directus';
import { readItems } from '@directus/sdk';
export async function load({ fetch }) {
	const directus = getDirectusInstance(fetch);
	return {
		global: await directus.request(readItems('global')),
	};
}
```

frontend/src/routes/+page.js

Update the file ```+page.svelte``` in the directory ```frontend/src/routes/``` as follows:

```
<script>
	/** @type {import('./$types').PageData} */
	export let data;
</script>

<h1>{data.global.title}</h1>
<p>{data.global.description}</p>
```

frontend/src/routes/+page.svelte

Refresh your browser. You should see data from your Directus Global collection in your page.