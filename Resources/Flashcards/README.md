# Flashcard Guide

> How to build, import, and use flashcard decks for CompTIA A+ exam preparation.

---

## Why Flashcards Work

Flashcards implement two of the most powerful learning techniques simultaneously:

1. **Active Recall** — Each card forces you to retrieve the answer from memory rather than recognize it
2. **Spaced Repetition** — Anki's algorithm shows cards at the optimal interval before you would forget them

For the A+ exam, which requires memorizing hundreds of discrete facts (port numbers, pin counts, RAID specifications, command syntax), a well-built flashcard deck is one of the highest-return study investments you can make.

---

## Recommended Platform: Anki

**Download:** [apps.ankiweb.net](https://apps.ankiweb.net) — Free on Windows, macOS, Linux, and Android. The iOS app is a one-time paid purchase.

### Why Anki Over Quizlet

| Feature                     | Anki                            | Quizlet                                |
| --------------------------- | ------------------------------- | -------------------------------------- |
| Spaced repetition algorithm | Advanced (SM-2)                 | Basic / none in free tier              |
| Offline use                 | Full functionality              | Limited                                |
| Cost                        | Free (Android/Desktop); $25 iOS | Free basic; $35/year for full features |
| Deck sharing                | AnkiWeb community               | Large community                        |
| Customization               | Highly configurable             | Limited                                |

---

## Setting Up Anki

1. Download and install Anki from [apps.ankiweb.net](https://apps.ankiweb.net)
2. Create a free account at [ankiweb.net](https://ankiweb.net) for cloud sync across devices
3. Create a deck: **File → Create Deck** → Name it "CompTIA A+ Core 1" and "CompTIA A+ Core 2"

---

## Finding Pre-Built Decks

Before building your own deck from scratch, search for community decks:

### AnkiWeb Shared Decks

1. Open Anki → Click **Get Shared** (at the bottom)
2. Search: "CompTIA A+ 1201" or "CompTIA A+ 220-1102"
3. Preview the deck to verify quality and alignment with current objectives
4. Download and import

### Reddit / Community Decks

Search Reddit's r/CompTIA for posts like:

- "Anki deck for A+"
- "Shared flashcards port numbers"

One frequently recommended community deck covers all required port numbers with mnemonics. See the r/CompTIA subreddit.

---

## Building Your Own Deck (Recommended)

Building cards yourself is more time-consuming than downloading pre-built decks, but produces significantly better retention because the act of _creating_ the card is itself an active recall exercise.

### Card Types for A+ Content

#### Basic (Question → Answer)

Best for: Definitions, single-fact lookups

Example:

- **Front:** What port does SSH use?
- **Back:** Port 22 (TCP)

#### Cloze Deletion (fill-in-the-blank)

Best for: Remembering part of a list or sequence

Example:

- **Text:** The laser printer process steps are: Processing, Charging, {{c1::Exposing}}, Developing, Transferring, Fusing, Cleaning

#### Image-Occlusion

Best for: Hardware identification, diagram-based memory

Example: Use an image of a DIMM and mask the label — reveal the label (DDR4, 288-pin) when answering

---

## Suggested Card Categories

Build one sub-deck per category for organized review:

| Sub-deck                        | Cards to Include                                      |
| ------------------------------- | ----------------------------------------------------- |
| **Ports & Protocols**           | Port number → service/protocol; service → port number |
| **RAM Specs**                   | Generation → pin count; SODIMM vs DIMM                |
| **RAID Levels**                 | RAID level → function, min disks, fault tolerance     |
| **Wireless Standards**          | 802.11x → frequency, speed, key feature               |
| **CLI Commands**                | Command → function; task → command                    |
| **Troubleshooting Methodology** | Step number → name and key action                     |
| **Malware Types**               | Type → definition and key characteristics             |
| **OSI Layers**                  | Layer number/name → protocols/devices                 |
| **Security Concepts**           | Term → definition                                     |

---

## Effective Study Session with Anki

### Daily Review (15–30 minutes)

- Run your "Due" cards first — these are the cards Anki's algorithm has determined you need to review today
- Be honest with the difficulty rating (Again / Hard / Good / Easy) — inflating ratings defeats the algorithm
- Do not skip days — the algorithm is calibrated to consistent daily review

### Adding New Cards

- Add 5–15 new cards per study session
- Adding too many at once creates an unsustainable review load 2–3 weeks later
- Limit new card additions during the final two weeks before the exam — focus on review only

### Pre-Exam Review

Switch to "Custom Study" → Review ahead of time → Show cards due in the next 7 days. This gives you a final sweep of all material.

---

## Quizlet Alternative

If you prefer Quizlet:

1. Search [quizlet.com](https://www.quizlet.com) for "CompTIA A+ 1201" or "CompTIA A+ 220-1102"
2. Filter by creation date and star rating to find active, quality decks
3. Use the **Learn** mode (not Flashcards mode) — this implements a basic spaced repetition system
4. Use **Test** mode for paper-format active recall practice

---

## Card Quality Tips

| Do                                      | Don't                                                                   |
| --------------------------------------- | ----------------------------------------------------------------------- |
| One fact per card                       | Cram multiple facts onto one card                                       |
| Make questions specific                 | Use vague prompts like "Tell me about RAID"                             |
| Use mnemonics on the back of cards      | Only list the bare answer                                               |
| Test both directions when relevant      | Only test one direction (e.g., port → protocol but not protocol → port) |
| Include a context hint for tricky cards | Add so much context that you never have to recall anything              |

---

_Back to: [Resources Overview](../Recommended_Resources.md)_
