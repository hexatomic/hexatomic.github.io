# Sources for the Hexatomic project documentation

The project documentation for Hexatomic is built with 
[**mdBook**](https://github.com/rust-lang-nursery/mdBook). *mdBook* is built
in [*Rust*](https://www.rust-lang.org).

## Requirements

You do **not** need to install *Rust* in order to build the documentation.
Instead, *mdBook* is provided in binaries served from the project's [GitHub
releases page](https://github.com/rust-lang-nursery/mdBook/releases).

In order to build, you need:

- [**mdBook v0.2.1**](https://github.com/rust-lang-nursery/mdBook/releases/tag/v0.2.1)
[[Installation guide](https://rust-lang-nursery.github.io/mdBook/cli/index.html)]

## Setup

The documentation has been set up by running `mdbook init --theme` in the
root directory of this repository. This created a skeleton *mdBook* installation
as well as copied the theme files. In this version of the documentation, 
only the [Handlebars](https://handlebarsjs.com/) template file 
[`index.hbs`](/home/stephan/src/hexatomic.github.io/src/theme/index.hbs) has 
been changed (you can compare it with the original file by running
`mdbook init --theme` in another directory to create a vanilla setup of 
*mdBook*).

## Build

To build the documentation, run `mdbook build` in the root of this repository.
To serve the documentation locally, run `mdbook serve` in the root of this
repository. Without customization, the documentation will be served at 
<http://localhost:3000/>.

## License

The Hexatomic documentation is licensed under a Creative Commons 
Attribution-ShareAlike 4.0 International license
[![CC-By-SA-4.0 badge](src/static/img/cc-by-sa.png)](LICENSE).

Copyright (c) 2018ff. The [Hexatomic project team](https://github.com/orgs/hexatomic/teams/project/members)