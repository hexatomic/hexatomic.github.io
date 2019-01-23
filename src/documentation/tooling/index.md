# Tooling

This section provides details on *how* documentation for the research project,
and the **Hexatomic** software as well as the infrastructure used to develop and
provide it, is facilitated.

## Requirements

The requirements for documentation tooling are specific to our research project
in some respects (e.g., pertaining to Javadoc), but all others can be applied
to generic (research) software project setups. And those that are 
project-specific can probably be transferred to other use cases relatively 
easily.

### Sustainability

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

### Single tool "toolchain"

One of the key motivations behind the choice of tooling is to have *one single 
software* which we use for all of our (textual) documentation. This makes
maintainership transitions easier as it requires less learning effort from new
maintainers, as well as contributors.

### Usability

#### Human-readable sources

In the event of a failure in the documentation *software*, the documentation
*sources* must be readable and well-structured enough to function as a fallback
in place of, e.g., HTML- or PDF-rendered documentation.

We use a combination of hierarchical directory structures and human-readable
source file formats to achieve this.

#### Javadoc integration

As **Hexatomic** is written in Java, we use 
[Javadoc](https://en.wikipedia.org/wiki/Javadoc) to document source code 
in situ. This way, we can generate 
[API](https://en.wikipedia.org/wiki/Application_programming_interface) 
documentation in HTML directly from the source code via the 
[javadoc](https://docs.oracle.com/javase/1.5.0/docs/tooldocs/solaris/javadoc.html) 
tool. This specific API documentation format is used standardly across most
Java software projects[^ossrh-requirements] and is something that code contributors will expect to
find.

In order to boost findability of the API documentation, it would be helpful
to be able to integrate the Javadoc HTML in the text documentation for 
developers as easily as possible, ideally through native support for this by the
documentation software.

[^ossrh-requirements]: For example, all release artifacts of open source 
projects that are hosted on "Maven Central", the main repository for the 
dominant build system for Java (cf. [2]), are uploaded through the [Open Source
Software Repository Hosting 
(OSSRH)](https://central.sonatype.org/pages/ossrh-guide.html) system, which 
requires artifacts to include a bundled version of the Javadoc API documentation.

[2] S. Maple and A. Binstock, 'The Largest Survey Ever of Java Developers', 
*Java Magazine*, November/December, p. 20, 2018. Available:
<http://www.javamagazine.mozaicreader.com/NovemberDecember2018#&pageSet=20&page=0>.
[Accessed: 30-Nov-2018]

#### Continuous integration capabilities

In order to embed documentation deeply in the project as well as the development 
workflow, editing documentation must be as easy as possible and should ideally
not require more than making the actual change in the documentation without 
having to care about building the representation, deployment, etc.

The default way to achieve this for any kind of code, including documentation
sources, is to employ a continuous integration (CI) system which polls the 
version control system where the code is held for changes, and reacts to these 
changes by starting the appropriate action, e.g., by building the code and 
deploying the artifacts.

The documentation software should therefore enable continuous integration of its
builds and automated deployment of the documentation representations, either 
natively, or via the continuous integration system used in the project, or by 
simply not preventing the application of a CI system, to trigger builds and
deploy artifacts through, e.g., a custom script run on the CI system.

In addition to providing an easy way to produce documentation, automated 
deployment will also ensure that the user-facing representation of the
documentation can be up-to-date at all times.

#### Maintainability

The documentation software should be very easily maintainable.

This includes factors like easy updates to new versions of the software; 
no installation required or very simple to install; no or very few dependencies
on other software, or ready-made packages that include all dependencies.

#### Usability of representations

The documentation representations produced by the documentation software should
have a high level of usability. 

While some of the features that make 
documentation "usable" for a reader may depend on a specific reader's
approach to documentation as well as her own preferences, some factors of
usability are more easily quantifiable, e.g., a representation's ability to
display well on different devices - which is usually a feature of responsive or 
reactive design paradigms. Further factors include the existence and behaviour
of a table of contents or menu, font choices, colour schemes, intuitivity of
interfaces, simplicity, and a consistent style that users can "learn".


### Different representation forms

The documentation software should ideally be able to produce representations
in different formats, e.g., produce a HTML representation of the documentation,
a PDF file, an EPUB file, etc.

Different representations are required to serve the purposes of different
parts of the documentation. While API documentation may be read mainly
during development work and should therefore be provided as hyperlinked
documents in a website for quick accessibility and browsing, user documentation
may be read in larger portions at a time, e.g., during preparation or evaluation
phases, and should therefore *also* be available as a portable and potentially
printable format such as PDF or EPUB.