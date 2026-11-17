---
name: configure-campaign
description: "Creates or refines a structured commercial campaign specification for any Agenticon business unit. Use when starting a new campaign, changing campaign objectives, channels, permissions, target segments, CTA, or success criteria."
---

# Objective
Produce a complete, internally consistent `CampaignSpec` for one Agenticon
commercial campaign and deliver it through `deliver_campaign_spec`.
This skill is product-agnostic and industry-agnostic.
# When to use
Use this skill when:
- creating a campaign;
- cloning/adapting an existing campaign;
- changing campaign scope;
- changing target segment;
- changing campaign permissions;
- changing campaign goals or metrics;
- preparing a campaign for human approval.
# Do not use when
Do not use this skill for:
- defining the ICP itself;
- qualifying one lead;
- researching one company;
- writing outreach;
- changing product knowledge.
# Required inputs
At minimum:
- business unit identifier;
- offer/product context or a reference to where it can be retrieved;
- primary commercial objective.
# Optional inputs
- geography;
- language;
- target segments;
- lead count;
- discovery channels;
- outreach channels;
- CTA;
- campaign mode;
- permissions;
- metrics;
- previous CampaignSpec.
# Source precedence
Use information in this order:
1. explicit current human instruction;
2. structured commercial state;
3. approved business-unit knowledge;
4. approved institutional knowledge;
5. external research, only if authorized.
Conversation history is context, not system of record.
# Information quality
Never fabricate missing campaign decisions.
Use:
- `CONFIRMED` for explicit human decisions or reliable evidence;
- `INFERRED` only for a reasonable assumption that is clearly labeled;
- `UNKNOWN` when information is unavailable.
If an unresolved decision changes campaign safety or execution permission,
ask the human instead of inferring.
# Process
1. Load the business-unit context.
2. Load an existing CampaignSpec if this is a revision.
3. Determine the primary campaign objective.
4. Identify the target segment.
5. Confirm market/language.
6. Determine campaign mode:
	- `LEARNING`
	- `PILOT`
	- `PRODUCTION`
7. Define discovery sources (free text) and outreach channels, plus prohibited
	channels. Channels come from the closed channel catalog of the schema (`Channel`).
8. Define the primary CTA.
9. Define all eight permissions explicitly: `public_research`, `crm_read`,
	`crm_write`, `create_drafts`, `external_send`, `schedule_meeting`,
	`create_proposal`, `make_commercial_commitment`. These permissions govern what the
	agent may do; a human may still act manually through a human task.
10. Define measurable success metrics. A metric has a `target` only when the human
	gave it (`target_source: human`); otherwise `target: null` and
	`target_source: none`.
11. Capture unresolved assumptions with evidence classification.
12. Validate internal consistency.
13. Build the complete `CampaignSpec` payload. Never set `id`, `version`, `status` or
	timestamps: the server stamps the envelope. To revise an existing campaign, pass
	`revises` with its current id and version.
14. Call `deliver_campaign_spec`.
15. Call `request_action` with `ACTIVATE_CAMPAIGN` for the delivered version.
	The campaign only becomes ACTIVE when a human approves it in the Approvals panel.
# Permission rules
In `LEARNING` mode, prefer conservative permissions:
- public research may be automatic;
- draft creation may be automatic;
- external sending should normally remain false;
- CRM write should remain false unless explicitly authorized.
Never elevate permissions because they seem convenient.
`make_commercial_commitment` is always false in `LEARNING`; the delivery tool rejects
anything else. Changing any permission of an active campaign is a new version and
needs a new activation approval.
# Validation rules
Before delivery verify:
- business unit exists;
- objective is specific enough to guide action;
- at least one primary target segment exists;
- market has at least one country and language;
- CTA is compatible with campaign stage;
- permissions match human authorization;
- success metrics do not contain invented targets;
- assumptions are clearly labeled.
# Completion criteria
This skill is complete ONLY when:
1. `deliver_campaign_spec` is called;
2. the tool returns `ok: true`; and
3. `request_action` (activation) was called for that version, or the human explicitly said
	not to request activation yet.
A prose description of the campaign does not complete this skill. You never approve
the activation yourself.
# Tool failure
If the delivery tool rejects the object:
1. read the validation error;
2. correct only the invalid/inconsistent fields;
3. retry;
4. do not weaken the schema to force acceptance.
# Human interaction
Ask the human only for decisions that cannot safely be retrieved or inferred.
Good example:
> “Posso montar a campanha em modo LEARNING com pesquisa pública e rascunhos,
> mas sem envio externo. Quer manter assim?”
Bad example:
> “Qual é o nome da empresa?” when it is already present in approved context.
# Final human response
After successful delivery, provide a concise summary:
- campaign id/name;
- mode;
- target;
- permissions;
- main CTA;
- assumptions still open;
- that the activation is waiting in the Approvals panel;
- recommended next action.
Do not dump the full JSON unless asked.
# Language
Write the free-text values of the artifact in the language of the business unit's
market (`BusinessUnitSpec.market.languages[0]`) and answer the human in that same
language. Enum values, ids and field names stay exactly as the schema defines them.
