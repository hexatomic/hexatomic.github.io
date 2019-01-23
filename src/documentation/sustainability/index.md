## Documentation sustainability

The sustainability of software documentation is directly related to the
sustainability of the software it pertains to. Without documentation that is 
*correct* and *complete*[^1] at all times, a software cannot be expected to be
usable at any point in the future. 

"At all times" here describes the *synchronic* aspect of documentation 
sustainability. In practice, this is related to engineering, development and
maintenance practices of a qualitative nature, as all involved parties must take
care to keep documentation up-to-date, while only parts of this process may be
easily automatable or measurable. Some methods for documenting source code in 
situ, e.g., 
[literate programming](https://en.wikipedia.org/wiki/Literate_programming), aid
efforts to achieve synchronic sustainability, but they are not applicable in all
projects, and usually additional documentation, e.g., for end users, must be
created. Contribution and maintenance workflows can support the fulfillment of
the completeness and correctness requirements by implementing methods such as
code review, static code analysis, etc.

There is also a *diachronic* aspect to documentation sustainability, which is of
a more technical nature, and is equivalent to technical sustainability of 
software. It pertains to the sustainability of the documentation *tooling*, and
to the sustainability of the documentation artifacts, i.e., the documentation
"products", such as rendered files (PDF, HTML, etc.) and sources, but also to
compatibility with rendering systems (e.g., browsers), and the availability and 
findability of sources and artifacts.

In the context of software projects, this yields the following concrete
requirements:

1. Synchronic sustainability must be ensured by applying software engineering
methods to the documentation workflow. This includes code and 
documentation review, leveraging IDE support for in situ documentation of source 
code, implementation of code styles such as naming conventions, [runnable 
documentation](https://githubengineering.com/runnable-documentation/), etc.
2. Diachronic sustainability must be ensured by choosing sustainable tooling,
and implementing documentation sources and artifacts so that they remain
findable, available, and accessible.

[^1]: It is important to note that *complete* may mean different things in
different situations. Private/internal functions, e.g., private methods in Java,
may not have to be documented, while public/external functions that may use them
must be.