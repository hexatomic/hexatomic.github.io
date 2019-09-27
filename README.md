[![Build Status](https://travis-ci.org/hexatomic/hexatomic.github.io.svg?branch=src)](https://travis-ci.org/hexatomic/hexatomic.github.io)

# Sources for the Hexatomic project documentation

The project documentation for Hexatomic is built with 
[**mdBook**](https://github.com/rust-lang-nursery/mdBook). *mdBook* is built
in [*Rust*](https://www.rust-lang.org).

## Development

Development, i.e., additions and changes to the project documentation, are
pushed to the [**`src`**](https://github.com/hexatomic/hexatomic.github.io/tree/src) 
branch, i.e., the default branch. Travis CI automatically
picks up the changes from this branch, makes the build, and pushes the product
to the 
[`master` branch](https://github.com/hexatomic/hexatomic.github.io/tree/master), 
from where it is automatically rendered on 
[hexatomic.guithub.io](https://hexatomic.guithub.io) via the 
[GitHub Pages](https://pages.github.com/) functionality. 

GitHub Pages looks for a repository in
a GitHub [organization](https://help.github.com/articles/about-organizations/) 
called `{organization}.github.io` (e.g., 
`hexatomic.github.io`), and will try to render the files in the `master` branch
of this repository.

## Requirements

You do **not** need to install *Rust* in order to build the documentation.
Instead, *mdBook* is provided in binaries served from the project's [GitHub
releases page](https://github.com/rust-lang-nursery/mdBook/releases).

In order to build, you need:

- [**mdBook >= v0.3.1**](https://github.com/rust-lang-nursery/mdBook/releases/tag/v0.3.1)
[[Installation guide](https://rust-lang-nursery.github.io/mdBook/cli/index.html)]

## Setup

The documentation has been set up by running `mdbook init --theme` in the
root directory of this repository. This created a skeleton *mdBook* installation
as well as copied the theme files. In this version of the documentation, 
only the [Handlebars](https://handlebarsjs.com/) template file 
[`index.hbs`](/home/stephan/src/hexatomic.github.io/src/theme/index.hbs) has 
been changed (you can compare it with the original file by running
`mdbook init --theme` in another directory to create a vanilla setup of 
*mdBook*, and then diffing the two `index.hbs` files).

## Build

To build the documentation, run `mdbook build` in the root of this repository.
To serve the documentation locally, run `mdbook serve` in the root of this
repository. Without customization, the documentation will be served at 
<http://localhost:3000/>.

## Hosting

The documentation is hosted as a [GitHub page](https://pages.github.com/) on 
<hexatomic.github.io>.

The deployment is automated via [Travis CI](https://travis-ci.org/) continuous 
integration, see section `deploy` in the Travis configuration file 
[`.travis.yml`](.travis.yml).

## Making changes

The structure of the documentation is configured in 
[`src/SUMMARY.md`](src/SUMMARY.md). Only files that are added to the structure
there appear in the documentation.

To add new sections to the documentation, create a 
[Markdown](https://en.wikipedia.org/wiki/Markdown) file called
`{name}.md` in a reasonable place in the `src` directory. 

Add a link to your file to `src/SUMMARY.md` to render it, either in the front or
back matter (as a simple Markdown link `[text](relative path)`), or in the 
nested list of contents (as a Markdown list item `- [text](relative path)`).

### Images & code style

If you want to use images, place them in the same directory as your Markdown
file. Only files that are used globally should go in `src/static/img/`. This
makes it easier and less verbose to reference files in the Markdown (instead of
`![text](../../../static/img/img.png)` you can simply use `![text](img.png)`).

### Markdown dialect

*mdBook* uses the
[CommonMark](https://commonmark.org/) specification of Markdown, specifically in 
its Rust implementation 
[*pulldown-cmark*](https://github.com/raphlinus/pulldown-cmark).

This is a generic Markdown implementation which is feature-complete and also
supports tables in the 
[PHP Markdown Extra](https://michelf.ca/projects/php-markdown/extra/#table) 
syntax.

### Known bugs

- [Table headers aren't always aligned correctly in the second and following 
tables in the same file](https://github.com/rust-lang-nursery/mdBook/issues/825).

## Creating a PDF file of the documentation

PDFs, or single page HTML views, of the documentation can be created via the
print button in the upper right corner of the documentation. The browser can
be used to print to PDF.

## License

The Hexatomic documentation is licensed under a Creative Commons 
Attribution-ShareAlike 4.0 International license
[![CC-By-SA-4.0 badge](src/static/img/cc-by-sa.png)](LICENSE).

Copyright (c) 2018ff. The [Hexatomic project team](https://github.com/orgs/hexatomic/teams/project/members)
