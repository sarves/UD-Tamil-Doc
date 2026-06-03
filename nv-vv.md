# Multiword Tokenisation: Verb–Verb and Noun–Verb Constructions

This section discusses multiword tokenisation cases involving **V+V** and **N+V** constructions in Tamil. These include auxiliary verb constructions, serial verb constructions, light verb constructions, and open clausal complements.

At the tokenisation stage, these forms may look similar because more than one verbal or verbal-like element appears together. However, they should not all be treated in the same way syntactically. The final distinction between these constructions will be made during UD syntactic annotation using dependency labels.

The potential syntactic relation labels used to distinguish these constructions include:

```text
aux
compound:svc
compound:lvc
xcomp
```

In this section on multiword tokenisation, only the following broad structural types are discussed:

```text
V + V
N + V
```

## Tamil Verbal Forms: Infinitive and Verbal Participle

In traditional Tamil grammar, the **infinitive** form is represented by forms such as:

```text
செய்ய
ceyya
to do
```

The **verbal participle** form is represented by forms such as:

```text
செய்து
ceytu
having done / do-CVB
```

In actual sentences, these forms may combine with another verb. For example:

```text
செய்யமுடியும்
ceyyamutiyum
ceyya-mutiyum
do.INF-can.PRS
can do
```

```text
செய்துவிட்டான்
ceytuviṭṭāṉ
ceytu viṭṭāṉ
do.CVB-left.3SGM
he finished doing
```

In UD annotation, these elements are treated according to their syntactic function. For example, an infinitival verb may be analysed as an `xcomp`, while an auxiliary-like verb may be analysed using `aux`. Verbal participle constructions may be analysed as auxiliary constructions, serial verb constructions, or other complex predicates depending on their function.

---

## Auxiliary Verb Constructions

Auxiliary verb constructions involve a lexical verb and an auxiliary verb. The auxiliary verb contributes grammatical meaning such as aspect, mood, passive voice, causation, polarity, or attitude.

These constructions are usually of the form:

```text
V + AUX
```

Example:

```text
அவன் செய்துவிட்டான். 
```

Tokenisation:

```text
அவன் செய்து விட்டான் .
```

Gloss:

```text
அவன்    செய்து     விட்டான்
he      do-CVB     leave-PST-3SG.M
He finished doing it.
```
Here, **விடு** has the lexical meaning “leave”, but in this construction it contributes completive aspect.

### Auxiliary Verbs in Tamil

Source: Thomas Lehmann, *A Grammar of Modern Tamil*, Pondicherry Institute of Linguistics and Culture, 1989.

| Grammatical type | Tamil auxiliary | Transliteration | Lexical meaning | Grammatical meaning |
|---|---|---|---|---|
| Aspect | ஆகு | āku | become | change of state |
| Aspect | ஆயிற்று | āyiṟṟu | became | completive / resultative |
| Aspect | இரு | iru | be | perfect or continuative, has/have |
| Aspect | விடு | viṭu | leave | completive or perfective |
| Mood | ஆம் | ām | — | possibility / permission |
| Mood | ஆகாது | ākātu | not become | impossibility or prohibition |
| Mood | இரு | iru | be | modal-like auxiliary in some constructions |
| Mood | கூட | kūṭu | join | possibility, can |
| Mood | அட்டும் | aṭṭum | let | permissive / optative |
| Mood | பார் | pār | see, look | try |
| Mood | போ | pō | go | prospective aspect |
| Mood | வா | vā | come | towards-speaker orientation |
| Mood | மாட்டு | māṭṭu | be unwilling / be unable | negative modal |
| Mood | முடி | muṭi | finish, complete | ability, can |
| Mood | வேண்டும் | vēṇṭum | want, need, pray | obligation or necessity |
| Passive | படு | paṭu | undergo, suffer, sleep | passive voice |
| Causation | வை | vai | keep, place | causative or make |
| Causation | செய் | cey | do | causative or light verb-like support |
| Causation | பண்ணு | paṇṇu | do | causative or light verb-like support |
| Negative polarity | இல்லை | illai | be not / not exist | negation |
| Attitude | கிட | kiṭa / kiṭai | lie / be available / get | attitude / speaker evaluation |
| Attitude | கிழி | kiḻi | tear | attitude / speaker evaluation |
| Attitude | தள்ளு | taḷḷu | push | attitude / forceful completion |
| Attitude | தீர் | tīr | solve, finish | completive / exhaustive meaning |
| Attitude | தொலை | tolai | lose, miss | negative attitude / undesirable event |
| Attitude | போ | pō | go |  undesirable completion |
| Attitude | போடு | pōṭu | put | sudden / forceful completion |
| Non-attitude | அழு | aḻu | cry, weep | non-attitudinal auxiliary use |
| Non-attitude | கொடு | koṭu | give | benefactive  |
| Non-attitude | கொள் | koḷ | take, hold | reflexive / self-benefactive |
| Non-attitude | பார் | pār | see, look | attemptive, try |
| Non-attitude | வை | vai | keep, place | resultative / causative-like support |

---

## Serial Verb Constructions

Serial verb constructions involve more than one verb in the same clause, where the verbs together describe a closely connected event sequence. In Tamil, the first verb often appears in the verbal participle form.

These constructions are usually of the form:

```text
V-CVB + V
```

Example:

```text
அவன் ஓடிவந்தான்.
அவன் ஓடி வந்தான் .
he      run-CVB    come-PST-3SG.M
He came running.
```

Possible UD analysis:

```text
ஓடி       VERB
வந்தான்   VERB     and the rel lable would be compound:svc
```

In this construction, both verbs contribute lexical meaning. The action involves both **running** and **coming**. Therefore, this is different from an auxiliary construction, where the second verb mainly contributes grammatical meaning.

---

## Light Verb Constructions

Light verb constructions involve a noun or verbal noun combined with a light verb. The noun carries the main lexical meaning, while the verb has a weak or bleached lexical meaning. The verb mainly contributes verbal features such as tense, agreement, aspect, and argument structure. Together, the noun and the light verb form a single predicate and license the arguments of the clause.

More research should be done related to V+V light verb constructions. In this documentation, we focus more on N+V construction:

```text
N + V
```

Example:

```text
அவன் உதவிசெய்தான்.
அவன் உதவி செய்தான் .
he      help.N    do-PST-3SG.M
He helped.
```

Possible UD analysis:

```text
உதவி       NOUN
செய்தான்   VERB     and the rel lable would be compound:lvc
```

Here, **உதவி** “help” provides the main lexical meaning, while **செய்** “do” functions as a light verb / verbaliser in this case. The construction as a whole behaves like a predicate.

---

## Open Clausal Complements / xcomp

Some V+V constructions involve an infinitival verb followed by another verb. In such cases, the first verb functions as an open clausal complement of the second verb. In UD, these are commonly analysed using the label `xcomp`.

These constructions are usually of the form:

```text
V-INF + V
```

Example:

```text
அவன் படிக்கவிரும்புகிறான்.
அவன் படிக்க விரும்புகிறான் .
he      study-INF    want-PRS-3SG.M
He wants to study.
```

Possible UD analysis:

```text
படிக்க          VERB     and the rel lable would be xcomp
விரும்புகிறான்   VERB
```

---

## Summary of Distinctions

| Construction type | Common structure | Example | Main UD label |
|---|---|---|---|
| Auxiliary verb construction | V-CVB + AUX | செய்து விட்டான் | `aux` |
| Serial verb construction | V-CVB + V | ஓடிவந்தான் | `compound:svc` |
| Light verb construction | N + V | உதவி செய்தான் | `compound:lvc` |
| Open clausal complement | V-INF + V | படிக்கவிரும்புகிறான் | `xcomp` |

These constructions may look similar at the surface level, especially because Tamil frequently combines verbal elements into complex predicates. Therefore, tokenisation should separate the relevant syntactic units, while the exact construction type should be determined later during syntactic annotation.
