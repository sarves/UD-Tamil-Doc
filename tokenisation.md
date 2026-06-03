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

### MWE-01: Participial Nouns / வினையாலணையும் பெயர்

Participial nouns are forms that combine verbal and nominal properties. For example, **வந்தவன்** means “the one who came” or “the man who came”. It contains a verbal element, **வந்த** “came / who came”, and a nominal or pronominal element, **அவன்** “he / man”.

In UD annotation, these forms are treated as multiword tokens because they cannot be assigned a single UPOS category in a satisfactory way. The first part shows verbal behaviour, including tense information, while the second part shows nominal behaviour, such as reference to person, gender, number, and case-marking potential. Therefore, these forms should be tokenised into separate syntactic words.

This treatment is motivated by the mixed-category nature of such forms (https://kops.uni-konstanz.de/server/api/core/bitstreams/72c0aa32-7778-4f88-be85-79dcb3d4a0ba/content) : they show both verbal and nominal properties. For this reason, participial nouns should be split during multiword tokenisation.

| Surface form | Tokenisation | Gloss | Meaning |
|---|---|---|---|
| வந்தவன் | வந்த + அவன் | come-PST.RP + he/man | the man who came |
| வந்தவள் | வந்த + அவள் | come-PST.RP + she/woman | the woman who came |
| வந்தவர்கள் | வந்த + அவர்கள் | come-PST.RP + they/people | the people who came |
| வருகிறவர்கள் | வருகிற + அவர்கள் | come-PRS.RP + they/people | the people who come / are coming |

#### Example

```text
வருகிறவர்கள் மாணவர்கள்.
வருகிற அவர்கள் மாணவர்கள் .
வருகிற       அவர்கள்       மாணவர்கள்
come-PRS.RP  they/people   students
The people who are coming are students.
```

Participial nouns such as **வந்தவன்**, **வந்தவள்**, **வந்தவர்கள்**, **செய்தவன்**, and **படித்தவன்** should be tokenised as multiword tokens when the form contains both a relative participial/verbal element and a nominal or pronominal element. This tokenisation allows the verbal element to receive a verbal analysis and the nominal element to receive a nominal or pronominal analysis. 

### Clitic

#### Clitic **-உம் / -ம்** (-um)

The form **-உம் / -ம்** is very common in Tamil texts. It is used to mark different syntactic and semantic functions in different constructions. Depending on the context, it may express additivity, emphasis, totality, concession, enumeration, alternative coordination, paired contrast, or predicative coordination.

Traditional Tamil grammar, including the **Tolkāppiyam** tradition, identifies eight major uses of **-உம்**. In Universal Dependencies (UD), however, these uses can mostly be handled using either **PART** or **CCONJ**, depending on the syntactic role of **-உம்** in the sentence.


##### Traditional uses of **-உம் / -ம்**

| Tamil term | English translation | Basic function |
|---|---|---|
| எச்சம் | residual / additive inclusion | Indicates that the marked item is included, while others are also implied |
| சிறப்பு | special emphasis / scalar emphasis | Highlights something by elevating or lowering it; often similar to ‘even’ |
| ஐயம் | doubt / uncertainty / alternative | Marks uncertainty, doubt, or alternatives |
| எதிர்மறை | contrast / contrary / concessive meaning | Indicates a meaning contrary to expectation; often similar to ‘even if’ |
| முற்று | totality / completeness | Indicates completeness or total inclusion |
| எண் | enumeration | Lists several items in sequence |
| தெரிநிலை | explicit contrast / clarificatory contrast | Clarifies a contrastive meaning, often in paired expressions |
| ஆக்கம் | change of state / becoming | Indicates change into another state or quality, often with coordinated predicates |


---

##### Additive inclusion / எச்சம்

**எச்சம்** indicates an incomplete or residual meaning: the marked item is included, but other relevant items are also implied.

Examples:

| Surface form | Tokenisation | Gloss | Meaning |
|---|---|---|---|
| இராமனும் வந்தான் | இராமன் + உம் வந்தான் | Raman-ADD come-PST.3MSG | Raman also came |

Rule:

```text
இராமனும் → இராமன் + உம்
```

Explanation:

In **இராமனும் வந்தான்**, **-உம்** means ‘also/too’. It implies that Raman came in addition to others. Since it does not link two overt noun phrases in the sentence, it is treated as **PART**, not **CCONJ**.

UD-oriented decision:

```text
-உம் → PART
```

---

##### Scalar emphasis / சிறப்பு

**சிறப்பு** gives special emphasis. It may elevate or lower the referent on a scale. In many contexts, it is close to English **even**.

Examples:

| Surface form | Tokenisation | Gloss | Meaning |
|---|---|---|---|
| அறிஞருக்கும் எட்டாப்பொருள் | அறிஞர் + க்கு + உம் எட்டா + பொருள் | scholar-DAT-ADD reach.NEG-thing | a thing beyond even scholars |

Rule:

```text
அறிஞருக்கும் → அறிஞர் + க்கு + உம்
```

Explanation:

Here **-உம்** gives scalar focus. It means that the thing is beyond scholars too, or even beyond scholars. Since **-உம்** modifies the scope of one phrase and does not coordinate two overt elements, it is treated as **PART**.

UD-oriented decision:

```text
-உம் → PART
```

---

##### Totality / முற்று

**முற்று** indicates totality or completeness.

Examples:

| Surface form | Tokenisation | Gloss | Meaning |
|---|---|---|---|
| எல்லாரும் வந்தனர் | எல்லார் + உம் வந்தனர் | everyone-ADD come-PST.3PL | Everyone came |

Rule:

```text
எல்லாரும் → எல்லார் + உம்
```

Explanation:

In **எல்லாரும் வந்தனர்**, **-உம்** contributes a totality meaning. It marks the whole set as included. It does not coordinate separate overt elements. Therefore, it is treated as **PART**.

UD-oriented decision:

```text
-உம் → PART
```

---

##### Concessive meaning / எதிர்மறை

**எதிர்மறை** gives a contrary or concessive meaning, often similar to **even if**.

Examples:

| Surface form | Tokenisation | Gloss | Meaning |
|---|---|---|---|
| நாள் தவறினும் நாத்தவறான் | நாள் தவறு + இன் + உம் நா + தவறு + ஆன் | day fail-COND-CONC tongue-fail-NEG.3MSG | Even if the day fails, his word will not fail |

Rule:

```text
தவறினும் → தவறு + இன் + உம்
```

Explanation:

Here **-உம்** contributes a concessive meaning. It does not coordinate two overt comparable elements. Therefore, it is treated as **PART**.

UD-oriented decision:

```text
-உம் → PART
```

---

##### **-உம் / -ம்** as `CCONJ`

When **-உம் / -ம்** links two or more overt comparable elements, it functions conjunctively. In such cases, it participates in a coordination structure and may be treated as a coordinating conjunction.

Use:

```text
UPOS = CCONJ
```

This applies especially when **-உம்** is used in:

```text
enumeration
alternative coordination
paired contrast
predicative coordination
```

This includes uses such as **எண்**, **ஐயம்**, **தெரிநிலை**, and **ஆக்கம்**.

---

##### Enumeration / எண்

**எண்** is used when several items are listed in sequence.

Examples:

| Surface form | Tokenisation | Gloss | Meaning |
|---|---|---|---|
| நிலமும் நீரும் தீயும் | நிலம் + உம் நீர் + உம் தீ + உம் | earth-CONJ water-CONJ fire-CONJ | earth, water and fire |

Rule:

```text
நிலமும் → நிலம் + உம்
நீரும் → நீர் + உம்
தீயும் → தீ + உம்
```

Explanation:

Here **-உம்** links several nominal elements: **நிலம்**, **நீர்**, and **தீ**. Since it links overt comparable elements in an enumeration, it functions as a coordinator.

UD-oriented decision:

```text
-உம் → CCONJ
```

---

##### Alternative or doubtful coordination / ஐயம்

**ஐயம்** marks uncertainty, doubt, or alternatives. In UD terms, when **-உம்** links comparable alternatives, it can be treated as conjunctive.

Examples:

| Surface form | Tokenisation | Gloss | Meaning |
|---|---|---|---|
| பத்தாயினும் எட்டாயினும் கிடைக்கும் | பத்து + ஆயின் + உம் எட்டு + ஆயின் + உம் கிடைக்கும் | ten-be.COND-CONJ eight-be.COND-CONJ get-FUT/PRS | Whether ten or eight, it will be available |

Rule:

```text
பத்தாயினும் → பத்து + ஆயின் + உம்
எட்டாயினும் → எட்டு + ஆயின் + உம்
```

Explanation:

Here **-உம்** occurs in an alternative structure, similar to **whether…or**. Since it links comparable alternatives, it may be treated as **CCONJ**.

UD-oriented decision:

```text
-உம் → CCONJ
```

---

##### Paired contrast / தெரிநிலை

**தெரிநிலை** clarifies a contrastive meaning, often in paired expressions.

Examples:

| Surface form | Tokenisation | Gloss | Meaning |
|---|---|---|---|
| நன்றும் அன்று தீதும் அன்று | நன்று + உம் அன்று தீது + உம் அன்று | good-CONJ not bad-CONJ not | It is neither good nor bad |

Rule:

```text
நன்றும் → நன்று + உம்
தீதும் → தீது + உம்
```

Explanation:

Here **-உம்** participates in a paired contrastive structure. The expression is similar to **neither good nor bad**. Since it links two comparable elements in a contrastive coordination, it is treated as **CCONJ**.

UD-oriented decision:

```text
-உம் → CCONJ
```

---

##### Predicative coordination / ஆக்கம்

**ஆக்கம்** indicates a change into another state or quality. In this use, **-உம்** often links two predicative nominal or adjectival elements.

Examples:

| Surface form | Tokenisation | Gloss | Meaning |
|---|---|---|---|
| நெடியனும் வலியனும் ஆயினான் | நெடியன் + உம் வலியன் + உம் ஆயினான் | tall.one-CONJ strong.one-CONJ become-PST.3MSG | He became tall and strong |

Rule:

```text
நெடியனும் → நெடியன் + உம்
வலியனும் → வலியன் + உம்
```

Explanation:

Here **-உம்** links two predicative nominal/adjectival elements: **நெடியன்** and **வலியன்**. Since these are coordinated predicative properties, **-உம்** functions as a conjunctive marker.

UD-oriented decision:

```text
-உம் → CCONJ
```

---



The annotation of **-உம் / -ம்** should be based on its syntactic function, not only on the traditional Tamil grammatical label.

Rule:

```text
If -உம் modifies the scope of one word or phrase → PART
If -உம் links two or more overt comparable elements → CCONJ
```

In other words:

```text
-உம் as additive/focus/scalar/totality/concessive marker (**எச்சம்**, **சிறப்பு**, **முற்று**, **எதிர்மறை**) → PART
-உம் as coordinator in enumeration or paired structures   → CCONJ
```

---


The traditional eight-way classification of **-உம்** is useful for understanding Tamil grammar and meaning. However, it should not be mapped mechanically to UD categories.

For UD annotation, we can use an idea like,

```text
Does -உம் modify one element, or does it link multiple elements?
```

If it modifies one element, annotate it as **PART**.

If it links multiple comparable elements, annotate it as **CCONJ**.
