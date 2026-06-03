## Lexicalised ADV + Verb Forms

Some Tamil verbs may appear to contain an adverbial element plus a verb. For example, **முன்னேறு, பின்வாங்கு** can be understood as involving **முன்** “front / forward” and **ஏறு** “climb / rise”. However, in modern usage, **முன்னேறு** functions as a single lexical verb meaning “advance”, “progress”, or “move forward”.

Therefore, such forms should **not** be split during multiword tokenisation.

### Example

```text
அவன் வாழ்க்கையில் முன்னேறினான்.
he      life-LOC          progress-PST-3SG.M
He progressed in life.
```

The form **முன்னேறினான்** should not be tokenised as:

```text
முன் + ஏறினான்
```

## 1 Noun + ஆக _āka_ / ஆன _āṉa_ Forms

Tamil has forms where a noun combines with **ஆக** / _āka_ or **ஆன** / _āṉa_ to form adverbial or adjectival expressions. These forms should usually **not be split during multiword tokenisation** as they function as lexicalised adverbs or adjectives.

### Noun + ஆக: Adverb Formation

The element **ஆக** / _āka_ can combine with a noun to form an adverbial expression.

Example:

```text
அவன் அமைதியாக பேசினான்
he      calmly          speak-PST-3SG.M
He spoke calmly


அமைதியாக    ADV
பேசினான்    VERB
```

The form **அமைதியாக** should not be split as:

```text
அமைதி + ஆக
```

More examples: அமைதியாக calmly, வேகமாக  quickly, அழகாக beautifully, தெளிவாக clearly, மெதுவாக slowly

### Noun + ஆன: Adjective Formation

The element **ஆன** / _āṉa_ can combine with a noun to form an adjectival expression.

Example:

```text
அவன் முக்கியமான முடிவை எடுத்தான்.
அவன்    முக்கியமான      முடிவை        எடுத்தான்
he      important       decision-ACC  take-PST-3SG.M
He took an important decision.

முக்கியமான    ADJ     amod
முடிவை        NOUN
```

The form **முக்கியமான** should not be split as:

```text
முக்கியம் + ஆன
```

More examples: அழகான beautiful, அமைதியான peaceful, தேவையான  necessary, சரியான  correct


## 1 Noun + ஆக _āka_ / ஆன _āṉa_ Forms
