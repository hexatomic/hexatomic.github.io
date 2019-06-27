## Documentation tooling &mdash; evaluation and implementation

> **Disclaimer**
>
> Although we have attempted to make our evaluation as objective as possible,
> subjective biases and preferences will usually influence choice of tooling
> (cf. the [editor war](https://en.wikipedia.org/wiki/Editor_war)).
> Additionally, our evaluation methods are informal to some extent, not strictly 
> empirical, and non-reproducible. Nevertheless we feel that publishing them
> here may be useful to record the criteria we have taken into account.


In order to choose a suitable documentation tool that fulfils the requirements
outlined in the [previous section](./index.md) (listed below for reference), 
we[^1] have built a shortlist of dedicated documentation tools that would be
feasible to use as the single tool for text-based documentation (as compared to
Javadoc) in our project (requirement (2)). At the same time, we only considered
tools that use a human-readable source format as input to create documentation
representations from (requirement (3a)). This included only tools that use an
easily human-readable text-based markup language, i.e., a 
[Markdown](https://en.wikipedia.org/wiki/Markdown) dialect,
[reStructuredText](https://en.wikipedia.org/wiki/ReStructuredText) or
[AsciiDoc](https://en.wikipedia.org/wiki/AsciiDoc).

Requirements:
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

It also excluded other commonly used tools, e.g., 
[Pandoc](https://en.wikipedia.org/wiki/Pandoc), if they are not mainly
targeted at creating software documentation.

Additionally, we have excluded tools which seemed too little known, i.e., which
failed the "list test", the hypothesis being that if a tool would not be 
included in a sample of list websites ("Top 10 software documentation tools", 
"15+ Software Documentation Tools That Will Simplify Your Life", etc.) it would
not have enough market share, which may imply a small user base and therefore
not enough community incentive to keep it alive over the next few years.

Out of the whole section of generic static site generators (of which most 
documentation tools are a subset of), we have chosen Jekyll because it is
natively supported by [GitHub Pages](https://pages.github.com/), our chosen
documentation hosting solution. The reasons why we use GitHub Pages are
explained in another section (forthcoming).

We ended up with the following shortlist of tool options.

- [Sphinx](http://www.sphinx-doc.org/en/master/) (Python) with reStructuredText (rST) input
- Sphinx with [CommonMark](https://recommonmark.readthedocs.io/en/latest/index.html) (CM) input
- [Asciidoctor](https://asciidoctor.org/) (Ruby) with AsciiDoc input
- [mkDocs](https://www.mkdocs.org/) (Python) with [Markdown](https://python-markdown.github.io/) input
- [mdBook](https://github.com/rust-lang-nursery/mdBook) (Rust) with [CommonMark](https://github.com/raphlinus/pulldown-cmark) input
- [Jekyll](https://jekyllrb.com/) (Ruby) with [Kramdown](https://kramdown.gettalong.org/) or other Markdown input

We have not taken into account the specifics of the different Markdown dialects
for our evaluation.

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

#### Sphinx <i class="fa fa-star"></i><i class="fa fa-star"></i><i class="fa fa-star"></i><i class="fa fa-star"></i><i class="fa fa-star"></i>

[Sphinx](http://www.sphinx-doc.org/) is a documentation generator written in
Python. It is used to generate the [documentation for the Python programming
language](https://docs.python.org/) itself as well as many large 
[Python projects](http://www.sphinx-doc.org/en/master/examples.html). The
documentation platform [Read the Docs](https://readthedocs.org/) uses Sphinx to
automate the creation and deployment of software documentation.

We have rated the sustainability of Sphinx as very high (5).

Python, Sphinx' implementation language, is a highly used programming language, with an estimated [**41% market share**](https://insights.stackoverflow.com/survey/2019#technology-_-programming-scripting-and-markup-languages),
as of 2019, and [**increasing interest**](https://trends.google.com/trends/explore?date=all&q=%2Fm%2F05z1_#TIMESERIES) as of June 2019.
Sphinx has a **high criticality** due to its use as the Python language documentation platform,
and its **pervasiveness** of the Python community, where it must be regarded as the default documentation tool.
As of June 2019, Sphinx is [**used by over 57,000 projects**](https://github.com/sphinx-doc/sphinx/network/dependents) on Github alone.
The Sphinx hosting service Read the Docs has hosted around [100,000 projects](https://blog.readthedocs.com/read-the-docs-2018-stats/) in 2018 (including Sphinx and mkDocs projects).
Sphinx is a mature project, with **[126 releases](https://github.com/sphinx-doc/sphinx/releases)**, the first one from [Mar 2008](https://github.com/sphinx-doc/sphinx/releases/tag/v0.1.61611).
It is also actively developed, with an average of around **3 commits per day**, with the last **100 commits within the last 17 days** at the time of writing, 
a **contributor base of [422](https://github.com/sphinx-doc/sphinx/graphs/contributors)**, averages of **0.9 issues per day** and **0.5 pull requests per day**.
Its **5 dependencies** seem to be mature, based on the fact that they all have been released in major versions.

#### mdBook <i class="fa fa-star"></i><i class="fa fa-star"></i><i class="fa fa-star"></i><i class="fa fa-star"></i><i class="fa fa-star-o"></i>

[mdBook](https://rust-lang-nursery.github.io/mdBook/) is a documentation generator written in
Rust. It is used to generate the main documentation (both the [reference documentation](https://doc.rust-lang.org/nightly/reference/), and "[The Book](https://doc.rust-lang.org/book/)") for the [Rust programming
language](https://www.rust-lang.org/) itself.

We have rated the sustainability of mdBook as high (4).

Although Rust, mdBook's implementation language, is relatively young - [development has started in 2006](http://web.archive.org/web/20160609195720/https://www.rust-lang.org/faq.html#project) -
it is growing [in popularity](https://insights.stackoverflow.com/survey/2019#most-loved-dreaded-and-wanted) and sees [increasing interest](https://trends.google.com/trends/explore?date=all&q=%2Fm%2F0dsbpg6#TIMESERIES).
Major software projects are written in Rust, such as the [Quantum and Servo browser engines](https://en.wikipedia.org/wiki/Quantum_(Mozilla)), developed by Mozilla and used in the Firefox web browser,
Facebook's Libra cryptocurrency, Dropbox's file system, and security features in the [Tor](https://www.torproject.org/) project. 
mdBook has a **high criticality** as the main documentation tool for the Rust language itself and its pervasiveness as the documentation tool for many Rust projects.
mdBook is a relatively mature project, with [**44 releases**](https://github.com/rust-lang-nursery/mdBook/releases), the first one from [Aug 2015](https://github.com/rust-lang-nursery/mdBook/releases/tag/v0.0.1).
It is also actively developed, with an average of around **0.86 commits per day**, with the last **100 commits within the last 96 days** at the time of writing, 
a **contributor base of [124](https://github.com/rust-lang-nursery/mdBook/graphs/contributors)**, averages of **0.34 issues per day** and **0.33 pull requests per day**.
Its **25 dependencies** seem somewhat mature, with 13 of them having been released in major versions.

#### Jekyll <i class="fa fa-star"></i><i class="fa fa-star"></i><i class="fa fa-star"></i><i class="fa fa-star"></i><i class="fa fa-star-o"></i>

[Jekyll](https://jekyllrb.com/) is a static site generator written in
Ruby. It is the tool used to automatically generate [Github Pages](https://pages.github.com/) from Markdown files.

We have rated the sustainability of Jekyll as high (4).

The popularity of Jekyll's implementation language, Ruby, seems to stagnate at around [**9% market share**](https://insights.stackoverflow.com/survey/2019#technology-_-programming-scripting-and-markup-languages) and sees [**decreasing interest**](https://trends.google.com/trends/explore?date=all&q=%2Fm%2F06ff5#TIMESERIES).
Nevertheless, its market share has remained largely unchanged in the developer community over the last 6 years, and several large software projects are written in Ruby,
including the [Github](https://github.com/) development platform, Airbnb, Kickstarter, SlideShare.
Jekyll has a **high criticality** as the main tool for generating Github pages.
It is a mature project, with [**136 releases**](https://github.com/jekyll/jekyll/releases), the first one from [Dec 2008](https://github.com/jekyll/jekyll/releases/tag/v0.1.3).
Jekyll is also actively developed, with an average of around **2.7 commits per day**, with the last **100 commits within the last 76 days** at the time of writing.
It has a **contributor base of [852](https://github.com/jekyll/jekyll/graphs/contributors)**, averages of **1 issue per day** and **0.9 pull requests per day**.
As of June 2019, Jekyll is [**used by over 296,000 projects**](https://github.com/jekyll/jekyll/network/dependents) on Github alone.
Its **13 dependencies** seem to be mostly mature, based on the fact that all but 2 have been released in major versions.

#### Asciidoctor <i class="fa fa-star"></i><i class="fa fa-star"></i><i class="fa fa-star"></i><i class="fa fa-star-o"></i><i class="fa fa-star-o"></i>

#### mkDocs <i class="fa fa-star"></i><i class="fa fa-star"></i><i class="fa fa-star"></i><i class="fa fa-star-o"></i><i class="fa fa-star-o"></i>

---


[1] S. Druskat, 'A proposal for the measurement and documentation of research 
software sustainability in interactive metadata repositories', in Proceedings of 
the Fourth Workshop on Sustainable Software for Science: Practice and 
Experiences (WSSSPE4), University of Manchester, Manchester, UK, 2016 [Online]. 
Available: <http://ceur-ws.org/Vol-1686/>

[^1]: The evaluation was carried out by [S. Druskat](https://sdruskat.net/) and 
[T. Krause](https://www.linguistik.hu-berlin.de/de/institut/professuren/korpuslinguistik/mitarbeiter-innen/thomas).