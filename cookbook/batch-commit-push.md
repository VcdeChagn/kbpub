---
command: for r in ~/repo-a ~/repo-b; do git -C "$r" add -A; git -C "$r" commit -m "session update"; git -C "$r" push; done
when_to_use: Commit everything and push several repos in one paste; safe to run when a repo has nothing to commit.
tested_on: 2026-10-12, any Linux with git 2.x
expected_output: Per repo: "[main abc1234] session update ..." then push output; "nothing to commit, working tree clean" is a pass, not an error.

Loop over as many repo dirs as needed. git add -A stages all changes so one
commit captures the whole batch. To collapse recent local commits into one
before pushing: git reset --soft HEAD~<n> then a single git commit.
