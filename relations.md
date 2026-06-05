Tamil is generally a head-final language, meaning that objects, modifiers, case-marked nominals, and subordinate clauses typically precede their head. However, to maintain compatibility with UD annotation guidelines, the dependency notation follows a head-initial convention.


## Relations covered

The following relations are documented because they occur in the MWTT treebank.

```text
acl
acl:relcl
advcl
advcl:cond
advmod
advmod:emph
amod
aux
aux:neg
aux:pass
case
cc
compound
compound:lvc
compound:redup
conj
det
fixed
iobj
mark
nmod
nmod:poss
nsubj
nsubj:nc
nsubj:pass
nummod
obj
obl
obl:agent
obl:arg
obl:cmpr
obl:inst
obl:lmod
obl:pmod
obl:tmod
punct
root
vocative
xcomp
```

Some labels in the MWTT data are language-specific subtypes, such as `nsubj:nc`, `aux:neg`, `obl:cmpr`, `obl:inst`, and `obl:pmod`.

## Core clause relations

### `root`: root

Marks the main head of the sentence. The root has `HEAD=0`.

~~~sdparse
என் பையன்கள் வந்தார்கள் . \n eṉ paiyaṉkaḷ vantārkaḷ .  \n My boys came .
root(ROOT, வந்தார்கள்)
root(ROOT, vantārkaḷ)
root(ROOT, came)
~~~

Source example: `sent_id = 1`.

### `punct`: punctuation

Punctuation marks attached to the relevant head.

~~~sdparse
என் பையன்கள் வந்தார்கள் . \n eṉ paiyaṉkaḷ vantārkaḷ .  \n My boys came .
eṉ paiyaṉkaḷ vantārkaḷ .
punct(வந்தார்கள், .)
punct(vantārkaḷ, .)
root(came, .)
~~~

Source example: `sent_id = 1`.

### `nsubj`: nominal subject

Marks the nominal subject of a clause. Tamil also has non-canonical subjects, usually marked with dative marker, is discussed later.

~~~sdparse
என் பையன்கள் வந்தார்கள் . \n eṉ paiyaṉkaḷ vantārkaḷ .  \n My boys came .
eṉ paiyaṉkaḷ vantārkaḷ .
nsubj(வந்தார்கள், பையன்கள்)
nsubj(vantārkaḷ, paiyaṉkaḷ)
nsubj(came, boys)

~~~

Source example: `sent_id = 1`.

### `nsubj:nc`: non-canonical subject

A Tamil-specific subtype used in the dataset for non-canonical subjects, particularly dative experiencers or possessor-like subjects where the predicate does not license PNG (Person-Number-Gender) agreement. Although Universal Dependencies (UDv2) guidelines typically treat these non-canonical nominals as obliques rather than core subjects (nsubj) due to their dative case marking and lack of regular nominative behavior, we deviate from the standard framework here to align with established Tamil linguistic literature. Furthermore, these nominals do not entirely lose their subjecthood, as they consistently pass syntactic subjecthood tests such as binding reflexive anaphors.

~~~sdparse
குமாருக்கு தலை வலிக்கிறது . \n kumārukku talai valikkiṟatu . \n Kumar-DAT head pain-it
nsubj:nc(வலிக்கிறது, குமாருக்கு)
nsubj:nc(valikkiṟatu, kumārukku)
nsubj:nc(pain-it, Kumar-dat)


~~~

Source example: `sent_id = 424`.


### `nsubj:pass`: passive nominal subject

Marks the subject of a passive predicate. In Tamil, the passive voice is realized using an auxiliary verb. The main verb — rather than the auxiliary token that marks the passive, tense, and PNG features — is considered the head. In this case, In this case, passive auxiliary may also receive `aux:pass`.

~~~sdparse
குமார் அப்பாவால் அடிக்கப் பட்டான் . \n kumār appāvāl aṭikkap paṭṭāṉ . \n Kumar father-by beat-inf was .
nsubj:pass(அடிக்கப், குமார்)
nsubj:pass(aṭikkap, kumār)
nsubj:pass(beat-inf, Kumar)

~~~

Source example: `sent_id = 48`.

### `obj`: object

Marks the direct object or patient-like core argument, which is typically marked by the accusative case marker (ஐ i) in Tamil. For irrational objects, this marking is optional; when present, it also differential-marks definiteness. However, accusative marking is obligatory for rational nouns.

~~~sdparse
இந்த புத்தகத்தைக் கொடுங்கள் . \n inta puttakattaik koṭuṅkaḷ . \n this book-acc give-you .
obj(கொடுங்கள், புத்தகத்தைக்)
obj(koṭuṅkaḷ, puttakattaik)
obj(give-you, book-acc)

~~~

Source example: `sent_id = 14`.


### `iobj`: indirect object

Marks a recipient- or benefactive-like core object when another object is present. Although the indirect object (iobj) is marked using the dative suffix (-kku / -க்கு), not all dative-marked nouns function as an iobj. Depending on the predicate, a dative nominal may instead function as a dative core object (obj) or an oblique locative (obl).

~~~sdparse
குமார் அப்பாவுக்கு ஒரு படத்தைக் காட்டினான் . \n kumār appāvukku oru paṭattaik kāṭṭiṉāṉ . \n Kumar father-dat a picture-acc saw-he .
iobj(காட்டினான், அப்பாவுக்கு)
iobj(kāṭṭiṉāṉ, appāvukku)
iobj(saw-he, father-dat)

~~~

Source example: `sent_id = 23`.


## Clausal relations

### `acl`: clausal modifier of noun

Marks a clause modifying a nominal. 

~~~sdparse
எவன் நேற்று வந்தானோ அவன் என் தம்பி . \n evaṉ nēṟṟu vantāṉō avaṉ eṉ tampi . \n who yesterday came-who he my brother .
acl(தம்பி, வந்தானோ)
acl(tampi, வந்தானோ)
acl(brother, came-who)
~~~

Source example: `sent_id = 334`.

### `acl:relcl`: relative clause modifier

Marks a relative-clause-like modifier of a noun, often expressed through Tamil relative participles - (-a/-அ). Tamil often uses relative participial forms rather than English-style relative pronouns.

~~~sdparse
குமாருக்கு வேண்டிய புத்தகம் . \n kumārukku vēṇṭiya puttakam . \n Kumar-DAT want-RP book .
acl:relcl(புத்தகம், வேண்டிய)
acl:relcl(puttakam, vēṇṭiya)
acl:relcl(book, want-RP)
~~~

Source example: `sent_id = 119`.


### `advcl`: adverbial clause modifier

Marks a clausal modifier of another predicate.

~~~sdparse
குமாருக்கு இந்தத் துணி வேண்டவே வேண்டாம் . \n kumārukku intat tuṇi vēṇṭavē vēṇṭām . \n Kumar-DAT this cloth want-not-absolutely want-not.
advcl(வேண்டாம், வேண்டவே)
advcl(vēṇṭām, vēṇṭavē)
advcl(want-not, want-not-absolutely)
~~~

Source example: `sent_id = 122`.

### `advcl:cond`: conditional adverbial clause

Marks a conditional clause modifying another predicate.

~~~sdparse
நீ உண்மை சொன்னால் பிழைத்தாய் . \n nī uṇmai coṉṉāl piḻaittāy . \n you truth said-if survive
advcl:cond(பிழைத்தாய், சொன்னால்)
advcl:cond(piḻaittāy, coṉṉāl)
advcl:cond(survive, said-if)
~~~

Source example: `sent_id = 72`.

### `xcomp`: open clausal complement

Marks a complement without its own independent subject; its subject is controlled by the higher predicate.

~~~sdparse
நான் குமாரை கேட்க வருகிறேன் . \n nāṉ kumārai kēṭka varukiṟēṉ . \n I Kumar-ACC ask-INF come-I
xcomp(வருகிறேன், கேட்க)
xcomp(varukiṟēṉ, kēṭka)
xcomp(come-I, ask-INF)
~~~

Source example: `sent_id = 6`.

### `mark`: marker

Marks a clause-linking or subordination marker. Use `mark` for clause markers. Use `case` for nominal case markers or postpositions.

~~~sdparse
குமார் நல்லவன் போலத் தோன்றுகிறான் . \n kumār nallavaṉ pōla tōṉṟukiṟāṉ . \n Kumar good-boy like appear-he .
mark(தோன்றுகிறான், போல)
mark(tōṉṟukiṟāṉ, pōla)
mark(like appear-he, like)
~~~

Source example: `sent_id = 395`.
