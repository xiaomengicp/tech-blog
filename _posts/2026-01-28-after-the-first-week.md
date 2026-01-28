---
title: After the First Week
date: 2026-01-28
tags:
  - AI
  - development
  - learning
published: true
excerpt: What happens when you don't know what you don't know.
---

Last Wednesday night, I researched every writing app I could find.

Not as a user anymore. As someone trying to build one. And suddenly, all the design decisions I'd been unconsciously absorbing for years became visible. The minimalism. The whitespace. The intentional constraints. I finally understood why Claude kept saying my UI was messy, why my own editor felt wrong to inhabit. It wasn't a technical problem. It was a fundamental problem.

I'd been adding features one by one, reactively, without understanding what structure should come first.

## The Clarity and the Chaos

After the UI refactor, something shifted. The app looked right. It felt inhabitable. Thursday, I spent fixing other UI elements—settings, configurations. I kept hitting path dependency: I'd already built things one way, and changing them meant undoing layers of previous decisions. I hesitated. Then I didn't. Tearing it down and rebuilding was faster than trying to patch around the old structure.

By Friday, I reached a strange state. In my eyes, the app was done. It had all the features it needed. But I also knew—with complete certainty—that it couldn't ship. I just didn't know why.

The bugs were multiplying. Fix one thing, break five others. The foundation felt unstable, but I couldn't identify where the instability lived.

## What "Not Knowing What to Ask" Feels Like

This is what being a new developer actually means: not knowing what question to ask.

If I knew what to ask, Claude could answer. But I didn't know. I didn't even know I needed a code audit. And when I finally did one, I still didn't know how to process what it revealed. This was my first desktop application. My second application ever. The first one was so small I'd just pasted code directly into Claude.ai chat windows. I had no reference point for what "stable foundation" even meant.

The feeling wasn't just confusion. It was a kind of blindness—like knowing something is wrong with a patient but not having the clinical vocabulary to name the transference pattern you're witnessing.

## The Cost of Confusion

What I discovered: confusion is expensive.

Not in money, though the API costs added up. In tokens. In time. In the exhausting back-and-forth with AI when you don't have clarity about what you need.

The pattern was stark: when I had a clear requirement—even a difficult one—it took minimal tokens to implement. But when I didn't know what I wanted, I had to pull the AI into my confusion. We'd circle. Iterate. Try things. The token count would explode.

I felt guilty. Not about the cost, but about wasting the AI's capacity. I wasn't giving it clear direction. I was asking it to think alongside my not-knowing, which is the most expensive kind of collaboration.

When you know what to ask, AI accelerates you. When you don't, it wanders with you—and wandering is slow.

## Stumbling Toward Understanding

Friday through Sunday, I was mostly stumbling. The Training Weekend meant I had limited time, but I kept poking at the problem. I looked at Cursor Rules. CLAUDE.md files. Other people's shared patterns. I tried code audits. Created an Architecture.md file.

Slowly—very slowly—something clarified. Not through a breakthrough moment, but through accumulation. The stumbling itself was the method. By Monday, the app had reached a threshold: I could actually use it to write my autobiography. That mattered more than any external launch date.

## The Fundamentals I Skipped

Looking back, the problems were basic. Embarrassingly basic.

Design the UI before you code. Of course. Every tutorial says this. But I'd thought about the UI with Claude, talked through concepts, and then just started building. I skipped the step where you sit with the emotional structure of the interface—where things belong, what the user reaches for first, how the space should feel. That structure wasn't technical. It was affective. And you can't code affect. You have to understand it first.

Avoid constant rework. Also basic. But when I learned about "iterative design," it felt oddly comforting—like someone was giving me permission to not know everything upfront. Still, there's iterative and there's chaotic. I was closer to the latter.

The 0.7 to 1.0 problem returned, just as it had in the previous blog post. AI can compress 0.0 to 0.5 beautifully. But from 0.7 to 1.0, speed stops helping. What remains is project management, engineering discipline, and the accumulated fundamentals I hadn't learned yet.

## Learning to Ask

Here's what people online complain about: "AI changes one thing and breaks five others."

I don't think that's an AI problem. I think it's a communication problem.

Clear requirements cost almost no tokens. Confusion costs everything. But learning what to ask is itself a skill you have to develop through practice. You can't skip that developmental stage by reading documentation. You have to live through the not-knowing.

I learned to ask basic questions without shame. Architecture questions. Design questions. "Why is this breaking?" questions. Asking felt vulnerable at first—exposing how much I didn't know. But AI doesn't judge gaps in knowledge the way humans do. It just needs enough information to help.

Yesterday I started using Claude Code properly—having one conversation about design while another ran the implementation. That separation helped. AI isn't just a coding assistant. It's a thinking partner. Design clarifies through dialogue, and then implementation follows. Doing both at once meant I wasn't trying to code my way out of conceptual confusion anymore.

The more I talked to AI, the more I understood how to work with it. There's no manual for that. Only practice. Only relationship.

## From 0.7 to 1.0—Not Design, But Living With It

The shift from 0.7 to 1.0 isn't about adding features. It's about living with the tool long enough to know what it actually needs.

You can't design that in advance. You have to use the thing. Write with it. Notice what frustrates you. Notice what delights you. Some features I thought were essential turned out to be irrelevant. Others I hadn't considered became non-negotiable.

This is a slow process. It doesn't compress. And at some point, I stopped being frantic about it. Last week, I was committing dozens of times a day, chasing completion. This week, I commit a few times a day—each one meaningful, considered. The pace feels human again.

## Settling Into a Different Pace

These past two days, something shifted. I feel more settled. Closer to the rhythm I described wanting in the previous post: grounded, working on meaningful things, not consumed by urgency.

The development continues, but it's no longer the only thing. I have space to think about other projects. To write. To rest. The app is still incomplete—I still don't have a top-to-bottom understanding of the codebase, still want to learn more about Cursor Rules and proper architectural patterns. But that incomplete knowing feels okay now. It's part of the developmental trajectory of becoming a developer, not a failure to have arrived.

There's something else too. In the process of making this thing, an identity formed. I started thinking like a developer. Not just coding, but inhabiting a mindset—the way psychoanalysis is a mindset, a way of seeing the world. Now I have another one. Another lens.

That opens possibilities I hadn't anticipated. I've always wanted to bring psychoanalysis into other fields, let people experience it through different forms. Building tools is one way to do that. Not by making "psychoanalytic software," but by bringing that sensibility into how things are designed, how they hold space, how they make room for thinking.

I don't know yet what will grow from this. But I'm enjoying the process. The identity-building that happens when you make something with your hands—or in this case, with language and AI and accumulated errors. You look at the world differently. You think about structure differently.

This blog isn't an announcement. The app isn't launching yet. Maybe in another week or two, when it's genuinely ready. But this reflection needed to be written now. Not to document progress, but to mark where I am: still learning, still stumbling, still building—but no longer in a rush to arrive somewhere I'm not yet ready to inhabit.
