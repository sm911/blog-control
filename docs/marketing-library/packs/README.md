# Marketing Packs Directory

**Last Updated:** September 2026

---

## Purpose

This directory contains **marketing packs** — complete sets of presentation material for each service × audience combination. Each pack includes a one-pager, talk track, optional slide outline, and blog cross-links.

---

## Directory Structure

```
packs/
  <site>/                       # e.g., securitymedic, hudson-valley-ciso, cyberintelpro, privacymedic
    <service-slug>/             # e.g., fractional-ciso-tier-1, shadow-ai-sprint, ai-privacy-program
      <audience>.md             # e.g., smb.md, private-enterprise.md, public-sector.md, k12-secondary.md
```

---

## Pack Format

Each pack is a markdown file following this template:

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
- "Objection X" → [response]
- "Objection Y" → [response]

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

## Naming Conventions

### Site Names (Directory Level 1)
Use lowercase, hyphenated directory names matching the site brand:
- `securitymedic`
- `hudson-valley-ciso`
- `cyberintelpro`
- `privacymedic`

### Service Slugs (Directory Level 2)
Use lowercase, hyphenated slugs describing the service:
- `fractional-ciso-tier-1`
- `shadow-ai-sprint`
- `nist-csf-operationalization`
- `ai-privacy-program`

### Audience Files (File Level)
Use lowercase, hyphenated filenames matching audience names:
- `smb.md`
- `private-enterprise.md`
- `public-sector.md`
- `k12-secondary.md`

**Special case:** MSPs may be treated as an audience file (`msp.md`) or referenced within service-specific context if the service is MSP-only (e.g., MSP Partnership Program).

---

## How to Create a New Pack

1. **Check the INDEX:** Review `docs/marketing-library/INDEX.md` to see which packs are planned and their status (todo, draft, ready).

2. **Read the audience profile:** Consult `docs/marketing-library/audiences/<audience>.md` to understand pains, triggers, language, and proof requirements.

3. **Read the site README:** Consult `docs/marketing-library/sites/<site>/README.md` to understand the service offering, deliverables, and typical engagement model.

4. **Create the pack file:** Use the pack template above. Save to `packs/<site>/<service-slug>/<audience>.md`.

5. **Follow GUIDANCE.md:** Voice, tone, proof standards, and CTA guidelines from `GUIDANCE.md` apply to all packs.

6. **No fake proof:** Do not invent case studies, client names, or metrics. If real proof doesn't exist, say "designed for organizations facing [trigger]" or "available on request."

7. **Update the INDEX:** Add a row to `docs/marketing-library/INDEX.md` with status `draft`. After review and approval, update status to `ready`.

---

## Review Checklist

Before marking a pack as `ready` in the INDEX:

- [ ] Voice matches Security Medic tone (practical, framework-first, vendor-neutral, regionally grounded)
- [ ] Audience language is appropriate (consult audience profile for language guidance)
- [ ] Proof is real or clearly marked as designed/in-development
- [ ] Objection handling addresses common concerns for this audience
- [ ] Blog cross-links are current and relevant
- [ ] CTA is soft, clear, and links to the correct service site
- [ ] Pricing (if mentioned) is accurate or marked as "contact for pricing"
- [ ] No vendor product pitches or fake SOC claims

---

## Ownership

- **Content creation:** Marketing Wizard agent or Jim Venuto
- **Accuracy & voice:** All packs must follow GUIDANCE.md standards
- **Maintenance:** Review quarterly or when service offerings, pricing, or proof changes

---

## Current Status

As of September 2026, this directory is empty (except for this README). See `docs/marketing-library/INDEX.md` for the planned pack inventory (76 packs across 4 sites × multiple services × 5 audiences).

Priority packs (based on sales pipeline demand):
1. Fractional CISO — Tier 1 × SMB
2. Shadow AI Sprint × Private Enterprise
3. Cyber Insurance Program Build × SMB
4. AI Governance Retainer × Private Enterprise
5. NIST CSF 2.0 Operationalization × MSPs

---

## Questions?

If you're unsure how to structure a pack, which audience to target, or what proof to include, consult:
1. The pack template above
2. The audience profiles in `docs/marketing-library/audiences/`
3. The site READMEs in `docs/marketing-library/sites/<site>/README.md`
4. `GUIDANCE.md` for voice, tone, and content standards
5. Jim or Marketing Wizard if still unclear
