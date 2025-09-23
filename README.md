# Amariuta Lab Website Source Code

This repository contains code for the website hosted at https://amariutalab.github.io through `gh-pages` at the custom domain https://www.amariutalab.org. It was built using [`quarto`](https://quarto.org/), an [open-source](https://github.com/quarto-dev) scientific and technical publishing system sponsored by [Posit, PBC](https://posit.co/).

## Setting up `quarto` for `gh-pages` GitHub Websites

To create this static website with `quarto`, we performed the following steps:

1. Downloaded `quarto` for the respective operating system and tool of choice from the [Getting Started](https://quarto.org/docs/get-started/) page. (i.e., as an example for this website, @mragsac used `quarto` for macOS and [Visual Studio Code](https://code.visualstudio.com/) to develop things locally)

2. Created a [website project](https://quarto.org/docs/websites/) using the `quarto` CLI utility where `$WEBSITE_NAME_HERE` is `$GITHUB_USERNAME.github.io`

```bash
# Create a new website project with the quarto CLI
quarto create project website $WEBSITE_NAME_HERE
```

3. After creating a new website project, made sure that the following files were present:
    * `_quarto.yml` : Contains website options and HTML defaults for documents created for the website (this includes [navigation options](https://quarto.org/docs/websites/website-navigation.html), [search options](https://quarto.org/docs/websites/website-search.html), and [other tools](https://quarto.org/docs/websites/website-tools.html))
    * `index.qmd` : Contains the landing page for the website
    * `404.qmd` : Contains the default stylings for a [`404` website page](https://quarto.org/docs/websites/website-navigation.html#pages-404)
    * `.gitignore` : Contains specific files to ignore when pushing changes to GitHub, such as the `/.quarto/` hidden folder and `/_site/` default directory
    * `.nojekyll` : An empty file which prevents additional processing of the `quarto` website with Jekyll (i.e., as this is turned on by default by GitHub)

## Configuring the `_quarto.yml` file to export to a custom directory for easy deployment

We published the site with GitHub Pages using the [documentation](https://quarto.org/docs/publishing/github-pages.html) on the `quarto` website, but to make things easier for those that wish to update things, you can follow the steps below to do the same.

1. Change the default website rendering directory from `/_sites/` to `docs` by specifying it as the output directory in the `_quarto.yml` configuration file

```yml
# _quarto.yml

project:
  type: website
  output-dir: docs
```

2. Next, render the website and initialize all files to add to the `$GITHUB_USERNAME.github.io` repository

```bash
# First render the website and then add the rendered files to GitHub 
quarto render
git add docs
git commit -m "Publish site to docs/"
git push
```

3. Finally, configure the GitHub repository (`$GITHUB_USERNAME.github.io`) to publish from the `/docs/` directory of your `main` branch in the `Settings > Pages` section under "Code and automation"

Once you've set this up, GitHub will trigger a deployment of your website to the `https://$GITHUB_USERNAME.github.io` URL (or a custom domain if you have that configured) whenever you commit and push to your main branch!

---

# Adding Information to the Website with Templates

## The Publications Page

Lab Publications can be found in the `publications.qmd` file.

## The GitHub Page

While the stylings for this page of the website can be found in the `github.qmd` file, the contents can be found in the `/tools/` directory, where each entry is a separate `.qmd` file.

If you would like to add a new tool to the website, you can use the following template for the `.qmd` file:

```yml
---
title: "**TOOL NAME**: Tool Description"
subtitle: "[{{< fa brands github >}} GitHub](https://github/repository/link/goes/here)&ensp;&emsp;[{{< fa solid book >}} Paper](https://paper/link/goes/here)"
description: "Manuscript Citation."
date: XX/XX/202X
image: /img/tools/Placeholder-Figure-1.jpeg
---
```

### Tips and Considerations

* With this `.qmd` file, we are only using the header block (i.e., denoted with `---`) like with YAML files
* The **title** contains the tool name or acronym, along with a short description of the tool as introduced within the associated manuscript
* The **subtitle** contains links to the GitHub Repository for the tool (i.e., as denoted with `[{{< fa brands github >}} GitHub](https://github/repository/link/goes/here)`) and the Manuscript for the tool (i.e., as denoted with `[{{< fa solid book >}} Paper](https://paper/link/goes/here)`)
    * These links are separated with `&ensp;&emsp;`
* The **description** includes the proper citation for the associated manuscript
* The **date** reflects the manuscript publication date (or upload date for pre-prints)
* The **image** reflects an overarching diagram of the tool, which is usually presented in Figure 1 of the manuscript

## The People Page (i.e., Lab Members)

Lab Members can be found in the `people.qmd` file. 

If you would like to add a person to the website, you can use the following template:

```md
<!-- ####################################################################### -->

## FirstName Last Name
::: columns

<!-- Person Icon -->
::: {.column width="45%"}
![](img/people/Placeholder-Person.jpg)
:::

::: {.column width="5%"}
:::

<!-- Person Description -->
::: {.column width="50%"}
### Position Title Here

*2-3 Sentence Description of Person*

:::
:::
```

### Tips and Considerations

* With `.qmd` files, comments are denoted by `<!-- ... -->` tags like with HTML
* For each **individual's name**, they're marked with `H2` Headers denoted by the `##` from Markdown Syntax
* There are three columns to each individual, denoted by `:::` blocks (within which you can use HTML or Markdown Syntax): 
    1. The first block contains the **individual's profile icon** as stored in `/people/` with a column width of 45% as denoted by `::: {.column width="45%"}`
    2. The second block is a blank divider as denoted by `::: {.column width="5%"}`
    3. The third block contains the **individual's description** with a column width of 50% as denoted by `::: {.column width="50%"}`
* For each **individual's description**, their position title is marked with a `H3` header denoted by `###` from Markdown Syntax
