# Indra and the Wandering Words

A browser-based reading adventure for a 4–5 year old. It is an adventure game
first: the child explores a forest, meets characters, finds secrets and
collects treasure — and reading is the magic that makes all of it work.

**She can play it on her own.** Every screen reads itself out loud, every
button is a picture, a hand points at what to tap, and an ear button in the
same corner of every screen repeats whatever was just said. The only words she
is ever asked to read are the ones the game is teaching her.

No build step, no frameworks, no network, no accounts, no adverts. Open it and
play.

---

## Running it

**Simplest:** double-click `index.html`. It works straight off the disk
(the scripts are classic `<script>` tags, not ES modules, precisely so that
`file://` works).

**Recommended** — a local web server, so the browser will let the game save
progress in `localStorage` on every platform:

```bash
cd Learn-to-Read
python3 -m http.server 8000
# then open http://localhost:8000
```

To host it, upload the folder to any static host (GitHub Pages, Netlify,
S3…). There is nothing to compile.

**Sound:** the voice comes from the browser's built-in speech synthesis, so
the first tap anywhere unlocks audio (a browser rule). No audio files ship
with the game.

---

## The story

Every word in the world lives in the Great Book of Everything. One night the
words flew out and scattered across the kingdom as little glowing lights.
Bridges forgot how to be bridges. Doors forgot how to open.

The player is a Word Keeper. Reading a word calls it home, and the world
mends itself a piece at a time.

**The cast**

| | | |
|---|---|---|
| 🦊 **Pip** | your companion | A very small fox who is very sure he is very brave. |
| 🦉 **Luma** | the wise one | Keeper of the Great Book. Carries a lantern of old, patient light. |
| 🦔 **Bramble** | forest friend | Loses things roughly once every ten minutes. |
| 🐰 **Poppy** | forest friend | Hears every sound in the whole forest. |
| 🐢 **Tock** | forest friend | Never in a hurry. Not even a little. |
| 🏮 **The Lantern Wanderer** | mysterious | Leaves maps. Says little. Turns up when you need a path. |
| ☁️ **Grumblewink** | the trouble | Took the letters because nobody ever read him a story. Becomes a friend. |

There is no villain. Nothing in this game is frightening.

---

## Chapters

| # | Region | Teaches | Scenes |
|---|--------|---------|--------|
| 1 | 🌳 The Letter Forest | letters, upper/lowercase, letter sounds, beginning sounds | 13 |
| 2 | 🏞️ Sound Valley | blending CVC words (c‑a‑t → cat), rhyme and word families | 10 |
| 3 | 🏘️ Word Village | high-frequency sight words, whole-word reading | 9 |
| 4 | ⛵ Sentence Sea | building and reading first sentences | 9 |
| 5 | ⛰️ Story Mountain | short stories, comprehension, everything together | 9 |

All five are fully playable, end to end, around 90 reading interactions in
total. Each region follows the same shape: arrive and meet someone, learn the
new idea in a story scene, practise it in two or three activities, find a
hidden thing, then open a multi-lock gate that mixes every skill learned so
far. The last one fills the Great Book back up and Grumblewink finally gets
his story.

Progress saves after every single answer, and the map remembers which scene
she stopped on.

---

## What is built

**Reading activities** (all reusable across chapters, all data-driven)

| Activity | Skill | Where |
|---|---|---|
| Letter Fireflies — catch the firefly carrying a letter | letter recognition, letter sounds | ch1, ch5 |
| Mushroom Match — pair the big letter with its little one | upper/lowercase | ch1 |
| Hidden Leaf Hunt — find a letter hidden in the scenery | letter recognition | every chapter |
| Sound River — hop the stone whose picture starts with the sound | letter sounds | ch1, ch2, ch5 |
| Magic Spell — build a word letter by letter | phonics / blending | ch1, ch2, ch3, ch5 |
| Rhyme Time — find the word that rhymes | word families | ch2 |
| Treasure Cave — read the clue, open the right chest | word reading | ch1, ch2, ch3 |
| Sight Signs — hear a word, tap the signpost that says it | sight words | ch3, ch4, ch5 |
| Word Bridge — pick the word that names the picture | word reading | ch3, ch4, ch5 |
| Sentence Boat — put scattered words back in order | sentence reading | ch4, ch5 |
| Reading the Waves — read a sentence, pick the picture | sentence reading | ch4 |
| Story Detective — read a tiny story, answer a question | comprehension | ch5 |

Every one of the seven tracked skills now has at least one activity that
practises it, and the parent dashboard has real numbers for all of them.

**Systems**

- **Reading Power** — a visible meter and ranks (Letter Explorer → Sound
  Detective → Word Wizard → Sentence Sailor → Story Reader → Word Keeper).
  Never a score, never a percentage, never a grade.
- **Adaptive difficulty** — per skill, invisible to the child. Three clean
  answers raise the ceiling (harder words, more choices, more of the
  alphabet); two misses in a row quietly lower it. She is never told.
- **Three-step hints** — 💡 gives a picture clue, then the sound, then shows
  the answer and lets her tap it. Hints still earn Reading Power: asking for
  help is never penalised. Two misses auto-reveals, so she can never be stuck.
- **Wrong answers** — no buzzer, no red X, no failure screen. A friendly
  "Almost!", the option gently fades out of the way, and she carries on.
- **Rewards** — stars, gems, stickers, animal friends, treasures, places,
  and a secret area. Big moments get a celebration; small ones do not, so the
  big ones still mean something.
- **My Adventure Book** — friends, animals, treasures, stickers, letters,
  words and places, with empty slots hinting at what is still out there.
- **Surprises** — a shooting star, a chest that was definitely not there a
  second ago, a mouse with an acorn, one of Pip's terrible jokes. Roughly one
  in four scene transitions, each one only ever happens once.
- **Autosave** — after every answer, and flushed when the tab is hidden or
  closed. There is no save button.
- **Nothing needs reading** — see below. This is the design constraint the
  whole game is built around.

---

## A four-year-old can play this alone

The point of a game that teaches reading is that it cannot *require* reading.
Every place the game asked a child to read a word before she could carry on
has been removed:

- **Every screen introduces itself out loud** the moment it opens — the title,
  the character creator, the map, the adventure book, every story scene, every
  round of every activity, every reward, every locked region, every
  celebration. There is no screen that is silent on arrival.
- **Every button is a picture**, with the word underneath for whoever is
  reading over her shoulder. ▶️ next, ✅ go, 👍 ready, 🏠 home, 📔 book,
  🗺️ map, 🎉 yay.
- **The 👂 ear button** sits in the same corner of every single screen and
  repeats whatever was just said. It is the one control she has to learn, and
  she only has to learn it once.
- **A pointing hand** appears on the thing to tap. On the map it sits on the
  region she should play next; in a scene it sits on the continue button.
- **Going quiet is noticed.** If nothing is tapped for a while the game offers
  the instruction again and points. It keeps offering — less often, but never
  stopping — because there may be nobody nearby to ask.
- **Story words light up as they are spoken**, one at a time, so the sounds
  she hears are visibly attached to the marks on the page.
- **She cannot get stuck.** Wrong options fade away, two wrong tries reveals
  the answer, and after a long silence the game walks her to it and lets her
  tap it herself. Every round is winnable.
- **The first tap wakes the book.** Browsers refuse to make a sound until the
  page has been touched, so a cold start shows a big hand and "tap anywhere"
  rather than narrating into silence.

The only text a child is ever *required* to read is the text she is being
taught to read — the letter on the firefly, the word on the plank, the
sentence on the page. That is the game.

The one screen that is deliberately exempt is the Parent Zone, which is for a
grown-up, is behind a gate, and stays silent.

---

## Parent Zone

Hold the small ⚙ button (bottom left) for **2.5 seconds**, then answer a
multiplication question. It shows Reading Power, per-skill accuracy and
adaptive level, letters/sounds/words mastered and in progress, hints used,
recent activities, and where a little extra practice may help — plus voice and
sound toggles, a full save-data dump, and a reset.

None of this is ever visible to the child.

**Privacy:** everything is stored in this browser's `localStorage` only.
No accounts, no network calls, no analytics, no adverts, no purchases.

---

## Developer mode

Off by default. Turn it on with `?dev=1` in the URL, `LTR.DEV = true` in
`js/game.js`, or `LTR.dev.enable()` in the console. A 🛠 button appears
bottom-right with: reset save, unlock all chapters, ±Reading Power, jump to
any chapter or any minigame, simulate correct/incorrect answers to exercise
the adaptive engine, and live skill statistics.

```js
LTR.dev.playGame('magicSpell');       // jump straight into a minigame
LTR.dev.simulate('phonics', false, 2); // two misses → difficulty drops
LTR.dev.stats();                       // console.table of every skill
LTR.state.data                         // the whole save
```

---

## Layout

```
index.html
css/
  styles.css          layout, components, responsive rules
  animations.css      keyframes, particles, celebrations
js/
  util.js             DOM builder, RNG, event bus, screen-scoped subscriptions
  storage.js          persistence layer  ← swap the adapter for cloud saves
  state.js            the save file and every mutation that touches it
  audio.js            a speech QUEUE + procedurally generated sound effects
  guide.js            narration, the pointing hand, idle nudges  ← read this
  art.js              every character and prop, as inline SVG
  progression.js      Reading Power, ranks, the adaptive engine
  readingEngine.js    chooses what to ask (spaced, adaptive, fair distractors)
  ui.js               screens, backdrops, HUD, particles, modals, rewards
  dev.js              developer tools (off by default)
  game.js             boot
  data/
    letters.js        the alphabet, with sounds and example words
    words.js          the word corpus (~145 words, add as many as you like)
    characters.js     the cast
    stories.js        tiny stories + simple sentences
    chapters.js       the adventure itself, as data
  minigames/
    base.js           the shared engine: prompts, hints, feedback, scoring
    letterFireflies.js  mushroomMatch.js  soundStones.js   magicSpell.js
    wordBridge.js       treasureCave.js   storyDetective.js rhymeTime.js
    sightSigns.js       sentenceBuild.js  (sentenceBuild registers two games)
  screens/
    title.js  characterCreator.js  worldMap.js  chapter.js
    adventureBook.js  parentMode.js
assets/               (empty — all art is SVG/CSS, all audio is synthesised)
```

### Adding content

**A word** — one line in `js/data/words.js`, and every activity can use it:

```js
w('nest', 2, ['n','e','st'], 'nature', '🪺', 'cvc', 'est')
//  word  difficulty  phonemes  category  picture  type  rhyme family
```

**A chapter** — append an object to `js/data/chapters.js`. The engine reads
nodes of type `story`, `activity`, `gauntlet` and `discover` and needs no
changes:

```js
{
  id: 6, name: 'Rhyme Reef', emoji: '🐚', env: 'river',
  requiredPower: 20, skills: ['phonics'], mapPos: { x: 50, y: 20 },
  nodes: [
    { id: 'c6-hello', type: 'story', cast: ['tock'], beats: [ … ] },
    { id: 'c6-rhymes', type: 'activity', game: 'rhymeTime',
      skill: 'phonics', rounds: 4, rewards: [ … ] }
  ],
  completion: { title: '…', rewards: [ … ], unlocks: 7 }
}
```

**A minigame** — register one round-builder; the base engine supplies the
prompt bar, the hint ladder, praise, scoring and rewards:

```js
LTR.game('myGame', {
  name: 'My Game', skill: 'wordReading',
  buildRound: function (ctx) {
    var word = LTR.reading.pickWord(ctx.skill);          // adaptive pick
    return {
      prompt: 'Find the word', bucket: 'words', key: word.word,
      // The spoken cue. A plain string is read as a sentence; a list lets you
      // mix speech with letter names, letter sounds and words, which matters
      // because engines read a lone "A" as the article "uh". Leave it out and
      // the written prompt is read instead — no round is ever silent.
      autoVoice: [{ text: 'Find the word' }, { word: word.word }],
      render: function (area, api) {
        area.appendChild(api.choice({ txt: word.word, correct: true }));
      }
    };
  }
});
```

**Cloud saves later** — implement three methods and register them; nothing
else changes:

```js
LTR.storage.useAdapter({ name: 'cloud', load, save, remove });
```

---

## Tested

Driven headlessly (jsdom) and rendered in Chromium:

- **Full playthrough** — a robot that taps options at random, the way a child
  mashing the screen does, completes all five chapters: every one of the 11
  minigames plays, ~90 reading interactions, no runtime errors, no stalls, no
  screen it cannot get out of.
- **Round contract** — 600 generated rounds per game per skill level. Each is
  checked for exactly one correct answer, no two options sharing a picture or
  a word, and no beginning-sound distractor that makes the target's sound.
  Zero failures.
- **Non-reader audit** — every screen, every chapter opening and every
  minigame is checked to speak on arrival, to offer the ear button, and to
  have no text-only button anywhere.
- **Layout** — no horizontal overflow at 320×640, 390×844, 420×820, 768×1024,
  820×380 (landscape) or 1280×800.
- **By hand** — parent gate (short taps rejected, long press + correct answer
  accepted), reload-and-resume mid-chapter, the full hint ladder, adaptive
  difficulty moving up and down, and voice toggles.

## What to build next

1. **Recorded audio** for the letter sounds. Speech synthesis says "buh" well
   enough, but a real voice is warmer and more accurate — drop it behind
   `LTR.audio.letterSound()`. Every caller already goes through that one
   function.
2. **More words and more sentences.** The corpus is ~145 words and 20
   sentences; the engine is built for thousands and adding one is one line.
3. **Chapter 6 and beyond** — digraphs (sh, ch, th), longer vowels, and
   chapter books. Appending to `chapters.js` needs no engine changes.
4. **A writing activity** — tracing letters with a finger, using the same
   `LTR.game()` contract.
5. **Cloud save** via the storage adapter, so progress follows her between the
   tablet and the laptop.
