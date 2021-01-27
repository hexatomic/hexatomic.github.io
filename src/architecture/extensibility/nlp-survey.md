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


### [CoreNLP](<https://stanfordnlp.github.io/CoreNLP/>)

1. [X] Implemented in Java
   1. [ ] Not Java, but API can be addressed from Java
      - Can be addressed as follows: n/a <or add brief description of how to address the API>
2. [X] Uses Maven (`pom.xml` exists)
3. [X] Is available as OSGi bundle (has `MANIFEST.MF`)
4. [ ] Is available from a p2 repository: n/a <!--<https://mvnrepository.com/artifact/edu.stanford.nlp/stanford-corenlp>-->

#### Feature matrix

<div style="font-size:.8rem;">

|                           | Has functionality        | Functionality extensible | Functionality documentation | Extension documentation      | Input data                           | Output data |
|---------------------------|--------------------------|--------------------------|-----------------------------|------------------------------|--------------------------------------|-------------|
| Tokenization/segmentation | X                        | X                        | <https://stanfordnlp.github.io/CoreNLP/tokenize.html> | <https://stanfordnlp.github.io/CoreNLP/faq.html#can-you-say-more-about-adding-a-custom-annotator>   | -string of document text </br> -CoreNLPs `CoreDocument` (Instatiated with string document text) | -list of strings </br> -list of characteroffsetbegin indices </br> -list of characteroffsetendindices </br> `CoreDocument` with previous annotation properties |
| Sentencing                | X                        | X                        | <https://stanfordnlp.github.io/CoreNLP/ssplit.html> | <https://stanfordnlp.github.io/CoreNLP/faq.html#can-you-say-more-about-adding-a-custom-annotator> | tokenized `CoreDocument` | `CoreDocument` with Sentence List of POS-Tags as property |
| POS-tagging               | X                        | X                        | <https://stanfordnlp.github.io/CoreNLP/pos.html> | <https://stanfordnlp.github.io/CoreNLP/faq.html#can-you-say-more-about-adding-a-custom-annotator> | tokenized and sentence-splitted `CoreDocument` | `CoreDocument` with String List of POS-Tags as property |
| Constituency parsing      | X                        | X                        | <https://stanfordnlp.github.io/CoreNLP/parse.html>  | <https://stanfordnlp.github.io/CoreNLP/faq.html#can-you-say-more-about-adding-a-custom-annotator> | tokenized, sentence-splitted (and for some models POS-tagged) `CoreDocument` | `CoreDocument` with TreeAnnotation (exact form depends on chosen parser) |
| Dependency parsing        | X                        | X                        |<https://stanfordnlp.github.io/CoreNLP/depparse.html> | <https://stanfordnlp.github.io/CoreNLP/faq.html#can-you-say-more-about-adding-a-custom-annotator> | tokenized, sentence-splitted and POS-tagged `CoreDocument` | `CoreDocument` with DependencyAnnotation (exact form depends on chosen parser)            |
| Trainable models          | X                        |                          | <https://stanfordnlp.github.io/CoreNLP/human-languages.html#models> | |                                |             |
| Can consume own models    | X                        | <!-- X or leave empty--> | <https://stanfordnlp.github.io/CoreNLP/caseless.html#training-caseless-models>                   |                           |                                      |             |


</div>

### [NLP Architect](<https://intellabs.github.io/nlp-architect/>)

1. [ ] Implemented in Java
   1. [ ] Not Java, but API can be addressed from Java
      - Can be addressed as follows: n/a <or add brief description of how to address the API>
2. [ ] Uses Maven (`pom.xml` exists)
3. [ ] Is available as OSGi bundle (has `MANIFEST.MF`)
4. [ ] Is available from a p2 repository: n/a

#### Feature matrix

<div style="font-size:.8rem;">

|                           | Has functionality | Multiple Options   | Functionality documentation | Is Trainable| Training documentation      | Input data                           | Output data |
|---------------------------|:--------------------------:|--------------------------|-----------------------------|:----------:|--------------------------------------|-------------|-------------|
| Tokenization/segmentation | <!-- X or leave empty--> | <!-- X or leave empty--> | <add url>                   | <eg string of document text> | <eg comma-separated list of strings> |             |
| Sentencing                | <!-- X or leave empty--> | <!-- X or leave empty--> | <add url>                   |                              |                                      |             |
| POS-tagging               | X | X | [POS-Tagger Documentation](<https://intellabs.github.io/nlp-architect/tagging/sequence_tagging.html>) | https://intellabs.github.io/nlp-architect/tagging/sequence_tagging.html#custom-training-parameters |                                      |             |
| Constituency parsing      | <!-- X or leave empty--> | <!-- X or leave empty--> | <add url>                   |                              |                                      |             |
| Dependency parsing        | X | X | [DepParse Documentation](<https://intellabs.github.io/nlp-architect/bist_parser.html>) |                              |                                      | - Filepath with POS-tagged Dataset in CONNLL-U format </br> -list of list of `ConllEntry`, where each entry represents a POS-tagged Token and each nested List a sentence  |          |
| Trainable models          | X | <!-- X or leave empty--> | <add url>                   |                              |                                      |             |
| Can consume own models    | X | <!-- X or leave empty--> | <add url>                   |                              |                                      |             |


</div>



### [Pattern](<https://github.com/clips/pattern>)

1. [ ] Implemented in Java
   1. [ ] Not Java, but API can be addressed from Java
      - Can be addressed as follows: n/a <or add brief description of how to address the API>
2. [ ] Uses Maven (`pom.xml` exists)
3. [ ] Is available as OSGi bundle (has `MANIFEST.MF`)
4. [ ] Is available from a p2 repository: ?

#### Feature matrix

<div style="font-size:.8rem;">

|                           | Has functionality | Multiple Options   | Functionality documentation | Is Trainable| Training documentation      | Input data                           | Output data |
|---------------------------|:--------------------------:|--------------------------|-----------------------------|:----------:|--------------------------------------|-------------|-------------|
| Tokenization/segmentation | X |  |[General documentation](<https://github.com/clips/pattern/wiki>)  |  | | String of text | nested list : [sentences[chunks[tokens]]]  |
| Sentencing                | X |  | [General documentation](<https://github.com/clips/pattern/wiki>)| |  | String of text | nested list : [sentences[chunks[tokens]]] |                                     |             |
| POS-tagging  | X |  | [General documentation](<https://github.com/clips/pattern/wiki>) |  |   | String of text | nested list : [sentences[chunks[tokens]]] |
| Constituency parsing      |  |  |   |  |   |                   |             |
| Dependency parsing        |  | | | |        |    |                                               |
| Functionalities extensible | |  |  |       |                              |             |
| Can consume own models    |  |  |  |    |                     |                 |             |


</div>


### [Lingpipe](<http://www.alias-i.com/lingpipe/>)

1. [X] Implemented in Java
   1. [ ] Not Java, but API can be addressed from Java
      - Can be addressed as follows: n/a <or add brief description of how to address the API>
2. [?] Uses Maven (`pom.xml` exists) <!-- Couldn't find pom.xml but https://mvnrepository.com/artifact/com.aliasi/lingpipe/4.0.1-->
3. [X] Is available as OSGi bundle (has `MANIFEST.MF`)
4. [?] Is available from a p2 repository: ? 

#### Feature matrix

<div style="font-size:.8rem;">

|                           | Has functionality        | Functionality extensible | Functionality documentation | Extension documentation      | Input data                           | Output data |
|---------------------------|--------------------------|--------------------------|-----------------------------|------------------------------|--------------------------------------|-------------|
| Tokenization/segmentation | X | <!-- X or leave empty--> | <http://www.alias-i.com/lingpipe-book/lingpipe-book-0.5.pdf> Chapter 3 (p.33) </br> <http://www.alias-i.com/lingpipe/docs/api/com/aliasi/tokenizer/Tokenizer.html> </br> -<http://www.alias-i.com/lingpipe/docs/api/com/aliasi/tokenizer/Tokenization.html> |  | -String of text </br> -Character array, Startindex, Endindex |             |
| Sentencing                | X | <!-- X or leave empty--> | <http://www.alias-i.com/lingpipe/demos/tutorial/sentences/read-me.html>                   |                              |                                      |             |
| POS-tagging               | X | <!-- X or leave empty--> | <http://www.alias-i.com/lingpipe/demos/tutorial/posTags/read-me.html> |                              |                                      |             |
| Constituency parsing      | <!-- X or leave empty--> | <!-- X or leave empty--> | <add url>                   |                              |                                      |             |
| Dependency parsing        | <!-- X or leave empty--> | <!-- X or leave empty--> | <add url>                   |                              |                                      |             |
| Trainable models          | <!-- X or leave empty--> | <!-- X or leave empty--> | <add url>                   |                              |                                      |             |
| Can consume own models    | <!-- X or leave empty--> | <!-- X or leave empty--> | <add url>                   |                              |                                      |             |


</div>

<!-- additional features: Topic Classification, Stemming, Lemmatization ,NER, Clustering, Spelling Correction, String Comparison, Interesting Phrase Detection, Hyphenation and Syllabification, Sentiment Analysis, Language Identification, Word Sense Disambiguation-->

### [SpaCy](<https://www.nltk.org/>)

1. [ ] Implemented in Java
   1. [ ] Not Java, but API can be addressed from Java
      - Can be addressed as follows: n/a <or add brief description of how to address the API>
2. [ ] Uses Maven (`pom.xml` exists)
3. [ ] Is available as OSGi bundle (has `MANIFEST.MF`)
4. [ ] Is available from a p2 repository: n/a

#### Feature matrix

<div style="font-size:.8rem;">

|                           | Has functionality        | Functionality extensible | Functionality documentation | Extension documentation      | Input data                           | Output data |
|---------------------------|--------------------------|--------------------------|-----------------------------|------------------------------|--------------------------------------|-------------|
| Tokenization/segmentation | X | X | <https://spacy.io/usage/linguistic-features#native-tokenizers> | -<https://spacy.io/usage/linguistic-features#special-cases> </br> -<https://spacy.io/usage/linguistic-features#native-tokenizers> | raw document text | SpaCy's `Doc` type |
| Sentencing                | X | X | <https://spacy.io/usage/linguistic-features#sbd> | <https://spacy.io/usage/linguistic-features#sbd-custom> | SpaCy's `Doc` type | SpaCy's `Doc` type |
| POS-tagging               | X |  | <https://spacy.io/usage/linguistic-features#pos-tagging> | | Spacy's `Doc` type                        |Spacy's `Doc` type |
| Constituency parsing      | <!-- X or leave empty--> | <!-- X or leave empty--> | <add url>                   |                              | <!--Spacy's `Doc` type--> | <!--Spacy's `Doc` type--> |
| Dependency parsing | X | | <https://spacy.io/usage/linguistic-features#dependency-parse> |                              | Spacy's `Doc` type | Spacy's `Doc` type |
| Trainable models          | X | <!-- X or leave empty--> | <https://spacy.io/usage/models>          |                              |                                      |             |
| Can consume own models    | X | <!-- X or leave empty--> | <https://spacy.io/usage/training> |                              |                                      |             |


</div>

### [Spark NLP](<https://nlp.johnsnowlabs.com/>)

1. [ ] Implemented in Java
   1. [ ] Not Java, but API can be addressed from Java
      - Can be addressed as follows: [Using Spark NLP via Scala and Maven](<https://nlp.johnsnowlabs.com/docs/en/install#scala-and-java>)
2. [X] Uses Maven (`pom.xml` exists)
3. [ ] Is available as OSGi bundle (has `MANIFEST.MF`)
4. [ ] Is available from a p2 repository: ? https://mvnrepository.com/artifact/JohnSnowLabs/spark-nlp

#### Feature matrix

<div style="font-size:.8rem;">

|                           | Has functionality | Multiple Options   | Functionality documentation | Is Trainable| Training documentation      | Input data                           | Output data |
|---------------------------|:--------------------------:|--------------------------|-----------------------------|:----------:|--------------------------------------|-------------|-------------|
| Tokenization/segmentation | X | [^2]  | [Tokenizer Documentation](<https://nlp.johnsnowlabs.com/docs/en/annotators#tokenizer>) |  |  | Document | Token |
| Sentencing                | X | [^2] | [Sentence Detector Documentation](<https://nlp.johnsnowlabs.com/docs/en/annotators#sentencedetector>) |   |  |  Document | Sentences |
| POS-tagging               | X | [^2] | [POS-Tagger Documentation](<https://nlp.johnsnowlabs.com/docs/en/annotators#postagger-part-of-speech-tagger>) |  X | [POS Training Documentation](<https://nlp.johnsnowlabs.com/docs/en/training#pos-dataset>) </br> [General Training Documentation](<https://nlp.johnsnowlabs.com/docs/en/concepts#training-annotators>)| Document, Token | POS |
| Constituency parsing      |  |  |  |  |  |   |  |
| Dependency parsing        | X | -[Typed Dependency Parser](<https://nlp.johnsnowlabs.com/docs/en/annotators#typed-dependency-parser-labeled-grammatical-relation>)</br>[Untyped Dependency Parser](<https://nlp.johnsnowlabs.com/docs/en/annotators#untyped-dependency-parser-unlabeled-grammatical-relation>) | [Dependency Parser Documentation](<https://nlp.johnsnowlabs.com/docs/en/annotators#dependency-parsers>)| X | [General Training Documentation](<https://nlp.johnsnowlabs.com/docs/en/concepts#training-annotators>)  | Document,POS,Token | (unlabeled) Dependeny |
| Functionalities extensible  | X | | [Manipulating Pipelines](<https://nlp.johnsnowlabs.com/docs/en/concepts#manipulating-pipelines>) |   |   |      |       |
| Can consume own models    | X  |  | [General Concept Documentation](<https://nlp.johnsnowlabs.com/docs/en/concepts>)   |  |     |   |  |


</div>

[^2]:Spark NLP provides a [library of pretrained Pipelines](<https://nlp.johnsnowlabs.com/docs/en/pipelines>) and a [library of models](<https://nlp.johnsnowlabs.com/models>). This survey however refers to the general Annotators.


### [TextBlob](<https://textblob.readthedocs.io/en/dev/>)

1. [ ] Implemented in Java
   1. [ ] Not Java, but API can be addressed from Java
      - Can be addressed as follows: n/a <or add brief description of how to address the API>
2. [ ] Uses Maven (`pom.xml` exists)
3. [ ] Is available as OSGi bundle (has `MANIFEST.MF`)
4. [ ] Is available from a p2 repository:

#### Feature matrix

<div style="font-size:.8rem;">

|                           | Has functionality | Multiple Options   | Functionality documentation | Is Trainable| Training documentation      | Input data                           | Output data |
|---------------------------|:--------------------------:|--------------------------|-----------------------------|:----------:|--------------------------------------|-------------|-------------|
| Tokenization/segmentation | X | | [Tokenization Tutorial](<https://textblob.readthedocs.io/en/dev/quickstart.html#tokenization>)</br>[Advanced Tokenization Documentation](<https://textblob.readthedocs.io/en/dev/advanced_usage.html#tokenizers>) | | | String of raw text | `TextBlob` data type - access through `words` property: WordList of word strings |
| Sentencing                | X |  | [Sentence-Splitting Tutorial](<https://textblob.readthedocs.io/en/dev/quickstart.html#tokenization>)</br>[Advanced Sentence-Splitting Documentation](<https://textblob.readthedocs.io/en/dev/advanced_usage.html#tokenizers>) | | | String of raw text | `TextBlob` data type - access through `sentences` property: List of Sentence Objects|
| POS-tagging               | X | -PatternTagger </br> -NLTKTagger  | [POS-Tagger Tutorial](<https://textblob.readthedocs.io/en/dev/quickstart.html#part-of-speech-tagging>) </br> [POS-Tagger Advanced Usage](<https://textblob.readthedocs.io/en/dev/advanced_usage.html#pos-taggers>) | | | String of raw text | `TextBlob` data type - access through `tags` property: List of word string tag string tuples |
| Constituency parsing      | X |  | [Parser Tutorial](<https://textblob.readthedocs.io/en/dev/quickstart.html#parsing>) </br> [Parser Advanced Usage](<https://textblob.readthedocs.io/en/dev/advanced_usage.html>)|               |               | String of raw text | `TextBlob` data type - access through `parse()` method: TaggedString |
| Dependency parsing        | X |  |[Parser Tutorial](<https://textblob.readthedocs.io/en/dev/quickstart.html#parsing>) </br> [Parser Advanced Usage](<https://textblob.readthedocs.io/en/dev/advanced_usage.html#>)|  | |String of raw text | `TextBlob` data type - access through `parse()` method: TaggedString |
|Functionalities extensible | |  |        |                              | | | |
| Can consume own models    |  X  |  | [Passing models into the Pipeline](<https://textblob.readthedocs.io/en/dev/advanced_usage.html#tokenizers>) </br> [Training own data](<https://textblob.readthedocs.io/en/dev/classifiers.html#classifiers>)       | |         |                              |  |



</div>


<!-- end of template -->

[^1]: The survey was carried out by Clara Lachenmaier.
