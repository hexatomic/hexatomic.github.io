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

### [Apache OpenNLP](<https://opennlp.apache.org/>)

1. [x] Implemented in Java
   1. [ ] Not Java, but API can be addressed from Java
      - Can be addressed as follows: n/a <or add brief description of how to address the API>
2. [x] Uses Maven (`pom.xml` exists)
3. [ ] Is available as OSGi bundle (has `MANIFEST.MF`)<!-- Not sure about that. MANIFEST.MF doesn't exist but there is this: https://opennlp.apache.org/docs/1.8.3/apidocs/opennlp-tools/opennlp/tools/util/ext/OSGiExtensionLoader.html-->
4. [ ] Is available from a p2 repository: n/a
#### Feature matrix

<div style="font-size:.8rem;">

|                           | Has functionality          | Functionality extensible   | Functionality documentation | Extension documentation      | Input data                           | Output data |
|---------------------------|:--------------------------:|:--------------------------:|-----------------------------|------------------------------|--------------------------------------|-------------|
| Tokenization/segmentation | X                          | X                          | <https://opennlp.apache.org/docs/1.9.0/manual/opennlp.html#tools.tokenizer.api> |<https://opennlp.apache.org/docs/1.9.0/manual/opennlp.html#tools.extension.writing>                                                                                                  | string of (untokenized) text |-array of strings</br> -array of token spans|
| Sentencing                | X                          | X                          |<https://opennlp.apache.org/docs/1.9.0/manual/opennlp.html#tools.sentdetect.detection.api>| <https://opennlp.apache.org/docs/1.9.0/manual/opennlp.html#tools.extension.writing>                                                                          | string of document text | -array of strings</br> -array of sentence spans|
| POS-tagging               | X                          | X                          | <https://opennlp.apache.org/docs/1.9.0/manual/opennlp.html#tools.postagger.tagging.api>                   | <https://opennlp.apache.org/docs/1.9.0/manual/opennlp.html#tools.extension.writing>                                                                  | string array of tokens               | string array of tags |
| Constituency parsing      | X                          | X                          | <https://opennlp.apache.org/docs/1.9.0/manual/opennlp.html#tools.parser.parsing.api> | <https://opennlp.apache.org/docs/1.9.0/manual/opennlp.html#tools.extension.writing> | String of whitespace tokenized Sentence | array of OpenNLP's Parse Type |
| Dependency parsing        |                            |                            |                             |                               |                                     |            |
| Trainable models          | X                          | X                          | <http://opennlp.sourceforge.net/models-1.5/> | <https://opennlp.apache.org/docs/1.9.0/manual/opennlp.html#tools.extension.writing>              |                                      |             |
| Can consume own models    | X                          | X                          | - <https://opennlp.apache.org/docs/1.9.0/manual/opennlp.html#tools.postagger.training.api> </br> -<https://opennlp.apache.org/docs/1.9.0/manual/opennlp.html#tools.sentdetect.training.api> </br> -<https://opennlp.apache.org/docs/1.9.0/manual/opennlp.html#tools.tokenizer.training.api> </br> -<https://opennlp.apache.org/docs/1.9.0/manual/opennlp.html#tools.parser.training.api> | <https://opennlp.apache.org/docs/1.9.0/manual/opennlp.html#tools.extension.writing> |             |

</div>
<!-- additional features: Language Detector, NER, Document Categorizer, Lemmatization, Chunking, Coreference Resolution-->


<!-- end of template -->

[^1]: The survey was carried out by Clara Lachenmaier.
