# Blog Folder Structure

## How Blog Content Is Organized

Each cluster gets its own subfolder:

```
04-BLOG/
  cluster-index.md
  [cluster-slug]/
    [post-slug]/
      draft.md
      final.md
      metadata.json
```

## Rules

- Create the cluster subfolder only after it is approved in `04-BLOG/cluster-index.md`
- Create the post subfolder only after the post is approved in the topical map
- Do not name folders with spaces - use hyphens
- draft.md is the working document; final.md is the approved-to-publish version
- metadata.json must be filled in before draft.md is started

## When a Post Is Published

1. Update metadata.json: set status to "published", add live URL, add publish_date
2. Update topical-map.csv with the live URL
3. Update intent-log.md to confirm the intent is now owned
4. Update all linked posts' metadata.json (internal_links_in field)
5. Create derivative-plan.md in 06-REPURPOSING/[post-slug]/
