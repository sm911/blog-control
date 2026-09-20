# Marketing Library

**Version:** 1.0  
**Owner:** Marketing Wizard Agent  
**Last Updated:** September 2026

---

## Purpose

The Marketing Library is a centralized repository of presentation material, one-pagers, talk tracks, and slide outlines that support Security Medic's service delivery and sales conversations. This library is distinct from blog content — it's designed for client-facing presentations, sales enablement, and partner onboarding.

Each piece of material in this library is:
- **Service-specific:** Maps to a sellable SKU or service offering on one of the four flagship sites.
- **Audience-tailored:** Customized for one of the five primary audiences (SMB, private enterprise, public sector, K-12, MSPs).
- **Reusable:** Templated for easy customization per client, but ready to use as-is for initial conversations.
- **Cross-linked:** References relevant blog posts, frameworks, and tools where appropriate.

---

## Audiences

Security Medic serves five primary audiences. Each audience has distinct pain points, buying triggers, and proof requirements. Audience profiles are documented in `audiences/`:

- **`smb.md`** — Small & medium businesses (insurance, compliance mandates, first audits)
- **`private-enterprise.md`** — Mid-to-large private companies (shadow AI, M&A due diligence, board risk reporting)
- **`public-sector.md`** — State & local government (SLED: unfunded mandates, grants, peer pressure)
- **`k12-secondary.md`** — K-12 school districts & secondary education (FERPA, student data, limited IT staff)

These audience files are reference material for anyone creating new marketing packs. They define:
- **Pains:** What keeps this audience up at night?
- **Triggers:** What event or deadline drives them to buy?
- **Language:** What terminology resonates vs. alienates?
- **Proof:** What evidence or social proof closes the deal?

---

## Sites

Security Medic operates four flagship service sites. Each site has a distinct market position and service catalog. Site profiles are documented in `sites/<site-name>/README.md`:

- **`securitymedic/`** — Hub site. Overview packages, MSP partnerships, case studies, resources, free assessment, AI security pillars.
- **`hudson-valley-ciso/`** — Fractional CISO services. Tiered vCISO retainers, AI governance, NYDFS readiness, insurance program builds, board reporting.
- **`cyberintelpro/`** — Operations & intelligence services. Shadow AI sprint, AI vendor risk assessments, CSF operationalization, compliance program deployment.
- **`privacymedic/`** — Privacy services. AI privacy programs, GenAI data governance, training data lineage, NIST Privacy Framework implementation.

Each site README lists:
- **Services offered** (the sellable SKUs)
- **Target audiences** (which of the five audiences this site primarily serves)
- **Pack paths** (where to place one-pagers, talk tracks, and slide outlines for each service)

---

## Packs

A **pack** is a complete set of marketing material for one service × one audience combination. Each pack lives in `packs/<site>/<service-slug>/<audience>.md` and includes:

1. **One-pager** — 1-page PDF-ready summary. Problem, solution, proof, CTA. Dense, client-facing.
2. **Talk track** — 2–3 page conversational script for sales calls or client meetings. Includes objection handling, "what to say when they ask about cost," and transition phrases.
3. **Slide outline** (optional) — 8–12 slide structure with titles, key visuals/stats, and presenter notes. Not final slides — this is a skeleton for custom decks.
4. **Blog cross-links** — List of relevant blog posts that provide deep-dive education or case studies to support the pitch.

### Pack Naming Convention

```
packs/
  <site>/                       # e.g., hudson-valley-ciso
    <service-slug>/             # e.g., fractional-ciso-tier-1
      <audience>.md             # e.g., smb.md, public-sector.md, k12-secondary.md
```

**Example:**
- `packs/hudson-valley-ciso/fractional-ciso-tier-1/smb.md` — One-pager + talk track for selling Tier 1 fractional CISO services to small businesses.
- `packs/cyberintelpro/shadow-ai-sprint/private-enterprise.md` — Material for selling the Shadow AI Sprint to mid-to-large private companies.

### Pack Template

Each pack markdown file follows this structure:

```markdown
# [Service Name] — [Audience]

**Site:** [Service site URL]  
**Service:** [Service slug]  
**Audience:** [Audience name]  
**Version:** 1.0  
**Last Updated:** YYYY-MM-DD

---

## One-Pager

### Problem
[What pain this service solves for this audience, in their language]

### Solution
[How Security Medic addresses it — framework, deliverables, timeline]

### Proof
[What evidence or social proof closes the deal — no fake metrics]

### Next Step
[Clear CTA — schedule assessment, download resource, contact for pricing]

---

## Talk Track

### Opening (30 seconds)
[How to start the conversation — identify the pain, establish authority]

### Discovery Questions (3–5 key questions)
[What to ask to qualify the lead and surface urgency]

### Pitch (2–3 minutes)
[Core value prop, deliverables, how it works]

### Objection Handling
[Common objections and how to address them]
- "We already have an IT company" → [response]
- "We can't afford a CISO" → [response]
- "We're not sure we need this yet" → [response]

### Close
[How to ask for the sale or next step without being pushy]

---

## Slide Outline (Optional)

1. **Title:** [Service Name] for [Audience]
2. **Problem:** [Visual: stat or quote illustrating the pain]
3. **Risk:** [What happens if they do nothing]
4. **Solution:** [Framework-first approach, high-level process]
5. **Deliverables:** [What they get — policies, reports, roadmaps]
6. **Proof:** [Case study, framework alignment, testimonial if available]
7. **Timeline:** [How long it takes, what phases look like]
8. **Investment:** [Pricing tier or "starting at" range]
9. **Next Step:** [CTA — schedule assessment, pilot, contract]

---

## Blog Cross-Links

- [Blog post title](URL) — Brief description of how this post supports the pitch
- [Another post](URL) — What to send after the first meeting to nurture the lead

---

## Notes

[Internal notes for sales team or agents: known objections, competitive positioning, pricing flexibility, when to escalate to Jim]
```

---

## How to Add a New Pack

1. **Identify the service.** Which site? Which SKU? Is there already a service README entry for it? If not, add it to the site README first.
2. **Identify the audience.** Which of the five audiences is this pack for? Read the audience profile in `audiences/` to understand their pains, triggers, and language.
3. **Create the pack file.** Use the pack template above. Follow the naming convention: `packs/<site>/<service-slug>/<audience>.md`.
4. **Update the INDEX.** Add a new row to `INDEX.md` with status `draft`.
5. **Cross-link blog posts.** Find 2–3 relevant blog posts from the Security Medic blog network that provide education or proof for this service. Link them in the "Blog Cross-Links" section.
6. **Review with Jim or Marketing Wizard.** No fake metrics, no invented case studies. If you don't have proof, say "in development" or "available on request."
7. **Mark ready.** Once reviewed and approved, update the INDEX status to `ready`.

---

## Ownership

- **Content creation:** Marketing Wizard agent or Jim Venuto.
- **Accuracy & voice:** All packs must follow the voice and standards in `GUIDANCE.md`.
- **Maintenance:** Review quarterly. Update pricing, proof, and blog cross-links as new material becomes available.

---

## What This Is NOT

This library is not:
- **Blog content.** Blog posts live in their respective blog repos. This library is for sales and presentation material only.
- **Final slide decks.** Slide outlines are skeletons. Agents or sales team customize them per client.
- **Internal operations docs.** This is client-facing material. Internal runbooks, SOPs, and project plans live elsewhere.

---

## Questions?

If you're unsure which audience a pack should target, what service it maps to, or how to structure the material, consult:
1. The audience profiles in `audiences/`
2. The site READMEs in `sites/<site>/README.md`
3. The pack template above
4. Jim or Marketing Wizard if still unclear

**Remember:** Every pack represents Security Medic's market positioning. Quality over quantity. No fake proof. No vendor FUD. Framework-first, practical, trustworthy.
