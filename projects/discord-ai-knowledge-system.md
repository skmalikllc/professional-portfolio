# Discord AI knowledge and contribution system

**Full case study:** [discord-ai-knowledge-base-automation](https://github.com/skmalikllc/discord-ai-knowledge-base-automation)
**Reference architecture:** [discord-knowledge-assistant](https://github.com/skmalikllc/discord-knowledge-assistant)

---

## Overview

A production system for a documentation-heavy online community: an AI assistant that answers member questions from an approved document set, and a separate automation path that scores member contributions and drives rank promotion.

## Problem

The community had a large body of written material built up over years, across several products with more than one edition of each in active use. The material existed; almost nobody read it. The same questions repeated weekly and a small number of people answered them by hand.

The obvious fix — point a retrieval model at everything and drop it in the channel — is where these builds usually fail. They produce answers that sound right and are not, blending two editions of the same document into one confident reply that matches neither. Once members catch that, the assistant becomes something they check rather than something they use.

A second, separate need: recognising member contribution consistently rather than depending on who happened to be paying attention.

## My role

Sole implementer — server setup and process management, the bot, knowledge-base preparation and loading, the routing layer, scoring and rank automation, the operator dashboard concept, testing and the written handover.

## Work performed

- Prepared and loaded six routed knowledge areas, backed by eight vector stores
- Built the routing layer so each channel resolves to exactly one store before the model is involved — unmapped channels return nothing rather than falling back
- Designed the assistant to decline rather than guess, with a fixed refusal phrase and source attribution on every answer
- Built the contribution scoring path: deduplication, classification, per-type daily caps, logging and score derivation
- Built rank promotion: automatic for lower ranks, held for staff approval at higher ranks, synced back as role changes
- Diagnosed and fixed a promotion-status bug that was blocking members from later promotion checks after their first promotion
- Specified an operator dashboard covering assistant status, server health, credit balance, items needing attention and per-store performance

## Tools

Node.js · Discord bot · OpenAI vector stores · Airtable · Make.com · Google Drive · PM2 · Ubuntu server · DigitalOcean

## Solution

Two independent systems sharing only the chat platform, so the knowledge base can be rebuilt without stopping scoring, and a scoring fault cannot change what the assistant answers.

## Outcome

Six routed knowledge areas configured and tested against their own documents; two further products identified as not yet wired and recorded as outstanding rather than quietly omitted. Routing isolation verified for the new knowledge base and one existing control route. Contribution scoring and rank promotion running end to end.

No throughput, accuracy or engagement figures are published, because they were not measured under conditions worth quoting.

## Skills demonstrated

System design under reliability constraints · AI retrieval architecture · server administration and process management · database and automation integration · diagnostic fault-finding · documentation and handover

## Privacy note

The client is not named. No code, configuration, document content, product title, member name, server address, credential or identifier from the live system appears in the public repository. The full sanitization policy is published inside it.
