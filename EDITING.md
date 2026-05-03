# Editing Workflow

This guide explains how to edit a freshly AI-translated chapter so it reads like a professional English fantasy novel without drifting from the original Chinese.

`TRANSLATING.md` covers Step 1 (raw → English draft). This document picks up at Step 2: turning that draft into the final published chapter.

It is distilled from a longer editing curriculum and adapted to the specific quirks of machine-translated Chinese xuanhuan/xianxia prose.

---

## The Two Hard Constraints

Every edit you make must respect both of these. If a change improves flow but violates either, undo it.

1.  **Fidelity.** The translation must preserve the original plot, lore, character intent, descriptions, and imagery. You are polishing language, not rewriting story. Do not add events, cut descriptions, change which character does what, or invent new cultivation lore.
2.  **Structural integrity.** Keep the same paragraph count and the same sentence count as the raw Chinese. Do not merge paragraphs to tighten the pace. Do not split a long Chinese sentence into three English ones to "clean it up." If you genuinely cannot make a one-to-one English sentence read naturally, restructure within that sentence, not across the boundary.

These constraints exist because the glossary, navigation, and any future re-translation all assume the structure of the source. Break them and downstream work breaks.

Everything below sits underneath these two rules.

---

## Mindset: What You Are Actually Doing

You are not the author. The author is My Dog-Skin Plaster (我的狗皮膏药). You are not the translator either — that was the AI.

You are the **editor**. Your job is to be invisible. The reader should feel the author's voice, not yours. When you finish a chapter, a reader should not be able to point at any sentence and say "an editor changed that." They should just feel that the prose flows.

That means:

-   When the AI's draft already works, leave it alone. Confirmed-good sentences are not opportunities to show off.
-   When you change something, change the smallest amount needed. Replacing a single weak verb is almost always better than rewriting the whole sentence.
-   When you are tempted to "improve" a description by adding a metaphor or sensory detail Chen Yi did not write — stop. That is co-authorship, not editing.

A useful test: if you removed your edit and showed the before/after to a reader of the original Chinese, would they say you got closer to the source or further from it? If "further," roll it back.

---

## The Three Passes

Edit in passes, not all at once. Every pass has a different focus, and trying to do them simultaneously is how mistakes slip through.

### Pass 1 — Fidelity Check (read with the raw open)

Open the raw file (`raws/N.md`) and the translated draft (`translations/N.md`) side by side.

Read the chapter once for accuracy only. You are not yet thinking about prose quality. You are checking:

-   **Paragraph count matches.** Count them if you have to.
-   **Sentence count per paragraph matches.** Chinese commas often correspond to English periods, so a Chinese "sentence" full of commas may become several English sentences — that is fine, follow the source structure as the prompt requires it.
-   **No content was added or dropped.** Watch for whole sentences the AI either skipped or hallucinated. Combat scenes and lore exposition are the most common drop zones.
-   **Names match the glossary.** Every character name, sect name, technique name, place name, and item should resolve to its glossary entry. If a name appears that is not in the glossary, flag it for Step 5 of `TRANSLATING.md` (glossary update).
-   **Pronouns match gender.** Chinese 他/她/它 collapses in speech and the AI guesses. Cross-check every he/she/it against the glossary's `gender` field. This is the single most common AI translation error.
-   **Numbers, ranks, and counts.** "Three hundred" vs. "thirty," "Seventh Elder" vs. "Elder Seven," "fifth realm" vs. "fifth stage" — verify against the raw.
-   **Internal vs. spoken.** Internal thoughts should be in `*italics*`. Spoken dialogue should be in `"double quotes"`. The AI sometimes mixes them up, especially when a character mutters to themselves.

This pass is mechanical and slow. Don't rush it — every fidelity error caught here saves a reader-reported issue later.

### Pass 2 — Language Cleanup (read for ESL artifacts)

Now close the raw and read the English on its own. AI translators inherit the same patterns as ESL writers, because Chinese-to-English models have to bridge the same grammatical gaps. The errors below are the ones to hunt.

This is the longest section of the guide because this is where 90% of editing time goes. Each subsection is a discrete pattern to scan for.

#### 2a. Articles (a / an / the / zero)

Chinese has no articles. The AI guesses, and it guesses badly under pressure.

-   Specific reference (already established or unique in context) → `the`.
    > He drew the sword. (the one he is known for, mentioned earlier)
-   First mention of a generic instance → `a` / `an`.
    > A young disciple stepped forward. (we have not met this person)
-   Abstract noun, mass noun, proper noun, formal title before a name → no article (zero article).
    > Cultivation is difficult. / He spoke to Elder Wang.
-   Use `an` before a vowel **sound**, not letter: an hour, a unicorn.

Symptoms to fix: "He took out *a* Nine Revolutions Star Technique" (it is *the* unique technique). "She entered *the* sect" when no specific sect has been named yet should usually be "*a* sect." "Han Yang is *firefighter*" → "Han Yang is *a* firefighter."

#### 2b. Singular / plural

Chinese does not pluralize nouns morphologically. The AI often leaves nouns in their dictionary singular form.

-   "He killed all the demon" → "He killed all the demons."
-   "Many disciple watched" → "Many disciples watched."
-   "How many spirit stone do you have?" → "How many spirit stones..."

Conversely, watch for over-pluralization of mass nouns: "spiritual energies" should usually be "spiritual energy" unless the text genuinely means several distinct kinds.

#### 2c. Tense and aspect

Default narrative tense for this novel is **simple past**. Keep it consistent. Common slips:

-   Drift into present tense in action scenes ("He swings the sword" inside an otherwise-past paragraph).
-   Awkward present perfect where simple past is meant ("He has killed the disciple" → "He killed the disciple").
-   Past perfect where simple past is meant. Past perfect is for an action *before* another past action: "By the time he arrived, she had already left." Don't use it for plain narration.

#### 2d. Pronoun antecedents

When two characters are in a scene, "he ... he ... he ..." gets ambiguous fast — Chinese tolerates this far more than English. Replace with the name when ambiguity creeps in.

-   AI: "Han Yang glared at the elder. He raised his hand." → Whose hand? Rewrite: "Han Yang glared at the elder, who raised his hand." or "Han Yang glared at the elder. The elder raised his hand."

#### 2e. Prepositions

Chinese-to-English routinely misroutes prepositions because Chinese encodes the relationship differently. Common fixes:

-   "in my mind" → "on my mind" (when it means "preoccupying me")
-   "go to home" → "go home"
-   "discuss about it" → "discuss it"
-   "married with her" → "married to her"
-   "different than" → "different from" (formal)

If a preposition makes you pause, swap it and see if the new one feels native.

#### 2f. "Very," "really," "quite," "extremely" — weak intensifiers

The AI loves stacking intensifiers because Chinese 非常, 极其, 十分, 相当 all look intense in source. In English, intensifiers usually *weaken* the word they modify. Strip them and pick a stronger verb or adjective.

-   "very angry" → "furious"
-   "very fast" → "blistering" / "headlong" / "in a blur"
-   "extremely powerful" → "overwhelming"
-   "really shocked" → "stunned"

Watchwords to scan for and usually delete: *very, really, quite, rather, somewhat, pretty, actually, certainly, definitely, in fact, obviously, of course, basically, simply, just, indeed, truly*.

#### 2g. Empty noun phrases

Cluttered noun constructions hide a sharper version. Trim toward the shape on the right.

| Wordy                              | Tight                |
| ---------------------------------- | -------------------- |
| the level of his cultivation rose  | his cultivation rose |
| the amount of spiritual qi present | the spiritual qi     |
| in the process of breaking through | breaking through     |
| made the decision to leave         | decided to leave     |
| had a feeling of unease            | felt uneasy          |
| gave a smile                       | smiled               |
| let out a laugh                    | laughed              |

Verb-as-noun constructions ("made the decision," "had the feeling," "gave a glance") are the single biggest source of bloat in machine-translated prose.

#### 2h. Redundancy

Chinese 4-character idioms and parallel constructions often translate as English doublets that mean the same thing twice.

-   "completely and totally destroyed" → "destroyed"
-   "surrounded on all sides" → "surrounded"
-   "first and foremost" → "first"
-   "shouted loudly" → "shouted" (or "roared," if loudness is the point)
-   "nodded his head" → "nodded"
-   "smiled with his mouth" → "smiled"
-   "future plans" → "plans"
-   "true fact" → "fact"

Doublets are sometimes intentional — the original parallelism is part of the rhythm. If cutting one half loses a beat the Chinese clearly wanted, keep the doublet but strengthen one of the halves.

#### 2i. Transitional phrase overuse

The AI sprinkles "however," "moreover," "furthermore," "in addition," "as a result," "thus," and "therefore" between sentences that already flow. They are scaffolding. Pull them out unless the logical connection genuinely needs marking.

Test: read the paragraph with the transition removed. If it still flows, the transition was padding.

Keep transitions when:

-   You are signaling a real contrast the reader would otherwise miss ("however," "but").
-   You are marking causation the syntax does not show ("because," "so").
-   You are signaling a sequence that is non-obvious ("then," "next").

Cut otherwise.

#### 2j. Adverbs (especially -ly)

Each `-ly` adverb is a chance to upgrade the verb instead.

-   "ran quickly" → "sprinted" / "tore" / "bolted"
-   "said angrily" → "snapped" / "snarled" / "growled"
-   "looked carefully" → "studied" / "scrutinized"
-   "walked silently" → "stalked" / "slipped"

Adverbs are not banned. Variety in sentence rhythm sometimes demands the longer form. But if every dialogue tag has an adverb, you have a verb-choice problem.

Adverb placement also matters: focusing adverbs go *between* the auxiliary and the main verb — "I have *never* seen this," not "I never have seen this."

#### 2k. Passive voice

Default to active. The AI overuses passive constructions because Chinese topic-comment sentences often invert subject and object.

-   "The sword was wielded by Han Yang" → "Han Yang wielded the sword."
-   "The blow was received with no injury" → "He took the blow without flinching."

Passive is correct when (a) the actor is unknown, (b) the actor doesn't matter, or (c) you need to keep the focus character in the subject slot across sentences. Use it deliberately, not by default.

#### 2l. Combat scene punch-up

Combat is where AI prose dies. Sentences flatten into "He attacked. The enemy blocked. He attacked again." Three things to do:

-   **Vary sentence length.** Short sentences = impact. Long sentences = sweep. Alternate them.
-   **Active verbs, concrete nouns.** "His sword cut through the air" is weaker than "The blade tore a seam through the air." Both are faithful; the second has weight.
-   **Sensory specifics.** Sound, light, weight, the *feel* of qi moving. The Chinese usually has these — recover them, don't invent them.

Restraint: if the raw doesn't have the detail, don't add it. The line is "make the language match the energy of what's already there," not "add things that aren't there."

#### 2m. Dialogue

-   Each speaker gets their own paragraph. The AI sometimes packs two speakers into one paragraph; split them.
-   Punctuation goes inside the closing quote: `She said, "I'll go."` not `She said, "I'll go".`
-   Question marks and exclamation marks go inside the quote when they belong to the spoken line: `"Are you serious?" he asked.`
-   Tag verbs: prefer "said" / "asked" / "replied" for most lines. Reach for "snapped," "muttered," "whispered," "snarled" when the manner genuinely matters. Don't reach for "ejaculated," "interjected," "expostulated" — these draw attention to themselves and pull the reader out.
-   Cultivation-world dialogue tends toward formal register. Watch for AI dropping in modern colloquialisms ("Yeah, right," "No way, dude," "OK"). Replace with period-appropriate equivalents.

### Pass 3 — Voice and Rhythm (read aloud)

Now read the chapter top to bottom, aloud or sub-vocalized. This pass catches:

-   Sentences that read fine on the page but trip the tongue.
-   Stretches of sameness — five sentences in a row of similar length and structure.
-   Tone breaks — a sudden modern phrase in a classical scene, or a clinical phrase in a violent scene.
-   Echoes — the same word three times in two sentences.

When you hit a rough patch, the fix is usually one of:

-   Combine within a sentence (not across sentences) for rhythm.
-   Replace the repeated word with a synonym or restructure to remove it.
-   Cut a phrase entirely. The most common fix is "delete two words and the line works."

A chapter that survives Pass 3 is ready to commit.

---

## Style Decisions (the Style Sheet)

Below are the project's standing style decisions. When you make a new judgment call that future chapters will need to follow, **add it here** rather than re-deciding each time. This is the project's style sheet.

### Spelling and dialect

-   **US English.** color, honor, traveling, realize.
-   **Serial (Oxford) comma.** "swords, spears, and sabers."

### Quotation conventions

-   `"Double quotes"` for spoken dialogue.
-   `*Italics*` for unspoken internal thoughts.
-   Punctuation inside the closing quote (US convention).

### Names and terms

-   Personal names: Pinyin, no tone marks, capitalized syllables joined: `Han Yang`, `Chen Qiaoqian`. Two-syllable given names are run together: `Qiaoqian` not `Qiao Qian`.
-   Place names and sects: translated unless the glossary overrides — `Azure Cloud Sect`, `Heavenly Wind City`.
-   Cultivation techniques: glossary translation; otherwise translate the meaning into evocative English (`Nine Revolutions Star Technique`).
-   Honorifics: English equivalents — `Senior`, `Elder`, `Young Master`, `Patriarch`, `Senior Sister`. Capitalized when used as a title before a name (`Elder Wang`), lowercase when used generically (`an elder of the sect`).
-   Family / clan / house: when the glossary names a group as `X Family` (e.g., `Su Family`, `Wang Family`), use `Family` consistently for that group. Do not switch to `clan` or `house` mid-chapter — those words have different connotations in English and create the impression of distinct entities. If a generic reference is needed and `Family` would echo awkwardly, prefer dropping the noun (`a puppet of the Wang Family`) over substituting a synonym.
-   Cultivation-rank capitalization: capitalize when it functions as a proper title or named realm (`Foundation Building stage`, `Spirit Severing realm`). Lowercase generic words (`his cultivation`, `the realm above`).

### Numbers

-   Spell out one through one hundred. Use numerals for 101 and above.
-   Always spell out numbers at the start of a sentence.
-   Cultivation realms and ranks: spell out (`Third Elder`, `the seventh realm`).
-   Large round numbers idiomatic in Chinese (`万`, `亿`) translate to English equivalents: `ten thousand`, `a hundred million`. Don't render `三万` literally as `30000`.

### Formatting

-   No bold in the body text.
-   Italics: for unspoken internal thoughts (the default — see Quotation conventions above), or for emphasis on a single word. Do not italicize Pinyin terms or sect names.
-   One Markdown heading per file: the chapter title (`# Chapter N: Title`).
-   Navigation block at the top, exactly as in the template.

### Things we do NOT do

-   No Chinese characters in the published chapter.
-   No tone marks on Pinyin.
-   No translator's notes or footnotes — work cultural concepts into the prose.
-   No "TL/N:" or "[note: ...]" interjections.
-   No emoji.

When you discover a recurring issue not covered above and you make a decision about it — add a line to the relevant section. The whole point of a style sheet is that the next chapter inherits the decision.

---

## Quick Reference: Find-and-Fix Checklist

Run this checklist on every chapter before committing.

-   [ ] Paragraph count matches the raw.
-   [ ] No Chinese characters anywhere in the file.
-   [ ] No tone marks on Pinyin (no `Hán Yáng`).
-   [ ] All character names match the glossary.
-   [ ] All pronouns match the glossary's `gender` field.
-   [ ] Internal thoughts use `*italics*`; speech uses `"double quotes"`.
-   [ ] No "very," "really," "quite," "actually" survives unless load-bearing.
-   [ ] No `-ly` adverb survives where a stronger verb exists.
-   [ ] No "made the X / had the X / gave a X" verb-as-noun unless deliberate.
-   [ ] Every "however / moreover / furthermore" earns its place.
-   [ ] Combat scenes have varied sentence length.
-   [ ] Each speaker gets their own paragraph.
-   [ ] Numbers follow the spell-out rules above.
-   [ ] Navigation block at the top, links to N-1 and N+1, both correct.
-   [ ] Chapter heading present and matches the title in the glossary if listed.
-   [ ] Read aloud once. No tongue-trips, no echoes, no sameness stretches.

---

## When You Are Unsure

The two-question test for any debatable edit:

1.  Does this change move the English closer to the spirit of the Chinese, or further from it?
2.  Will a reader feel the editor's hand, or only the author's voice?

If the answers are "closer" and "only the author," keep the edit. Otherwise revert.

When you genuinely cannot tell what the Chinese means — open the raw, check the glossary, search for the term across earlier chapters. If still unclear, leave the AI's rendering and add an issue with the raw line quoted, so it can be revisited rather than guessed at.

---

## When You Are Done

1.  Save the edited chapter in `translations/N.md`.
2.  If you made any new style decisions, update the relevant section above.
3.  If new terms appeared, run Step 5 of `TRANSLATING.md` to update the glossary.
4.  Commit:

    ```bash
    git add translations/N.md assets/glossary.json EDITING.md
    git commit -m "Chapter N: <title> (edited)"
    git push
    ```
