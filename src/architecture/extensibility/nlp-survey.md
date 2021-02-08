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
---
### [AllenNLP](<https://allennlp.org/>)

1. [ ] Implemented in Java
   1. [ ] Not Java, but API can be addressed from Java
      - Can be addressed as follows: there are some [taggers](<https://github.com/allenai/taggers>) and [NLPstack](<https://github.com/allenai/nlpstack>) available as Scala-packages. AllenNLP also provides [Docker images](<https://github.com/allenai/allennlp#installing-using-docker>)
2. [ ] Uses Maven (`pom.xml` exists)
3. [ ] Is available as OSGi bundle (has `MANIFEST.MF`)
4. [ ] Is available from a p2 repository: n/a

#### Feature matrix

<div style="font-size:.8rem;">

|                           | Has functionality | Multiple Options   | Functionality documentation | Is Trainable| Training documentation      | Input data                           | Output data |
|---------------------------|:--------------------------:|--------------------------|-----------------------------|:----------:|--------------------------------------|-------------|-------------|
| Tokenization/segmentation | X | [-SpacyTokenizer](<https://docs.allennlp.org/v1.3.0/api/data/tokenizers/spacy_tokenizer/>)</br> [-PretrainedTransformerTokenizer](<https://docs.allennlp.org/v1.3.0/api/data/tokenizers/pretrained_transformer_tokenizer/>) | [AllenNLP Tokenizer Documentation](<https://docs.allennlp.org/v1.3.0/api/data/tokenizers/tokenizer/>) | | | Text as str | List[Token] |
| Sentencing | X | -Sentence Splitter </br> -SpaCy Sentence Splitter | [Sentence Splitter API](<https://docs.allennlp.org/v1.3.0/api/data/tokenizers/sentence_splitter/>) | |  | Text as str  |  List[str] |
| POS-tagging               |  |  |   | X | [Train SentenceTaggerPredictor](<https://docs.allennlp.org/v1.3.0/api/predictors/sentence_tagger/#sentencetaggerpredictor>) | Sentence as str | Dict[str, numpy.ndarray] |
| Constituency parsing      | X |  | [Constituency Parser Demo](<https://demo.allennlp.org/constituency-parsing/constituency-parser>)                   |                              |                                      |             |    |
| Dependency parsing        | X |  | [Dependency Parser Demo](<https://demo.allennlp.org/dependency-parsing/dependency-parser>)    |    |       |                                      |             |
| Named Entity Recognition  | | | | X | [Train SentenceTaggerPredictor](<https://docs.allennlp.org/v1.3.0/api/predictors/sentence_tagger/#sentencetaggerpredictor>) | Sentence as str | Dict[str, numpy.ndarray] | 
| Functionalities extensible |  |  |   |  |  |  |  |
| Can consume own models    | X  |  | [Building own models in AllenNLP](<https://guide.allennlp.org/building-your-model>) |  |  |  |  |


</div>



### [Apache OpenNLP](<https://opennlp.apache.org/>)

1. [x] Implemented in Java
   1. [ ] Not Java, but API can be addressed from Java
      - Can be addressed as follows: n/a <or add brief description of how to address the API>
2. [x] Uses Maven (`pom.xml` exists)
3. [ ] Is available as OSGi bundle (has `MANIFEST.MF`)<!-- Not sure about that. MANIFEST.MF doesn't exist but there is this: https://opennlp.apache.org/docs/1.8.3/apidocs/opennlp-tools/opennlp/tools/util/ext/OSGiExtensionLoader.html-->
4. [X] Is available from a p2 repository: <https://mvnrepository.com/artifact/org.apache.opennlp/opennlp-tools>
#### Feature matrix

<div style="font-size:.8rem;">

|                           | Has functionality | Multiple Options | Functionality documentation | Is Trainable | Training documentation | Input data                           | Output data |
|---------------------------|:--------------------------:|--------------------------|-----------------------------|:----------:|--------------------------------------|-------------|-------------|
| Tokenization/segmentation |X|-Whitespace Tokenizer </br> -Character Tokenizer </br> -Maximum Entropy Tokenizer |<https://opennlp.apache.org/docs/1.9.0/manual/opennlp.html#tools.tokenizer.api>| X | <https://opennlp.apache.org/docs/1.9.0/manual/opennlp.html#tools.tokenizer.training.api> |string of (untokenized) text | array of strings</br> -array of token spans|
| Sentencing|X| |<https://opennlp.apache.org/docs/1.9.0/manual/opennlp.html#tools.sentdetect.detection.api>| X | <https://opennlp.apache.org/docs/1.9.0/manual/opennlp.html#tools.sentdetect.training.api> |string of document text | -array of strings</br> -array of sentence spans |
| POS-tagging| X |  | <https://opennlp.apache.org/docs/1.9.0/manual/opennlp.html#tools.postagger.tagging.api> | x | <https://opennlp.apache.org/docs/1.9.0/manual/opennlp.html#tools.postagger.training.api> | string array of tokens | string array of tags |
| Constituency parsing      | X |  | <https://opennlp.apache.org/docs/1.9.0/manual/opennlp.html#tools.parser.parsing.api> | X | <https://opennlp.apache.org/docs/1.9.0/manual/opennlp.html#tools.parser.training.api> | String of whitespace tokenized Sentence | array of OpenNLP's Parse Type |
| Dependency parsing  | | | | | | | |
| Named Entity Recognition  | X | | [NER Documentaion](<https://opennlp.apache.org/docs/1.9.3/manual/opennlp.html#tools.namefind>)| X | [NER Training Documentation] (<https://opennlp.apache.org/docs/1.9.3/manual/opennlp.html#tools.namefind.training>) | | |
|Functionalities extensible|X| | <https://opennlp.apache.org/docs/1.9.0/manual/opennlp.html#tools.extension.writing>| |String of Text | Span Array |
| Can consume own models    |  |  | |  |             | | |

</div>
<!-- additional features: Language Detector, NER, Document Categorizer, Lemmatization, Chunking, Coreference Resolution-->


### [CogComp NLP Pipeline](<https://github.com/CogComp/cogcomp-nlp/tree/master/pipeline>)

1. [X] Implemented in Java
   1. [ ] Not Java, but API can be addressed from Java
      - Can be addressed as follows: n/a <or add brief description of how to address the API>
2. [X] Uses Maven (`pom.xml` exists)
3. [ ] Is available as OSGi bundle (has `MANIFEST.MF`)
4. [X] Is available from a p2 repository: <https://mvnrepository.com/artifact/edu.illinois.cs.cogcomp/illinois-nlp-pipeline>

#### Feature matrix

<div style="font-size:.8rem;">

|                           | Has functionality | Multiple Options   | Functionality documentation | Is Trainable| Training documentation      | Input data                           | Output data |
|---------------------------|:--------------------------:|--------------------------|-----------------------------|:----------:|--------------------------------------|-------------|-------------|
| Tokenization/segmentation | X |  | [General description](<https://github.com/CogComp/cogcomp-nlp/tree/master/pipeline#components-and-requirements>) | | | String of raw text | `TextAnnotation` data structure with method `.getView(Viewname)` for each Annotation |
| Sentencing                |  |  |  |                              |  |  |  |
| POS-tagging               | X | | [General description](<https://github.com/CogComp/cogcomp-nlp/tree/master/pipeline#components-and-requirements>) |               |             | String of raw text | `TextAnnotation` data structure with `View` for each Annotation |
| Constituency parsing      | X | | [General description](<https://github.com/CogComp/cogcomp-nlp/tree/master/pipeline#components-and-requirements>)</br> [Parser documentation](<https://nlp.stanford.edu/software/lex-parser.shtml> )                  |             |           | String of raw text | `TextAnnotation` data structure with method `.getView(Viewname)` for each Annotation |
| Dependency parsing        | X | -Stanford NLP Parser </br> -CogComp Parser (requires POS-Tagger and Chunker as part of the Pipeline) | [General description](<https://github.com/CogComp/cogcomp-nlp/tree/master/pipeline#components-and-requirements>)</br> [Stanford Parser documentation](<https://nlp.stanford.edu/software/lex-parser.shtml> )  |         |                     | String of raw text | `TextAnnotation` data structure with method `.getView(Viewname)` for each Annotation |
| Named Entity Recognition  | X (isn't part of the Pipeline) | | [NER Documentation](<https://github.com/CogComp/cogcomp-nlp/blob/master/ner/README.md>) | X | [Training Documentation](<https://github.com/CogComp/cogcomp-nlp/blob/master/ner/README.md#how-to-train-the-tagger-on-new-data>) | String of raw text | `TextAnnotation` data structure with `View` for each Annotation |
| Functionalities extensible  | X |  | [Configuration documentation](<https://github.com/CogComp/cogcomp-nlp/tree/master/pipeline#configuration-options>)  |                              |  |  | |
| Can consume own models    | X | | [Use own Tokenizer](<https://github.com/CogComp/cogcomp-nlp/tree/master/pipeline#usage>) |                              |  |  | |


</div>


### [GATE & ANNIE](<https://gate.ac.uk/family/embedded.html>)

1. [X] Implemented in Java
   1. [ ] Not Java, but API can be addressed from Java
      - Can be addressed as follows: n/a <or add brief description of how to address the API>
2. [X] Uses Maven (`pom.xml` exists)
3. [ ] Is available as OSGi bundle (has `MANIFEST.MF`)
4. [ ] Is available from a p2 repository:

#### Feature matrix

<div style="font-size:.8rem;">

|                           | Has functionality | Multiple Options   | Functionality documentation | Is Trainable| Training documentation      | Input data                           | Output data |
|---------------------------|:--------------------------:|--------------------------|-----------------------------|:----------:|--------------------------------------|-------------|-------------|
| Tokenization/segmentation | X |  | [ANNIE Tokenizer Documentation](<https://gate.ac.uk/sale/tao/splitch6.html#sec:annie:tokeniser> )| |  | <eg string of document text> | <eg comma-separated list of strings> |          
| Sentencing                | X | -ANNIE Default Sentence Splitter</br>-ANNIE Regex Sentence Splitter | [ANNIE Sentence Splitter Documentation](<https://gate.ac.uk/sale/tao/splitch6.html#sec:annie:splitter> )                  |                              |                                      |             |
| POS-tagging               | X | <!-- X or leave empty--> | [ANNIE POS-Tagger Documentation](<https://gate.ac.uk/sale/tao/splitch6.html#sec:annie:tagger>)                   |                              |                                      |             |
| Constituency parsing      | <!-- X or leave empty--> | <!-- X or leave empty--> | <add url>                   |                              |                                      |             |
| Dependency parsing        | <!-- X or leave empty--> | <!-- X or leave empty--> | <add url>                   |                              |                                      |             |
| Named Entity Recognition  | x | | [Gazeteer documentation](<https://gate.ac.uk/sale/tao/splitch6.html#sec:annie:gazetteer>) | | | | |
| Trainable models          | <!-- X or leave empty--> | <!-- X or leave empty--> | <add url>                   |                              |                                      |             |
| Can consume own models    | <!-- X or leave empty--> | <!-- X or leave empty--> | <add url>                   |                              |                                      |             |

<!-- Further Features:gazeteer (i.e. simple NER),  Semantic Tagger, Orthografic and pronominal coreference -->
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
| Named Entity Recognition  | X | [Neural Tagger- CNNLSTM module](<https://intellabs.github.io/nlp-architect/tagging/sequence_tagging.html#cnnlstm>)</br> [Neural Tagger- IDCNN](<https://intellabs.github.io/nlp-architect/tagging/sequence_tagging.html#idcnn>)</br>[Transformer Token Classifier](<https://intellabs.github.io/nlp-architect/tagging/sequence_tagging.html#transformertokenclassifier>) | [NER Documentation](<https://intellabs.github.io/nlp-architect/tagging/sequence_tagging.html#named-entity-recognition>) | X | [NER Training Documentation](<https://intellabs.github.io/nlp-architect/tagging/sequence_tagging.html#cnnlstm>) | | |
| Trainable models          | X | <!-- X or leave empty--> | <add url>                   |                              |                                      |             |
| Can consume own models    | X | <!-- X or leave empty--> | <add url>                   |                              |                                      |             |


</div>

### [NLP4J](<https://emorynlp.github.io/nlp4j/>)

1. [x] Implemented in Java
   1. [ ] Not Java, but API can be addressed from Java
      - Can be addressed as follows: n/a <or add brief description of how to address the API>
2. [X] Uses Maven (`pom.xml` exists)
3. [ ] Is available as OSGi bundle (has `MANIFEST.MF`)
4. [X] Is available from a p2 repository: <https://mvnrepository.com/artifact/org.nlp4j/nlp4j-core>

#### Feature matrix

<div style="font-size:.8rem;">

|                           | Has functionality | Multiple Options   | Functionality documentation | Is Trainable| Training documentation      | Input data                           | Output data |
|---------------------------|:--------------------------:|--------------------------|-----------------------------|:----------:|--------------------------------------|-------------|-------------|
| Tokenization/segmentation | X  | | [Tokenizer basic information](<https://emorynlp.github.io/nlp4j/components/tokenization.html>)</br>[Tokenizer Demo](<https://github.com/emorynlp/nlp4j/blob/master/api/src/test/java/edu/emory/mathcs/nlp/component/tokenizer/TokenizerDemo.java>) | X | [Basic Training information](<https://emorynlp.github.io/nlp4j/quickstart/train.html>) | -string line of text </br> -Raw document text </br> tsv-format | List of Token types |
| Sentencing | | | | | | | |
| POS-tagging               | X |  | [POS-Tag basic information](<https://emorynlp.github.io/nlp4j/components/part-of-speech-tagging.html>) | X | [Basic Training information](<https://emorynlp.github.io/nlp4j/quickstart/train.html>) | -string line of text </br> -Raw document text </br> tsv-format | Output-file with annotations|
| Constituency parsing      |  |  |  |  |  |  |  |
| Dependency parsing        | X  |  | [Dependency Parse basic information](<https://emorynlp.github.io/nlp4j/components/dependency-parsing.html>)                   | X | [Basic Training information](<https://emorynlp.github.io/nlp4j/quickstart/train.html>) | -string line of text </br> -Raw document text </br> tsv-format | Output-file with annotations |
| Named Entity Recognition  | X | | [NER Documentation](<https://emorynlp.github.io/nlp4j/components/named-entity-recognition.html>)| X | [Basic Training information](<https://emorynlp.github.io/nlp4j/quickstart/train.html>) | -string line of text </br> -Raw document text </br> tsv-format | Output-file with annotations |
| Functionalities extensible |  |  |  |  |  |  |  |
| Can consume own models    |  |  |  |  |  |  |  |


</div>


### [NLTK](<https://www.nltk.org/>)

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
| Tokenization/segmentation | X | [-Casual module](<https://www.nltk.org/api/nltk.tokenize.html#module-nltk.tokenize.casual>) </br> [-Destructive module](<https://www.nltk.org/api/nltk.tokenize.html#module-nltk.tokenize.destructive>)</br>[-Regexp Tokenizer](<https://www.nltk.org/api/nltk.tokenize.html#module-nltk.tokenize.regexp>)</br> [-Repp Tokenizer](<https://www.nltk.org/api/nltk.tokenize.html#module-nltk.tokenize.repp>)</br> [-Simple Tokenizer](<https://www.nltk.org/api/nltk.tokenize.html#module-nltk.tokenize.simple>)</br> [-Stanford Segmenter](<https://www.nltk.org/api/nltk.tokenize.html#module-nltk.tokenize.stanford_segmenter>) </br> [-TokTok Tokenizer](<https://www.nltk.org/api/nltk.tokenize.html#module-nltk.tokenize.toktok>) </br> [-Penn Treebank Tokenizer](<https://www.nltk.org/api/nltk.tokenize.html#module-nltk.tokenize.treebank>)| [-NLTK Tokenizer/Sentence Splitter Documentation](<https://www.nltk.org/api/nltk.tokenize.html#module-nltk.tokenize>)</br> [-NLTK Book Chapter 3](<https://www.nltk.org/book/ch03.html>)           |        | | String | String of Text | List of Token Strings            |
| Sentencing                | X | [-Punkt Sent Module](<https://www.nltk.org/api/nltk.tokenize.html#module-nltk.tokenize.punkt>)</br>[-Regexp Tokenizer](<https://www.nltk.org/api/nltk.tokenize.html#module-nltk.tokenize.regexp>)</br> [-Simple Tokenizer](<https://www.nltk.org/api/nltk.tokenize.html#module-nltk.tokenize.simple>) | [-NLTK Tokenizer/Sentence Splitter Documentation](<https://www.nltk.org/api/nltk.tokenize.html#module-nltk.tokenizel>)</br> [-NLTK Book Chapter 3](<https://www.nltk.org/book/ch03.html>) |X | [-Punkt Sent Module](<https://www.nltk.org/api/nltk.tokenize.html#module-nltk.tokenize.punkt>)  | String of Text | List of Sentence Strings  |
| POS-tagging               | X | [-Brill Tagger](<https://www.nltk.org/api/nltk.tag.html#module-nltk.tag.brill>)</br>[-CRF Tagger](<https://www.nltk.org/api/nltk.tag.html#module-nltk.tag.crf>)</br>[-HMM Tagger](<https://www.nltk.org/api/nltk.tag.html#module-nltk.tag.hmm>) </br>[-HunPos Tagger](<https://www.nltk.org/api/nltk.tag.html#module-nltk.tag.hunpos>)</br>[-Perceptron Tagger](<https://www.nltk.org/api/nltk.tag.html#module-nltk.tag.perceptron>)</br>[-Senna POS Tagger](<https://www.nltk.org/api/nltk.tag.html#module-nltk.tag.senna>)</br>[-Sequential Backoff Tagger](<https://www.nltk.org/api/nltk.tag.html#module-nltk.tag.sequential>)</br>[-Stanford Tagger](<https://www.nltk.org/api/nltk.tag.html#module-nltk.tag.stanford>)</br>[-TNT Tagger](<https://www.nltk.org/api/nltk.tag.html#module-nltk.tag.tnt>)| [-NLTK Tagger Documentation](<https://www.nltk.org/api/nltk.tag.html#module-nltk.tag>)</br>[-NLTK Book Chapter 5](<http://www.nltk.org/book/ch05.html>)  | X| [-Brill Tagger Training](<https://www.nltk.org/api/nltk.tag.html#module-nltk.tag.brill_trainer>)</br>[-CRF Tagger](<https://www.nltk.org/api/nltk.tag.html#module-nltk.tag.crf>)</br>[-HMM Tagger](<https://www.nltk.org/api/nltk.tag.html#module-nltk.tag.hmm>)  </br>[HunPos Tagger](<https://www.nltk.org/api/nltk.tag.html#module-nltk.tag.hunpos>)</br>[-Perceptron Tagger](<https://www.nltk.org/api/nltk.tag.html#module-nltk.tag.perceptron>)</br> [-Sequential Backoff Tagger](<https://www.nltk.org/api/nltk.tag.html#module-nltk.tag.sequential>)</br>[-Stanford Tagger](<https://www.nltk.org/api/nltk.tag.html#module-nltk.tag.stanford>)</br>[-TNT Tagger](<https://www.nltk.org/api/nltk.tag.html#module-nltk.tag.tnt>)            | tokens (list(str))</br> sentences (list(list(str))) |  list(tuple(str, str)) </br> list(list(tuple(str, str)) ) |
| Constituency parsing | X | [-Early Chart Parser](<https://www.nltk.org/api/nltk.parse.html#module-nltk.parse.earleychart>) </br> [-Recursive descent Parser](<https://www.nltk.org/api/nltk.parse.html#module-nltk.parse.recursivedescent>)</br> [-Shift Reduce Parser](<https://www.nltk.org/api/nltk.parse.html#module-nltk.parse.shiftreduce>)</br>[-Standford Parser](<https://www.nltk.org/api/nltk.parse.html#module-nltk.parse.stanford>)</br> | [-NLTK Parser Documentation](<https://www.nltk.org/api/nltk.parse.html#module-nltk.parse>)</br>[-NLTK Book - Chapter 8](<https://www.nltk.org/book/ch08.html>)                   |              |                |    sent (list(str)) </br> sentences (list(list(str))) |   iter(Tree) </br> iter(iter(Tree))  |
| Dependency parsing        | X | [-CoreNLP Dependency Parser](<https://www.nltk.org/api/nltk.parse.html#module-nltk.parse.corenlp>) </br> [-Malt Parser](<https://www.nltk.org/api/nltk.parse.html#module-nltk.parse.malt>) </br>[-Nonprojective Dependency Parser](<https://www.nltk.org/api/nltk.parse.html#module-nltk.parse.nonprojectivedependencyparser>)</br>[-Projective Dependency Parser](<https://www.nltk.org/api/nltk.parse.html#module-nltk.parse.projectivedependencyparser>)</br>[-Transition Parser](<https://www.nltk.org/api/nltk.parse.html#module-nltk.parse.transitionparser>) | [-NLTK Parser Documentation](<https://www.nltk.org/api/nltk.parse.html#module-nltk.parse>)[-NLTK Book - Chapter 8 Pargraph 5](<https://www.nltk.org/book/ch08.html>)  | X | [Malt Parser](<https://www.nltk.org/api/nltk.parse.html#module-nltk.parse.malt>) </br>[-Nonprojective Dependency Parser](<https://www.nltk.org/api/nltk.parse.html#module-nltk.parse.nonprojectivedependencyparser>) </br>[-Projective Dependency Parser](<https://www.nltk.org/api/nltk.parse.html#module-nltk.parse.projectivedependencyparser>)</br>[-Transition Parser](<https://www.nltk.org/api/nltk.parse.html#module-nltk.parse.transitionparser>)         |    CoreNLP: sentences (list(str)) – Input sentences to parse </br> Malt:     sentences | CoreNLP: iter(iter(Tree)) </br> Malt:iter(DependencyGraph) |
| Named Entity Recognition  | X |  | [NLTK Book Chapter 7 Paragraph 5](< https://www.nltk.org/book/ch07.html>) </br> [-NE Chunker](<https://www.nltk.org/api/nltk.chunk.html#module-nltk.chunk.named_entity>)| X | [-NE Chunker](<https://www.nltk.org/api/nltk.chunk.html#module-nltk.chunk.named_entity>)| list of Pos-Tagged tokens | |
| Functionalities extensible  | |  |  |  |  |  |  |
| Can consume own models    | X  |  |   |  |  |  |  |


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
| Named Entity Recognition  | | | | | | | |
| Functionalities extensible | |  |  |       |                              |             |
| Can consume own models    |  |  |  |    |                     |                 |             |


</div>



### [Lingpipe](<http://www.alias-i.com/lingpipe/>)

1. [X] Implemented in Java
   1. [ ] Not Java, but API can be addressed from Java
      - Can be addressed as follows: n/a <or add brief description of how to address the API>
2. [?] Uses Maven (`pom.xml` exists) <!-- Couldn't find pom.xml but https://mvnrepository.com/artifact/com.aliasi/lingpipe/4.0.1-->
3. [X] Is available as OSGi bundle (has `MANIFEST.MF`)
4. [X] Is available from a p2 repository: <https://mvnrepository.com/artifact/com.aliasi/lingpipe>

#### Feature matrix

<div style="font-size:.8rem;">

|                           | Has functionality | Multiple Options   | Functionality documentation | Is Trainable| Training documentation      | Input data                           | Output data |
|---------------------------|:--------------------------:|--------------------------|-----------------------------|:----------:|--------------------------------------|-------------|-------------|
| Tokenization/segmentation | X | [-IndoEuropeanTokenizer](<http://www.alias-i.com/lingpipe/docs/api/com/aliasi/tokenizer/IndoEuropeanTokenizerFactory.html>)</br>[-CharacterTokenizer](<http://www.alias-i.com/lingpipe/docs/api/index.html>)</br>[-RegExTokenizer](<http://www.alias-i.com/lingpipe/docs/api/com/aliasi/tokenizer/RegExTokenizerFactory.html>)</br>[-NGramTokenizer](<http://www.alias-i.com/lingpipe/docs/api/index.html>)</br>[-LineTokenizerFactory](<http://www.alias-i.com/lingpipe/docs/api/com/aliasi/tokenizer/LineTokenizerFactory.html>) | [Lingpipe Book](<http://www.alias-i.com/lingpipe-book/lingpipe-book-0.5.pdf>) Chapter 3 (p.33) </br> [Tokenizer API](<http://www.alias-i.com/lingpipe/docs/api/com/aliasi/tokenizer/Tokenizer.html>) </br> [Tokenization API](<http://www.alias-i.com/lingpipe/docs/api/com/aliasi/tokenizer/Tokenization.html> )| |  | -String of text </br> -Character array, Startindex, Endindex |             |
| Sentencing                | X |  | [Sentence-Splitter Tutorial](<http://www.alias-i.com/lingpipe/demos/tutorial/sentences/read-me.html> )| X |  |                                     |             |
| POS-tagging               | X | [-Chain CRF Tagger](<http://www.alias-i.com/lingpipe/docs/api/com/aliasi/crf/ChainCrf.html>)</br>[-Classifier Tagger](<http://www.alias-i.com/lingpipe/docs/api/com/aliasi/tag/ClassifierTagger.html>)</br>[-HMMDecoder](<http://www.alias-i.com/lingpipe/docs/api/com/aliasi/hmm/HmmDecoder.html>) | [-Lingpipe Book Chapter 11](<http://www.alias-i.com/lingpipe-book/lingpipe-book-0.5.pdf#chapter.11>)</br>[-POS-Tagger Tutorial](<http://www.alias-i.com/lingpipe/demos/tutorial/posTags/read-me.html>) | X | [POS-Tagger Tutorial Paragraph: Training Training Part-of-Speech Models](<http://www.alias-i.com/lingpipe/demos/tutorial/posTags/read-me.html>)    | List<String> tokenList | [Tagging<String>](<http://www.alias-i.com/lingpipe/docs/api/index.html>) |
| Constituency parsing      | <!-- X or leave empty--> | <!-- X or leave empty--> | <add url>                   |                              |                                      |             |
| Dependency parsing        | <!-- X or leave empty--> | <!-- X or leave empty--> | <add url>                   |                              |  | |     |
| Named Entity Recognition  | X | | [NER Documentation](<http://www.alias-i.com/lingpipe/demos/tutorial/ne/read-me.html>)| | | | |
| Functionalities extensible  | X | | [Paragraph 3. Evaluating and Tuning Tagging Models](<http://www.alias-i.com/lingpipe/demos/tutorial/posTags/read-me.html>)  |  |    |                                      |             |
| Can consume own models    | X  | | [Developing and Tuning Sentence Models](<http://www.alias-i.com/lingpipe/demos/tutorial/sentences/read-me.html>)                   |                              |                                      |             |


</div>

<!-- additional features: Topic Classification, Stemming, Lemmatization ,NER, Clustering, Spelling Correction, String Comparison, Interesting Phrase Detection, Hyphenation and Syllabification, Sentiment Analysis, Language Identification, Word Sense Disambiguation-->

### [SpaCy](<https://spacy.io/>)

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
| Tokenization/segmentation | X |  | [Tokenizer Documentaion](<https://spacy.io/usage/linguistic-features#native-tokenizers> )|  | |raw document text | SpaCy's `Doc` type - tokens accessible through `token.text` property |
| Sentencing                | X |  | [Sentencizer Documentation](<https://spacy.io/usage/linguistic-features#sbd>) | | | SpaCy's `Doc` type | SpaCy's `Doc` type - sentence access through `doc.sents` property |
| POS-tagging               | X |  | [POS-Tagger Documentation](<https://spacy.io/usage/linguistic-features#pos-tagging>) |X | [Training Basics](<https://spacy.io/usage/training>)</br> [Updating POS-Tagger](<https://spacy.io/usage/training#example-train-tagger>) | Spacy's `Doc` type                        |Spacy's `Doc` type - POS-Tags access through`token.pos_` attribute|
| Constituency parsing      |  | | | | | | |
| Dependency parsing | X | | [Parser Documentation](<https://spacy.io/usage/linguistic-features#dependency-parse>) |     X| [Training Basics](<https://spacy.io/usage/training>)</br>[Updating Dependencs Parser](<https://spacy.io/usage/training#example-train-parser>) | Spacy's `Doc` type | Spacy's `Doc` type - Parse-tags access through `token.dep_` attribute  |
| Named Entity Recognition  | X | | [NER Documentation](<https://spacy.io/usage/linguistic-features#named-entities>)| | |SpaCy's `Doc` type | SpaCy's `Doc` type - entitytags access through `doc.ents` property|
| Functionalities extensible | X |  | [Extend Tokenizer](<https://spacy.io/usage/linguistic-features#special-cases>)</br> [Customize Tokenizer](<https://spacy.io/usage/linguistic-features#native-tokenizers>) </br> [Custom Component](<https://spacy.io/usage/processing-pipelines#custom-components>)         |                              |                                      |             |
| Can consume own models    | (X) |  | [Load different Tokenizer](<https://spacy.io/usage/linguistic-features#custom-tokenizer>)
 |                              |                                      |             |


</div>

### [Spark NLP](<https://nlp.johnsnowlabs.com/>)

1. [ ] Implemented in Java
   1. [ ] Not Java, but API can be addressed from Java
      - Can be addressed as follows: [Using Spark NLP via Scala and Maven](<https://nlp.johnsnowlabs.com/docs/en/install#scala-and-java>)
2. [X] Uses Maven (`pom.xml` exists)
3. [ ] Is available as OSGi bundle (has `MANIFEST.MF`)
4. [X] Is available from a p2 repository: <https://mvnrepository.com/artifact/JohnSnowLabs/spark-nlp>

#### Feature matrix

<div style="font-size:.8rem;">

|                           | Has functionality | Multiple Options   | Functionality documentation | Is Trainable| Training documentation      | Input data                           | Output data |
|---------------------------|:--------------------------:|--------------------------|-----------------------------|:----------:|--------------------------------------|-------------|-------------|
| Tokenization/segmentation | X | [^2]  | [Tokenizer Documentation](<https://nlp.johnsnowlabs.com/docs/en/annotators#tokenizer>) |  |  | Document | Token |
| Sentencing                | X | [^2] | [Sentence Detector Documentation](<https://nlp.johnsnowlabs.com/docs/en/annotators#sentencedetector>) |   |  |  Document | Sentences |
| POS-tagging               | X | [^2] | [POS-Tagger Documentation](<https://nlp.johnsnowlabs.com/docs/en/annotators#postagger-part-of-speech-tagger>) |  X | [POS Training Documentation](<https://nlp.johnsnowlabs.com/docs/en/training#pos-dataset>) </br> [General Training Documentation](<https://nlp.johnsnowlabs.com/docs/en/concepts#training-annotators>)| Document, Token | POS |
| Constituency parsing      |  |  |  |  |  |   |  |
| Dependency parsing        | X | [-Typed Dependency Parser](<https://nlp.johnsnowlabs.com/docs/en/annotators#typed-dependency-parser-labeled-grammatical-relation>)</br>[Untyped Dependency Parser](<https://nlp.johnsnowlabs.com/docs/en/annotators#untyped-dependency-parser-unlabeled-grammatical-relation>) | [Dependency Parser Documentation](<https://nlp.johnsnowlabs.com/docs/en/annotators#dependency-parsers>)| X | [General Training Documentation](<https://nlp.johnsnowlabs.com/docs/en/concepts#training-annotators>)  | Document,POS,Token | (unlabeled) Dependeny |
| Named Entity Recognition  | X | [-NER CRF](<https://nlp.johnsnowlabs.com/docs/en/annotators#ner-crf-named-entity-recognition-crf-annotator>) </br> [-NER DL](<https://nlp.johnsnowlabs.com/docs/en/annotators#ner-dl-named-entity-recognition-deep-learning-annotator>)| [NER Documentation](<>)| X |  [-NER CRF](<https://nlp.johnsnowlabs.com/docs/en/annotators#ner-crf-named-entity-recognition-crf-annotator>) </br> [-NER DL](<https://nlp.johnsnowlabs.com/docs/en/annotators#ner-dl-named-entity-recognition-deep-learning-annotator>) | | |
| Functionalities extensible  | X | | [Manipulating Pipelines](<https://nlp.johnsnowlabs.com/docs/en/concepts#manipulating-pipelines>) |   |   |      |       |
| Can consume own models    | X  |  | [General Concept Documentation](<https://nlp.johnsnowlabs.com/docs/en/concepts>)   |  |     |   |  |


</div>

[^2]:Spark NLP provides a [library of pretrained Pipelines](<https://nlp.johnsnowlabs.com/docs/en/pipelines>) and a [library of models](<https://nlp.johnsnowlabs.com/models>). This survey however refers to the general Annotators.

### [Stanford CoreNLP](<https://stanfordnlp.github.io/CoreNLP/>)

1. [X] Implemented in Java
   1. [ ] Not Java, but API can be addressed from Java
      - Can be addressed as follows: n/a <or add brief description of how to address the API>
2. [X] Uses Maven (`pom.xml` exists)
3. [X] Is available as OSGi bundle (has `MANIFEST.MF`)
4. [X] Is available from a p2 repository: <https://mvnrepository.com/artifact/edu.stanford.nlp/stanford-corenlp>

#### Feature matrix

<div style="font-size:.8rem;">

|                           | Has functionality | Multiple Options   | Functionality documentation | Is Trainable| Training documentation      | Input data                           | Output data |
|---------------------------|:--------------------------:|--------------------------|-----------------------------|:----------:|--------------------------------------|-------------|-------------|
| Tokenization/segmentation | X | see [list](<https://nlp.stanford.edu/nlp/javadoc/javanlp/>) of classes implementing the Tokenizer interface  | [Tokenizer Documentation](<https://stanfordnlp.github.io/CoreNLP/tokenize.html>) | | | -string of document text </br> -CoreNLPs `CoreDocument` (Instatiated with string document text) | -list of strings </br> -list of characteroffsetbegin indices </br> -list of characteroffsetendindices </br> `CoreDocument` with previous annotation properties |
| Sentencing | X |  | [Sentencer Documentation](<https://stanfordnlp.github.io/CoreNLP/ssplit.html>) | | | tokenized `CoreDocument` | `CoreDocument` with Sentence List of POS-Tags as property |
| POS-tagging               | X |                        | [POS-Tag Documentation](<https://stanfordnlp.github.io/CoreNLP/pos.html>) | | | tokenized and sentence-splitted `CoreDocument` | `CoreDocument` with String List of POS-Tags as property |
| Constituency parsing      | X | [Viterbi Parser](<https://nlp.stanford.edu/nlp/javadoc/javanlp/edu/stanford/nlp/parser/ViterbiParserWithOptions.html>) </br> [Shift reduce Parser](<https://nlp.stanford.edu/software/srparser.html>)</br> [Iterative CKYPCFG Parser](<https://nlp.stanford.edu/nlp/javadoc/javanlp/edu/stanford/nlp/parser/lexparser/IterativeCKYPCFGParser.html>)</br> [Fast Factored Parser](<https://nlp.stanford.edu/nlp/javadoc/javanlp/edu/stanford/nlp/parser/lexparser/FastFactoredParser.html>) </br> [Exhaustive PCFG Parser](<https://nlp.stanford.edu/nlp/javadoc/javanlp/edu/stanford/nlp/parser/lexparser/ExhaustivePCFGParser.html>) | [Constituency Parser Documentation](<https://stanfordnlp.github.io/CoreNLP/parse.html>) | |  | tokenized, sentence-splitted (and for some models POS-tagged) `CoreDocument` | `CoreDocument` with TreeAnnotation (exact form depends on chosen parser) |
| Dependency parsing | X |[BiLexPCFGParser](<https://nlp.stanford.edu/nlp/javadoc/javanlp/edu/stanford/nlp/parser/lexparser/BiLexPCFGParser.html>)</br> [Exhaustive Dependency Parser](<https://nlp.stanford.edu/nlp/javadoc/javanlp/edu/stanford/nlp/parser/lexparser/ExhaustiveDependencyParser.html>) |[DepParse Documentation](<https://stanfordnlp.github.io/CoreNLP/depparse.html>) | X | [Train own Model](<https://stanfordnlp.github.io/CoreNLP/depparse.html#training-a-model>) |tokenized, sentence-splitted and POS-tagged `CoreDocument` | `CoreDocument` with DependencyAnnotation (exact form depends on chosen parser) |
| Named Entity Recognition  | X | [NER Classifier Combiner](<>https://stanfordnlp.github.io/CoreNLP/ner.html) </br> [-RegexNERAnnotator](<https://stanfordnlp.github.io/CoreNLP/regexner.html>)  | [NER Documentation](<https://stanfordnlp.github.io/CoreNLP/ner.html>)| X | [NER Training Documentation](<https://stanfordnlp.github.io/CoreNLP/ner.html#training-or-retraining-new-models>) | tokenized, ssplitted, pos-tagged, (lemmatized) `CoreDocument` | `CoreDocument` with `NamedEntityTagAnnotation` or `NormalizedNamedEntityTagAnnotation`|
| Functionalities extensible | X | [Custom annotator](<https://stanfordnlp.github.io/CoreNLP/new_annotator.html>) | |                                |             |
| Can consume own models    | X  | | [Example of including own (caseless) model](<https://stanfordnlp.github.io/CoreNLP/caseless.html#training-caseless-models>)                   |                           |                                      |             |


</div>


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
| Named Entity Recognition  | | | | | | | |
| Functionalities extensible | |  |        |                              | | | |
| Can consume own models    |  X  |  | [Passing models into the Pipeline](<https://textblob.readthedocs.io/en/dev/advanced_usage.html#tokenizers>) </br> [Training own data](<https://textblob.readthedocs.io/en/dev/classifiers.html#classifiers>)       | |         |                              |  |



</div>


<!-- end of template -->

[^1]: The survey was carried out by Clara Lachenmaier.
