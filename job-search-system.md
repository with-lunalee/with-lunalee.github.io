---
layout: default
title: "From borrowed prompts to my own rules: how I built a job-search system with Claude Code as a non-developer"
---

# From borrowed prompts to my own rules: how I built a job-search system with Claude Code as a non-developer

*Notes from my first job search as a non-developer.*

---

## TL;DR

I'm an entry-level job seeker who doesn't write code. **I designed my own job-search system with Claude Code.**

- Reviewing job postings used to take me more than half a day. It now takes **about 20 minutes**.
- I organized my experiences into blocks that I reuse as material for applications.
- When the AI made a mistake, I didn't just fix it once. **I turned it into a rule so it wouldn't happen again.**

---

## Context: how it started

I'm a non-developer. I don't write code myself; I build things with AI tools.

The first time I really used AI was during a short startup internship in my undergrad.
Through vibe coding with ChatGPT and Gemini, I tried database design and web development for the first time.
**It showed me firsthand what I could do with AI, and that's when I got interested in it.**

Later, I came across the idea of a "harness": the files and rules an AI reads before it starts working.
I wondered if it was something like a well-organized folder structure. If so, I thought I could apply it without much trouble.
Then I found a guide on X (Twitter) by a Claude Code user who had automated their job search. The author was an experienced professional who had used the system to change jobs. The goal of the guide was to cut down the time a job search takes.

**I started with one thought: "I can build what I need most right now, fitted to me."**

## Problem: what wasn't working

**I started my first job search right after wrapping up my coursework.**
I hadn't figured out how to write applications, or how to choose which postings to apply to.

### Picking postings was the first wall

1. I wanted postings that matched the work I wanted to do and my own conditions. But I couldn't pin down the right job titles, and I didn't know what criteria to filter by.
2. Just reviewing postings took me **more than half a day**.

### AI wasn't an instant answer either

I'd seen plenty of posts saying "AI is all you need" or "just use this prompt."
But I had only ever used AI in a chat window, so I hit a wall right away.
I had to learn how chat differs from Claude Code and what the terms in those posts meant, and setting up my environment took hours at a time.

Pasting in someone else's prompt as-is almost never gave me what I wanted.
**A prompt is shaped by the purpose and situation of the person who wrote it.**
Even general-purpose prompts had their own ways of being tuned to a situation, and what people with a technical background take for granted wasn't a given for me.
I only learned then that GitHub existed, and how much it matters to developers.
The guide's design had the same issue. It was built by an experienced professional for changing jobs, so it didn't fit my situation as someone without work experience, or how internship and contract roles are screened.

**Instead of using it as-is, I had to rebuild it so the AI would work by my own judgment.**

---

## What I built

At first, I asked a chat assistant for the commands to type into Claude Code, then pasted them in.
While building a job-posting filter, my chat sessions kept running out of tokens, so **I moved to working directly in Claude Code.**
The system I ended up with has three parts.

### 1. Job-posting filter

**I set the criteria first.**
Even when the work I wanted was vague and hard to measure, I talked it through with AI and laid out everything.
The AI pulled those conditions together. Even vague ones that made me wonder "can I really filter by this?", it interpreted and connected to real job postings.
I then fixed all of it in a separate criteria file, including conditions that would rule a posting out, like required experience or location, and the scoring criteria.

> Example: read the main duties before the job title.
> - "Forward Deployed Engineer": an engineering title, but if the actual work is helping non-technical colleagues adopt AI, it's a match
> - "AI 기획" (AI planning): in Korea, 기획 is a job family close to product management, and "AI" in front names the domain. If the actual work is model training or building data pipelines, it's not a match

I was paying for a Claude subscription, but I couldn't spend much on running the system. So I focused on what I could use for free.
**Gemini offered several models I could call for free, so I gave it the first-pass filtering and had Claude do the scoring.**
Recommended postings from email alerts went through this flow, and the results came back in a fixed format that I could review quickly.

> ```
> Setting criteria: the work and conditions I want (even vague ones) → AI collects and interprets them
>                   → connects them to real postings → fixed in a criteria file
> Filtering:        recommended postings from email → Gemini first pass → Claude scoring
>                   → results in a fixed format → my review
>                   (both Gemini and Claude read the criteria file)
> ```

### 2. Experience blocks

I wrote up my experiences one by one as STAR (Situation, Task, Action, Result) blocks.
**Each block gets tags from 22 options across four axes. The AI skims a one-line summary index first, then opens only the blocks it needs.**

> ```
> Experience → STAR block (one file per block) → tags (4 axes, 22 tags)
>            → skim the one-line index → open only the blocks needed
> ```

> ```
> Situation      zero-to-one · improvement · adversity · leading · seeing it through
> Communication  explaining · requirements definition · coordination · persuasion   (with people only)
> Skill          structuring · visualization · problem reframing · resource allocation · reading the rules
>                · fast learning · verification · end-to-end ownership · AI collaboration
> Outcome        award · delivered to client · adopted internally · unfinished
> ```

### 3. Application drafts

In Korea, many companies ask for application essays, similar to a cover letter but answering set questions from each company.
I built a flow that matches a posting's required skills with my blocks, then has the AI write and review a draft.
**But the AI's job ends at choosing material and writing the draft.** A rule blocks it from writing any fact that isn't in my blocks, and I decide what stays and what changes.
Reading the drafts helped me pin down the flow I wanted, and I fixed the structures that read as logical into the prompts.
When there was a direction or a story I wanted to work in, I brought it up in conversation to make the essay stronger.

> ```
> Posting's required skills ↔ my blocks → AI draft and review (fact rules apply)
>   → I shape the flow and add stories (in conversation) → structure fixed in prompts
> ```

---

## Decisions: three key calls

At first, I saw a harness as a folder structure. Building one showed me the core isn't the folders. It's fixing in files the context the AI reads every time.

That idea sits under all three decisions.
Unlike people, an AI doesn't lose track of context that's been fixed in a file.
**So when the criteria live in files, the AI works in the same order, by the same criteria, every time.** Writing down the filter's conditions came from the same reasoning.

### 1. I changed how results are proven

The original design asked for numbers behind every result. That fits experienced people changing jobs.
But for entry-level and internship applications, making up percentage improvements only reads as exaggeration.
**So I changed the standard: results are proven by scale, scope of what was built, whether it was actually used, and what constraints applied.** That matches what reviewers expect from an entry-level candidate.

### 2. I turned the AI's mistakes into rules

AI fills in blanks convincingly. Two real mistakes each became a rule.

> ```
> Mistake 1. I only said someone had been in a doctoral program. The AI recorded it as "PhD in Engineering,"
>            adding a field I never mentioned
>   → Rule: don't fill in details I never gave
>
> Mistake 2. The AI treated a file it had once generated for me as if it existed in my folder
>   → Rule: don't assume a file exists
> ```

Leaving unknowns blank wasn't the answer either. I saw that as avoidance. So the AI handles uncertain points in one of three ways:
use my exact words, make an estimate with its reasoning stated and get my approval, or mark it `[NEEDS CHECK]`.

**What this system produces goes to real people. So I treated unverified content going out as-is as the biggest risk.**

### 3. I split files by the kind of work

At first, all my experience blocks were in one file, and all the prompts were in another.
**I separated tasks that need judgment from tasks that only need a summary, and facts read every time from criteria read only now and then, so the AI opens only the files it needs.**

> ```
> Before: all experience blocks → one file / prompts → one file
>
> After:
> CLAUDE.md                 ← rules and per-task entry points the AI reads first
> profile/
> ├── _overview.md          ← summary for a quick skim
> ├── _index.md             ← tag index for when judgment is needed
> ├── _tagging-guide.md     ← tagging logic (only when tagging)
> ├── _tagging-log.md       ← history of tag criteria changes
> ├── 0_block_writing_standards.md  ← block writing standards (only when editing blocks)
> └── blocks/A~I.md         ← one file per block
> writing/                  ← application writing steps, prompts, and a log of my judgment calls
> backlog/                  ← material not yet turned into blocks
> submitted/ · candidate/   ← applications sent · ones reviewed and not sent
> _structure-log.md         ← structure check history
> ```

---

## Results: what changed

**I started my first job search right after wrapping up my coursework, and still got from reviewing postings to actually applying quickly.**

- **Reviewing postings**: more than half a day → **about 20 minutes**
- **Applications**: after building the system, 2 submitted, and 2 more reviewed and deliberately not submitted
- **Organizing experience**: 9 experience blocks tagged, with changes tracked in git since September 17, 2026
- **Getting started**: less time stuck doing nothing because everything felt vague

## What I learned

Once the system was in place, my work changed.
The basic steps run without much effort, and my role became adjusting the structure and refining what to tell the AI.

**I learned that using AI well isn't about getting answers. It's about deciding what to trust and what to check.**
First, I make clear what I want through conversation, and expand it.
Then I put it under clear rules and criteria, and check thoroughly that the result came out the way I wanted.

---

## Credits

- **Base design**: @moneynena's guide to automating a job search with Claude Code, in Korean. The free article "Job-search automation #2-A: 22 experience blocks" (https://x.com/moneynena/article/2047897472379584932) and the author's subscriber posts
- **A README in every folder**: the webinar "Hands-on AI for Researchers" (Korean, August 26, 2026)
- **Git basics**: the YouTube video "If you use Claude Code, watch this: 3 Git and GitHub essentials + tips for non-developers" (Korean), https://www.youtube.com/watch?v=Y8lGdEyNv-M
