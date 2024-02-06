# 200 - Using Global Metadata and Settings

In your Directus project, navigate to Settings -> Data Model and create a new collection called global. Under the Singleton option, select 'Treat as a single object', as this collection will have just a single entry containing global website metadata.

Create two text input fields - one with the key of title and one description.

Navigate to the content module and enter the global collection. Collections will generally display a list of items, but as a singleton, it will launch directly into the one-item form. Enter information in the title and description field and hit save.