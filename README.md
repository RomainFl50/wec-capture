# wec-capture

Planificateur d'ingestion du dashboard [wec-dashboard](https://github.com/RomainFl50/wec-dashboard).

Ce dépôt **public** ne contient qu'un workflow GitHub Actions (`.github/workflows/capture.yml`)
dont les minutes sont illimitées. Il appelle périodiquement `/api/ingest/tick` sur le site :
capture live toutes les 30 s pendant les séances WEC, veille toutes les 5 min sinon, et ne
fait rien hors des week-ends de course.

## Configuration (une fois)

- **Secret** `CRON_SECRET` — même valeur que la variable `CRON_SECRET` du projet Vercel
  `wec-dashboard` (Settings → Secrets and variables → Actions → New repository secret).
- **Variable** `BASE_URL` = `https://wec-dashboard-rho.vercel.app`
  (Settings → Secrets and variables → Actions → Variables).

## Archiver une séance précise (backfill ponctuel)

Actions → « Capture WEC » → **Run workflow** → renseigner `sid` (ex. `18162` pour Monza).
Un seul appel `?sid=…` est émis, puis le run s'arrête.

Aucune donnée n'est stockée ici : tout est écrit dans la base du site.
