## Multiword Tokenisation

UD annotation is based on syntactic words rather than purely orthographic words. Therefore, a single written Tamil form may sometimes need to be split into more than one syntactic word. This is especially relevant for forms involving clitics, auxiliaries, and certain postpositional elements.

Multiword tokenisation should be applied only when the separated elements are syntactically relevant. It should not be used to split every morphologically complex word. Annotators should follow the general UD principles on tokenisation and word segmentation before applying the Tamil-specific rules: https://universaldependencies.org/u/overview/tokenization.html

The example sentences used in this document are taken from the grammar books *A Grammar of Modern Tamil* by Thomas Lehmann and *Adippadai Tamil Ilakkanam* by M. A. Nuhman.

## Tokenisation Workflow

The input to the annotation process is a document or text file. As a first step, the text is divided into individual sentences through sentence tokenisation. Each sentence is then processed separately for word tokenisation.

In the initial stage of word tokenisation, tokens are usually identified by splitting the sentence at whitespace boundaries. Punctuation marks are also treated as separate tokens. Therefore, a space should be introduced before and after punctuation symbols such as:

```text
! ( ) - [ ] { } ; : ' " \ , < > . / ? @ # $ % ^ & * _ ~

For example:

```text
அவன் வந்தான்.
```

is tokenised as:

```text
அவன் வந்தான் .
```

After this basic tokenisation, multiword tokens must be identified and split where necessary. This is a critical stage in Tamil UD annotation, because a single written form may contain more than one syntactic word. Such cases cannot be handled by simple whitespace- or punctuation-based tokenisation alone.

Multiword tokenisation requires careful linguistic analysis. Annotators should decide whether a surface form should be split by considering its syntactic function, morphological structure, and the UD guidelines. Some common cases include forms involving clitics, auxiliaries, postpositions, and particles.

## Multiword Tokens

In Tamil, spaces are normally used to separate tokens in a sentence. If two words are separated by a space, they are usually treated as different tokens. However, Tamil also has many surface forms where more than one linguistic unit is written together as a single orthographic word.

These forms may include noun-noun compounds, verb-verb compounds, verb-noun forms, and words with clitics. For example:

| Type | Example | Possible segmentation |
|---|---|---|
| Noun-noun compound | விசைப்படகு | விசை + படகு |
| Verb-verb compound | வந்துகொண்டிருக்கிறான் | வந்து + கொண்டு + இருக்கிறான் |
| Verb-noun form | செய்தவன் | செய்த + அவன் |
| Clitic attachment | அவனும் | அவன் + உம் |

Such forms may need to be split into multiple syntactic tokens depending on the context and the UD annotation principles. The purpose is not to split every compound word mechanically, but to identify cases where the parts function as separate syntactic units.

Multiword tokenisation is important because a single written Tamil word may contain information that corresponds to more than one syntactic word. If these forms are not split, it becomes difficult to assign accurate UPOS tags, morphological features, and dependency relations. It also affects cross-lingual comparison, because the same syntactic structure may be represented as separate words in another language. Therefore, careful multiword tokenisation helps make Tamil annotation more consistent, transparent, and comparable with other UD treebanks.
