# Bruno Explore catalog

An [OpenCollection](https://www.opencollection.com) API Catalog of every public
Bruno collection found on GitHub. It is the same catalog the public catalog
site renders, kept as a git repository instead of a generated JSON file.

This is an **aggregate** catalog (`scope: aggregate`): entries come from many
owners, and each entry carries its own namespace (`github.com/<owner>`). An org
catalog such as
[bruno-collections-catalog](https://github.com/abhishek-bruno/bruno-collections-catalog)
lists one owner.

## Layout

```
catalog.yml          name, scope (aggregate), logo, links, contact, tag vocabulary
<category>/folder.yml  folder name, order and the category tag its entries inherit
<category>/<name>.yml  one entry per collection or workspace
other/               entries without a category
```

An entry holds only authored fields: listing name, namespace, type, tags,
order, `featured`, and one `source`. Descriptions, versions and repository
details are read from the collection itself. Stars and other observed numbers
are not in this repo; a host publishes them in a separate observed file.

## Where it comes from

Generated from the scraper's data with `node indexer/git-catalog.mjs <dir>` in
bruno-public-catalog. `featured: true` marks the entries the curation rules
picked. Once the public registry is live, organizations claim their namespace
and manage their own entries; this file becomes the registry's public catalog.

## Use it

- Open it on the catalog site: Catalog button in the header, paste this repo's URL.
- Bundle it into one file: `opencollection-parser bundle . --out catalog.bundled.yml`
