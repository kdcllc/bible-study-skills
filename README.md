# bible-study-skills

[![skills.sh](https://skills.sh/b/kdcllc/bible-study-skills)](https://skills.sh/kdcllc/bible-study-skills)

AI skills for tracing New Testament words back to their Hebrew Old Testament origins using Strong's numbers and the Septuagint.

## Install

```bash
npx skills add kdcllc/bible-study-skills --skill bible-study-nt-hebrew-trace
```

Works with Claude Code, Cursor, Codex, GitHub Copilot, Windsurf, Gemini CLI, and other agents that support the open skills format.

## Skills

### `bible-study-nt-hebrew-trace`

Trace a New Testament Greek word to its Old Testament Hebrew root — entirely with free web-based Bible tools (Blue Letter Bible, BibleHub, STEP Bible), no desktop software required.

**How it works** — the Septuagint (LXX), the Greek translation of the Hebrew Bible, is tagged with the same Greek Strong's numbers as the New Testament:

```
NT English word → Greek word + G-number → LXX occurrences (OT verses)
              → Hebrew word behind each verse → Hebrew Strong's H-number
              → first-mention study in context
```

**Example prompts:**

- "Trace the word 'grace' in Ephesians 2:8 back to the Old Testament"
- "What's the Hebrew behind the Greek word for 'peace' in John 14:27?"
- "Do a word study on 'redeem' — where is its first mention?"

**Example result:** "grace" (χάρις, G5485) → 70+ LXX occurrences → first mention Genesis 6:8, where Noah "found grace in the eyes of the LORD" → Hebrew חֵן *chen*, H2580 — illuminating Ephesians 2:8's grace-through-faith as an Old Testament principle.

The skill handles words with multiple Hebrew equivalents honestly (it tabulates the distribution rather than asserting a single answer), corroborates via lexicons (HELPS, Thayer's, BDB) and NT-quotes-OT indexes, and reports a confidence level with every trace.

## Methodology

Adapted from these moedim.dev articles:

- [Principles for the Study of the Bible: Word Study](https://moedim.dev/posts/principles-for-the-study-of-the-bible-word-study)
- [Principles for the Study of the Bible](https://moedim.dev/posts/principles-for-the-study-of-the-bible)

The methodology uses original-language word study via Strong's numbers, the first-mention principle, and the law of context, with the article's tool steps replaced by web-based equivalents and additional scholarly guardrails (LXX equivalence distributions, Hatch-Redpath, and quotation indexes).

## Repo structure

```
bible-study-skills/
├── README.md
└── skills/
    └── bible-study-nt-hebrew-trace/
        ├── SKILL.md
        └── references/
            └── tools.md   # URL patterns & fallbacks for BLB, BibleHub, STEP, etc.
```

## License

CC BY-SA 4.0. See the [license deed](https://creativecommons.org/licenses/by-sa/4.0/).
