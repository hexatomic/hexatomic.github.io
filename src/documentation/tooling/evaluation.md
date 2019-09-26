## Documentation tooling &mdash; evaluation and implementation

> **Disclaimer**
>
> Although we have attempted to make our evaluation as objective as possible,
> subjective biases and preferences will usually influence choice of tooling
> (cf. the [editor war](https://en.wikipedia.org/wiki/Editor_war)).
> Additionally, our evaluation methods are informal to some extent, not strictly 
> empirical, and non-reproducible. Nevertheless we feel that publishing them
> here may be useful to record the criteria we have taken into account.


Requirements for single tool documentation software (cf. [documentation tooling section](./index.md)):
- (1) Sustainability
- (2) Single tool toolchain
- (3) Usability  
	- (3a) Human-readable source format  
	- (3b) Javadoc integration  
	- (3c) Continuous integration capabilities  
	- (3d) Maintainability
	- (3e) Maintainability (dependencies)
	- (3f) Usability of representations
- (4) Different representation forms  

To evaluate which documentation tool may be the most suitable for our needs, we
have marked it with a value from 1-5 for each requirement, with 1 being the
lowest ("worst") mark and 5 the highest ("best").

The calculations below are also available as a 
[Jupyter notebook](https://nbviewer.jupyter.org/github/sdruskat/hexatomic.github.io/blob/src/src/static/ipynb/Hexatomic%20Project%20-%20Documentation%20Tooling%20Evaluation.ipynb).

|     Tool     | 1 | 3a | 3b | 3c | 3d | 3e | 3f | x̄(3)  | 4 |
|--------------|---|----|----|----|----|----|----|-------|---|
| Sphinx (rST) | 5 | 3  | 4  | 3  | 4  | 3  | 4  |  3.5  | 4 |
| Sphinx (CM)  | 3 | 5  | 1  | 3  | 2  | 3  | 4  |  3.0  | 4 |
| Asciidoctor  | 3 | 4  | 1  | 4  | 3  | 3  | 3  |  3.0  | 3 |
| mkDocs       | 3 | 5  | 1  | 3  | 4  | 3  | 2  |  3.0  | 1 |
| mdBook       | 4 | 5  | 1  | 3  | 4  | 4  | 5  |  3.67 | 3 |
| Jekyll       | 4 | 5  | 1  | 3  | 4  | 2  | 2  |  2.83 | 2 |


### Sustainability

As of now, reliable measures for predicting the sustainability of a software do 
not exist [1], and intrinsically, the actual sustainability of a software can
only be determined in hindsight. Therefore, assessing the sustainability
potential for a software is a qualitative process, partly driven by the
requirements of the project for which the software is assessed.

Despite this constraint, assumptions over the sustainability potential of a
documentation software project can be based on some assessable factors, e.g., 
age of the software, approximated user base, development status, frequency of 
contributions, architecture, pervasiveness of a technological community,
level of documentation, maturity of its dependencies, etc.

In the evaluation process, we have tried to approximate each candidate's
potential for sustainability, which we present in the following.
Additionally, we give the [SourceRank metric for high quality packages]() used by libraries.io, based on the actual products we would employ.

#### Sphinx <i class="fa fa-star"></i><i class="fa fa-star"></i><i class="fa fa-star"></i><i class="fa fa-star"></i><i class="fa fa-star"></i>

[Sphinx](http://www.sphinx-doc.org/) is a documentation generator written in
Python. It is used to generate the [documentation for the Python programming
language](https://docs.python.org/) itself as well as many large 
[Python projects](http://www.sphinx-doc.org/en/master/examples.html). The
documentation platform [Read the Docs](https://readthedocs.org/) uses Sphinx to
automate the creation and deployment of software documentation.

We have rated the sustainability of Sphinx as very high (5).  
SourceRank metric: [23](https://libraries.io/pypi/Sphinx/sourcerank)

Python, Sphinx' implementation language, is a highly used programming language, with an estimated [**41% market share**](https://insights.stackoverflow.com/survey/2019#technology-_-programming-scripting-and-markup-languages),
as of 2019, and [**increasing interest**](https://trends.google.com/trends/explore?date=all&q=%2Fm%2F05z1_#TIMESERIES) as of June 2019.
Sphinx has a **high criticality** due to its use as the Python language documentation platform,
and its **pervasiveness** of the Python community, where it must be regarded as the default documentation tool.
As of June 2019, Sphinx is [**used by over 57,000 projects**](https://github.com/sphinx-doc/sphinx/network/dependents) on Github alone.
The Sphinx hosting service Read the Docs has hosted around [100,000 projects](https://blog.readthedocs.com/read-the-docs-2018-stats/) in 2018 (including Sphinx and mkDocs projects).
Sphinx is a mature project, with **[126 releases](https://github.com/sphinx-doc/sphinx/releases)**, the first one from [Mar 2008](https://github.com/sphinx-doc/sphinx/releases/tag/v0.1.61611).
It is also actively developed, with an average of around **3 commits per day**, with the last **100 commits within the last 17 days** at the time of writing, 
a **contributor base of [422](https://github.com/sphinx-doc/sphinx/graphs/contributors)**, of which **51 (12%) have actively contributed over the last year**, and in this period, **45 contributors (11%) have made more than 1 commit**.
Sphinx has averages of **0.9 issues per day** and **0.5 pull requests per day**.
Its **5 dependencies** seem to be mature, based on the fact that they all have been released in major versions.

#### mdBook <i class="fa fa-star"></i><i class="fa fa-star"></i><i class="fa fa-star"></i><i class="fa fa-star"></i><i class="fa fa-star-o"></i>

[mdBook](https://rust-lang-nursery.github.io/mdBook/) is a documentation generator written in
Rust. It is used to generate the main documentation (both the [reference documentation](https://doc.rust-lang.org/nightly/reference/), and "[The Book](https://doc.rust-lang.org/book/)") for the [Rust programming
language](https://www.rust-lang.org/) itself.

We have rated the sustainability of mdBook as high (4).  
SourceRank metric: [15](https://libraries.io/cargo/mdbook/sourcerank)

Although Rust, mdBook's implementation language, is relatively young - [development has started in 2006](http://web.archive.org/web/20160609195720/https://www.rust-lang.org/faq.html#project) -
it is growing [in popularity](https://insights.stackoverflow.com/survey/2019#most-loved-dreaded-and-wanted) and sees [increasing interest](https://trends.google.com/trends/explore?date=all&q=%2Fm%2F0dsbpg6#TIMESERIES).
Major software projects are written in Rust, such as the [Quantum and Servo browser engines](https://en.wikipedia.org/wiki/Quantum_(Mozilla)), developed by Mozilla and used in the Firefox web browser,
Facebook's Libra cryptocurrency, Dropbox's file system, and security features in the [Tor](https://www.torproject.org/) project. 
mdBook has a **high criticality** as the main documentation tool for the Rust language itself and its pervasiveness as the documentation tool for many Rust projects.
mdBook is a relatively mature project, with [**44 releases**](https://github.com/rust-lang-nursery/mdBook/releases), the first one from [Aug 2015](https://github.com/rust-lang-nursery/mdBook/releases/tag/v0.0.1).
It is also actively developed, with an average of around **0.86 commits per day**, with the last **100 commits within the last 96 days** at the time of writing, 
a **contributor base of [124](https://github.com/rust-lang-nursery/mdBook/graphs/contributors)**, of which **43 (35%) have contributed over the last year**, and in this period, **22 contributors (18%) have made more than 1 commit**.
mdBook has averages of **0.34 issues per day** and **0.33 pull requests per day**.
Its **25 dependencies** seem somewhat mature, with 13 of them having been released in major versions.

#### Jekyll <i class="fa fa-star"></i><i class="fa fa-star"></i><i class="fa fa-star"></i><i class="fa fa-star"></i><i class="fa fa-star-o"></i>

[Jekyll](https://jekyllrb.com/) is a static site generator written in
Ruby. It is the tool used to automatically generate [Github Pages](https://pages.github.com/) from Markdown files.

We have rated the sustainability of Jekyll as high (4).  
SourceRank metric: [27](https://libraries.io/rubygems/jekyll/sourcerank)

The popularity of Jekyll's implementation language, Ruby, seems to stagnate at around [**9% market share**](https://insights.stackoverflow.com/survey/2019#technology-_-programming-scripting-and-markup-languages) and sees [**decreasing interest**](https://trends.google.com/trends/explore?date=all&q=%2Fm%2F06ff5#TIMESERIES).
Nevertheless, its market share has remained largely unchanged in the developer community over the last 6 years, and several large software projects are written in Ruby,
including the [Github](https://github.com/) development platform, Airbnb, Kickstarter, SlideShare.
Jekyll has a **high criticality** as the main tool for generating Github pages.
It is a mature project, with [**136 releases**](https://github.com/jekyll/jekyll/releases), the first one from [Dec 2008](https://github.com/jekyll/jekyll/releases/tag/v0.1.3).
Jekyll is also actively developed, with an average of around **2.7 commits per day**, with the last **100 commits within the last 76 days** at the time of writing.
It has a **contributor base of [852](https://github.com/jekyll/jekyll/graphs/contributors)**, of which **12 (1%) have contributed over the last year**, and in this period, **7 contributors (<1%) have made more than 1 commit**.
Jekyll has averages of **1 issue per day** and **0.9 pull requests per day**.
As of June 2019, Jekyll is [**used by over 296,000 projects**](https://github.com/jekyll/jekyll/network/dependents) on Github alone.
Its **13 dependencies** seem to be mostly mature, based on the fact that all but 2 have been released in major versions.

#### Asciidoctor <i class="fa fa-star"></i><i class="fa fa-star"></i><i class="fa fa-star"></i><i class="fa fa-star-o"></i><i class="fa fa-star-o"></i>

[Asciidoctor](https://asciidoctor.org/) is a processor and publishing toolchain for the [AsciiDoc](https://asciidoctor.org/docs/what-is-asciidoc/#what-is-asciidoc) markup language.
It is written in Ruby.
Asciidoctor is used to build documentation for a number of larger software projects, including Grails, the Gradle build automation tool, Red Hat documentation, 
Solr, [and many others](https://github.com/asciidoctor/asciidoctor.org/issues/270).

We have rated the sustainability of Asciidoctor as medium (3).  
SourceRank metric of the AsciiDoctor Maven plugin: [10](https://libraries.io/maven/org.asciidoctor:asciidoctor-maven-plugin/sourcerank)

The popularity of Asciidoctor's implementation language, Ruby, seems to stagnate at around [**9% market share**](https://insights.stackoverflow.com/survey/2019#technology-_-programming-scripting-and-markup-languages) and sees [**decreasing interest**](https://trends.google.com/trends/explore?date=all&q=%2Fm%2F06ff5#TIMESERIES).
Nevertheless, its market share has remained largely unchanged in the developer community over the last 6 years, and several large software projects are written in Ruby,
including the [Github](https://github.com/) development platform, Airbnb, Kickstarter, SlideShare.
It is a mature project, with [**60 releases**](https://github.com/asciidoctor/asciidoctor/releases), the first one from [Feb 2014](https://github.com/asciidoctor/asciidoctor/releases/tag/v1.5.0.preview.2).
Asciidoctor is actively developed, with an average of around **1.7 commits per day**, with the last **100 commits within the last 82 days** at the time of writing.
It has a **contributor base of [115](https://github.com/asciidoctor/asciidoctor/graphs/contributors)**, of which **21 (18%) have contributed over the last year**, and in this period, **6 contributors (5%) have made more than 1 commit**.
Asciidoctor has averages of **0.8 issues per day** and **0.5 pull requests per day**.
Its **3 dependencies** seem to be immature, as none of them have a major release version.


#### mkDocs <i class="fa fa-star"></i><i class="fa fa-star"></i><i class="fa fa-star"></i><i class="fa fa-star-o"></i><i class="fa fa-star-o"></i>

[mkDocs](https://www.mkdocs.org/) is a static site generator for project documentation.
It is written in Python.

We have rated the sustainability of mkDocs as medium (3).  
SourceRank metric: [9](https://libraries.io/pypi/mkdocs/sourcerank)

Python, mkDocs' implementation language, is a highly used programming language, with an estimated [**41% market share**](https://insights.stackoverflow.com/survey/2019#technology-_-programming-scripting-and-markup-languages),
as of 2019, and [**increasing interest**](https://trends.google.com/trends/explore?date=all&q=%2Fm%2F05z1_#TIMESERIES) as of June 2019.
Its **criticality** seems to be low, as we could not find any large software projects documented with it.
It is a mature project, with [**41 releases**](https://github.com/mkdocs/mkdocs/releases), the first one from [Jan 2014](https://github.com/mkdocs/mkdocs/releases/tag/0.2).
mkDocs is actively developed, with an average of around **0.7 commits per day**, with the last **100 commits within the last 444 days** at the time of writing.
It has a **contributor base of [126](https://github.com/mkdocs/mkdocs/graphs/contributors)**, of which **27 (21%) have contributed over the last year**, and in this period, **6 contributors (5%) have made more than 1 commit**.
mkDocs has averages of **0.6 issues per day** and **0.4 pull requests per day**.
Its **7 dependencies** seem to be mature, as 6 out of 7 have a major release version.

### Usability

Assessing the usability of software is an opinionated process which takes into account encountered and predicted use in a specific context.
In our evaluation, we have taken into account the readability of the source format, Javadoc integration, continuous integration capabilities,
maintainability, maintainability of dependencies, and the usability of representations.

#### Human-readable source format

*Sphinx (rST)* <i class="fa fa-star"></i><i class="fa fa-star"></i><i class="fa fa-star"></i><i class="fa fa-star-o"></i><i class="fa fa-star-o"></i>   
We have evaluated reStructuredText to be less-than-perfectly human-readable and human-usable due to 

- its syntax for hyperlinks, which is not in-situ but instead uses an in-text underscore syntax ``Text `link text_` text`` in combination
with a text-external external footnote syntax `.. _link text: https://hyperlink` for named links, which compares unfavourably with the Markdown
format;
- the four-whitespace indentation convention for code blocks, which disallows easy copy and paste of valid source code snippets.

*Sphinx (CM), mkDocs, mdBook, Jekyll* <i class="fa fa-star"></i><i class="fa fa-star"></i><i class="fa fa-star"></i><i class="fa fa-star"></i><i class="fa fa-star"></i>  
We have evaluated Markdown to be very human-readable and human-usable, independent of implementation dialects. Markdown
does not exhibit the same syntax-specific issues as reStructuredText.

*Asciidoctor* <i class="fa fa-star"></i><i class="fa fa-star"></i><i class="fa fa-star"></i><i class="fa fa-star"></i><i class="fa fa-star-o"></i>  
We have evaluated AsciiDoc, the input format for Asciidoctor, to be human-readable, despite some idiosyncrasies in the syntax, such as
`<whitespace>+` for single line breaks, and the less graphic headline syntax.

#### Javadoc integration

We have eventually decided to disregard the integration of Javadoc API documentation as a deciding factor for the best-suited documentation
tool for the project. Javadoc-based HTML generation has been a standard feature of Java and Maven for years, and linking from any 
running text documentation to the respective API documentation is trivial, and can be automated in continuous integration. 
Nevertheless we provide a quick overview of the evaluations here.




- (3a) Human-readable source format  
    - (3b) Javadoc integration  
    - (3c) Continuous integration capabilities  
    - (3d) Maintainability
    - (3e) Maintainability (dependencies)
    - (3f) Usability of representations

| Sphinx (rST) | 5 | 3  | 4  | 3  | 4  | 3  | 4  |  3.5  | 4 |
| Sphinx (CM)  | 3 | 5  | 1  | 3  | 2  | 3  | 4  |  3.0  | 4 |
| Asciidoctor  | 3 | 4  | 1  | 4  | 3  | 3  | 3  |  3.0  | 3 |
| mkDocs       | 3 | 5  | 1  | 3  | 4  | 3  | 2  |  3.0  | 1 |
| mdBook       | 4 | 5  | 1  | 3  | 4  | 4  | 5  |  3.67 | 3 |
| Jekyll       | 4 | 5  | 1  | 3  | 4  | 2  | 2  |  2.83 | 2 |

---


[1] S. Druskat, 'A proposal for the measurement and documentation of research 
software sustainability in interactive metadata repositories', in Proceedings of 
the Fourth Workshop on Sustainable Software for Science: Practice and 
Experiences (WSSSPE4), University of Manchester, Manchester, UK, 2016 [Online]. 
Available: <http://ceur-ws.org/Vol-1686/>

[^1]: The evaluation was carried out by [S. Druskat](https://sdruskat.net/) and 
[T. Krause](https://www.linguistik.hu-berlin.de/de/institut/professuren/korpuslinguistik/mitarbeiter-innen/thomas).