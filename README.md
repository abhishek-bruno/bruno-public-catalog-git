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
catalog.yml                     name, scope (aggregate), logo, links, contact, tag vocabulary
github.com/<owner>/<name>.yml   one entry per collection or workspace
```

There is no `folder.yml`: owner folders pass nothing down to their entries.
Add one to a folder only when its entries should inherit tags or an order.

Folders follow ownership, not categories. An entry's owner never changes, so
files stay put when a collection is recategorized, each owner's entries can be
reviewed by that owner (one CODEOWNERS line per folder), and claiming or
opting out of a namespace is a change to one folder. Categories are entry tags,
defined in the `catalog.yml` vocabulary, and the catalog site groups by them.

An entry holds only authored fields: listing name, a one-line summary,
namespace, type, tags, order, `featured`, and where the collection lives:
`source.git` (the GitHub repo) and `source.url` (the store's scanned copy,
which the catalog site opens for Docs). Stars and other observed numbers are
not in this repo; a host publishes them in a separate observed file.

## Where it comes from

Generated from the scraper's data with `node indexer/git-catalog.mjs <dir>` in
bruno-public-catalog. `featured: true` marks the entries the curation rules
picked (the top three, pinned first). Once the public registry is live, organizations claim their namespace
and manage their own entries: their folder moves to the registry, and this
catalog becomes the registry's public catalog.

## Use it

- Open it on the catalog site: Catalog button in the header, paste this repo's URL.
- Bundle it into one file: `opencollection-parser bundle . --out catalog.bundled.yml`
