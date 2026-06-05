## Head-final Tamil and head-initial dependency notation

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

```text
என் பையன்கள் வந்தார்கள் . \n eṉ paiyaṉkaḷ vantārkaḷ .  \n My boys came .
root(ROOT, வந்தார்கள்)
root(ROOT, vantārkaḷ)
root(ROOT, came)
```

Source example: `sent_id = 1`.

### `punct`: punctuation

Punctuation marks attached to the relevant head.

```text
என் பையன்கள் வந்தார்கள் . \n eṉ paiyaṉkaḷ vantārkaḷ .  \n My boys came .
eṉ paiyaṉkaḷ vantārkaḷ .
punct(வந்தார்கள், .)
punct(vantārkaḷ, .)
root(came, .)
```

Source example: `sent_id = 1`.

### `nsubj`: nominal subject

Marks the nominal subject of a clause. Tamil also has non-canonical subjects, usually marked with dative marker, is discussed later.

```text
என் பையன்கள் வந்தார்கள் . \n eṉ paiyaṉkaḷ vantārkaḷ .  \n My boys came .
eṉ paiyaṉkaḷ vantārkaḷ .
nsubj(வந்தார்கள், பையன்கள்)
nsubj(vantārkaḷ, paiyaṉkaḷ)
nsubj(came, boys)

```

Source example: `sent_id = 1`.

### `nsubj:nc`: non-canonical subject

A Tamil-specific subtype used in the dataset for non-canonical subjects, particularly dative experiencers or possessor-like subjects where the predicate does not license PNG (Person-Number-Gender) agreement.

```text
குமாருக்கு ஒரு வீடு வேண்டும் . \n kumārukku oru vīṭu vēṇṭum . \n Kumar-dat  a house want
nsubj:nc(வேண்டும், குமாருக்கு)
nsubj:nc(vēṇṭum, kumārukku)
nsubj:nc(want, Kumar-dat)


```

Source example: `sent_id = 32`.


### `nsubj:pass`: passive nominal subject

Marks the subject of a passive predicate. In Tamil, the passive voice is realized using an auxiliary verb. The main verb — rather than the auxiliary token that marks the passive, tense, and PNG features — is considered the head. In this case, In this case, passive auxiliary may also receive `aux:pass`.

```text
குமார் அப்பாவால் அடிக்கப் பட்டான் . \n kumār appāvāl aṭikkap paṭṭāṉ . \n Kumar father-by beat-inf was .
nsubj:pass(அடிக்கப், குமார்)
nsubj:pass(aṭikkap, kumār)
nsubj:pass(beat-inf, Kumar)

```

Source example: `sent_id = 48`.

### `obj`: object

Marks the direct object or patient-like core argument, which is typically marked by the accusative case marker (ஐ i) in Tamil. For irrational objects, this marking is optional; when present, it also differential-marks definiteness. However, accusative marking is obligatory for rational nouns.

```text
இந்த புத்தகத்தைக் கொடுங்கள் . \n inta puttakattaik koṭuṅkaḷ . \n this book-acc give-you .
obj(கொடுங்கள், புத்தகத்தைக்)
obj(koṭuṅkaḷ, puttakattaik)
obj(give-you, book-acc)

```

Source example: `sent_id = 14`.


### `iobj`: indirect object

Marks a recipient- or benefactive-like core object when another object is present. Although the indirect object (iobj) is marked using the dative suffix (-kku / -க்கு), not all dative-marked nouns function as an iobj. Depending on the predicate, a dative nominal may instead function as a dative core object (obj) or an oblique locative (obl).

```text
குமார் அப்பாவுக்கு ஒரு படத்தைக் காட்டினான் . \n kumār appāvukku oru paṭattaik kāṭṭiṉāṉ . \n Kumar father-dat a picture-acc saw-he .
iobj(காட்டினான், அப்பாவுக்கு)
iobj(kāṭṭiṉāṉ, appāvukku)
iobj(saw-he, father-dat)

```
