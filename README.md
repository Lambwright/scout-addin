# scout-addin

## Einbau ID role matrix

Access is managed in HELM through the role matrix (done): `user.apps` is computed from the
matrix and SCOUT's gate is `apps.includes('SCOUT')`. Nothing reads the retired `user.role`, and the
workers (netsuite, procore, scout) make the same `apps` check server-side. Known leftover (waiting
on a HELM field/tool permission, proposed 2026-10-21): the estimator list and their Procore ids
(`ESTIMATOR_PROCORE_IDS`/`ESTIMATOR_DISPLAY_NAMES`), an Alfonso-only greeting/avatar, and
support e-mail addresses in the help text are still hardcoded in app.html.