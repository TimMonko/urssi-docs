# Making your docs shine :star: :rainbow:

This is a [great reference guide](https://squidfunk.github.io/mkdocs-material/reference/) to many advanced features of Mkdocs, but doesn't necessarily explain things well.

## Code blocks :computer:

Code blocks can be rendered with a few mkdocs extensions. Add to your `mkdocs.yml`:

```yaml
markdown_extensions:
  - pymdownx.superfences
  - pymdownx.highlight
  - pymdownx.inlinehilite
```

Then you can use code blocks in your markdown like this:

````raw
```python
def hello_world():
    print("Hello, world!")
```
````

Displays as

```python
def hello_world():
    print("Hello, world!")
```

## Emojis :cat:

Emojis can can be added with the mkdocs markdown extension `pymdownx.emoji`. To use it, add the following to your `mkdocs.yml`:

```yaml
markdown_extensions:
  - pymdownx.emoji:
      emoji_index: !!python/name:material.extensions.emoji.twemoji
      emoji_generator: !!python/name:material.extensions.emoji.to_svg
```

Then you can use emojis in your markdown like `:cat:` or `:rainbow:`.

## Admonitions :exclamation: :exclamation: :exclamation:

Admonitions are a general part of doc making libraries. To use [mkdocs style admonitions](https://squidfunk.github.io/mkdocs-material/reference/admonitions/), add the following to your `mkdocs.yml`:

```yaml
markdown_extensions:
  - admonition
```

Then you can use admonitions in your markdown like this:

````raw
!!! note "Note Title"
    This is a note admonition. It can contain **bold text**, *italic text*, and even [links](https://www.example.com).
````

Displays as
!!! note "Note Title"
    This is a note admonition. It can contain **bold text**, *italic text*, and even [links](https://www.example.com).

## Cross-references :link:

`[Versioning](versioning.md)` will link as [Versioning](versioning.md).

`[Versioning Sub Header](versioning.md#versioning-frameworks)` will link to a sub-header as [Versioning Sub Header](versioning.md#versioning-frameworks) and link directly to the section!

## Math :heavy_plus_sign:

Math can be added with the mkdocs markdown extension `pymdownx.arithmatex`. **But** you also need to have javascript at runtime. To use it, add the following to your `mkdocs.yml`:

```yaml
markdown_extensions:
  - pymdownx.arithmatex

extra_javascript:
  - https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js
```

`$E = mc^2$` inline math

$E = mc^2$

`$$\int_0^\infty e^{-x} dx = 1$$` block form

$$\int_0^\infty e^{-x} dx = 1$$
