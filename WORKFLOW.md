# Take the Baton workflow

The human decides expected behavior, material tradeoffs, and when to publish or merge. Agents handle routine technical work within the approved scope.

Read the work project's instructions and the profile supplied by the user or referenced by the task record. The default profile is `.take-the-baton/profile.md`. Use [SETUP.md](SETUP.md) when a profile is needed. Follow the project rules and the user's authorizations throughout.

## 1. Take in the task

Create or reuse a [task record](templates/task.md) in the profile's task directory. Use a stable filename based on the task key or a local ID. Keep the original key or URL in the record. Record the requested action and destination. Before a remote create call, save the registration attempt and any stable request ID supported by the tool.

- **Existing task.** Read the task, its latest relevant comments, and linked requirements. Record its key or URL and surface any conflict that changes the work.
- **Register an idea.** Draft a title, problem, expected outcome, and any known acceptance criteria. Ask about gaps that affect what gets registered or where it belongs. Use the profile's destination when the user asks to register it. Confirm the created record and return its reference. Registration alone ends here.
- **Register and implement.** Register it, then continue to analysis. For an implementation request given as a description, use a local task record unless the user requests registration or the project requires a tracker task.

When remote creation is unavailable, prepare the draft or use the agreed local destination. Record remote registration as pending when required. If a create request has an uncertain result, record it and check whether the task exists before trying again. If uncertainty remains, ask the user to resolve it. Reuse a confirmed task reference when retrying or resuming. If the project requires a tracker key for a step, hold that step until the key is available and complete any analysis the project allows.

## 2. Agree on behavior

The analyst checks current code, contracts, project documentation, and tests. Record the baseline examined, what already exists, and the behavior that should change. Write a use-case spec covering the actor or trigger, inputs, expected flow, observable outcome, significant alternatives, and acceptance checks.

Resolve routine questions from project sources. Bring the human questions that change behavior, scope, or risk, with options and a recommendation when possible. Record the answers. Begin implementation after the human agrees to the spec.

## 3. Implement and verify

Hand the agreed spec, baseline, and acceptance checks to a fresh developer session when available. The developer checks the workspace against the recorded baseline, preserves unrelated changes, and implements within the agreed scope. Bring any material change to the spec back to the human.

Run focused checks during development and the project's relevant final checks. Record the base and exact change reviewed, such as a commit or a saved diff that includes the in-scope changes. Record test commands, outcomes, test counts when available, and any blocked or skipped checks. A run with zero relevant tests leaves those scenarios unverified.

## 4. Give the human the diff

Present the change, its verification evidence, and any remaining questions. Apply requested cleanup, then update the diff identity and rerun affected checks. Continue to independent review when the human hands off the diff. Record the identity of the diff they handed off.

## 5. Review and resolve findings

Give a fresh, independent reviewer the spec, exact diff, project rules, and check results. Where the current agent cannot start one, prepare a handoff for a separate agent session or a person and keep review pending.

The reviewer describes each finding with a location, consequence, and evidence. The developer validates it against the current change and records one disposition for it:

- **Confirmed.** Fix within scope and record the evidence.
- **Dismissed.** Record the evidence that resolves the concern.
- **Needs a decision.** Bring the human the tradeoff when the finding is disputed, expands scope, or requires accepting a material risk.

Run affected checks after a fix and ask for targeted re-review of substantial changes. Finish the loop when each finding has a disposition, any required decisions are recorded, and substantial fixes have been rechecked.

## 6. Publish and respond to feedback

When the user asks for a PR, compare the current diff with the last reviewed change before publishing. Recheck anything that affects the review or test evidence. Use the profile's route and the project's rules for commits and pushes, then verify the published diff matches the reviewed scope. Include the task reference, final behavior, and check results. If publication is unavailable, prepare the title, description, and exact diff for a manual handoff.

Record the PR reference and distinguish local verification from remote CI. Process colleagues' findings through the same validation and fix loop. The human makes the merge decision and merges the PR.

## Resume in any session

Update the task record at each handoff with the stage, owner of the next action, spec approval, exact diff identity, checks, and review decisions. Use the location agreed in the profile.

To resume, read the record and refresh relevant task or PR updates. Compare the current changes with the recorded diff. If the code changed, mark affected evidence as stale and repeat the relevant checks or review. If the handed-off diff changed outside the recorded review fixes, return the new diff to the human before resuming independent review. If requirements changed, resolve any material differences with the human before continuing.
