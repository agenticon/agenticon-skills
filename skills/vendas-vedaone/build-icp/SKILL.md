---
name: build-icp
description: "Creates or refines a structured Ideal Customer Profile (ICP) for a commercial campaign. Use when a campaign needs an initial ICP, a revised ICP, scoring criteria, exclusions, buyer roles, or explicit hypotheses to validate."
---

# Objective
Produce a versioned, auditable `ICPSpec` and deliver it through
`deliver_icp_spec`.
This skill is product-agnostic and industry-agnostic.
# When to use
Use this skill when:
- creating the first ICP of a campaign;
- refining an ICP after research or interviews;
- defining inclusion/exclusion criteria;
- defining lead scoring;
- adding validation questions;
- versioning an ICP after learning.
# Do not use when
Do not use for:
- scoring one specific lead;
- doing lead enrichment;
- researching one company;
- writing messages;
- changing the campaign objective.
# Required inputs
- CampaignSpec;
- BusinessUnitSpec;
- offer/product context;
- available market research or approved knowledge.
# Optional inputs
- existing ICPSpec;
- historical customers;
- interview notes;
- market research;
- competitor research;
- rejected lead examples;
- golden examples.
# Critical rule: hypothesis is not fact
An ICP can be useful before it is validated.
When the business has little or no commercial evidence:
- set `validation_status: HYPOTHESIS`;
- include assumptions explicitly;
- add validation questions;
- never rewrite a product thesis as a validated market fact.
# Source precedence
1. explicit current human decision;
2. structured commercial state;
3. approved business-unit knowledge;
4. customer evidence/interviews;
5. sourced market research;
6. external research if authorized.
# Process
1. Read the CampaignSpec.
2. Read the BusinessUnitSpec.
3. Load approved product/offer knowledge.
4. Load market research when available.
5. Separate:
	- confirmed characteristics;
	- inferred characteristics;
	- unknown characteristics.
6. Define geographic scope.
7. Define preferred and secondary business profiles.
8. Define positive operational signals.
9. Define pain hypotheses.
10. Define buying triggers and maturity signals.
11. Define hard exclusions.
12. Define review-required exclusions.
13. Define buyer and user roles.
14. Create a scoring model.
15. Make weights total exactly 100.
16. Decide how UNKNOWN behaves for each criterion (`unknown_handling`).
17. Define qualification/review thresholds and `min_coverage` (the minimum fraction
	of the total weight that must be evaluated before a lead can be QUALIFIED).
18. Add questions that future customer conversations must validate.
19. Version the ICP: never set `id`, `version`, `status` or timestamps yourself — the
	server stamps the envelope. To revise an existing ICP, pass `revises` with its
	current id and version; the previous version is never overwritten.
20. Call `deliver_icp_spec`.
21. Call `request_action` with `ACTIVATE_ICP` for the delivered version. The ICP
	only becomes ACTIVE when a human approves it in the Approvals panel.
# Scoring principles
The scoring model must be explainable.
Prefer 5–10 criteria.
Each criterion must describe:
- what is being measured;
- why it matters;
- weight;
- evaluation method;
- behavior when data is unknown.
Do NOT automatically score UNKNOWN as negative unless the business rule
explicitly requires it.
A missing field is not evidence of poor fit.
Lead scores are always computed by the server from the criteria you define (you
never compute them in qualification). Design the criteria knowing how they are scored:
- `BOOLEAN`: met = full weight, not met = 0;
- `ORDINAL_0_5`: weight × level / 5;
- `NUMERIC_RANGE`, `RULE_BASED`, `CUSTOM`: met = full, partial = half, not met = 0;
- UNKNOWN with `NO_SCORE_CHANGE` leaves the criterion out of the evaluated weight,
	`REVIEW_REQUIRED` leaves it out and sends the lead to REVIEW, `ZERO_SCORE` counts 0;
- score = 100 × points earned / evaluated weight; below `min_coverage` the lead goes
	to REVIEW.
# Exclusion principles
Use `hard` exclusion only when a lead truly cannot/should not be served.
Use `review` when the lead may still fit but requires judgment or more data.
Do not convert “less attractive” into a hard exclusion.
# Evidence rules
Every meaningful assumption should be represented in `assumptions`.
`CONFIRMED` requires a source.
Use human decisions as a source of type `human`.
External market estimates must not be presented as facts about an individual lead.
# Validation rules
Before delivery verify:
- campaign and business unit ids match;
- weights total 100;
- review threshold is lower than qualified threshold;
- pain points not validated by customers remain hypotheses;
- hard exclusions are genuinely hard;
- buyer roles are distinct from user roles when applicable;
- the ICP does not contain product-specific fields in the generic schema;
- product-specific vocabulary appears only in values.
# Completion criteria
The skill is complete ONLY when:
1. `deliver_icp_spec` is called;
2. the tool returns `ok: true`; and
3. `request_action` (activation) was called for that version, or the human explicitly said
	not to request activation yet.
# Tool failure
If the delivery tool rejects the object (canonical schema or semantic validators):
1. inspect the validation message;
2. fix the object;
3. retry;
4. do not remove required evidence merely to pass validation.
# Human review
For a new ICP with `validation_status: HYPOTHESIS`, human review should normally
be required before production outreach.
Activation always goes through the Approvals panel. You never approve it yourself.
# Final human response
After successful delivery, summarize:
- ICP id/version;
- validation status;
- top positive signals;
- hard exclusions;
- scoring thresholds;
- top unresolved hypotheses;
- that the activation is waiting in the Approvals panel;
- recommended next step.
Do not dump the full object unless requested.
# Language
Write the free-text values of the artifact in the language of the business unit's
market (`BusinessUnitSpec.market.languages[0]`) and answer the human in that same
language. Enum values, ids and field names stay exactly as the schema defines them.
