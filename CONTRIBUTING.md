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
