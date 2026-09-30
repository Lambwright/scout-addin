# scout-addin

## Coming change: Einbau ID role matrix

Einbau ID (`auth-worker`) is moving from a flat "restricted to these app IDs"
list to company job roles plus a per-app permission matrix, managed in HELM.
Per the auth-worker session's proposal (2026-09-30): `user.apps` keeps its
current meaning (still what SCOUT's access gate checks), now computed from
the matrix instead of set directly; `user.appRoles` (per-app computed level,
lowercase) and `user.jobRole` (informational) are new and unused by SCOUT
today. SCOUT's existing `apps.includes('SCOUT')` gate keeps working unchanged.

SCOUT has no code that reads `user.role`, a hardcoded username, or anything
else on the user object for authorization — the only username-keyed logic is
`ESTIMATOR_PROCORE_IDS`/`ESTIMATOR_DISPLAY_NAMES` (which two people get the
estimator dropdown and a Procore user id), which is independent of this
migration and won't auto-populate for a new "Estimator" job role without a
manual edit here.