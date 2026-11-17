# Direction: matrix-docker-ansible-deploy (owner's fork)

The owner's GitHub fork of the upstream Matrix Ansible/Docker playbook. It is used to
deploy the IrregularChat Matrix homeserver. This file covers the fork only. Upstream's
direction belongs to upstream.

Status: dormant (last change 2024-11-24). The fork was created on 2024-11-21, synced up to
upstream commit 5483925e and never pushed again. It is now 3,878 commits behind upstream.

## Where it is heading
- The fork carries no changes of its own. It has 0 commits ahead of upstream, and none of
  its 8,667 commits are by the owner (GitHub compare `spantaleev:master...gitayam:master`:
  ahead 0, behind 3,878).
- It is used as a deployment checkout, not a code fork. Server settings live in the
  gitignored `inventory/` (upstream `.gitignore`), and the owner runs the playbook through
  the dotfiles helpers `matrix_setup` and the user-registration helper, which assume this
  checkout (`dotfiles: shared/zsh/.zsh_utils`).
- The owner's working copy holds about 218 untracked files that look like newer upstream
  files (Element Call / LiveKit docs, REUSE licence files, more roles under `roles/custom`).
  It may have been updated outside git (ai-coding-env
  `docs/reviews/2026-11-03-repository-inventory.json`; file names only).

## Priorities
1. Decide whether this fork is still needed (open question). If it is, sync it to
   upstream's current release and record which upstream commit the server runs (inferred).
2. Before any sync, read upstream's CHANGELOG.md from 2024-11-24 to now for breaking
   changes that affect the IrregularChat inventory (for example, KeyDB was replaced by
   Valkey in ca8c1cf2) (inferred).
3. Keep the dotfiles `matrix_setup` helpers in step with the playbook tags and paths the
   synced version uses (inferred).

## Non-goals and constraints
- Don't develop playbook features or fixes in this fork. Changes to roles belong upstream.
  The fork has never diverged (compare above).
- Never commit `inventory/` or anything from it (hosts, vars, secrets). Upstream ignores it
  on purpose (.gitignore).
- Don't run the playbook against the production homeserver as part of a coding job. Running
  it is a host operation that needs the owner's go-ahead (global ops rules; no deploy is
  defined for this repo).
- The Hermes ship config marks this repo `merge: auto` with `deploy: none`
  (ai-coding-env `servers/hermes-coding/ship/config.json`). Automated merges to a fork of
  a large upstream should be limited to upstream syncs (inferred).

## Decisions
- 2024-11-24: fork synced to upstream 5483925e; no later pushes (GitHub `pushed_at`, HEAD)
- 2024-11-21: forked upstream into the owner's account (GitHub `created_at`)

## Open questions for the owner
1. Is the IrregularChat Matrix homeserver still deployed with this playbook, and from which
   checkout? The fork's HEAD is two years old, but the working copy has newer upstream files.
2. Should the fork be kept at all (for example, for future patches), or should the server
   be deployed from a plain upstream clone, with the repo dropped from the Hermes board?
3. If kept: should the bot open upstream-sync PRs on a schedule, or only when you ask?

## Related documents
- Upstream: `README.md`, `CHANGELOG.md`, `docs/` (upstream's, not the owner's)
- Owner's tooling around it: dotfiles `shared/zsh/.zsh_utils` (`matrix_setup`),
  ai-coding-env `docs/syncthing/LESSONS_LEARNED.md` (root-owned `roles/galaxy` and Syncthing)
