# Versioning

To be forthright, I have no experience manually versioning code, so this tutorial will focus on using `git tags` for versioning. However, when I have seen others manually version code I often see mistakes and re-releases. It seems that using tagged versioning helps prevent some more typical mistakes. Furthermore, tagged versioning can also be a nice way to trigger CI for deployments.

## Versioning frameworks

1. EffVer (Effective): Effective versioning. How much effort does it take to upgrade to the new version? `super.major.minor` Where minor introduces little to no breaking changes, but can introduce features. Major is usually a shift in dependencies, API changes, and dropping old versions of things like Python. Super are the big API re-rewrites or foundational milestones.
2. SemVer (Semantic): Semantic versioning. `major.minor.bugfix`. Supposedly, projects out of beta should be at 1.0.0+ but this rarely happens. 
3. CalVer (Calendar): Use the date of release for the version. Version is self explanatory, but the type of release is certinaly not! 

## Versioning conventions (at least with Python)

Version with 3 decimals. `0.0.0`

In this order:
`0.0.1a0` first alpha, often used to get out "working tags" for users to test specific changes, used especially if projects work from dev branches.
`0.0.1b0` first beta. not as frequently used.
`0.0.1rc0` first release candidate. the final build for testing.
`0.0.1` full release

## Tagging with `git`

First, we'll use a `git` workflow to add tags with the understanding that this is what a repo host like GitHub is doing when a tag is created on the webpage. 

1. Checkout branch and/or commit intended for tagging. 
2. `git tag ... `
3. `git push`

## Tagging with GitHub

1. Click the tag-looking button or go to releases and "draft a new release"
2. Auto-generate release notes; the commits between last full-release and this release will 