# Git Tidbits

## Rewrite author and committer on branch

```bash
FILTER_BRANCH_SQUELCH_WARNING=1 \
N='New Name' \
E=new-email@example.com \
git filter-branch -f --env-filter 'GIT_AUTHOR_NAME=$N; GIT_COMMITTER_NAME=$N; GIT_AUTHOR_EMAIL=$E; GIT_COMMITTER_EMAIL=$E' -- HEAD
```
