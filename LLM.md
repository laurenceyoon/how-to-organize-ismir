
### Anonymization and publication policy (public-safe)
- Remove names, emails, phone numbers, and any personal identifiers from notes and guides
- Use roles or pseudonyms (e.g., "Industry Chair", "Reviewer A") instead of names
- When quoting Slack, paraphrase and summarize; avoid verbatim quotes that include PII
- Redact file links and IDs that expose private drives or systems; summarize content instead
- For datasets or tallies, aggregate to safe levels; avoid small-N breakdowns that could re-identify individuals
- Keep raw Slack JSON and sensitive docs only in `_source_*` folders; do not paste PII in area guides
- If in doubt, omit and add a TODO note describing what’s missing and where it came from

## Note to LLM: LLM's Procedure (Below this is not useful for human readers)

### Writing style for all guides
- Start each major section with a brief 1–2 sentence overview that frames the bullets.
- Interleave short connective paragraphs between groups of bullets to explain transitions or reasoning.
- End sections with an optional 1–2 sentence takeaway when helpful.
- Keep sentences concise; prefer bullets for lists of actions or facts, prose for context.
- Use consistent, formal tone; avoid emojis.

### 1. Understand the slack data and the related docs
- Related docs: classified under each area
- Slack space data
    - organizers' slack: channels are mostly matched to each area
    - attendees' slack: source of data for missing information, to understand what was actually announced and done during the conference, what was needed to be done.
    - focus on both virtual attendee side and the in-person attendance


### 2. Extract information into 
- `$each_area$/_raw_notes.md`
- A non-organized list of information from various sources
    - Specify the sources so that later we won't need to look into every source again
    - the sources can be not only the direct 1:1 mapped channels and docs, but also attendees' slack, general chairs' channel, and any other channels. 

### 3. Write suggestion docs
- `$each_area$/README.md`
- Structure the guide with the following sections:
  - `Goal` (what this area aims to achieve overall)
    - Start with a 1–2 sentence overview of the area's purpose.
  - `Chairs' Goal` (what the chairs specifically must accomplish: e.g., oversee submission, selection, execution)
    - Focus on the chairs' personal objectives and deliverables.
  - `Scope & Responsibilities`
    - Focus on core duties and accountabilities (e.g., "manage submissions" not "use OpenReview").
    - Avoid year-specific tools or policies; keep evergreen.
  - `General Advice vs This Year's Choices`
    - General Advice (timeless best practices)
    - This Year's Choices (year-specific numbers/policies; explain context)
  - `Rationale & Consequences`
    - Why this matters; what breaks if inconsistent; alternatives/otherwise
  - `Topics to Discuss / Decisions to Make`
    - For each major topic, add subsections:
      - Context (why this matters; constraints)
      - Decision owner(s) and stakeholders
      - Options considered
      - This year's decision (facts; who decided; when)
      - Pros/Cons and consequences
      - Open questions / follow-ups
      - Recommendations for next year
    - Include year-specific issues like policy exceptions (e.g., waivers), cross-area integrations (e.g., jam sessions), and lessons from discussions to ensure comprehensive coverage.
  - `Suggested Timeline` (months/weeks/days)
    - Use relative months (e.g., Month -8 to -6) assuming an October conference; provide concrete examples tied to these phases. Always use the actual months too together. E.g., "Month -8 to -6 (Feb to Apr)"
  - `Dependencies & Blockers`
  - `Stakeholders`
    - List key individuals/teams and briefly explain their role/collaboration points (e.g., "General Chairs for policy alignment" rather than just names).
    - Include potential cross-area integrations (e.g., Jam Session Hosts for collaborative performances) to highlight interdependencies.
  - `Caveats / Pitfalls`
- For each section, precede bullets with a 1–2 sentence overview and add brief connective sentences between bullet groups where clarity benefits.
- Prefer bullet lists for checkable items; use short prose to connect ideas.
- Make it succinct, formal, easy, simple.
- Use the TODO List below to check the progress


## TODO List (living list)
This section includes list of [] todo items. 


- [x] Define anonymization and publication policy for this repo (public-safe)
  - [x] Add guidance in this `README.md` on redaction and pseudonymization (no separate doc)

- [x] Inventory all areas and sources
  - [x] Enumerate areas from top-level directories (e.g., `chairs-*/`, `committee-*/`)
  - [x] Map sources in `_source_related_docs/` to their destination areas
  - [x] Map Slack export channels in `_source_slack_data/` to areas (organizers vs attendees)
  - [x] Produce `areas/_index.csv` with columns: area, source_type, source_path, notes

- [ ] Create per-area scaffolds
  - [x] For each `chairs-*` and `committee-*` area, add `_raw_notes.md` (raw notes with source refs)
  - [ ] For each area, add `README.md` (guide: goals, scope, responsibilities, timeline, caveats)
  - [x] Add a standard template in `templates/area_README_template.md`

- [ ] Extract information into `_raw_notes.md` (cite sources)
  - [ ] Chairs: scientific program (incl. best paper, outstanding reviewers)
  - [ ] Chairs: tutorials
  - [ ] Chairs: industry
  - [x] Chairs: LBD
  - [ ] Chairs: music
  - [ ] Chairs: local organization / volunteers / virtual
  - [ ] Chairs: sponsorship / social media / publication / newcomer initiative / web designer
  - [ ] Committees: test of time award, special sessions, best paper award

- [ ] Write per-area guides (`README.md` in each area)
  - [ ] Define goals, scope, and responsibilities
  - [ ] Provide suggested timelines (assume conference in early Nov)
  - [ ] List dependencies/blockers and cross-area coordination points
  - [ ] Add pitfalls/caveats and lessons learned
  - [ ] Add stakeholders to talk to (other chairs, PCO, GC, PC chairs, etc.)

- [ ] Build dependency map across areas
  - [ ] Create `planning/dependencies.md` describing sequencing and blockers
  - [ ] Add quick visual (mermaid or image) to illustrate dependencies

- [ ] Slack data: light-weight analysis utilities
  - [ ] Add a Jupyter notebook `analysis/slack_inspect.ipynb` to query channels/messages
  - [ ] Implement helpers to search announcements, deadlines, and FAQ themes
  - [ ] Document queries used and samples (ensure no PII in outputs)

- [ ] Registration data: confirm outputs and document insights
  - [ ] Review `registration.py` and `outputs/` figures
  - [ ] Add `chairs-dei/_raw_notes.md` notes from demographics
  - [ ] Summarize insights in relevant area guides (dietary, sizing, languages)

- [ ] Consolidate into `ismir2025-execution-manual.md`
  - [ ] Create an outline mirroring areas with links to each guide
  - [ ] Include an annual timeline overview (12-month roll-up)
  - [ ] Include checklist per quarter/month with cross-links

- [ ] Quality review and consistency pass
  - [ ] Verify all guides contain the required sections
  - [ ] Check links, filenames, and references
  - [ ] Ensure consistent terminology and tone

- [ ] Export/hand-off
  - [ ] Prepare copy-ready Google Doc templates per area
  - [ ] Include instructions for yearly update/maintenance
  - [ ] Tag remaining gaps with TODOs and open issues
