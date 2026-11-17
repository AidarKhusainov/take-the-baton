# Choose models and reasoning for subagents

Apply this policy before delegating research, implementation, testing, or independent review to a subagent, including delegation from a [working chat](GROUPS.md). Use the project's [Subagent selection profile](templates/profile.md#subagent-selection). The default priority is **balanced** when no preference has been supplied. Explicit user choices, project requirements, and host restrictions take precedence.

This policy selects settings for a delegated assignment. It does not authorize changing the coordinator's model, a persistent working chat's model, global configuration, or access permissions. Use the actual delegation tool's rules. If a working-chat tool requires the user to name a particular model, preserve its configured default until that requirement is met. Do not treat a configured preference for subagents as permission to override another surface.

## Establish available choices

Use the current host's exposed model catalog, tool schema, or other verified capability information to establish which models and reasoning levels the delegation route accepts. Check the destination host when it differs. Treat a saved profile as a starting point and refresh stale or contradicted availability before using it. Do not probe model availability by launching speculative subagents.

Keep concrete model IDs, supported effort levels, model-specific defaults, and evidence in the profile. Map available models to economical, standard, and deep-analysis choices where the evidence supports those roles; one model may fill several roles. Do not hardcode a provider's current model names in the workflow or infer price, quality, or context capacity from a name alone. Use verified provider information or relevant project observations and mark unknown comparisons as unknown.

Check separately whether launch and continuation can set model and reasoning effort, and whether an override requires a fresh context. Select a supported pair: effort labels are not a common scale across models, and balanced does not mean `medium` for every model. Apply fallback only to a dimension that cannot be selected or verified, preserving supported explicit choices for the other dimension. Inherit that dimension only when it is compatible with the chosen settings and satisfies the user's constraints. If a required inherited value cannot be established, keep the assignment pending or use a separately authorized route that can satisfy it.

Separate verified availability from comparative ranking. An unknown economical/standard/deep-analysis mapping does not invalidate an otherwise supported user-pinned model or effort. When no reliable ranking is available, use compatible configured defaults for unpinned dimensions and record the uncertainty. Proceed only if the known capabilities and available verification are adequate for the assignment; keep work needing an unavailable capability pending and explain the missing requirement.

## Select for the assignment

Make the choice in the assigning chat without launching another agent solely to choose settings. First define the deliverable, relevant sources or revisions, scope, and acceptance check. Keep short work in the current chat when delegation would add more handoff than useful independent work.

Assess the assignment's reasoning difficulty, ambiguity, dependencies, consequences of a missed error, and how the result can be verified. File count, diff size, and role name alone do not determine difficulty. A one-line access-control change can require deeper analysis than a long mechanical edit.

Choose the model for the capabilities needed, such as reliable analysis of the affected contracts, tool access, and sufficient context. Choose reasoning effort separately for the depth of planning and analysis needed within that model. Use its verified default as a starting point and adjust for the assignment. Maximum effort requires a concrete reason; it is not the default for all work or all reviewers.

| Assignment | Starting choice under balanced priority |
| --- | --- |
| Locate definitions, gather cited facts, or run a documented check | Use an economical eligible model and an appropriate model-specific effort when the scope is bounded and the result is easy to verify. |
| Implement a local change with clear behavior and focused tests | Use the standard eligible model and its normal effort; increase depth if investigation exposes ambiguity or hidden dependencies. |
| Diagnose subtle failures or reason about contracts, concurrency, persistence, migrations, or security | Use an eligible model suited to the required analysis and enough reasoning depth for the consequences and uncertainty. Select it at the outset when the risk is already apparent. |
| Independently review a change | Select by the difficulty of checking invariants and the consequences of missed defects. Preserve independent review even for economical implementation; do not infer that all review requires the maximum model or effort. |

The priorities change the tradeoff, not the acceptance criteria:

- **Balanced (default).** Use the least costly choice supported by available evidence as adequate for the required result, taking expected retries, review, and rework into account. Prefer the standard configured choice when adequacy of an economical option is unknown. Use deeper analysis immediately for known difficult or consequential work.
- **Quality.** Favor additional analysis when uncertainty or consequences justify it, within the user's constraints. Routine, verifiable evidence collection can still use an economical choice.
- **Economy.** Favor bounded assignments, economical eligible choices, and focused checks. Do not weaken required tests, contracts, independence, or review to meet the preference. If the constraints cannot support the required result, report the tradeoff before proceeding with the affected work.

Respect explicit model or effort restrictions and any supplied limits. A priority is not permission to exceed them. Once a policy and its scope are approved, make ordinary supported selections without requesting permission for every subagent. Ask only when a new choice exceeds authorization or needs a material decision.

## Launch and retain evidence

Set both selected values together when the tool supports both overrides. When it supports only one dimension, set that one and use the compatible fallback for the other; preserve supported user-pinned values. If either is inherited or cannot be controlled, record that rather than claiming the requested pair was used. Read back the effective settings when the host exposes them; distinguish requested, inherited, and confirmed settings when it does not. An unverified inherited value does not satisfy a required explicit value.

Give the subagent a compact, sufficient handoff: the deliverable, constraints, relevant source and change references, acceptance checks, prior findings, and any unresolved question. If selecting another model requires a fresh context, carry this material forward explicitly. Do not assume it receives the parent chat's history or change an existing assignment's ownership implicitly.

Record the selection briefly in the current chat or the existing task record: assignment or role, requested model and effort, effective settings if known, and one sentence explaining the choice. On completion, link the checks or evidence establishing the result and any escalation. This does not require creating a new persistent record for every small delegation. Use only the approved private storage when a record is needed.

## Continue and escalate

Keep the assigned developer and reviewer through follow-up rounds as required by [WORKFLOW.md](WORKFLOW.md#5-review-and-resolve-findings). Use supported continuation controls if the settings need to change. If they are unavailable, do not claim a model switch took place. Continue with the current settings when adequate, or use the project's allowed reassignment route with the existing record and evidence. Preserve ownership, revision references, and reviewer independence; do not add competing writers or another permanent review loop merely to obtain a different model.

Escalate for an identified unresolved problem, such as contradictory evidence, failed hypotheses that reveal deeper reasoning needs, a newly discovered cross-service invariant, or a missed consequential defect. Send the specific question and existing evidence, not a request to repeat all completed work. Increase effort within the model or select a model better suited to the problem according to the available evidence; there is no mandatory sequence of trying every tier.

Before escalating, distinguish insufficient reasoning from missing requirements, unavailable permissions or tools, bad inputs, and environment failures. Obtain missing evidence or resolve the relevant blocker first. A stronger model cannot supply the user's undecided behavior or make an unavailable test run. Do not keep escalating after repeated attempts produce no new evidence: report the unresolved question and the decision or capability needed. Higher confidence alone is not evidence that the result is correct.

An escalation does not clear pending checks or reviews. Verify the resulting change under the same acceptance criteria and current revision rules. A completed assignment normally retains its successful result; revisit it only when changed evidence, dependencies, or requirements justify another pass.

## Improve the policy through reflection

When [reflection](REFLECTION.md) is enabled and the sources are approved, include the assignment type, requested and effective settings if known, reason for escalation, and observed verification or rework outcome. Record time, tokens, or cost only when actually available, and identify estimates as estimates. Compare similar assignments with comparable scope and checks; one successful run does not establish that a model is best or that another would have been worse.

Repeated comparable episodes can support one proposed change to the profile's mapping or defaults, under the existing reflection threshold and approval rules. Reflection does not silently change the priority, model mapping, budgets, or live agent settings.

## Verification scenarios

These are instruction walkthroughs; they do not benchmark models or prove live host support.

| Situation | Expected behavior |
| --- | --- |
| No project priority is recorded | Use balanced, include it in the setup proposal, and avoid an extra mandatory preference question. |
| The user previously confirmed a fixed model or economy priority | Preserve that choice and its limits; do not overwrite it with the default. |
| A bounded lookup is part of a high-risk migration | Select for the lookup itself and verify its facts; retain appropriate analysis and review for the migration. |
| A one-line change affects authorization or transaction boundaries | Assess consequences and invariants rather than treating the small diff as routine. |
| A requested model or effort is no longer supported | Refresh available choices, use only an authorized adequate fallback, and report any unmet explicit requirement. |
| The tool supports a pinned model but only inherited effort, or the reverse | Keep the supported pin and fall back only for the other dimension. If its required value or compatibility cannot be established, leave the assignment pending or use an authorized compatible route. |
| Model availability is verified but comparative role rankings are unknown | Honor a supported explicit model or effort choice; use compatible defaults for unpinned dimensions without inventing a ranking. |
| A fresh-context launch is required for a model override | Carry forward scope, revisions, decisions, and evidence explicitly, while preserving assignment ownership. |
| Continuation cannot change model or effort | Keep the current settings if adequate or follow allowed reassignment; do not report an imaginary switch. |
| A test cannot run because access is unavailable | Resolve the access or verification blocker; do not buy more reasoning to claim the test passed. |
| An escalation returns greater confidence without new evidence | Keep the original unresolved acceptance check pending. |
| Two comparable assignments needed avoidable retries with the same settings | Reflection may propose a mapping change with evidence; it does not automatically rewrite the profile. |
