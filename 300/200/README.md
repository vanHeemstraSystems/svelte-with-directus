# 200 - Using Global Metadata and Settings

In your Directus project (e.g. https://directus-iqgn.onrender.com/) login (email: wvanheemstra@icloud.com as ADMIN_EMAIL, password: get it from https://dashboard.render.com/web/srv-cn0v14en7f5s73fbndkg/env as ADMIN_PASSWORD), navigate to Settings -> Data Model and create a new collection called global. Under the Singleton option, select 'Treat as a single object', as this collection will have just a single entry containing global website metadata.

Create two text input fields - one with the key of title and one description.

Navigate to the content module and enter the global collection. Collections will generally display a list of items, but as a singleton, it will launch directly into the one-item form. Enter information in the title and description field and hit save.

![global](https://github.com/vanHeemstraSystems/svelte-with-directus/assets/1499433/fd47b006-a239-41f4-8ee9-cda28521ecdf)

By default, new collections are not accessible to the public. Navigate to Settings -> Access Control -> Public and give Read access to the Global collection.