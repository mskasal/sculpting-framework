# Sculpting Framework — Empirical Validation Log (7 Multi-Agent Simulations)

Sculpting Framework v1.0 was stress-tested and refined across **7 multi-agent swarm simulations** covering happy paths, compliance constraints, real-world chaos, veto deadlocks, 1-day micro-features, and an A/B regression replay.

| # | Scenario | Version | Dimension Tested | Key Findings & Rules Added |
| :--- | :--- | :--- | :--- | :--- |
| **1** | Unified Enterprise Billing *(€180k ARR, 1.5 BE, EU VAT)* | v0.1 | Initial Cross-Cutting baseline | **Structural bugs caught:** unilateral business-rule lock, deferred spike ("Slice 0"), strawman 3rd option, meta-jargon → Added **Templates 1–4**, **Conditional Approval Lock**, **No-Go vs. Deferred**, **Pre-Detail Spike**. |
| **2** | Enterprise SSO & Granular RBAC *(12k SMB + SOC2)* | v0.2 | v0.2 validation + Security vs. UX | **5/5 PASSED.** Edge cases caught → Added **Vendor/Sub-processor gate**, **Template 5 (Spike Summary)**, **Re-ping/Reset rule**, **Single-owner parallelism + capacity confirmation**, **Trigger column** in Template 3. |
| **3** | EU Data Residency (GDPR) & AI Summarization | v0.3 | Convergence & over-ceremony check | **5/5 PASSED, 0 structural/edge-case bugs.** Completed in 12 messages, 0 meetings, 0 wasted pings. |
| **4** | Usage-Based Pricing *(Chaos Stress Test 1/3)* | v0.3 | Delayed PM, mid-flight pivot, 1-week P0 pause & owner handoff | v0.3 broke under real-world chaos → Added **Minimal Recovery Protocol (1 Card + 2 Rules):** `Living State Card`, `Assumption + Expiry`, `Delta & Sign-off Reset`. |
| **5** | Public Shareable Links & SEO *(Stress Test 2/3)* | v0.4 | 2-round async veto deadlock & 25-min Meeting Fallback | `Living State Card` passed (6–7 lines); Meeting Fallback triggered cleanly → Added **Timeout/Tie-Breaker** and **Hard Veto (Red Line) non-negotiable** rules. |
| **6** | CSV Export & Date Filter *(Stress Test 3/3)* | v0.4 | 1-day Micro-Feature speed & over-ceremony test | Caught Triage-vs-Contract contradiction → Added **Fast-Track Rule** (≤2 days, single service/owner skips heavy templates; single ticket SSoT). |
| **7** | Unified Enterprise Billing *(Regression A/B Replay)* | v1.0-rc | Head-to-head v0.1 (Sim 1) vs. v1.0-rc | **5/5 Sim 1 bugs eliminated**, 8 messages vs. 7 (+1 = 1.5 BE capacity confirmation), **0 meetings, 0 over-complication, 0 regressions.** Added 1-line "do not copy-paste Living State Card into chat messages" rule → **Frozen as v1.0**. |
