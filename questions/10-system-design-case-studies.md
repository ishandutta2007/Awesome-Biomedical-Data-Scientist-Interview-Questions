# 10. System Design / Case Studies

Open-ended, senior-level scenarios synthesizing themes across the entire repo. As with the format established across this series, these are typically extended discussions rather than questions with one correct answer — evaluate reasoning quality, whether causal inference rigor and deployment/fairness considerations are integrated together rather than treated as separate silos, and whether the candidate reflexively distinguishes "statistically associated in this dataset" from "genuinely causal and ready for real clinical use."

---

### 10.1 🔴 Design the end-to-end approach you'd take to develop, validate, and deploy a machine learning model predicting 30-day hospital readmission risk, intended to help target a limited-capacity post-discharge care coordination program at the patients most likely to benefit.

**What a strong answer covers:**
- Should start with careful outcome and cohort definition (category 1.3, 1.13) — precisely defining what counts as a readmission, and validating this definition rather than assuming a straightforward claims/EHR-based derivation is automatically accurate.
- Should proactively address leakage (category 3.4) given how common this specific failure mode is for readmission prediction specifically (discharge-time features that circularly reflect the clinical team's own readmission concern).
- Should propose both temporal and external validation (categories 3.5-3.6) before any real deployment, not just a single retrospective split.
- Should build in subgroup performance analysis and proactive fairness consideration from the outset (categories 3.10-3.12, 8.4, 8.12) — particularly relevant given this is fundamentally a resource-allocation model, structurally similar to the biased care-management algorithm case study discussed throughout this repo.
- Should explicitly address actionability (category 3.13) — the model's value depends entirely on the care coordination program itself being genuinely effective, which is a separate question from the model's predictive accuracy.
- Should propose a staged deployment (shadow mode, per category 7.2) and ideally a randomized evaluation of the program's actual impact (category 7.8) rather than assuming a validated risk score alone establishes the intervention's real-world value.
- A strong answer explicitly proposes ongoing monitoring (category 7.5) and a change control plan (category 7.4) for the model's full deployment lifetime, not just its initial launch.

---

### 10.2 🟡 A pharma company's real-world evidence team shows you an analysis suggesting their already-approved drug is associated with a meaningfully lower rate of a specific adverse outcome compared to a competitor drug, based on claims data, and wants to use this finding in external communications. How would you evaluate this before it's used publicly?

**What a strong answer covers:**
- Should immediately apply the confounding-by-indication lens (category 2.2) — asking what clinical factors likely drove the choice between these two drugs, and whether those factors were adequately measured and adjusted for.
- Should propose negative control analysis and E-value sensitivity analysis (categories 2.11-2.12) as concrete, specific tools for assessing this finding's robustness to unmeasured confounding before any external use.
- Should raise the claims data limitation discussed in category 1.9 and 4.12 — the lack of direct clinical severity information in claims data is a genuinely serious limitation for exactly this kind of comparative safety claim.
- Should distinguish clearly between generating real-world evidence for internal, hypothesis-generating purposes versus evidence intended for external public communication (category 9.4) — the latter warrants a meaningfully higher evidentiary bar, and using an insufficiently robust finding in external communications carries real regulatory and reputational risk.
- Should recommend, at minimum, this finding be communicated with appropriate methodological caveats rather than presented as definitive, and should flag the appropriateness of involving regulatory affairs given the public communications context.

---

### 10.3 🔴 You're reviewing a colleague's proposed wearable-device-based digital biomarker for early detection of a specific clinical deterioration, based on a promising correlation found in a single pilot dataset of 200 patients. How do you evaluate this before supporting further investment?

**What a strong answer covers:**
- Should directly apply the digital biomarker validation framework discussed in category 6.9 — distinguishing an interesting statistical correlation in one dataset from genuine analytical validity, clinical validity, and clinical utility.
- Should specifically probe device compliance and signal quality (categories 6.7-6.8, 6.10) — asking how representative and reliable the underlying wearable data actually was across the pilot's 200 patients, and whether informative missingness in device-wearing compliance could be driving the observed correlation.
- Should raise external and temporal validation requirements (categories 3.5-3.6) applied to this new context — a single 200-patient pilot dataset is a promising but genuinely early-stage finding requiring independent replication before further significant investment.
- Should ask about the specific consumer device's independent validation evidence for the relevant physiological signal (category 6.10), given how much this varies across different consumer devices.
- A strong answer proposes a specific, staged path forward (a larger, ideally multi-site replication study with pre-specified validation criteria) rather than either dismissing the promising early finding or treating it as already sufficiently validated for major further investment.

---
