# CONTRIBUTING.md

Lucy in the Loop is an open‑source, privacy‑first AI companion for mental health, wellness, and peak performance. Our aim is to build capable software **without** burning out contributors. These guidelines explain how to contribute effectively, how we leverage AI (ethically), and how we protect everyone’s time, attention, and well‑being.

---

## TL;DR

* Be kind. Respect privacy. Default to transparency.
* Use AI to **reduce** human toil, not to bypass judgment.
* Every commit must include a DCO `Signed-off-by:` line.
* Small, well‑scoped PRs with tests → faster reviews.
* AI‑generated changes **require a human sponsor** and extra checks for safety, bias, and privacy.
* Two approvals (human + automated) for normal code; more for sensitive areas.
* No pager‑duty vibes: we use rotation, quiet hours, and AI triage so people aren’t overworked.

---

## What you can contribute

* **Code:** features, fixes, refactors, performance improvements.
* **Safety & ethics:** red‑teaming prompts, guardrail rules, bias/fairness tests, risk assessments.
* **Docs & tutorials:** setup guides, usage examples, diagrams, translations.
* **Testing:** unit/integration tests, reproducibility harnesses, regression cases.
* **Design & UX:** flows, microcopy, accessibility improvements.
* **Research:** evidence summaries; evaluation protocols.
* **Governance:** proposals (RFCs), triage, release checklists.

No contribution is too small. Even fixing a typo helps.

---

## Our principles (applied to contributions)

* **Autonomy & boundaries.** People have lives. Async by default, no expectation to respond off‑hours.
* **Non‑maleficence.** Don’t introduce harm: psychological, privacy, or security.
* **Justice.** Build for everyone; treat fairness regressions as critical bugs.
* **Transparency.** Explain what you changed and why. Keep decision trails public.
* **Privacy.** Local‑first, data‑minimizing. Never upload user data to third‑party services.
* **Accountability.** Every change is attributable, reproducible, and reversible.

---

## Using AI ethically in this repo

We love AI because it removes toil. We require **human judgment** where it matters.

**Allowed (encouraged):**

* Drafting tests, docs, examples.
* Generating scaffolds, refactors, or small fixes.
* Triage suggestions, label predictions, changelog drafts.
* Static analysis, security scans, bias/fairness test generation.

**Requires a human sponsor & review:**

* Any user‑facing behavior, especially mental‑health advice or tone.
* Changes to safety filters, crisis flows, privacy/crypto code, data handling.
* Model, prompt, or policy updates that can affect user outcomes.

**Provenance in commits:**
Include trailers when AI assists:

```
AI-Coauthored: yes
AI-Agent: <name or tool>   # e.g., "RefactorBot v1.2"
AI-Notes: <brief summary of what the agent did>
```

**Human responsibility:** A human sponsor must co‑review and add their own `Signed-off-by:`. AI cannot self‑approve or merge.

**Data rules:** Never feed private or identifying data into external AI systems. Keep prompts and test inputs synthetic or sanitized.

---

## Ground rules for a healthy workload

* **Rotation & quiet hours.** We rotate maintainers weekly; bots manage queues. Reviews pause during published quiet hours; “urgent” is reserved for security/safety.
* **No DM for reviews.** Use Issues/PR comments to avoid pressure and keep context public.
* **Reasonable SLAs.** Bot triage within 24 hours; human first‑pass within 5 business days.
* **Small PRs win.** Aim for <300 lines diff where possible; split larger changes.

---

## Development workflow

1. **Fork and clone**

   ```bash
   git clone https://github.com/quantumpipes/lucy-in-the-loop
   cd lucy-in-the-loop
   ```

2. **Create a branch**
   Use a descriptive name:

   ```
   feature/add-mood-tracker
   fix/race-in-safety-agent
   docs/translate-onboarding-es
   ```

3. **Set up tooling**

   * Python: PEP 8 style; run formatters/linters (e.g., `black`, `ruff`) and type checks (`mypy`) if configured.
   * Pre‑commit hooks: `pre-commit install`.
   * Run the full test suite locally before pushing.

4. **Implement your change**

   * Add/adjust tests. Aim for high coverage of new paths.
   * For model/prompt/policy changes, include evaluation notes and before/after examples.
   * For performance work, include a simple benchmark script and expected numbers.

5. **Commit in logical chunks**

   ```bash
   git add -A
   git commit -s -m "Safety: de‑escalate phrasing in crisis hints (resolves #123)"
   # Use -s to add the DCO Signed-off-by line
   ```

   Include a concise **what/why**. If AI assisted, add the trailers shown above.

6. **Push and open a PR**

   ```bash
   git push origin <your-branch>
   ```

   Fill out the PR template. Link issues. Explain risks, user impact, and test evidence. Mark as **Draft** if still iterating.

---

## Review & merge policy

* **Automated checks** (required): build, tests, lint/type, security scan, license scan, safety/bias suite (where relevant).
* **Approvals:**

  * *Standard code:* ≥1 human maintainer + automated checks passing.
  * *Sensitive surfaces* (safety, privacy, data handling, encryption, crisis flows, clinician‑facing content): ≥2 human approvals from different orgs **and** the safety/bias gates must pass.
* **Merge etiquette:**
  Maintainers merge during working hours. Avoid self‑merges unless trivial and documented. Squash‑merge by default; keep clear histories.

**Backouts:** If a change causes harm, privacy regression, or breaks safety tests, maintainers may revert immediately with explanation and follow‑up issue.

---

## Sensitive‑change checklist (attach in PR if applicable)

* Risk analysis: user impact, failure modes, mitigation.
* Safety/bias evaluation results and datasets used.
* Privacy notes: data touched, storage, retention, and access.
* Rollout plan: flags, staged rollout, fallback/rollback.
* Communications: release notes, user‑visible changes.

---

## Security & privacy

* Never include secrets in code, test data, or issue text.
* Use least‑privilege for any new permission.
* No telemetry or hidden data collection. Logging must be user‑owned/local and scrubbed of PII.
* Report vulnerabilities privately via the **Security Policy**; do not file public issues for exploitable bugs.

---

## Documentation & translations

* Write clear, accessible English; define terms on first use.
* Keep examples runnable. Prefer short, focused snippets.
* For translations, note regional language variants and mental‑health terminology; coordinate with other translators when possible.
* Docs PRs follow the same review path; screenshots/diagrams should include alt text.

---

## Issue triage (what happens after you click “submit”)

* **Bot pass:** label, deduplicate, request minimal repro, route to subsystem.
* **Triage rotation:** a human “sheriff” confirms scope/severity and assigns.
* **States:** `needs-info` → `ready` → `in-progress` → `needs-review` → `done`.
* **Escalation:** `security`, `safety`, and `privacy` labels jump the queue.

---

## Major changes (RFC)

For cross‑cutting designs (new agent frameworks, storage formats, core prompts), open an **RFC**:

* Problem statement, options considered, trade‑offs, risks, rollout plan.
* 1–2 week comment period (longer if holidays).
* Decision recorded with rationale; link to tracking issues.

---

## Governance (how decisions get made)

* Subsystems have maintainers listed in `MAINTAINERS`.
* A small **Technical Steering Committee** (TSC) arbitrates conflicts, approves RFCs, and guards project values.
* Organisations may nominate maintainers, but no single org controls a majority of TSC seats. Conflicts of interest must be disclosed on relevant PRs.

---

## Licensing, DCO, and third‑party code

* Code is Apache‑2.0. By contributing, you agree your contribution is licensed under the project license.
* All commits must include the DCO line (use `git commit -s`):

  ```
  Signed-off-by: Your Name <you@example.com>
  ```
* When importing third‑party code/models, verify license compatibility and include notices in `THIRD_PARTY_LICENSES`.

---

## Commit message conventions (example)

```
feat(ui): add daily mood tracker with optional journaling (closes #123)

- New component <MoodTracker/> with 3‑tap sentiment input
- Local‑only storage; no network calls
- Adds unit tests and a11y keyboard navigation

AI-Coauthored: yes
AI-Agent: RefactorBot v1.2
AI-Notes: scaffolded tests and refactor suggestions
Signed-off-by: Jane Doe <jane@ex.com>
```

Prefixes we commonly use: `feat`, `fix`, `perf`, `docs`, `test`, `chore`, `refactor`, `safety`, `privacy`.

---

## Community & conduct

We follow a **Code of Conduct**. Be respectful, assume good intent, prefer public discussion, and help newcomers. If you feel pressured or harassed, contact the maintainers privately; we will act.

---

## How to get help

* Questions: open a **Discussion**.
* Bugs/feature requests: open an **Issue** with repro steps or use cases.
* Security issues: follow the **Security Policy**.
* Ethical/safety concerns: use the “Ethical Issue” template; these are triaged immediately.

---

## Thank you

By contributing, you’re helping build a privacy‑first, compassionate AI that puts human well‑being first. We’re grateful for your time and we promise to protect it.
