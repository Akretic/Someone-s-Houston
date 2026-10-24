# Dormant public runner contract

Support remains discontinued as of September 26, 2026. All three workflows
remain manually disabled, and the backend remains paused. This change only
replaces dormant `runs-on` selectors; it does not enable Actions, dispatch a
workflow, restore hosting, import data or restart the issue-writing monitor.
The retirement instructions in `../docs/data-operations.md` continue to apply.

Every dormant job selects group `akretic-public-ci` and labels
`[self-hosted, Linux, X64, akretic-public-ci]`. Any future authorized activation
requires a separate public-only, isolated Ubuntu 24.04 x64 pool with a clean
VM baseline for each job. Public/fork code must never enter private or
production runner groups. This source change does not provision or qualify
that pool.

Existing triggers, checkout settings, permissions, timeouts, dependencies,
test commands and job names are preserved. The retired monitor retains its
main-only guard and existing `issues: write` permission; it must not run as
part of this runner migration. Its missing schedule stays removed.

The four required checks remain `Backend build and Node tests`,
`Python import safeguards`, `Migrations and SQL access/publication tests`, and
`Frontend tests and production build`. Main still requires one independent
approval of the last push and the existing branch-protection gates. Do not
weaken those rules to merge while CI is disabled. A future restart requires
the owner's explicit authorization and deliberate workflow reactivation;
this dormant selector update grants neither.
