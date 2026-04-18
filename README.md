# ai-augmented-learning
Personal Obsidian wiki + agentic AI study partner with citation and scope guardrails. Built during UW CSE 163.

# ML-Course-Vault

A personal experiment in using agentic AI as a study partner — with guardrails.

This repo is the knowledge system I built for **UW CSE 163 (Intermediate Data Programming)**. It pairs an Obsidian knowledge graph with a scope-constrained agentic AI (Claude), governed by a project spec (`CLAUDE.md`) that tells the AI how to behave: stay inside the course, cite every claim, follow my note conventions, and update the vault as I learn.

The interesting part is the **system design** — the constraints that make the AI verifiable instead of vibes-based.

---

## Origin

At **Boeing Defense** and **Boeing Space**, I built onboarding wikis for new engineers. In environments defined by legacy systems and proprietary information, a centralized knowledge hub compresses weeks of tribal knowledge into something a newcomer can actually navigate.

By Spring 2026, UW had given the green light to AI in coursework, and employers were shifting from permitting AI to *requiring and tracking* its use. Fluency with **agentic AI** was becoming a baseline expectation. I decided to treat agentic AI the same way — not as an oracle, but as a colleague working from an authoritative knowledge base.

I built on Andrej Karpathy's [**LLM Wiki**](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f) pattern, adding two things:

- **Course-specific guardrails** — scope constraints, citation discipline, and academic-honesty limits (walks through concepts, never writes graded solutions).
- **A personalized growth loop** — the system reads across chat threads to detect recurring struggles, then *promotes* those concepts into a dedicated **growth** section that's forced into the AI's context on every response. The AI becomes an active study partner with cross-session memory of where I need the most work.

---

## Why I built it

Most AI study tools hand you plausible-sounding answers with no way to check them, which is terrible for learning. I wanted a system where:

- Every answer is **traceable back to a source** I can verify (a lecture timestamp, a lesson page, a concept note I wrote, an Ed Discussion thread)
- The AI **refuses to hallucinate past the curriculum** — if the class hasn't covered a Python feature yet, it tells me so instead of filling in from general knowledge. Because the AI is also forced to cite course material for every claim, I've noticed significantly fewer hallucinations in practice
- My notes are **a knowledge graph**, not a linear document — so the AI can link new material into what I already know instead of re-explaining from scratch
- The system **learns my conventions** (tag vocabulary, wikilink style, frontmatter) and extends them rather than inventing new ones

---

## Architecture

    Me  ⇄  Claude (agentic AI)  ⇄  Obsidian ML-COURSE-VAULT.md (knowledge wiki)
                  │
                  ▼
            CLAUDE.md (project spec)
            .auto-memory/ (persistent context about me + the project)

- **Obsidian vault** — interlinked markdown notes organized by concept, lecture, and lesson. Wikilinks form a graph; the graph view shows concept clusters.
- **Claude** — agentic AI with file access to the vault. Reads notes, writes new notes, updates existing ones, answers questions.
- **`CLAUDE.md`** — the project spec. The most important file in this repo. It defines the rules the AI operates under every session.
- **Memory files** — persistent context about me (role, project state, feedback patterns) that carries across sessions so the AI doesn't start from zero each time.

---

## The guardrails (`CLAUDE.md`)

The spec file at the root of this repo constrains the AI along four axes:

1. **Explore the vault before answering.** Link and extend existing notes rather than re-explaining from scratch.
2. **Stay inside the course.** Answer only from what CSE 163 has actually covered. No `rsplit`, no list comprehensions, no pandas string methods — unless the course has shown them. If a technique hasn't been covered, say so explicitly.
3. **Cite sources in a dual-link format.** Every answer ends with a Sources block containing at least two different *kinds* of source (lecture + timestamp, lesson page, concept note, Ed thread, assignment). Links must be clickable in both chat and Obsidian.
4. **Never write solutions to graded assignments.** Walk through concepts; let me write the code.

These aren't suggestions the AI can drift away from — they're enforced every response.

---

## What I learned building this

- **Prompts are specs, not magic.** `CLAUDE.md` is really a behavioral contract. Tightening it is the same work as tightening a type signature — each rule rules out a class of bad outputs.
- **Citation is a forcing function.** Requiring the AI to cite its sources from my own notes exposes gaps in those notes. If it can't cite, I haven't written the note yet. The vault grows where my understanding is weakest.
- **Scope constraints outperform knowledge injection.** Telling the AI "don't use Python features the class hasn't covered" produced more useful, course-aligned help than feeding it the textbook would have.
- **Memory decouples sessions from context.** The memory system lets the AI pick up where we left off without re-explaining who I am or what I'm working on.

---

*Built by Angela Sposato, Spring 2026.*
