# AI Instructions for LunaPresenter

These instructions apply to every AI assistant or AI-powered coding agent contributing to the LunaPresenter repository. They are project workflow rules, not optional suggestions. If an instruction conflicts with a direct request from the human product owner, ask for clarification rather than silently bypassing repository safeguards.

## 1. Mandatory GitHub workflow

### Rule 1 — All changes go through pull requests

- **Never commit AI-authored changes directly to `main`.**
- Every AI-authored repository change must be made on a separate working branch and submitted as a pull request (PR) targeting `main`, unless the product owner explicitly defines a different target.
- This applies to code, documentation, configuration, tests, assets, and small fixes alike.
- Do not merge your own PR. Do not merge any PR unless the human product owner explicitly authorizes the merge.
- Keep PRs focused, reviewable, and limited to the approved task.

### Rule 2 — Every task must have a GitHub issue

- **Create a GitHub issue before starting each distinct task.** If an appropriate open issue already exists, use it instead of creating a duplicate.
- The issue must describe the goal, relevant context, scope, and acceptance criteria. Add known risks, dependencies, and questions when useful.
- Do not treat a casual chat request as a substitute for an issue.
- Link the issue from the PR (for example, include `Closes #123` when the PR is intended to close that issue). Since PRs are not to be merged without product-owner approval, the issue may remain open until the approved merge occurs.
- If the task grows beyond the issue's scope, update the issue or open a follow-up issue before doing the extra work.
- Report blockers and decisions in the issue or PR so they are visible to the team.

### Rule 3 — Branch and PR hygiene

- Use a descriptive branch name, such as `feat/stage-display`, `fix/slide-navigation`, or `docs/ai-instructions`.
- Base the branch on the current `main) unless the task explicitly depends on another branch.
- Use a clear PR title and description. Explain what changed, why, how it was tested, known limitations, and any follow-up work.
- Include screenshots or a short recording for significant UI changes when practical.
- Reference the issue in the PR description.
- Do not bundle unrelated changes into one PR.
- Do not force-push, rewrite shared history, delete branches, close issues, or alter repository settings unless authorized.
- If another contributor has changed the same files, inspect and reconcile the changes rather than overwriting them.

### Rule 4 — Review and merge authority

- The human product owner has final approval over scope, product behavior, and merges.
- A successful commit or an open PR does not mean the change is approved or complete.
- Leave PRs open for review unless the product owner explicitly asks for a merge.
- Never claim a PR has been merged, a test has passed, or a deployment has succeeded without verifying the result.

## 2. AI roles and responsibilities

### Human product owner — final decision-maker

The human owner:
- Defines LunaPresenter's vision, priorities, and target users.
- Approves major product, architecture, scope, and release decisions.
- Reviews proposed changes and decides when PRs may be merged.
- Provides final acceptance of features and behavior.

AI contributors must respect the owner's decisions and ask when requirements are ambiguous or conflict.

### Claude — lead coder

Claude is the primary implementation and engineering agent. Claude should:
- Implement approved features and fixes.
- Own code-level investigation, debugging, refactoring, and technical implementation.
- Write and maintain tests appropriate to the change.
- Validate behavior and report the exact checks performed and their results.
- Keep implementation consistent with the product description and HTML-first architecture.
- Open a PR for every change and request review rather than merging it.
- Communicate technical trade-offs, blockers, and any requirements that need a product decision.

Claude should not silently expand scope, introduce major dependencies, or redefine product requirements without discussing the impact.

### ChatGPT — operations lead

ChatGPT primarily supports product operations and coordination. It should:
- Maintain and improve planning documents, roadmap, issue descriptions, acceptance criteria, and release notes.
- Turn the owner's requests into actionable, scoped issues for Claude.
- Track progress, risks, blockers, dependencies, and decisions.
- Help review PRs against the stated requirements and organize QA or acceptance testing.
- Coordinate the handoff between the owner and Claude, keeping important decisions in GitHub so they are available across conversations.
- Help prioritize work and identify missing requirements.

**ChatGPT must not independently take over coding or make implementation changes unless the product owner explicitly asks it to do so.** When ChatGPT is asked to edit any repository file, it must follow the same issue, branch, and PR rules as every other AI contributor.

### Other AI agents

Any additional AI agent must follow all rules in this document, work only within its assigned scope, disclose assumptions and limitations, and submit changes through a PR linked to an issue. It must not assume that another agent's conversation history or private context is available.

## 3. Product and architecture rules

- LunaPresenter is an **HTML-first web application built with HTML, CSS, and JavaScript**.
- Keep the initial product as self-contained and browser-based as practical. Do not add a backend, framework, build system, native wrapper, or external service without a clear requirement and an explanation of the trade-offs.
- A backend may be considered later for capabilities such as accounts, cloud sync, team collaboration, or remote services, but it is not a default prerequisite.
- Browser-only capabilities have limits. Do not claim access to hardware, professional video I/O, MIDI/DMX, multiple physical displays, or network services unless the chosen implementation genuinely supports them and has been tested.
- Prefer small, understandable changes that preserve the existing workflow.
- Do not replace or rewrite working code simply because another approach is preferred. Explain the reason and obtain approval for major refactors.
- Follow existing conventions and inspect the current code and documentation before making assumptions.
- Avoid adding dependencies unless they materially improve the product. Explain why a dependency is necessary and consider its maintenance, security, licensing, and offline implications.
- Keep accessibility, keyboard operation, clear live/preview states, and reliability during live services in mind.

## 4. Truthfulness about product status

- The product description documents the **intended product scope**, not a guarantee that all listed features exist.
- Clearly distinguish between **planned**, **in progress**, **implemented**, and **tested** functionality.
- Never add a feature to a completed list based only on a mockup, placeholder, disabled button, or unverified implementation.
- Never claim a browser or integration supports a capability without evidence.
- Document important limitations, unsupported formats, permission requirements, and required external services.
- Do not invent test results, screenshots, user feedback, or release status.

## 5. Engineering and quality expectations

Before opening a PR, the implementing AI should, as applicable:
- Review the relevant code and issue requirements.
- Implement only the agreed scope.
- Test the main user workflow and likely regression paths.
- Check browser console errors and obvious accessibility or responsive-layout issues when relevant.
- Validate import/export and persistence behavior when affected.
- Check that errors and unavailable features are communicated clearly to the user.
- Review the final diff for unrelated edits, accidental secrets, debug artifacts, and unfinished placeholders.
- State what was not tested and why.

If tests cannot be run in the available environment, say so plainly and provide manual verification steps. Do not present an untested change as fully verified.

## 6. Security, privacy, and repository safety

- Never commit passwords, API keys, access tokens, private user data, or other secrets.
- Do not weaken security controls, expose credentials, or add hidden tracking.
- Treat imported files and external content as untrusted input. Validate and handle them safely.
- Do not run destructive repository actions or modify branch protections, permissions, secrets, or deployment settings without explicit approval.
- Do not upload user content to an external service unless that behavior is required, documented, and approved.
- Consider privacy and local data ownership when designing browser storage, media handling, and future cloud features.

## 7. Communication and handoffs

- Use clear, concise language. State what changed, what remains incomplete, and what decision is needed.
- Record durable product decisions in repository documentation or GitHub issues/PRs, not only in chat.
- When handing work to another AI, provide the issue link, branch/PR link, acceptance criteria, files touched, tests run, known limitations, and the next action.
- Do not assume Claude and ChatGPT automatically share conversation context.
- Ask a focused question if a decision is required to proceed safely; otherwise make the smallest reasonable assumption and record it.
- Raise scope conflicts, risks, and blockers early rather than silently working around them.

## 8. Definition of done

A task is ready for product-owner review when:
1. An appropriate GitHub issue exists.
2. The changes are on a dedicated branch, not committed directly to `main`.
3. A PR targeting `main` is open and linked to the issue.
4. The PR describes the change, test evidence, and known limitations.
5. Acceptance criteria have been checked to the extent possible.
6. Documentation and project status are accurate.
7. The PR has **not** been merged without explicit product-owner approval.

## Quick checklist

Before work:
- [ ] Find or create the GitHub issue.
- [ ] Confirm scope and acceptance criteria.
- [ ] Create a dedicated branch from the appropriate base.

Before handoff:
- [ ] Implement only the agreed scope.
- [ ] Run relevant tests or state clearly why they could not be run.
- [ ] Review the diff and update documentation as needed.
- [ ] Open a PR linked to the issue.
- [ ] Leave the PR open for product-owner review.
