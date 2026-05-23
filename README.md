# Muddy Children Puzzle Simulator

An interactive web-based simulator for the **Muddy Children Problem**.

Muddy Children Problem is a classic puzzle in epistemic logic that shows how agents reason about their own knowledge based on public announcements and the observed silence of others.

To access the simulator, click the link here: [https://h-ch125.github.io/Muddy-Children-Puzzle-Simulator/
](https://h-ch125.github.io/Muddy-Children-Puzzle-Simulator/)

---

## Introduction

The Muddy Children Problem is a foundational puzzle in epistemic and modal logic:

- A group of children are standing together. Some have mud on their foreheads.
- Each child can see every other child's forehead but not their own.
- A parent publicly announces: *"At least one of you is muddy."*
- The parent then repeatedly asks: *"Do you know whether you are muddy?"*

The elegant result: if there are **k** muddy children, then after **exactly k rounds**, all muddy children will correctly deduce that they are muddy.

This puzzle illustrates how **common knowledge** and **public announcements** drive cascading logical deductions across agents who each have only partial information.

---

## How to Use

No build step required, the entire app runs from a single `index.html` file.

1. **Set the parameters** using the sliders: choose the total number of children (2–7) and how many are muddy.
2. Click **"Start Puzzle"** to initialize a new game. The muddy children are randomly assigned.
3. Click **"Ask: Do you know if you're muddy?"** to advance the simulation by one round.
4. **Click on any child** in the circular display to open their reasoning panel — see their observation, internal thought, and current knowledge state.
5. Repeat until the puzzle is solved. The simulator will explain the outcome.
6. Click **"Reset"** to start over with new settings.

---

## How It Works

### Logical Core

The simulator implements the epistemic reasoning of each child via `getChildReasoning(childIndex, currentRound)`:

- **`seenMuddy`**: the number of muddy children visible to child `i`. A muddy child sees `k - 1` muddy faces; a clean child sees `k`.
- **Muddy children**: in rounds `1` through `k - 1`, a muddy child sees enough muddy peers that the situation is still ambiguous. In round `k`, since those peers *didn't* answer in round `k - 1`, the child deduces there must be one more muddy child than they can see — themselves.
- **Clean children**: they see all `k` muddy children and know they are clean, but do not announce anything (only muddy children speak up).

The core deduction for a muddy child in round `k`:

> *"If there were only the muddy children I see, they would have answered by round k−1. Since they haven't, I must also be muddy."*

---

## Background & References

- [Stanford Encyclopedia of Philosophy — Dynamic Epistemic Logic](https://plato.stanford.edu/entries/dynamic-epistemic/) — formal treatment of the Muddy Children Problem and related puzzles
- [Modal Logic Playground](http://rkirsling.github.io/modallogic/) — interactive tool for exploring modal and epistemic logic models
