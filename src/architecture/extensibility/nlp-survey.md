# Natural Language Processing libraries survey

Implementing Natural Language Processing (NLP) functionality in Hexatomic opens up the software for a potentially large number of use cases beyond manual annotation.
Its [extensible architecture](./) should allow for relatively easy *technological* integration of existing NLP libraries, as long as a number of basic requirements are met. Integration with Hexatomic's data model, Salt, must also be possible.

In order to decide which NLP libraries can be usefully integrated in Hexatomic, we have surveyed existing libraries[^1] and have checked if and how they meet the requirements for integration.

Specifically, the following properties were checked:

1. Is the library implemented in Java? If not, is there a way to address its API from Java?
2. If the library is implemented in Java, does it use the [Apache Maven](https://maven.apache.org/) project management tool?
3. Does the library exist as an OSGi bundle? Specifically, do releases contain an OSGi manifest?
4. Is an OSGi bundle of the library available for consumption from a [p2](https://www.eclipse.org/equinox/p2/) repository?
5. Does it provide the following features? If it does, does it also provide extension mechanisms for the feature? Which are the input and output data types or formats?
   1. Tokenization/segmentation
   2. Sentencing
   3. Part-of-speech tagging
   4. Contituency parsing
   5. Dependency parsing
   6. Trainability of models
   7. Consumption of own models

The results of the survey are below.

---
<!-- Template, please copy and paste to add entry (check checkboxes by adding an 'x' -> '[x]') -->

### [library-name](<URL-to-library-website>)

1. [ ] Implemented in Java
   1. [ ] Not Java, but API can be addressed from Java
      - Can be addressed as follows: n/a <or add brief description of how to address the API>
2. [ ] Uses Maven (`pom.xml` exists)
3. [ ] Is available as OSGi bundle (has `MANIFEST.MF`)
4. [ ] Is available from a p2 repository: n/a <or add repository URL>

#### Feature matrix

<div style="font-size:.8rem;">

|                           | Has functionality        | Functionality extensible | Functionality documentation | Extension documentation      | Input data                           | Output data |
|---------------------------|--------------------------|--------------------------|-----------------------------|------------------------------|--------------------------------------|-------------|
| Tokenization/segmentation | <!-- X or leave empty--> | <!-- X or leave empty--> | <add url>                   | <eg string of document text> | <eg comma-separated list of strings> |             |
| Sentencing                | <!-- X or leave empty--> | <!-- X or leave empty--> | <add url>                   |                              |                                      |             |
| POS-tagging               | <!-- X or leave empty--> | <!-- X or leave empty--> | <add url>                   |                              |                                      |             |
| Constituency parsing      | <!-- X or leave empty--> | <!-- X or leave empty--> | <add url>                   |                              |                                      |             |
| Dependency parsing        | <!-- X or leave empty--> | <!-- X or leave empty--> | <add url>                   |                              |                                      |             |
| Trainable models          | <!-- X or leave empty--> | <!-- X or leave empty--> | <add url>                   |                              |                                      |             |
| Can consume own models    | <!-- X or leave empty--> | <!-- X or leave empty--> | <add url>                   |                              |                                      |             |


</div>

---
<!-- end of template -->

[^1]: The survey was carried out by Prashant Dangwal.