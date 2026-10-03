# Indra and the Wandering Words

A browser-based reading adventure for a 4–5 year old. It is an adventure game
first: the child explores a forest, meets characters, finds secrets and
collects treasure — and reading is the magic that makes all of it work.

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

## Opening ident

Every launch opens on the Entropic Labs logo (`assets/video/entropic-ident.mp4`), played full-screen
by `js/ident.js` while the game loads underneath. A tap, click, Enter, Space or Escape
skips it; if the video can't load or autoplay, the game simply starts. Add
`?noident` to the URL to skip it while developing.

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

| # | Region | Teaches | Status |
|---|--------|---------|--------|
| 1 | 🌳 The Letter Forest | letters, upper/lowercase, letter sounds, beginning sounds | **fully playable** |
| 2 | 🏞️ Sound Valley | blending CVC words (c‑a‑t → cat) | preview postcard |
| 3 | 🏘️ Word Village | high-frequency sight words | preview postcard |
| 4 | ⛵ Sentence Sea | first sentences | preview postcard |
| 5 | ⛰️ Story Mountain | short stories, comprehension | preview postcard |

Chapter 1 is a 13-scene journey: meet Pip → catch letter fireflies → help
Bramble sort his mushrooms → follow a butterfly to a **secret glade** → cross
the Sound River with Poppy → learn spell-building from Luma → talk Grumblewink
into opening his gate (a five-lock finale mixing every skill) → make a friend
of him. Around 23 reading interactions, roughly 10–15 minutes, and it saves
after every single one.

---

## What is built

**Reading activities** (all reusable across chapters, all data-driven)

| Activity | Skill | Where |
|---|---|---|
| Letter Fireflies — catch the firefly carrying a letter | letter recognition | ch1 + finale |
| Mushroom Match — pair the big letter with its little one | upper/lowercase | ch1 + finale |
| Hidden Leaf Hunt — find a letter hidden in the scenery | letter recognition | ch1 secret |
| Sound River — hop the stone whose picture starts with the sound | letter sounds | ch1 + finale |
| Magic Spell — build a word letter by letter | phonics / blending | ch1 + finale |
| Word Bridge — pick the word that names the picture | word reading | ch1 finale |
| Treasure Cave — read the clue, open the right chest | word reading | ch1 secret glade |
| Story Detective — read a tiny story, answer a question | comprehension | ready for ch4–5 |
| Rhyme Time — find the word that rhymes | word families | ready for ch2 |

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
- **Spoken cues** — each round says its *cue* aloud once ("catch the letter
  M"), never the answer. Games where the written word **is** the answer only
  ever speak a generic instruction. Story dialogue is read aloud in each
  character's own voice, so a pre-reader can follow the adventure alone.
  Every 🔊 button re-reads on demand. Turn the automatic voice off in the
  Parent Zone and the buttons still work.

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
  util.js             DOM builder, RNG, event bus
  storage.js          persistence layer  ← swap the adapter for cloud saves
  state.js            the save file and every mutation that touches it
  audio.js            speech synthesis + procedurally generated sound effects
  art.js              every character and prop, as inline SVG
  progression.js      Reading Power, ranks, the adaptive engine
  readingEngine.js    chooses what to ask (spaced, adaptive, fair distractors)
  ui.js               screens, backdrops, HUD, particles, modals, rewards
  dev.js              developer tools (off by default)
  game.js             boot
  data/
    letters.js        the alphabet, with sounds and example words
    words.js          the word corpus (~130 words, add as many as you like)
    characters.js     the cast
    stories.js        tiny stories + simple sentences
    chapters.js       the adventure itself, as data
  minigames/
    base.js           the shared engine: prompts, hints, feedback, scoring
    letterFireflies.js  mushroomMatch.js  soundStones.js  magicSpell.js
    wordBridge.js       treasureCave.js   storyDetective.js  rhymeTime.js
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
      autoVoice: 'Find the word',                        // cue, never answer
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

Played end-to-end in Chromium at 900×700, 360×640, 390×740, 740×380
(landscape) and 820×1100, with zero console errors: full Chapter 1
completion, chapter unlock, reload-and-resume mid-chapter, wrong answers,
the full hint ladder, adaptive difficulty moving both up and down, the parent
gate (short taps rejected, long press + correct answer accepted), and every
minigame including the two not yet used in Chapter 1.

## What to build next

1. **Chapter 2, Sound Valley** — the pieces already exist: `magicSpell` with
   harder words, `rhymeTime`, and a new "stretch the sounds" activity.
   It is a data file, not engine work.
2. **Recorded audio** for the letter sounds. Speech synthesis says "buh" well
   enough, but a real voice is warmer and more accurate — drop it behind
   `LTR.audio.letterSound()`.
3. **More words.** The corpus is ~130; the engine is built for thousands.
4. **A word-family activity** (`-at`, `-og`, `-un`) — the `family` field is
   already in the data.
5. **Cloud save** via the adapter, so progress follows her between the tablet
   and the laptop.
