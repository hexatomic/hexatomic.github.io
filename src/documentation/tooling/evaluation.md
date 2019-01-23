## Documentation tooling &mdash; evaluation and implementation

In order to choose a suitable documentation tool that fulfils the requirements
outlined in the [previous section](./index.md) (listed below for reference), 
we[^1] have built a shortlist of dedicated documentation tools that would be
feasible to use as the single tool for text-based documentation (as compared to
Javadoc) in our project (requirement (2)). At the same time, we onyl considered
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
	- (3e) Usability of representations
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

We ended up with the following shortlist of tool options.

- Sphinx with reStructuredText input
- Sphinx with CommonMark input
- Asciidoctor with AsciiDoc input
- mkDocs with XXXMarkdown input
- mdBook with XXXMarkdown input
- Jekyll with XXXMarkdown input

### Sustainability

As of now, reliable measures for predicting the sustainability of a software do 
not exist [1], and intrinsically, the actual sustainability of a software can
only be determined in hindsight. Therefore, assessing the sustainability
potential for a software is a qualitative process, partly driven by the
requirements of the project for which the software is assessed.

[1] S. Druskat, 'A proposal for the measurement and documentation of research 
software sustainability in interactive metadata repositories', in Proceedings of 
the Fourth Workshop on Sustainable Software for Science: Practice and 
Experiences (WSSSPE4), University of Manchester, Manchester, UK, 2016 [Online]. 
Available: <http://ceur-ws.org/Vol-1686/>

[^1]: The evaluation was carried out by [S. Druskat](https://sdruskat.net/) and 
[T. Krause](https://www.linguistik.hu-berlin.de/de/institut/professuren/korpuslinguistik/mitarbeiter-innen/thomas).