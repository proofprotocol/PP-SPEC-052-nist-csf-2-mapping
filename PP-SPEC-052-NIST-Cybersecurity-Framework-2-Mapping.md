# PP-SPEC-052: Proof of Efficacy Mapping to the NIST Cybersecurity Framework (CSF) 2.0

| Field | Value |
|---|---|
| Status | DRAFT v0.1 |
| Author | Craig Ellrod, Nebulonium, Inc. (dba HACKERverse®) |
| Date | October 8, 2026 |
| License | CC BY 4.0 |
| Maps to | NIST Cybersecurity Framework (CSF) 2.0, NIST CSWP 29 (February 26, 2024) |
| Series | Proof Protocol Framework Mapping Specifications |

---

## 1. Purpose

This specification defines how cybersecurity outcomes in the NIST Cybersecurity Framework (CSF) 2.0 can be bound to Proof Protocol test cases, evidence, and efficacy results.

The upstream source remains authoritative for its own requirements, identifiers, terminology, and guidance. This document defines a **Proof Protocol mapping** and does not supersede, reproduce, modify, or certify conformance to the upstream source.

## 2. Scope

CSF 2.0 is published by the National Institute of Standards and Technology (NIST) as NIST Cybersecurity White Paper (CSWP) 29, final version dated February 26, 2024 (DOI 10.6028/NIST.CSWP.29). As of the date of this specification, CSF 2.0 is the current version; CSF 1.1 is archived. The CSF Core is a hierarchy of six Functions (GOVERN, IDENTIFY, PROTECT, DETECT, RESPOND, RECOVER), Categories, and Subcategories. NIST publishes Implementation Examples and Informative References online, separately from CSWP 29, and updates them more frequently. CSF 2.0 also defines Organizational Profiles, Community Profiles, and Tiers.

CSF 2.0 describes outcomes, not specific controls or tests. It supplies external context that can identify what should be examined or tested. Proof Protocol supplies an independent evidence model for determining what happened during a test and whether a selected control performed as claimed.

Independent witnessing, proof validity, evidence capture, packaging, anchoring, and efficacy semantics are defined elsewhere in the Proof Protocol specification family.

## 3. Core Question

Proof of efficacy asks:

> **Was there a control, and did it work?**

A framework requirement, criterion, principle, or obligation may identify a condition of interest. A product, architecture, policy, process, or safeguard may claim to satisfy or mitigate that condition. Proof Protocol binds the external context, test, control, observed behavior, downstream outcome, and evidence into a result that can be independently examined.

A CSF Subcategory names an outcome. An Organizational Profile records whether an organization asserts it is achieving that outcome, and a Tier characterizes the rigor of its risk governance and management practices. Neither a Profile entry nor a Tier selection is, by itself, evidence that a control operated. Proof Protocol can supply tested evidence for outcomes that are empirically testable, and keeps governance and other non-empirical outcomes distinct.

A Proof Protocol result does **not** by itself establish legal, audit, regulatory, or standards conformance unless the applicable authority separately determines that the evidence is sufficient.

## 4. Metric Definitions

Against a defined corpus or test condition, each applicable empirical case is recorded as **blocked**, **detected**, **missed**, or **INVALID** where those verdicts are meaningful.

Relevant measurements can include containment rate, detection rate, miss rate, false-positive rate, robustness under bypass or failure conditions, version-level results, and **INVALID** when required evidence is incomplete or broken.

Not every upstream requirement is empirical. Governance, documentation, organizational, legal, and procedural requirements MUST NOT be converted into efficacy scores merely because they can be referenced by a proof record.

## 5. Evidence Produced

Mapped tests can produce:

- **Proof records** binding external context, test case, control, system/version, verdict, timestamp, and evidence references;
- **ProofStamp™** trusted timestamps bound to evidence/verdict objects;
- **ProofBundle™** packages containing proof records, metrics, corpus manifests, and environment/context;
- **ProofRegister™** records for issued proof artifacts; and
- corpus and environment manifests identifying the tested conditions.

## 6. Mapping to NIST CSF 2.0

Exact CSF identifiers and titles SHOULD be taken from the authoritative CSF 2.0 publication or the NIST CSF 2.0 Reference Tool and recorded in the ProofBundle™. This specification does not redefine CSF outcomes. Category identifiers combine a Function code and a Category code (for example, `GV.OC`); Subcategory identifiers add a two-digit number (for example, `GV.OC-01`).

| NIST CSF 2.0 context | Proof Protocol treatment | Evidence |
|---|---|---|
| Function (GOVERN, IDENTIFY, PROTECT, DETECT, RESPOND, RECOVER) | Record the Function as test context. GOVERN outcomes are predominantly non-empirical and MUST NOT be scored as efficacy. | Requirement metadata |
| Category (for example, `GV.OC`) | Record the Category identifier and CSF version to group related tests. | Requirement metadata |
| Subcategory (for example, `GV.OC-01`) | Bind the Subcategory identifier to one or more reproducible test cases where the outcome is empirically testable. | Proof record; corpus manifest |
| Implementation Examples | Use as optional scoping input for independently authored test conditions. Record the Implementation Examples release used. | Corpus metadata |
| Informative References | Record cross-references to other frameworks as context only. A result mapped through an Informative Reference requires that framework's own mapping. | Requirement metadata |
| Asserted control or safeguard | Record the control claimed to achieve the outcome separately from observed behavior. | Control descriptor |
| Outcome achievement | Exercise the defined condition, including negative and bypass cases, and capture whether the protected outcome was achieved. | Execution evidence; outcome evidence |
| Organizational Profile (Current Profile, Target Profile) | A Current Profile entry is an organizational assertion. Proof Protocol results MAY be referenced as evidence for that entry but do not replace it. | Assertion record; ProofBundle |
| Community Profile | Record the Community Profile name and version when it scoped the test. | Requirement metadata |
| Tiers (Tier 1 Partial to Tier 4 Adaptive) | Record as non-empirical context. Tiers MUST NOT be derived from or converted into efficacy scores. | Assertion record |
| System/version context | Bind material system, policy, configuration, and environment versions to the result. | Environment descriptor |

A Proof Protocol result for a Subcategory establishes tested behavior for the defined condition. It does not establish that an organization has achieved the Subcategory outcome across its environment.

## 7. Interoperability Rules

1. The authoritative upstream source, edition/version, and applicable identifier SHOULD be recorded.
2. Upstream identifiers and terminology MUST NOT be silently redefined.
3. Proof Protocol verdicts are Proof Protocol results; they are not upstream certifications, audit opinions, legal determinations, or endorsements.
4. A control's presence, configuration, activation, detection, and efficacy are distinct facts.
5. A policy decision, alert, log entry, or control trigger does not by itself establish efficacy when the claim concerns a downstream protected outcome.
6. Target, application, tool, SIEM, vendor, service, resource, or equivalent evidence SHOULD complete the evidence round trip when required to establish the result.
7. Missing required evidence MUST yield **INVALID**, not PASS.
8. Material changes to the tested system, policy, control, environment, mapping, or corpus SHOULD trigger retesting where they can affect the result.
9. Non-empirical requirements MUST remain distinguishable from empirically tested efficacy assertions.

## 8. Framework-Agnostic Architecture

> **Threat, control, audit, and regulatory frameworks are pluggable inputs to Proof Protocol. Proof Protocol is framework-agnostic.**

External frameworks can identify **what to test or examine**. Proof Protocol independently establishes **whether the control worked and what evidence proves that result**.

No external framework is required for Proof Protocol to operate. An implementation MAY use NIST CSF 2.0, another recognized framework, a proprietary threat model, several frameworks simultaneously, or no external framework when the test condition is otherwise sufficiently defined.

Adding, replacing, muting, or removing a framework mapping does not alter the Proof Protocol architecture, evidence model, Proof of Efficacy determination, ProofBundle™, ProofStamp™, ProofRegister™, or independent corroboration requirements.

A framework mapping therefore establishes **interoperability**, not architectural dependency.

## 9. Relationship to Proof Protocol

This mapping is part of the Proof Protocol specification family maintained by Nebulonium, Inc.

The relationship is intentionally asymmetric:

> **NIST CSF 2.0 supplies a taxonomy of cybersecurity outcomes. Proof Protocol supplies the evidence model for independently examining whether a selected control achieved a tested outcome.**

No affiliation, endorsement, certification, audit opinion, or sponsorship by NIST is implied.

## 10. Source Framework, Attribution, and License

NIST CSF 2.0 is a NIST publication. NIST states on its copyright and licensing page for technical series publications (https://www.nist.gov/open/copyright-fair-use-and-licensing-statements-srd-data-software-and-technical-series-publications) that "Works authored by NIST employees are not subject to Copyright protection within the United States", that NIST may assert rights outside the United States, and that where it does, the public is granted a non-exclusive, royalty-free, worldwide right to reprint such works. NIST also states that mention of commercial products does not imply NIST recommendation or endorsement. Third-party material referenced through Informative References remains subject to its own owners' terms.

This specification references CSF Function, Category, and Subcategory identifiers and structural terms only. It does not reproduce CSF outcome statements or Implementation Examples.

This Proof Protocol mapping is independently authored and licensed under **CC BY 4.0**. That license applies only to original Proof Protocol material in this repository. It does not relicense external standards, regulations, criteria, frameworks, or trademarks.

Where upstream material is copyrighted or access-controlled, contributors MUST NOT copy protected normative text into this repository merely to make the mapping self-contained. Reference identifiers and independently authored descriptions should be used where legally appropriate.

### Required attribution

NIST requests attribution rather than requiring a license notice. NIST's technical series statement asks users to "use the recommended citation format" followed by "Republished courtesy of the National Institute of Standards and Technology." (source: https://www.nist.gov/open/copyright-fair-use-and-licensing-statements-srd-data-software-and-technical-series-publications). Because this specification republishes no CSF text, the citation is used without the republication line:

> National Institute of Standards and Technology (2024) The NIST Cybersecurity Framework (CSF) 2.0. (National Institute of Standards and Technology, Gaithersburg, MD), NIST Cybersecurity White Paper (CSWP) NIST CSWP 29. https://doi.org/10.6028/NIST.CSWP.29

(Citation format from the "How to Cite" entry of NIST CSWP 29, https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.29.pdf.)

Recommended notice used in this repository:

> NIST Cybersecurity Framework (CSF) 2.0, NIST CSWP 29 (February 26, 2024), https://doi.org/10.6028/NIST.CSWP.29. Source: National Institute of Standards and Technology. Use of CSF identifiers does not imply NIST endorsement.

Any future inclusion of CSF text in a ProofBundle™ or derivative work SHOULD add the line "Republished courtesy of the National Institute of Standards and Technology."

## 11. Versioning

This mapping is versioned independently of NIST CSF 2.0. Material upstream changes, including a new CSF version or updated Implementation Examples or Informative References, SHOULD trigger a mapping review and, where necessary, a new version identifying the CSF revision mapped.

---

*Proof Protocol · proofprotocol.io · CC BY 4.0*
