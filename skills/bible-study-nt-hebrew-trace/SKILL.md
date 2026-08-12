---
name: bible-study-nt-hebrew-trace
description: "Trace a New Testament Greek word to possible Old Testament Hebrew equivalents through the Septuagint (LXX). Use when studying a NT word, Strong's number, Greek-to-Hebrew bridge, LXX occurrence, first mention, Bible word study, or NT quotation/allusion of the OT."
argument-hint: "NT reference and target English or Greek word, e.g. Ephesians 2:8 grace"
---

# NT → OT Word Tracer

Trace New Testament Greek words to their Old Testament Hebrew equivalents via the Septuagint (LXX), using only free web-based tools. Methodology adapted from the moedim.dev articles [Principles for the Study of the Bible: Word Study](https://moedim.dev/posts/principles-for-the-study-of-the-bible-word-study) and [Principles for the Study of the Bible](https://moedim.dev/posts/principles-for-the-study-of-the-bible): recover original-language meaning through Strong's numbers, find the word's first mention, and interpret in context.

## Why this works

The Septuagint (LXX) is the pre-Christian Greek translation of the Hebrew Bible, and it is tagged with the **same Greek Strong's numbers** as the New Testament. So a Greek word in the NT can be searched in the LXX, which lands you in Old Testament verses — and the Hebrew text behind each of those verses reveals the Hebrew word (and Hebrew Strong's number) that the Greek word translates. Greek word → G-number → LXX occurrences → OT verse → Hebrew word → H-number.

## The procedure

Follow the stages in order. Use `web_fetch` to retrieve pages; construct URLs from the patterns below (full patterns and fallbacks in `references/tools.md` — read it if a URL fails or a tool is down).

### Stage 0 — Identify the Greek word

Input: an NT reference and target English word (e.g., "grace" in Ephesians 2:8).

Fetch the interlinear for the verse:
- `https://biblehub.com/interlinear/{book}/{chapter}-{verse}.htm` (book lowercase, e.g., `ephesians/2-8.htm`; numbered books like `1_corinthians`)

Read off the Greek word, its transliteration, and its Strong's number **G{num}**. If the user gives only an English word with no verse, ask for a verse or pick the best-known NT verse using that word and confirm.

### Stage 1 — Understand the Greek word (and capture any direct Hebrew bridge)

Fetch `https://biblehub.com/greek/{num}.htm` (no leading zeros, e.g., `5485.htm`).

Record:
- Strong's definition and usage
- NT occurrence count
- **Critically: check the HELPS Word-studies and Thayer's entries for a named Hebrew equivalent.** These often state the Hebrew directly (e.g., for G5485 *charis*, HELPS links to Hebrew 2580 and Thayer's names חֵן). If found, record the H-number as a *hypothesis to be confirmed* in Stages 2–4 — not as the final answer.

Optionally also fetch `https://www.blueletterbible.org/lexicon/g{num}/kjv/tr/0-1/` for KJV translation counts and the outline of biblical usage.

### Stage 2 — Find the Greek word in the Septuagint

Fetch the Blue Letter Bible LXX concordance for the Greek word:

```
https://www.blueletterbible.org/lexicon/g{num}/lxx/lxx/0-1/
```

This page reports how many times the word occurs in the LXX and lists **every OT verse**, with inline Strong's numbers on each Greek word. Record:
- The LXX occurrence count
- The **first occurrence in canonical order** (the "first mention")
- The spread of books/contexts

Fallbacks if BLB fails: STEP Bible `https://www.stepbible.org/?q=version=LXX|text=strong:G{num}` or studybible.info (LXX_WH version, search the G-number).

**If the word does not occur in the LXX**, the lexical bridge fails — say so plainly, then fall back to (a) any Hebrew equivalent named by the lexicons in Stage 1, (b) cognate/root words of the Greek term that do occur in the LXX, and (c) the thematic method (below).

### Stage 3 — Read the Hebrew behind the LXX occurrences

For the first mention **and** at least 3–5 representative occurrences (more if results diverge), fetch the Hebrew interlinear of each OT verse:

- `https://biblehub.com/interlinear/{book}/{chapter}-{verse}.htm`
- or `https://biblehub.com/text/{book}/{chapter}-{verse}.htm`

Align the target Greek word (from the BLB LXX listing) with the Hebrew word in the same slot of the verse. Record the Hebrew word, transliteration, and **Strong's H{num}** for each occurrence checked.

Then fetch `https://biblehub.com/hebrew/{num}.htm` for the Hebrew word's definition, root, and OT usage.

### Stage 4 — Resolve multiple Hebrew equivalents

**One Greek word often translates several different Hebrew words.** This is the method's biggest pitfall. Tabulate what you found in Stage 3:

| OT verse (LXX occurrence) | Hebrew word | H-number |
|---|---|---|
| ... | ... | ... |

- If one Hebrew word dominates → report it as the primary equivalent, note alternates.
- If several Hebrew words appear with similar frequency → **do not assert a single equivalent.** Report the range honestly and lean on the quotation and thematic methods instead.
- The first-mention verse's Hebrew word is a starting hypothesis, not proof — always check it against the distribution.

For exhaustive equivalence data, the Hatch-Redpath Concordance to the Septuagint (scans on the Internet Archive) is the scholarly standard; mention it to users who want to go deeper.

### Stage 5 — Corroborate three ways

Confirm the Greek↔Hebrew link with as many of these as apply:

1. **Lexicon citation** — did HELPS/Thayer's (Stage 1) or BDB/Gesenius (Stage 3) name this equivalence?
2. **LXX distribution** — does the Stage 4 table support it?
3. **Quotation check** — if the NT verse quotes or alludes to a specific OT passage, look up that passage directly (NT-quotes-OT indexes: kalvesmaki.com, bible-researcher.com) and read its Hebrew. A direct quotation is the strongest possible link.

State the confidence level in the final report: **high** (all three agree), **moderate** (lexicon + dominant LXX pattern), or **tentative** (single first-mention hit or mixed distribution).

### Stage 6 — Interpret: first mention + context

Apply the foundation article's interpretive principles to the first-mention passage:

- **First-mention principle**: read the full context of the earliest OT occurrence; its context sets the word's foundational biblical meaning.
- **Law of context**: "a text apart from its context is a pretext." Read surrounding verses; note who/what/when/where/why/how.
- **Literal-historical method / Cooper's Golden Rule**: take the plain sense unless context clearly indicates otherwise.
- Connect the thread: what does the OT first-mention context contribute to understanding the NT usage? (Classic example: "grace" G5485 first appears in the LXX at Genesis 6:8 — Noah "found grace [Hebrew *chen*, H2580] in the eyes of the LORD" — illuminating Ephesians 2:8's grace-through-faith as an Old Testament principle.)

Present first-mention as a productive study heuristic, not an ironclad rule of exegesis.

## Complementary methods (offer these alongside the lexical trace)

1. **Thematic/conceptual tracing** — follow the *idea* (covenant, redemption, grace) across both testaments, not just the lexeme. Use when the lexical bridge is weak or the user's question is conceptual.
2. **NT quotations of the OT** — where the NT explicitly quotes the OT (~283 direct quotations), the Hebrew source is given directly; always check whether the user's verse is one of them.

## Output format

Deliver a structured word-study report:

1. **The word** — English, Greek (with transliteration), G-number, NT usage summary
2. **The bridge** — LXX occurrence count, first mention, distribution table of Hebrew equivalents
3. **The Hebrew root** — Hebrew word, H-number, definition, OT usage
4. **Confidence** — high/moderate/tentative, with the corroboration evidence
5. **First-mention study** — the earliest OT passage in context and what it contributes
6. **The connection** — how the OT meaning illuminates the NT verse
7. **Sources** — the specific BLB/BibleHub/STEP URLs used, so the user can verify

Keep the tone reverent but scholarly-honest: flag uncertainty, never overstate a lexical link, and remind users that Strong's numbers are pointers into better lexicons, not final semantic authorities.

## Caveats to keep in mind (and share when relevant)

- The LXX is a translation with its own interpretive choices; a Greek word's LXX Hebrew source shows how Hellenistic Jews understood the word, not an etymological identity.
- Greek↔Hebrew mappings are routinely one-to-many in both directions.
- BibleHub's Apostolic Bible Polyglot LXX uses **modified** "AB-Strong's" numbers — do not treat them as standard Strong's numbers.
- If a constructed URL returns unexpected content, verify (does the page's Strong's number match?) and fall back per `references/tools.md`.

## Methodology references

- [Principles for the Study of the Bible: Word Study](https://moedim.dev/posts/principles-for-the-study-of-the-bible-word-study)
- [Principles for the Study of the Bible](https://moedim.dev/posts/principles-for-the-study-of-the-bible)

# New Testament to Old Testament Word Trace

Use this workflow to investigate an NT Greek word, the Greek word's LXX usage, and the Hebrew words behind selected OT occurrences. Produce a transparent, context-aware study rather than an etymological shortcut.

## Boundaries

- Treat Strong's numbers as lookup keys, not as complete lexical definitions.
- Treat the LXX as translation evidence. A Greek-to-Hebrew connection does not prove that the words are etymological or semantic equivalents.
- One Greek word may translate several Hebrew words, and one Hebrew word may have several Greek renderings. Never infer a unique Hebrew equivalent from one occurrence.
- Treat first mention as a teaching heuristic. It does not override immediate context, grammar, genre, historical setting, or the word's complete usage.
- Keep lexical tracing distinct from an NT quotation or allusion study. When the NT quotes the OT, identify and examine the OT source directly.
- Do not treat Apostolic Bible Polyglot numbering as standard Greek Strong's numbering without verification.

## Inputs

Obtain:

- The NT reference.
- The target English word, Greek lemma, or Greek Strong's number.
- Whether the user wants a concise result or a broad survey of LXX equivalents.

If the English word could correspond to multiple Greek words in the verse, identify the alternatives and ask which one to trace.

## Procedure

### 1. Identify the NT Greek word

1. Open a NT interlinear, preferably BibleHub: `https://biblehub.com/interlinear/{book}/{chapter}-{verse}.htm`.
2. Locate the target word in its clause. Record the Greek lemma, transliteration, morphology when relevant, and standard Strong's number `G{number}`.
3. Confirm the number with at least one Greek lexicon:
   - BibleHub: `https://biblehub.com/greek/{number}.htm`
   - Blue Letter Bible: `https://www.blueletterbible.org/lexicon/g{number}/kjv/tr/0-1/`

The verse's actual Greek form controls the study; do not select a Greek word only because its English gloss resembles the requested word.

### 2. Establish the Greek lexical range

1. Read the Strong's entry and a substantive lexicon on the page, such as Thayer's, HELPS Word-studies, or LSJ through STEP Bible.
2. Record only senses relevant to the NT context.
3. Record any Hebrew equivalent or Hebrew Strong's number named by the lexicon as corroboration, not as the conclusion.
4. Note the word class and any morphology or cognate distinction that affects the result.

### 3. Locate the Greek word in the LXX

1. Use BLB's LXX concordance as the primary occurrence search:
   `https://www.blueletterbible.org/lexicon/g{number}/lxx/lxx/0-1/`
2. Verify that the page matches the requested `G{number}` and is in LXX mode.
3. Record the stated occurrence count and OT verse list. Preserve at least the earliest canonical occurrence, representative occurrences for each apparent Hebrew equivalent, and occurrences relevant to the NT sense.
4. If BLB does not expose the expected data, use STEP Bible as a locator:
   `https://www.stepbible.org/?q=version=LXX|text=strong:G{number}`
5. If necessary, use studybible.info's LXX_WH Strong's search as a second backup.

Do not assume that a first result is the first or only Hebrew equivalent.

### 4. Read the Hebrew behind selected LXX occurrences

For each selected OT occurrence:

1. Open a Hebrew interlinear or text analysis page:
   - `https://biblehub.com/interlinear/{book}/{chapter}-{verse}.htm`
   - `https://biblehub.com/text/{book}/{chapter}-{verse}.htm`
2. Read the Hebrew word aligned to the LXX target. Record its spelling, transliteration, gloss, and `H{number}`.
3. Confirm the alignment from phrase and syntax. LXX and Masoretic Text word order or segmentation may differ.
4. Capture the immediate literary context and grammatical details that affect meaning.

STEP's LXX data is useful for locating Greek occurrences, but its Hebrew cross-tags are not a general MT-to-LXX alignment system.

### 5. Resolve multiple Hebrew equivalents

Tabulate the observed Hebrew lemmas, Strong's numbers, and references. State a dominant equivalent only when the survey meaningfully supports one, and report notable alternatives when contexts differ.

For an exhaustive equivalence list, consult Hatch-Redpath's *Concordance to the Septuagint* and its Hebrew index, including the Dos Santos expanded index where available.

Use these decision rules:

- A strongly dominant equivalent corroborated by a lexicon may be reported as the most common LXX rendering, with a confidence label.
- Several substantial equivalents require a range, not a claim that the Greek word means one Hebrew word.
- Rare or absent LXX occurrences make the bridge inconclusive; use lexicon citations, cognates, and thematic context instead.
- An explicit NT quotation or allusion takes priority: identify the OT source, read its Hebrew directly, and compare MT and LXX wording when relevant.

### 6. Corroborate

Seek at least two independent forms of support where practical:

1. A Greek lexicon naming a Hebrew equivalent.
2. The observed LXX-to-Hebrew distribution.
3. A Hebrew lexicon such as BDB or Gesenius.
4. An NT-OT quotation or allusion index.

Do not invent a quotation link. If no reliable index identifies one, describe the relationship only as a possible thematic connection.

### 7. Interpret in context

Read the full NT paragraph and the relevant OT passage. Explain the speaker, audience, grammar, genre, historical setting, and surrounding argument. Label first-mention observations as heuristics.

Separate the final claims into:

- **Lexical evidence:** what the Greek and Hebrew words can mean.
- **Translation evidence:** how LXX translators rendered Hebrew in the selected texts.
- **Thematic connection:** the possible OT-to-NT conceptual thread.
- **Exegetical conclusion:** what the NT passage means in its own context.

## Output format

Use this structure unless the user requests a shorter answer:

```markdown
## Word Trace: {English word} in {NT reference}

- **NT Greek:** {lemma} ({transliteration}), `G{number}`; {sense and morphology}
- **Greek lexical evidence:** {findings and any direct Hebrew citation}
- **LXX survey:** {verified count}; {scope surveyed}

| LXX OT reference | LXX Greek | Hebrew behind the verse | Strong's | Context note |
|---|---|---|---|---|
| {reference} | {Greek} | {Hebrew word} ({transliteration}, {gloss}) | `H{number}` | {note} |

- **Most supported Hebrew equivalent(s):** {word}, {transliteration}, `H{number}`; {distribution and confidence}
- **Alternatives / limits:** {other equivalents or uncertainty}
- **Contextual thread:** {careful connection}
- **First-mention observation:** {heuristic, if relevant}
- **Sources checked:** {URLs or named resources}
```

## Quality checks

Before finalizing, verify that:

- `G{number}` comes from the actual NT word in context.
- The BLB URL is in LXX mode and returns the requested number.
- Each Hebrew result includes the verse-level spelling, transliteration, gloss, and `H{number}`.
- Hebrew alignment was checked rather than assumed from word position.
- Multiple Hebrew equivalents are reported when the evidence shows them.
- Lexical, translational, thematic, and exegetical claims are clearly separated.
- First mention is explicitly presented as a heuristic.
- Conclusions do not depend on a Strong's number alone.

## Worked example: grace

For "grace" in Ephesians 2:8, verify `charis`, `G5485`, in the NT interlinear. Check the Greek lexicons for a Hebrew citation, then query BLB's `G5485` LXX concordance and inspect Genesis 6:8 in a Hebrew interlinear. Record the verse-level Hebrew equivalent only after checking the alignment, then survey additional LXX uses before claiming that it is the only equivalent. Explain Genesis 6 in its own context before drawing a thematic connection to Ephesians 2.

For the detailed methodology and resource comparison, see [`docs/plan.md`](docs/plan.md).