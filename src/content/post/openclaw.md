---
layout: ../../layouts/post.astro
title: OpenClaw is a disaster waiting to happen
description: Don't use OpenClaw. Just don't.
dateFormatted: Feb 5, 2026
---

OpenClaw is a disaster waiting to happen, and as an experienced SRE, you couldn’t pay me enough to run it.This is an autonomous AI agent that you're giving full system access to. We’re talking rights to execute shell commands & file operations. You feed it your API keys and credentials for your  email, your calendars, and your messaging platforms. All of this is controlled by a Node.js service that makes decisions on its own and can "proactively wake up" to do things you didn't ask for. The security model is essentially "trust the AI completely" with barely any guardrails. One misconfigured skill, one compromised npm module in the extensible architecture, one hallucinated command, and you're looking at arbitrary code execution with your production credentials. The fact that it's gone viral among developers who are hooking it up to their work Slack, corporate Gmail, and AWS accounts is genuinely terrifying.

The operational nightmare doesn't stop at security. You're running a long-lived service with memory state, autonomous scheduling, and cross-platform integrations that can fail in dozens of non-deterministic ways. When it breaks—and it will break, because AI agents get confused, APIs rate limit, and network calls timeout—you're debugging an opaque system where the "bug" might be the LLM's reasoning rather than your code. There's no rollback strategy for an agent that already sent emails, modified files, or kicked off deployments.

And all of this is packaged as "just run npm install and give it access to everything!" The hype is real and the demos are impressive, but from an SRE perspective this is production incident bingo. If you value your sleep and your sanity, and you just gotta try it, at least deploy this nowhere near anything that matters.


