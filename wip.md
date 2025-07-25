# GitHub CLI api
# https://cli.github.com/manual/gh_api

# GitHub CLI api
# https://cli.github.com/manual/gh_api

gh api \
  --method POST \
  -H "Accept: application/vnd.github+json" \
  -H "X-GitHub-Api-Version: 2022-11-28" \
  /orgs/demo-org-madkoo/actions/runners/generate-jitconfig \
   -f 'name=test-jit' -F "runner_group_id=1" -f 'labels[]=self-hosted' -f 'labels[]=X64' -f 'labels[]=windows' -f 'work_folder=_work'