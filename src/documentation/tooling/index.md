## Tooling

This section provides details on *how* documentation for the research project,
and the **Hexatomic** software as well as the infrastructure used to develop and
provide it, is facilitated.

### Requirements

The requirements for documentation tooling are specific to our research project
in some respects (e.g., pertaining to Javadoc), but all others can be applied
to generic (research) software project setups. And those that are 
project-specific can probably be transferred to other use cases relatively 
easily.

#### Sustainability

The [documentation sustainability](../sustainability/) section establishes that

> [documentation] sustainability must be ensured by choosing sustainable tooling 
[...].

Software sustainability covers many aspects, including community parameters such
as size, number and frequency of contributions; whether a code is open source;
the programming language it is implemented with; ease of installation; its
dependency tree, etc.

Accordingly, there is currently no canonic definition of software 
sustainability, as discussed in [1]. One of the definitions given in [1] seems
operationable enough to use in the context of documentation tooling:

> Sustainable software is software which is:  
> - Easy to evolve and maintain
> - Fulfils its intent over time
> - Survives uncertainty
> - Supports relevant concerns (Political, Economic, Social, Technical,
> Legal, Environmental)

[1] D. S. Katz, 'Defining Software Sustainability', 2016. [Online]. 
Available: <https://web.archive.org/web/20181122140500/https://danielskatzblog.wordpress.com/2016/09/13/defining-software-sustainability/>. 
[Accessed: 22-Nov-2018]

#### Single tool "toolchain"

One of the key motivations behind the choice of tooling is to have *one single 
software* which we use for all of our (textual) documentation. This makes
maintainership transitions easier as it requires less learning effort from new
maintainers, as well as contributors.

#### Usability

##### Human-readable sources

In the event of a failure in the documentation *software*, the documentation
*sources* must be readable and well-structured enough to function as a fallback
in place of, e.g., HTML- or PDF-rendered documentation.

We use a combination of hierarchical directory structures and human-readable
source file formats to achieve this.

#### Javadoc integration

#### Continuous integration capabilities

#### Maintainability

#### Usability of build artifacts XXX

### Export capabilities

