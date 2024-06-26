---
title: Getting Started
weight: 1
description: "Clone the docs and make a contribution"
---

The Crossplane documentation lives in the 
[docs GitHub repository](https://github.com/crossplane/docs).

## Local development
Clone the documentation and use [Hugo](https://gohugo.io/) to 
build the Crossplane documentation site locally for development and testing. 

### Clone the docs repository
Clone the 
[Crossplane docs repository](https://github.com/crossplane/docs) with

```command
git clone https://github.com/crossplane/docs.git
```

### Download Hugo
Download [Hugo](https://github.com/gohugoio/hugo/releases/latest), the
static site generator Crossplane docs uses.

{{< hint "important" >}}
Download the `hugo_extended` version. The standard Hugo package doesn't support
the Crossplane docs CSS.
{{< /hint >}}

Extract and run Hugo with `hugo server`.

Hugo builds the website and launch a local web server on
<a href="http://localhost:1313" data-proofer-ignore>http://localhost:1313</a>.

Any changes made are instantly reflected on the local web server. No need
to restart Hugo.

### Contribute to a specific version
Each Crossplane version is a unique folder inside `/content`. 

{{<hint "note" >}}
The next Crossplane release uses `/content/master` as the starting
documentation.
{{< /hint >}}

Make changes to the files in the associated version folder. To make changes
across more than one version, change the files in each version folder.

## Adding new content

To create new content create a new markdown file in the appropriate location. 

To create a new section, create a new directory and an `_index.md` file in the
root. 

### Front matter
Each page contains metadata called 
[front matter](https://gohugo.io/content-management/front-matter/). Each page 
requires front matter to render.

```yaml
---
title: "A New Page"
weight: 610
---
```

`title` defines the name of the page.
`weight` determines the ordering of the page in the table of contents. Lower
weight pages come before higher weights in the table of contents. The value of
`weight` is otherwise arbitrary. 

#### Alpha and beta features
Note features as alpha or beta in the front matter.

For alpha features set `state: alpha` and use `alphaVersion` to provide the 
version that introduced the feature. 

```yaml
---
title: Composition Functions
state: alpha
alphaVersion: "1.11"
---
```

For beta features set `state: beta` and use both `alhpaVersion` and
`betaVersion` to provide the version that introduced and graduated the feature.

```yaml
---
title: Composition Revisions
state: beta
alphaVersion: "1.4"
betaVersion: "1.11"
---
```

#### Descriptions

Hugo uses the `description` field to populate webpage metadata for search
engines.

```yaml
---
title: Compositions
weight: 30
aliases: 
  - composition
description: "Compositions are a template for creating Crossplane resources"
---
```

The description text isn't displayed anywhere in the docs.

### Headings
Use standard markdown for headings (`#`). The top level heading, a single hash
(`#`) is for the page title. All content headings should be two hashes (`##`) or
more.

### Hiding pages
To hide a page from the left-hand navigation use `tocHidden: true` in the front
matter of the page. The docs website skips pages with `tocHidden:true` when
building the menu.

### Changing page titles

The version dropdown list that links the same page in different versions 
together looks for pages with a matching title.

If a page title changes use the front matter value `matchTitle:` and a value of 
the old page title.

For example, if an older title was "Original Title" the new page would use:

```yaml
title: New Title
matchTitle: Original Title
```
