# 100 - Create a Wrapper for the SDK

We now need to setup the Directus SDK and make it accessible globally. In order to make the best use of SvelteKit's Server Side Rendering, we will need to use SvelteKit's own [fetch implementation](https://kit.svelte.dev/docs/load#making-fetch-requests). Create a new file ```directus.js``` inside of the ```src/libs``` directory:

```
import { createDirectus, rest } from '@directus/sdk';
import { readItems, readItem, updateItem, updateUser, createItem, deleteItem } from '@directus/sdk';
import { PUBLIC_APIURL } from '$env/static/public';

function getDirectusInstance(fetch) {
  	const options = fetch ? { globals: { fetch } } : {};
	const directus = createDirectus(PUBLIC_APIURL, options ).with(rest());
	return directus;
}

export default getDirectusInstance;
```

frontend/src/lib/directus.js

In order to make this work we also need to create a ```hooks.server.js``` file with the following content in the root directory. It makes sure that the required headers for fetching JavaScript content are returned by the SvelteKit Server:

```
export async function handle({ event, resolve }) {
	return await resolve(event, {
		filterSerializedResponseHeaders: (key, value) => {
			return key.toLowerCase() === 'content-type';
		},
	});
}
```

frontend/hooks.server.js

**NOTE**: Directus HTTP Requests. Theoretically you could also make HTTP requests to your Directus server endpoint directly via SvelteKit's ```fetch``` implementation. However the Directus SDK offers some [nice additional features](https://docs.directus.io/guides/sdk/getting-started).

Also create the environment variable inside a ```.env``` file in the root directory. Ensure your API URL is correct when initializing the Directus JavaScript SDK.

```
PUBLIC_APIURL = 'https://directus.example.com';
```

frontend/.env


