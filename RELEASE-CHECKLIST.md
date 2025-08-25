# Release Checklist

- [ ] Update `NOTICE` and `THIRD_PARTY_LICENSES/` with all current deps/models
- [ ] Include `EULA-BINARY.md` and `IN-APP-TERMS.txt` in installers/packages
- [ ] Verify `DISCLAIMER.md`, `TERMS.md`, `MEDICAL-DISCLAIMER.md` links in UI/README
- [ ] Ensure DCO check is required and passing for all merged commits
- [ ] Publish or update `SECURITY-ADVISORIES.md` if releasing security fixes
- [ ] Confirm `EXPORT.md` applicability for any new encryption/components
- [ ] Tag release and attach third-party licenses/artifacts as needed

## Legal Hardening Checklist

- [ ] Claims review: no medical/device claims; wellness/education framing only
- [ ] UI guardrails: crisis interstitial (988/local), high‑risk intent friction
- [ ] Clickwrap: `IN-APP-TERMS.txt` presented, acceptance logged (timestamp/hash)
- [ ] Outputs notice: UI mirrors `OUTPUTS-LICENSE.md` (informational, may be wrong)
- [ ] Liability cap present (US $100 or amounts paid) and conspicuous
- [ ] Privacy: local‑only default; any optional connectivity clearly opt‑in
- [ ] HBNR readiness: breach playbook updated; contacts and timelines confirmed
- [ ] Export/sanctions: embargo checks; CI blocks restricted parties where feasible
- [ ] EU track (if distributing in EU): AI Act role identified; docs/logging ready
- [ ] Trademarks: “Unofficial/Community Build” labeling for forks; no endorsement
