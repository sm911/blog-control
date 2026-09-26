# SMC Digital Estate Map

**Version:** 1.0  
**Owner:** Jim Venuto / Security Medic Consulting  
**Last Updated:** September 26, 2026  
**Source:** CoS GitHub estate review (96 repos across sm911)

---

## Purpose

This map is the **source of truth** for how Security Medic's GitHub estate is organized. It catalogs all production sites, blogs, products, pursuit work, legacy IBM artifacts, personal projects, and forks. Use it to understand what lives where, what's active vs. archived, and where new work should go.

**North star:** One estate map, one naming/topic system, fewer near-duplicates, forks only when actively diverging, blogs under a single control plane.

---

## Brands → Sites → Hosting

Security Medic operates four primary brand websites plus two reserved/redirect-only domains:

| Brand | Repo | Hosting | Primary Domain | Status |
|-------|------|---------|----------------|--------|
| **Security Medic** | [securitymedic](https://github.com/sm911/securitymedic) | Vercel (Next.js) | securitymedic.com | **Active** — hub site |
| **Hudson Valley CISO** | [hudson-valley-ciso-website](https://github.com/sm911/hudson-valley-ciso-website) | Vercel | hudsonvalleyciso.com, hvciso.com | **Active** — fractional CISO/Govern brand |
| **CyberIntelPro** | [cyberintelpro-website](https://github.com/sm911/cyberintelpro-website) | Vercel (Next.js) | cyberintelpro.com | **Active** — [CONFIRM: site vs redirect] |
| **Privacy Medic** | [privacymedic.com](https://github.com/sm911/privacymedic.com) | Vercel (Next.js) | privacymedic.com | **Active** — [CONFIRM: site vs redirect] |
| **GRC Resilience** | [grcresilience.com](https://github.com/sm911/grcresilience.com) | Content dump (not a site scaffold) | grcresilience.com | [GAP: rename to `grc-resilience-playbook` or fold into brand docs] |
| Resilience Medic | [resiliencemedic.com](https://github.com/sm911/resiliencemedic.com) | (empty stub) | resiliencemedic.com | **DELETE-CANDIDATE** — or keep name-parked private |
| SMC GRC AI | [smcgrc.ai](https://github.com/sm911/smcgrc.ai) | (empty stub, domain redirects to securitymedic.com/services) | smcgrc.ai | **DELETE-CANDIDATE** |

### Brand Domain Ambiguities (Needs Jim's Decision)

1. **privacymedic.com & cyberintelpro.com:** Are these standalone Vercel brand sites, or permanent 301 redirects into securitymedic.com? `sm-web-portfolio` domain-map documentation currently conflicts with live Next.js repos.
2. **grcresilience.com:** Future brand site, or one-off research drop? Repo contains playbook content, not site scaffold.

---

## Hub Routes & Known Gaps

The **securitymedic.com** Next.js hub must own these paths as the production entry points:

| Path | Points To | Status |
|------|-----------|--------|
| `/blog` | Should aggregate data-security.blog, securitymedic.blog, cloud-architecture.blog | **GAP: /blog missing or broken** |
| `/workshops/privacy` | privacymedic.com (if redirect) | [CONFIRM] |
| `/services` | Aggregates smcgrc.ai, dataprotectservices.com | Active |
| `/ny` | smbdataprotect.com | Active |
| `/healthcare/billing` | billing-pro(s).com | Active |
| `/services/lead-to-booking` | technology-assist*.com | Active |

**Known issue:** `/blog` hub page still missing per prior audit. Must rebuild index or point `*.blog` domains at GitHub Pages hubs.

---

## Blog Production (GitHub Pages)

Security Medic operates **seven production blogs** on GitHub Pages. All content is managed via the blog-control template system (this repo).

| Blog | Repo | URL | Focus | Audience |
|------|------|-----|-------|----------|
| **NIST CSF 2.0** | [CFS-2.0](https://github.com/sm911/CFS-2.0) | https://sm911.github.io/CFS-2.0/ | Framework education, CSF 2.0 adoption, Govern function | SMB, compliance officers, IT managers |
| **Leadership** | [leadership-blog](https://github.com/sm911/leadership-blog) | https://sm911.github.io/leadership-blog/ | CISO perspective, board governance, executive risk | CIOs, CFOs, boards, executive teams |
| **Compliance** | [compliance-blog](https://github.com/sm911/compliance-blog) | https://sm911.github.io/compliance-blog/ | HIPAA, NYDFS, SOC 2, regulatory analysis | Regulated entities, compliance managers |
| **Cloud Architecture** | [cloud-architecture-blog](https://github.com/sm911/cloud-architecture-blog) | https://cloud-architecture.blog/ | Cloud security design, IaC, AWS/Azure/GCP | Cloud engineers, DevOps, architects |
| **Data Security** | [data-security-blog](https://github.com/sm911/data-security-blog) | https://data-security.blog/ | Software security, supply chain risk, AI security | Developers, CISOs, risk managers |
| **Data Privacy** | [data-privacy-blog](https://github.com/sm911/data-privacy-blog) | https://sm911.github.io/data-privacy-blog/ | Privacy frameworks, GDPR/CCPA, AI training data | Privacy officers, legal, DPOs |
| **AI & Automation** | [ai-automation-blog](https://github.com/sm911/ai-automation-blog) | (TBD) | AI ops, automation, GenAI governance | CTOs, AI product leads, risk committees |

### Blog Registration Status

- **Six blogs** are registered in blog-control routing table and have theme files.
- **ai-automation-blog** is **MISSING from blog-control routing table** — must be added to `config.json` and assigned a template/theme.

### Blog Cross-References

See `GUIDANCE.md` for editorial focus, metadata requirements, and routing decisions. See `README.md` (this repo) for template system architecture and CLI usage.

---

## Staging & Control Plane

| Repo | Purpose | URL | Status |
|------|---------|-----|--------|
| **blog-staging** | Unlisted review site for all blogs | https://sm911.github.io/blog-staging/ | **Active** — Jim approves here before promotion |
| **blog-control** | Template library, marketing library, GUIDANCE, and this estate map | (this repo) | **Active** — control plane for all blog production |
| **hudsonvalleyciso-staging** | Govern homepage staging mockup | (unlisted GH Pages) | **Keep as canonical** |
| ~~hvciso-govern-staging~~ | Duplicate of above (byte-identical `index.html`) | (unlisted) | **DELETE-CANDIDATE** — confirmed identical SHA |
| **blogdrafts** | Legacy drafts (Mar 2026) | (local only) | **Merge useful drafts → blog-staging, then Archive** |
| **hvfusion** | Tiny static HTML Pages site (unclear brand role) | (Pages) | [GAP: document purpose or Archive] |

---

## Products (Internal & External Tools)

Active products, SaaS platforms, and productized tools that are sellable or support Security Medic operations:

| Repo | Purpose | Audience | Status |
|------|---------|----------|--------|
| [mission-control](https://github.com/sm911/mission-control) | SMC ops dashboard (Next.js, OpenClaw-linked) | Internal ops | **Active** |
| [SM-System](https://github.com/sm911/SM-System) | Security Medic OS — governed AI consulting framework | Internal governance | **Active** — [rename to `sm-system`] |
| [smc-app](https://github.com/sm911/smc-app) | Multi-tenant vCISO SaaS (Cynomi-style product path) | External SaaS | **Active** — [decide: product vs lab] |
| [privacy-assessor](https://github.com/sm911/privacy-assessor) | NIST Privacy Framework 1.1 assessor (FastAPI) | Clients, self-service | **Active** |
| [nist-ai-rmf-assessment](https://github.com/sm911/nist-ai-rmf-assessment) | NIST AI RMF multi-tenant assessor | Clients, self-service | **Active** |
| [trustframe-ai-risk-studio](https://github.com/sm911/trustframe-ai-risk-studio) | TrustFrame AI Risk Studio (related AI risk UX) | Clients | [GAP: merge with nist-ai-rmf or document boundary?] |
| [privacy-guardian-lab](https://github.com/sm911/privacy-guardian-lab) | Lovable-generated privacy lab scaffold | Lab/experimental | [Archive unless adopted] |
| [SEC8KBreachTracker](https://github.com/sm911/SEC8KBreachTracker) | 8-K breach tracker (Python) | Internal/research | [Keep or Archive if unused] |
| [claims-dashboard-v1](https://github.com/sm911/claims-dashboard-v1) | Claims dashboard (labeled "production") | Internal/sales tool | **Active as canonical** — [consolidate with claims_dashboard] |
| [claims_dashboard](https://github.com/sm911/claims_dashboard) | Parallel claims ROI app (same era, larger) | Internal/sales tool | [GAP: merge → decide winner vs v1] |
| [claims-roi-assessment](https://github.com/sm911/claims-roi-assessment) | Pre-sales ROI calculator (Next/API/worker) | Sales tool | [Merge into claims product monorepo] |
| [starter-kit](https://github.com/sm911/starter-kit) | HV CISO SMB Starter Kit (zip) | Client deliverable | **Active** — [rename `hv-ciso-starter-kit`] |
| ~~ic4g-catalog~~ | IC4G static product catalog (GH Pages) | IBM-era | **Archive** — legacy IBM product |
| [sm-web-portfolio](https://github.com/sm911/sm-web-portfolio) | Estate orchestration monorepo + domain-map (stale vs reality) | Estate docs | [GAP: revive as source of truth or fold map into blog-control?] |

### Product Ambiguities (Needs Jim's Decision)

- **smc-app vs mission-control vs SM-System:** Product SaaS vs ops desk vs governance OS — confirm lanes so they don't collide.
- **trustframe-ai-risk-studio vs nist-ai-rmf-assessment:** Same product line or separate tools?
- **Claims product winner:** `claims-dashboard-v1` vs `claims_dashboard` vs `claims-roi-assessment` — consolidate or archive duplicates?

---

## Pursuit Drawer (Time-Boxed Bid/RFP Work)

Active and archived pursuit repos. These are **time-boxed** — archive when pursuit closes or contract converts to product.

### Active Pursuits

| Repo | Purpose | Status |
|------|---------|--------|
| [rfp-agent](https://github.com/sm911/rfp-agent) | Active Python RFP agent | **Active** |
| [federal-market-intelligence](https://github.com/sm911/federal-market-intelligence) | HV CISO federal pursuit engine (planning) | **Active** |
| [hgcli](https://github.com/sm911/hgcli) | HigherGov CLI for SLED opportunities | **Active** |
| [HVHCP](https://github.com/sm911/HVHCP) | Hudson Valley Healthcare Consulting Pipeline folder | **Active** — [rename to `hv-healthcare-pipeline`] |

### Pursuit-Specific (Archive When Closed)

| Repo | Purpose | Action |
|------|---------|--------|
| [owosso-rfp](https://github.com/sm911/owosso-rfp) | City of Owosso civic engagement RFP analysis | Archive when pursuit closed |
| [cclri](https://github.com/sm911/cclri) | Cleveland Clinic LRI hybrid-cloud MVP demo | Keep while live, else Archive |
| [cc-lri-phase0-arch](https://github.com/sm911/cc-lri-phase0-arch) | Phase-0 architecture pack | [Merge under `cclri` monorepo or Archive suite] |
| [ccLRI-ibm-hybrid-cloud-wp](https://github.com/sm911/ccLRI-ibm-hybrid-cloud-wp) | Hybrid cloud whitepaper HTML | [Merge / Archive with CCLRI suite] |
| [CC-LRI-Hybrid-Cloud-Plan-To-Execuite-Two-Evaluation-Use-Cases](https://github.com/sm911/CC-LRI-Hybrid-Cloud-Plan-To-Execuite-Two-Evaluation-Use-Cases) | Pursuit plan HTML (typo in name) | [Merge / Archive · fix name if kept] |
| [mcbm](https://github.com/sm911/mcbm) / [mcbm1](https://github.com/sm911/mcbm1) / [mcbm2](https://github.com/sm911/mcbm2) | Tiny claims-marketing microsites (Pages) | [Merge one survivor or Archive all three] |
| [northstarhealth](https://github.com/sm911/northstarhealth) | Board pitch PDF/video + HTML (large media) | Archive post-pursuit (or move media to Drive) |

### Pursuit-Related Stubs

| Repo | Purpose | Action |
|------|---------|--------|
| [rfp-ai](https://github.com/sm911/rfp-ai) | Empty-ish demo stub (Dockerfile + stub src) | [Merge into `rfp-agent` or DELETE-CANDIDATE] |

---

## IBM Attic (Legacy Consulting Artifacts)

IBM-era consulting repos from Jim's prior work. **Archive all** unless actively referenced by current products.

| Repo | Purpose | Action |
|------|---------|--------|
| [IBM-Public-Cloud-Solutioning-Tool](https://github.com/sm911/IBM-Public-Cloud-Solutioning-Tool) | Learning guide for IBM cloud design/pricing | **Archive** |
| [ibm-cloud](https://github.com/sm911/ibm-cloud) | Tiny HCL stub | **DELETE-CANDIDATE** |
| [IBM-Enterprise-Application-Service](https://github.com/sm911/IBM-Enterprise-Application-Service) | Empty | **DELETE-CANDIDATE** |
| [O365-to-IBM-Cloud-Object-Storage](https://github.com/sm911/O365-to-IBM-Cloud-Object-Storage) | Terraform scaffold; README has unresolved merge conflict markers | Archive or fix then Archive |
| [OnboardingQA](https://github.com/sm911/OnboardingQA) | Pfizer→IBM Cloud onboarding Q&A (Flask) | **Archive** |
| [CRAG-IBMCLD](https://github.com/sm911/CRAG-IBMCLD) | Old GitLab Pages–style IBM cloud content | **Archive** |
| [cpa](https://github.com/sm911/cpa) | Cloud backup / IC4G HTML demos | **Archive** |
| [hpcs](https://github.com/sm911/hpcs) | IBM Hyper Protect Crypto Services HTML | **Archive** |
| [IL](https://github.com/sm911/IL) | IBM Illinois vision HTML | **Archive** |
| [pvs](https://github.com/sm911/pvs) | Tiny HTML page | **DELETE-CANDIDATE** / Archive |

---

## Personal Lane (Non-Business Projects)

Personal and experimental projects. Not client-facing, not Security Medic branded.

| Repo | Purpose | Status |
|------|---------|--------|
| [optionstrader](https://github.com/sm911/optionstrader) | CondorDesk trading app (herbie's primary workspace) | **Active** — personal |
| [herbie](https://github.com/sm911/herbie) | Agent instruction/feedback repo for CondorDesk | **Active** — personal |
| [exercise-routine](https://github.com/sm911/exercise-routine) | Personal workout tracker | Keep or Archive |
| [bootstrap-fedora42](https://github.com/sm911/bootstrap-fedora42) | Fedora bootstrap scripts | Keep (dotfiles-ish) or Archive |
| [Movie-Trailer-Website](https://github.com/sm911/Movie-Trailer-Website) | 2017 Udacity-era Python project | **Archive** |
| [music-blog](https://github.com/sm911/music-blog) | Single orphan HTML (Allan Holdsworth); not in hub | **Archive** |
| [sm911.github.io](https://github.com/sm911/sm911.github.io) | User Pages root (large HTML dump) | [CONFIRM: role vs blogs · likely Archive or reduce to redirects] |

### Personal Stubs (Delete Candidates)

| Repo | Action |
|------|--------|
| [myfintech](https://github.com/sm911/myfintech) | Empty | **DELETE-CANDIDATE** |
| [notes](https://github.com/sm911/notes) | Empty | **DELETE-CANDIDATE** |
| [obsi-cc](https://github.com/sm911/obsi-cc) | Empty (Obsidian/Claude?) | **DELETE-CANDIDATE** |
| [oc-kali](https://github.com/sm911/oc-kali) | Empty | **DELETE-CANDIDATE** |
| [test-n8n-20250627](https://github.com/sm911/test-n8n-20250627) | n8n test stub | **DELETE-CANDIDATE** |

---

## Fork Shelf (Upstream Mirrors)

Security Medic has **26 forks** of upstream repos. **Default policy: Archive unless actively forked-for-PR or runtime-pinned.**

### Forks to Evaluate (Archive Unless Jim Confirms Dependency)

| Repo | Upstream | Suggested Action |
|------|----------|------------------|
| [andrej-karpathy-skills](https://github.com/sm911/andrej-karpathy-skills) | multica-ai/… | Archive if unused |
| [ARTEMIS](https://github.com/sm911/ARTEMIS) | Stanford-Trinity/… | Archive |
| [awesome-claude-skills](https://github.com/sm911/awesome-claude-skills) | ComposioHQ/… | Archive (star upstream instead) |
| [cai](https://github.com/sm911/cai) | aliasrobotics/cai | Archive |
| [caii](https://github.com/sm911/caii) | torchy55/caii | Archive |
| [claude-code-obsidian-starter](https://github.com/sm911/claude-code-obsidian-starter) | ArtemXTech/… | Archive |
| [claude-flow](https://github.com/sm911/claude-flow) | ruvnet/ruflo | Archive |
| [claude-plugins-official](https://github.com/sm911/claude-plugins-official) | anthropics/… | **Keep only if** tracking/vendored plugins |
| [clawdbot](https://github.com/sm911/clawdbot) | openclaw/openclaw | **Keep if** Mission Control / herbie depends on local fork |
| [context-engineering-hub](https://github.com/sm911/context-engineering-hub) | dynamous-community/… | Archive |
| [Daemon](https://github.com/sm911/Daemon) | danielmiessler/Daemon | Archive |
| [DevSecOps-MaturityModel](https://github.com/sm911/DevSecOps-MaturityModel) | dsom/… | Archive |
| [docling](https://github.com/sm911/docling) | docling-project/… | Archive |
| [Fabric](https://github.com/sm911/Fabric) | danielmiessler/Fabric | Archive |
| [naabu](https://github.com/sm911/naabu) | projectdiscovery/… | Archive |
| [notebookllm-mindmap-exporter](https://github.com/sm911/notebookllm-mindmap-exporter) | rootsongjc/… | Archive |
| [personal-os-skills](https://github.com/sm911/personal-os-skills) | ArtemXTech/… | Archive |
| [Personal_AI_Infrastructure](https://github.com/sm911/Personal_AI_Infrastructure) | danielmiessler/LifeOS | Archive |
| [remote-coding-agent](https://github.com/sm911/remote-coding-agent) | dynamous-community/… | Archive unless course WIP |
| [SecLists](https://github.com/sm911/SecLists) | danielmiessler/SecLists (**huge, 2.8M+ size**) | **Archive or delete** — don't mirror massive wordlists |
| [skills](https://github.com/sm911/skills) | trailofbits/skills | Archive (or keep if actively used in agents) |
| [SOC-Analyst-Career-Guide](https://github.com/sm911/SOC-Analyst-Career-Guide) | PacktPublishing/… | Archive |
| [Substrate](https://github.com/sm911/Substrate) | danielmiessler/Substrate | Archive |
| [SuperClaude_Framework](https://github.com/sm911/SuperClaude_Framework) | SuperClaude-Org/… | Archive |
| [Telos](https://github.com/sm911/Telos) | danielmiessler/Telos | Archive |
| [zeroclaw](https://github.com/sm911/zeroclaw) | zeroclaw-labs/… | Archive unless evaluating vs OpenClaw |

### Fork Ambiguity (Needs Jim's Decision)

- **clawdbot / OpenClaw fork:** Required runtime pin for Mission Control/herbie, or safe to archive?
- **SecLists:** Huge mirror (2.8M+ size). Archive or delete — prefer upstream reference, not owned fork.

---

## Naming & Topic Conventions (For New Repos)

### Naming Rules

```
{scope}-{thing}[-{variant}]

scope:   sm | hv | blog | rfp | tool | lab | fork | personal
thing:   kebab-case noun (site, assessor, agent, pipeline)
variant: optional (staging, wp, v2)
```

**Examples:**
- `sm-securitymedic-site` (or keep short brand names for public flagships)
- `blog-compliance`, `blog-staging` (already good)
- `hv-ciso-site`, `hv-ciso-staging`
- `tool-privacy-assessor`, `tool-rfp-agent`
- `lab-privacy-guardian`
- `personal-optionstrader`

**Rules:**
1. Lowercase kebab-case only (fix `SM-System`, `CC-LRI-…`, spaces, typos).
2. Brand flagships may keep short domain-ish names (`securitymedic`, `privacymedic.com`) but add topics.
3. No date-in-name throwaways (`test-n8n-20250627`) — use `lab-n8n` + archive when done.
4. Staging: always suffix `-staging`; never a parallel inventively named twin.

### GitHub Topics (Apply to All Owned Repos)

| Topic | Use |
|-------|-----|
| `smc-brand` | Production brand sites |
| `smc-blog` | Production blogs |
| `smc-staging` | Staging/review |
| `smc-control` | Control-plane / estate docs |
| `smc-product` | Sellable/productized tools |
| `smc-pursuit` | Active bid/RFP |
| `smc-ibm-legacy` | IBM-era artifacts |
| `smc-personal` | Non-business |
| `smc-archive-candidate` | Queued for archive |
| `smc-fork` | Owned forks |

**Plus tech tags:** `nist-csf`, `privacy`, `ai-rmf`, `vercel`, `github-pages`, etc.

**Current state:** As of Sep 26, 2026, **0 repos have topics applied**. This is a high-impact, low-effort cleanup batch.

---

## Next Cleanup Batches (Do Not Execute — Planning Only)

The CoS review identified four piecewise cleanup batches. **This estate map documents them; it does not execute them.** Jim approves batches individually.

### Batch A — Safe Cleanup (Approve Anytime)

- Archive forks (except any Jim lists as runtime-pinned)
- Delete empty stubs: `resiliencemedic.com`, `smcgrc.ai`, `notes`, `myfintech`, `obsi-cc`, `oc-kali`, `IBM-Enterprise-Application-Service`, `test-n8n-20250627`
- Delete `hvciso-govern-staging` (duplicate)
- Archive `music-blog`, `blogdrafts` (after draft skim), IBM attic, `Movie-Trailer-Website`

### Batch B — Naming & Findability

- Apply topics to all owned repos (batch script via GitHub API)
- Rename worst offenders: `SM-System` → `sm-system`, `HVHCP` → `hv-healthcare-pipeline`, `CC-LRI-…` typo fix, `grcresilience.com` → `grc-resilience-playbook`

### Batch C — Brand/Blog Truth

- Jim answers ambiguities: privacymedic/cyberintelpro (site vs redirect), `/blog` hub rebuild, blog monorepo vs multi-repo decision
- Update this estate map + blog-control table
- Register `ai-automation-blog` in blog-control

### Batch D — Product Consolidation

- Claims trio merge (decide winner)
- CCLRI suite merge (four repos → one)
- `rfp-ai` merge into `rfp-agent`
- AI-risk tool boundary decision (trustframe vs nist-ai-rmf)

---

## Inventory Stats (As of Sep 26, 2026)

- **Total visible repos:** 96 (70 owned, 26 forks)
- **Archived:** 0
- **Empty stubs (size 0):** 9
- **Repos with GitHub topics:** 0
- **Duplicate staging pair:** `hudsonvalleyciso-staging` / `hvciso-govern-staging` confirmed identical

---

## Related Documentation

- **Blog editorial guidance:** See `GUIDANCE.md` (this repo) for voice, audience, metadata, and publishing workflow.
- **Blog template system:** See `README.md` (this repo) for template architecture, CLI usage, and rotation logic.
- **Marketing library:** See `docs/marketing-library/` for service-specific presentation material, one-pagers, and talk tracks.
- **Upstream estate audit:** See `uploads/sm911-estate-recommendations.md` (Sep 26, 2026 CoS review) for full 96-repo analysis and improvement plan.

---

## Maintenance

This estate map should be updated when:
- New repos are created or archived
- Blog routing table changes (new blog, template migration)
- Brand domains change (redirect vs standalone decision)
- Product consolidation batches complete (claims, CCLRI, AI-risk tools)
- Pursuit repos close and move to archive

**Owner:** Jim Venuto reviews quarterly or as estate changes warrant.

---

**End of Estate Map**
