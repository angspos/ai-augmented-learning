# ai-augmented-learning
Personal Obsidian wiki + agentic AI study partner with citation and scope guardrails. Built during UW CSE 163 in Spring 2026.

# ML-Course-Vault

A personal experiment in using agentic AI as a study partner — with guardrails.

This repo is the knowledge system I built for **UW CSE 163 (Intermediate Data Programming)**. It pairs an Obsidian knowledge wiki (also called the VAULT) with a scope-constrained agentic AI (Claude), governed by a project spec (`CLAUDE.md`) that tells the AI how to behave: stay inside the course, cite every claim, follow my note conventions, and update the vault as I learn.

**The VAULT grows according to how you interact with Agentic AI.** It tailors *your* learning style, gaps in *your* understanding, all within the in the framework of the course material and lectures.

--- 

## Origin

As an intern at **Boeing Defense** (2023) and **Boeing Space** (2024), I built onboarding wikis for new engineers. In environments defined by legacy systems and proprietary information, a centralized knowledge hub/wiki compresses weeks of tribal knowledge into something a newcomer can navigate.

By Spring 2026, UW had given the green light to AI in coursework. Simultaneously, employers began shifting from permitting AI to *requiring and tracking* its use. Fluency with **agentic AI** is becoming a baseline expectation. I decided to treat agentic AI as a colleague working from an authoritative knowledge base (aka the VAULT).

I built on Andrej Karpathy's [**LLM Wiki**](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f) pattern, adding:

- **Course-specific guardrails** — scope constraints, citation discipline, and academic-honesty limits (walks through concepts, never writes graded solutions).
- **A personalized growth loop** — the system reads across chat threads to detect recurring struggles, then *promotes* those concepts into a dedicated **growth** section that's forced into the AI's context on every response. The AI becomes an active study partner with cross-session memory of where I need the most work.
- **Forced Citations** (see below)

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
            .auto-memory/ (persistent context about me + the course)

- **Obsidian VAULT** — interlinked markdown notes organized by concept, lecture, and lesson. Wikilinks form a graph; the graph view shows concept clusters.
- **Claude** — agentic AI with file access to the vault. Reads notes, writes new notes, updates existing ones, answers questions.
- **`CLAUDE.md`** — the project spec. The most important file in this repo. It defines the rules the AI operates under every session.
- **Memory files** — persistent context about me (role, project state, feedback patterns) that carries across sessions so the AI doesn't start from zero each time.
- Note: .auto-memory/ is a built in function of Agentic AI. we are merely leveraging it.

---

## The guardrails (`CLAUDE.md`)

The spec file at the root of this repo constrains the AI along four axes:

1. **Explore the vault before answering.** Link and extend existing notes rather than re-explaining from scratch.
2. **Stay inside the course.** Answer only from what CSE 163 has actually covered. No `rsplit`, no list comprehensions, no pandas string methods — unless the course has shown them. If a technique hasn't been covered, say so explicitly.
3. **Cite sources in a dual-link format.** Every answer ends with a Sources block containing at least two different *kinds* of source (lecture + timestamp, lesson page, concept note, Ed thread, assignment). Links must be clickable in both chat and Obsidian.
4. **Never write solutions to graded assignments.** Walk through concepts; let me write the code.

AI cannot drift away from these guardrails — they're enforced every response.

---

## What I learned building this

- **Prompts are specs.** `CLAUDE.md` is really a behavioral contract. Each rule rules out a class of bad outputs.
- **Citation is a forcing function.** When the AI can't cite a vault note for a concept, it flags the gap and offers to create the note. Every missing citation becomes a prompt to write the note — so the vault grows in sync with whatever I'm currently engaging with, and the concepts I revisit most often become the most densely-connected parts of the graph.
- **Feedback loops allow for tailored learning.** Every chat with AI, allows the VAULT to grow in those particular subjects. The VAULT becomes most dense in the areas I struggle with the most.
- **Scope constraints outperform knowledge injection.** Telling the AI "don't use Python features the class hasn't covered" produced more useful, course-aligned help than feeding it the textbook would have.
- **Memory decouples sessions from context.** The memory system lets the AI pick up where we left off without re-explaining who I am or what I'm working on.
- **Tackles gaps in understanding on two fronts.** By having the forced citation, and prompting when we should add more to those subjects/concepts, and by having a weekly review of all concepts to promote etc. We effectively use two models working together to help fill gaps in understanding. Allowing equity for all students.

---

## Note

The full ML-Course-VAULT is kept private. UW course materials — lecture content, Ed Discussion threads, readings, and graded-assignment prompts — are not republished here, in respect of University of Washington copyright and the course's academic honesty policy. This repo showcases the **system**.

*Built by Angela Sposato, Spring 2026.*
