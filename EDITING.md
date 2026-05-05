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

**Webnovel register, not literary register.** This is a fantasy webnovel, not a literary novel. Readers want punchy, casual, vivid prose — not the sophisticated diction of a Western literary novel. When you face a choice between a clean punchy sentence and a more elegant compressed one, pick punchy. Cultivation novels live or die on energy. Compression, semicolon-stitching, and ornate participial constructions all read as the editor showing off — exactly the thing the previous bullets warn against.

A useful test: if you removed your edit and showed the before/after to a reader of the original Chinese, would they say you got closer to the source or further from it? If "further," roll it back.

---

## The Three Passes

Edit in passes, not all at once. Every pass has a different focus, and trying to do them simultaneously is how mistakes slip through.

**Each pass is a top-to-bottom read of the entire chapter.** Do not shortcut by scanning for the category of issue listed in each pass and stopping when you've checked the boxes. The worst sentences hide in benign-looking paragraphs the category-scan never re-reads. If you finish a pass without having read every line, you have not done the pass — you have done a search. The difference shows up as reader-flagged awkward prose after commit.

A useful test: count the number of sentences you actually re-read during the pass. If the number is materially smaller than the chapter's sentence count, you scanned. Go back.

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

Symptoms to fix: "He took out *a* Nine Revolutions Star Scripture" (it is *the* unique scripture). "She entered *the* sect" when no specific sect has been named yet should usually be "*a* sect." "Han Yang is *firefighter*" → "Han Yang is *a* firefighter."

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

**Weapon-shadow saturation.** Chinese uses 棍影 / 剑影 / 拳影 ("staff-shadow," "sword-shadow," "fist-shadow") to mean the visual blur of fast strikes. The literal "staff afterimages" rendering reads OK once but turns mechanical by the third use. Vary across the scene: "blur of staff motion," "storm of strikes," "flurry of blows," "the staff blurring with strikes too fast to track." Cap "afterimages" at one use per fight, used to establish the imagery, then switch off it.

**Pre-echo trap.** When the chapter contains a beast or element with "lightning," "thunder," "fire," "ice," or "blood" in its name, do not use that word as a metaphor for unrelated things in the same chapter. "Lightning-quick reflexes" three paragraphs before a Purple Lightning Mad Lion appears reads as if the prose is foreshadowing connection that does not exist. Pick a different metaphor: "instant," "razor-sharp," "in a flash without using the word."

#### 2m. Dialogue

-   Each speaker gets their own paragraph. The AI sometimes packs two speakers into one paragraph; split them.
-   Punctuation goes inside the closing quote: `She said, "I'll go."` not `She said, "I'll go".`
-   Question marks and exclamation marks go inside the quote when they belong to the spoken line: `"Are you serious?" he asked.`
-   Tag verbs: prefer "said" / "asked" / "replied" for most lines. Reach for "snapped," "muttered," "whispered," "snarled" when the manner genuinely matters. Don't reach for "ejaculated," "interjected," "expostulated" — these draw attention to themselves and pull the reader out.
-   Cultivation-world dialogue tends toward formal register. Watch for AI dropping in modern colloquialisms ("Yeah, right," "No way, dude," "OK"). Replace with period-appropriate equivalents.

#### 2n. Semicolon overuse

AI translations love semicolons because they preserve a Chinese comma without committing to a period. The result reads as overly formal — webnovel readers don't want to parse comma-splice substitutes. Default to period-splits over semicolons.

-   "Damn it!" Su Yang spat, qi bursting from him; gripping his staff, he struck back. → "Damn it!" Su Yang spat, qi bursting from him. He gripped his staff and struck back.
-   He flickered back at once; in that same heartbeat the earth shook. → He flickered back at once. In that same heartbeat, the earth shook.

Reserve semicolons for cases where the two clauses are tightly bound (parallel structure, immediate cause-effect) and a period would feel choppy. If you find more than one or two semicolons in a chapter, you are over-using them.

#### 2o. Participial vs explicit connector for simultaneous action

When two actions happen at the same time, the AI defaults to a participial phrase: "He flung the staff, the Battle Sage Art igniting within him." This is grammatical but reads as a literary style flag. Use a temporal connector (`as`, `while`, `just as`) instead.

-   "He flung the staff, the Battle Sage Art igniting within him." → "He flung the staff as the Battle Sage Art ignited within him."
-   "Su Yang stared at the attack, his expression grim, the imagery surfacing in his mind." → "Su Yang stared grimly at the attack as the imagery surfaced in his mind."

The participial form isn't banned — sometimes it's the cleanest option for a brief modifying phrase. But when the participial introduces a full clause-equivalent, prefer the explicit connector. Reading aloud is the test: if the participial makes the sentence stack-trip, it's the wrong tool.

#### 2p. Exclamation pile-ups

Chinese web fiction freely uses 多重感叹号 (`！！`, `！！！`) for emphasis. AI translations preserve them literally. English convention is one `!` per sentence — pile-ups read as juvenile or melodramatic. Normalize to a single `!` everywhere: dialogue, internal monologue, sound effects, onomatopoeia, battle cries.

-   "He sent the lion flying!!!" → "He sent the lion flying!"
-   "Die!!!" → "Die!"
-   "Hyaaaah!!!" → "Hyaaaah!"
-   "yours truly isn't dead yet!!!" → "yours truly isn't dead yet!"

The verb, the speaker's tone, and the surrounding context already carry the intensity. Stacking exclamation marks doesn't add force in English — it subtracts credibility.

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
-   `*Italics*` for unspoken internal thoughts. Render in **first-person, present tense** (free direct interior monologue) — `*Am I really going to give up like this?*`, not `*Was he really going to give up like this?*`. The Chinese 自己 is reflexive and can map either way; first-person present is the project default because it keeps the immediacy of an interior voice.
-   Punctuation inside the closing quote (US convention).

### Names and terms

-   Personal names: Pinyin, no tone marks, capitalized syllables joined: `Han Yang`, `Chen Qiaoqian`. Two-syllable given names are run together: `Qiaoqian` not `Qiao Qian`.
-   Place names and sects: translated unless the glossary overrides — `Azure Cloud Sect`, `Heavenly Wind City`.
-   Cultivation techniques: glossary translation; otherwise translate the meaning into evocative English (`Nine Revolutions Star Scripture`).
-   Honorifics: English equivalents — `Senior`, `Elder`, `Young Master`, `Patriarch`, `Senior Sister`. Capitalized when used as a title before a name (`Elder Wang`), lowercase when used generically (`an elder of the sect`).
-   Family / clan / house: when the glossary names a group as `X Family` (e.g., `Su Family`, `Wang Family`), use `Family` consistently for that group. Do not switch to `clan` or `house` mid-chapter — those words have different connotations in English and create the impression of distinct entities. If a generic reference is needed and `Family` would echo awkwardly, prefer dropping the noun (`a puppet of the Wang Family`) over substituting a synonym.
-   Beast/cultivator ranks: `品` renders as `rank-N` (`rank-four demonic beast`, `rank-six beast`). Established by chapters 2 and 6. Don't introduce `grade` or `tier` for the same concept.
-   **Possessives for established items.** When a character has been using or holding a specific item across the chapter (a known staff, a known vial, a known sword), use the possessive (`his staff`, `her vial`) rather than the definite article (`the staff`). The article reads as if the item is generic; the possessive cues that it's the character's known belonging. AI translators default to `the` because Chinese 长棍 / 玉瓶 / 长剑 don't morphologically mark possession, but English convention does. Especially watch the second and third reference — the first might justifiably be `the staff` (introducing a salient prop), but by the third reference it should be `his staff`.

### Aura and presence terms

Chinese xianxia stacks several closely-related terms for "aura/presence" that the AI tends to translate inconsistently. The project's settled renderings:

-   **战斗气息** → `combat aura`, not `battle aura`. "Battle aura" reads videogame-y in English; "combat aura" carries the same meaning with a more grounded register. Re-use across chapters even when the source phrase varies in modifier (`强大的战斗气息` → `powerful combat aura`, `肆虐的战斗气息` → `savage combat aura`).
-   **战意** → `fighting spirit` (preferred), `battle intent` (acceptable but flatter). "The fighting spirit hadn't faded" reads more naturally than "the battle intent hadn't ebbed."
-   **王者之威 / 王霸之气** → `the pressure of a king` / `domineering aura`. These are bare noun phrases in Chinese (subject + descriptor) often presented as a standalone atmospheric line. **Do not render as a bare English fragment** ("Kingly might, fearsome to behold."). Convert to a complete sentence: "The pressure of a king rolled off it, fearsome to face." The fragment reads as marketing copy in English even when it lands as poetic punch in Chinese.
-   **杀气** → `killing intent` (standard xianxia rendering, well-established).
-   **气势** → `presence` or `momentum` depending on context — physical bearing vs forward force.

### Imagery word echo (the "lightning-quick" trap)

When a chapter introduces a beast or element with `lightning`, `thunder`, `fire`, `ice`, `wind`, or `blood` in its name, scan the rest of the chapter for that word used as an unrelated metaphor and replace it. `Lightning-quick reflexes` three paragraphs before a `Purple Lightning Mad Lion` appears reads as if the prose is foreshadowing a connection that doesn't exist. Substitutes: `instant`, `razor-sharp`, `in a flash`, `lightning` → `electric` (when the meaning is "energetic," not "fast").

### Specific Chinese-English term mappings

Some Chinese words have a literal rendering and an idiomatic rendering, and the AI tends to pick the literal one when the idiomatic one is what readers expect. The project's settled choices:

-   **虚空** → `the void`, not `empty air`. Xianxia magic tears space itself; "empty air" is too grounded for the register.
-   **落空** (a strike landing on nothing, missing) → `met nothing` / `whiffed` / `swung at nothing`, not `met empty air`. The idiom is "the strike missed," not "the strike found air."
-   **闪电之声** → `the snap of lightning` / `the crackle of electricity` / `snapping and crackling with lightning`. The literal "sound of lightning" is misleading: lightning bolts make a close-up snap/crackle from electrical discharge, not the distant rumble of thunder. Stay accurate to the physics.
-   **人言** (when uttered by a beast) → `human tongue` / `human speech`, **without article**. "Spoke in *a* human tongue" reads as if the beast picked one of several human languages. The Chinese 人言 is a category ("human-style speech"), not a specific language. Drop the article.
-   **肉体碰撞** → `strike for strike` / `clash head-on` / `meet fist to claw`, not `body-to-body`. The literal "body-to-body" reads clinical; the idiom is about exchanging blows in physical combat, not bodies touching.
-   **气若游丝** (idiom: "breath like floating silk thread") → `barely breathing` / `hanging by a thread`, not `breath like a thread`. The literal English doesn't carry — the Chinese image is that life is so faint it's almost imperceptible. Use the matching English idiom.
-   **小厮** (a young male house servant) → `servant` (or `young servant` if the youth matters in context). Avoid `page` — "page" in English carries an Anglo-medieval connotation (knight's apprentice / royal court boy) that doesn't fit a Chinese xuanhuan manor staff role.
-   **圆满** (peak of a realm/stage) → in flowing prose, prefer `peak [Realm]` over `[Realm] Perfection`. Glossary entry "Perfection" remains the canonical formal/technical rendering, but in dialogue, internal monologue, or descriptive prose, "peak Tri-Profound Realm expert" reads more naturally than "Tri-Profound Realm Perfection expert." The glossary term anchors meaning; this rule governs in-prose register.
-   **体质** (innate physiological constitution / body type) → `physique` (often `extraordinary physique` / `remarkable physique` / `rare physique`), not `constitution beyond the ordinary`. In xianxia, 体质 specifically refers to a cultivator's innate physiology — `physique` is the standard webnovel rendering and reads cleanly.

When you discover a recurring AI-default mistranslation that has a settled idiomatic equivalent, add a line here so the next chapter inherits the decision.

### Chinese narrative artifacts

Chinese xianxia and webnovels use stock narrative tags that translate literally but mark the prose as obviously-translated. The reader should feel the author's voice, not the translation's footprint. We are translating for a Western audience — stay true to the author's intent, but if a phrasing reads as a Chinese-novel artifact when carried straight into English, restructure.

Common offenders:

-   **一人一兽 / 二人 / 三人** ("one human one beast," "two people," "three people") at sentence start → use a natural English subject (`the two of them`, `Su Yang and the lion`, or simply `they`). The species/count framing is a Chinese narrative convention; by this point in the scene English uses pronouns or names.
-   **话落 / 话音刚落** (literally "the words fell" / "the voice had just fallen") → `with that`, `on those words`, `and then`. Never `as the words fell` — the Chinese is a transition marker, not a physical action. (Lightning bolts fall; words don't.)
-   **大脑运转 / 脑筋转** ("brain turning/operating") → `mind working`, `wheels turning`, `thinking through`. Brains don't "turn" in English.
-   **看着 X,** ("watching X,") at sentence start → restructure so the watcher is the subject of the main verb, not stranded in a participle that floats free of its referent.
-   **两道身影 / 两道残影** ("two silhouettes," "two afterimages") in mid-action narration → use names or `the two of them` once identities are established for the reader.
-   **甩几条街** ("thrown several streets behind") → `left miles behind`, `outpaced by a wide margin`. The "streets" / "blocks" image is internet-era Chinese slang that doesn't carry; the English equivalent is "miles."
-   **铜铃般的双眸** ("eyes like bronze bells") — judgment call. Bronze bells is a culturally-specific image; English equivalents are `saucers`, `dinner plates`. Keep the Chinese image only when the cultural flavor is the point; otherwise prefer the English idiom.

The test: would a reader of the English alone, with no Chinese context, find this opening or transition natural? If it reads as poetic-translated rather than poetic-English, restructure. The bar is "stays true to the author's intent" + "easy to read for a Western audience" — both, not either.

### English economy

Chinese readily uses parallel constructions, list-style elaborations, and explanatory appositions that translate as redundancy in English. Trust the reader and the surrounding context. The rule of thumb: if a fact, name, or descriptor was just established in the previous sentence or paragraph, do not restate it in the next.

-   **Don't re-name characters within close proximity.** If Wang Lang has just been named, the next paragraph should use a pronoun, role (`Patriarch Wang`), or relational shorthand (`father and daughter`). Source: 我要苏阳这个人以及名字，还有尸骸，永远都消失 — literally "I want this person Su Yang, his name, his remains, gone forever." English: "I want every trace of his existence gone forever." (Su Yang was named in the prior sentence; the listed items synthesize cleanly into one phrase.)
-   **Drop appositional naming when the relationship has been established.** Source frequently writes `王朗和王依依，这一对父女` ("Wang Lang and Wang Yiyi, this pair of father-and-daughter"). In English, after both characters have been named earlier in the scene, prefer `Both father and daughter…` — naming + apposition is double-billing.
-   **Prefer terse English over elaborate description when the visual context already establishes meaning.** "Look at him" beats "Look at the state of him" once the reader has been shown his ravaged condition. The longer phrase is correct, just unnecessary.
-   **One scope of redundancy at a time.** This rule does not authorize cutting plot details, merging paragraphs, or eliminating sentences from the source. Only the within-sentence and within-adjacent-paragraph re-statement of already-known information.
-   Cultivation-rank capitalization: capitalize when it functions as a proper title or named realm (`Foundation Building stage`, `Spirit Severing realm`). Lowercase generic words (`his cultivation`, `the realm above`).
-   TCM anatomy lowercase: body-system terms borrowed from traditional Chinese medicine are common anatomy, not proper names. Lowercase: `eight extraordinary meridians` (奇经八脉), `meridians` (经脉), `dantian` (丹田), `five viscera and six bowels` (五脏六腑), `essence blood` (精血). Every cultivator has these — they aren't unique abilities or named systems. Reserve capitalization for true proper-noun techniques and named realms.

### Numbers

-   Spell out one through one hundred. Use numerals for 101 and above.
-   Always spell out numbers at the start of a sentence.
-   Cultivation realms and ranks: spell out (`Third Elder`, `the seventh realm`).
-   Large round numbers idiomatic in Chinese (`万`, `亿`) translate to English equivalents: `ten thousand`, `a hundred million`. Don't render `三万` literally as `30000`.

### Time units

Classical Chinese time units don't map one-to-one to English clock time. Convert to literal English measure (no footnotes per the project's no-translator's-notes rule):

-   `一个时辰` = **two hours**, not "an hour" or "the hour." A `时辰` is a fixed 2-hour block in classical reckoning.
-   `半个时辰` = **one hour**.
-   `一刻` = **fifteen minutes** (literally "one quarter").
-   `一炷香` = roughly **half an hour** (the time for one incense stick to burn). Use "half an hour" unless the prose specifically wants the incense imagery.
-   `半天` = **half a day**, but in idiomatic use often just means "a long while" — translate by ear.

When in doubt, prefer the literal numeric measure ("two hours") over loose English idiom ("the hour"). Threats and deadlines in cultivation novels are often precise; halving or doubling the window changes the stakes.

On first use of a unit in any chapter, consider adding a TL note (see Translator's Notes section below) so the reader can calibrate. Subsequent uses in the same chapter or in later chapters don't need to be re-noted.

### Formatting

-   No bold in the body text.
-   Italics: for unspoken internal thoughts (the default — see Quotation conventions above), or for emphasis on a single word. Do not italicize Pinyin terms or sect names.
-   One Markdown heading per file: the chapter title (`# Chapter N: Title`).
-   Navigation block at the top, exactly as in the template.

### Things we do NOT do

-   No Chinese characters in the **body prose** (Chinese is allowed inside translator's notes — see below).
-   No tone marks on Pinyin in the body prose (tone marks ARE used inside translator's notes for the original-Chinese gloss).
-   No "TL/N:" or "[note: ...]" interjections in the prose itself. Use proper markdown footnotes (see Translator's Notes section below).
-   No emoji.

When you discover a recurring issue not covered above and you make a decision about it — add a line to the relevant section. The whole point of a style sheet is that the next chapter inherits the decision.

---

## Translator's Notes (TL Notes)

Some Chinese-language and Chinese-cultural nuances don't survive translation into the prose itself. When a phrasing, character voice tic, idiom, or cultural reference would land richer for a reader who knows what's behind it, add a translator's note as a markdown footnote. This is a webnovel-translation convention readers actively appreciate — it lets the prose stay clean while the curious reader can dig into the original.

### Format

Use markdown footnote syntax:

-   In the prose: append `[^N]` (where N is a sequential number per chapter) immediately after the relevant word or phrase.
-   At the end of the chapter file (after the last paragraph, separated by `---`): `[^N]: definition text` — one definition per footnote, in order.

GitHub renders these as numbered footnotes with backlinks — the reader clicks the marker to jump to the note and clicks back to return.

### Style of the note itself

-   Open with the original Chinese in parentheses, then pinyin **with tone marks** (TL notes are one of the few places we use tones): `本家主 (běn jiā zhǔ)`.
-   Then a brief literal gloss in quotes: `literally "this family-head."`
-   Then 1–3 sentences of cultural or linguistic context that helps the reader appreciate the original choice. Educational, not pedantic — the reader should finish the note feeling enriched, not lectured.

### When to add a TL note

-   **Pompous self-reference conventions.** `本家主` ("this patriarch"), `老夫` ("this old one"), `本座` ("this seat" / "this one"). Repeated formal third-person self-reference is intentional characterization in Chinese — flag it once per character so the reader recognizes the pattern.
-   **Classical units of measure.** `时辰` = 2 hours, `里` ≈ 500 m, `丈` ≈ 3.3 m, `斤` ≈ 600 g. When the literal English measure sits naturally in the prose, a footnote on first use lets readers calibrate the original.
-   **Chinese idioms that lose their imagery in translation.** `做牛做马` ("be ox and horse" — to serve devotedly), `画蛇添足` ("draw a snake, add legs" — over-elaboration), etc. Note the literal once so the picture behind the meaning surfaces.
-   **Allusions to Chinese mythology, history, or Buddhist/Daoist concepts.** The Great Sage's connection to Sun Wukong (Journey to the West) is a perfect example — knowing that 大圣 invokes the Monkey King reframes the character's whole vibe.
-   **Wordplay, dialect markers, or register shifts that the English can't carry.** Beijing slang like `你丫的`, mock-formal honorifics, etc.

### When NOT to add a TL note

-   Anything already in the glossary — don't duplicate.
-   Translator's reasoning ("I chose X because the original Y means Z"). Notes are for the reader, not the editor's defense.
-   More than 2–3 per chapter on average. If a chapter would need five, condense the closely-related ones into a single combined note, or move a recurring item to the project glossary.
-   Modern profanity sanitization, em-dash decisions, paragraph splits — these are editor concerns, not reader concerns.
-   Content the prose already explains (the AI sometimes spells out a concept in-text and a TL note then becomes redundant).
-   **Common terms whose English translation already lands.** A generic insult that reads as an insult in English (e.g., "lap dog" for 走狗), a macho swagger that reads as macho swagger from the surrounding tone (e.g., 老子 contextually obvious from "Kill him!"), modern Chinese slang already familiar from internet culture — these don't need notes. The reader picks them up.

### Calibrating the bar

A TL note should add genuine reader value *beyond* what the English prose already carries. The useful test:

-   If a reader who doesn't know Chinese would feel the prose is **missing something** without the note, add it.
-   If they'd find the note an interesting tangent but the prose works fine without it, skip.

The bar is "the English alone leaves a gap" — not "the Chinese has more depth." Every Chinese term has more depth than its English translation; that doesn't mean every term gets a note. Reserve notes for cases where the gap *matters* to the scene (the 休 verb at the climax of Ch5, the Sun Wukong allusion that reframes the Great Sage's whole character, the patriarchal 本家主 that defines Wang Lang's voice).

### Footnote numbering

Per-chapter sequential: each chapter restarts at `[^1]`. The numbers are local to the file, not project-wide. Don't try to make footnotes consecutive across chapters.

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
-   [ ] TL notes added for any first-use cultural references, classical units, pompous self-reference, or untranslatable idioms (1–3 per chapter; see Translator's Notes section).

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
