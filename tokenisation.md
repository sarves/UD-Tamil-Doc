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
