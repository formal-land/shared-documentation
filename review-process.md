# Review process

Here is how we review our pull requests.

## Make a pull request

First we make a pull request to the `main` branch, or some other branches in rare cases where the current task starts from another one that is not yet merged.

We use the pull request as a way to expose and discuss the current work. So even if the work is not finished, we can still make a pull request. The convention is to add a "Draft: " prefix to the pull request title when it is not ready for review.

## Naming

There are no conventions to name the branch or the commits. What we usually do:

- prefix the branch name by the author name, as there is generally only one author per branch and it helps to filter the branches in the repository: `author_name@branch_name`
- prefix the commit messages by a category (that we can freely choose), such as `feat`, `core`, `proof`, `doc`, ... to quickly have an idea of what the commits are doing

## Git history

We always rebase our branches on the `main` branch before merging them. We use a merge commit to put the content of a branch into the `main` branch (this is what happens when clicking on the green "Merge" button in GitHub).

Thus the Git history should look like this:

```
* 3d6b6c3 (HEAD -> main) Merge pull request #25 from author_name@branch_name
|\
| * 2d6b6c3 feat: add a new feature
| * 1d6b6c3 feat: add another feature
|/
* 1a6b6c3 Merge pull request #19 from author_name@branch_name_bis
|\
| * 8a6b6ef fix: a bug
|/
* 5b6c8c9 Merge pull request #20 from author_name@branch_name_ter
|\
| * 9a727c3 feat: add a feature
...
```

When a branch is too hard to rebase, we can consider squashing its commits to make it simpler.

A guide for Git history that we got inspired from: https://delicious-insights.com/en/posts/getting-solid-at-git-rebase-vs-merge/

## Calling for review

When a pull request is done by its author, it means it is ready for reviewing. We should review each pull request by at least one more person, in order to:

- decrease the risk of introducing bugs or unclean code
- share knowledge and good practices

We post the link to the pull request on Discord. Then people from the team review it, and communicate with the following emojis on the Discord message:

- 👀 to mean that I am looking at it
- ↩️ to mean that I made some comments
- ✅ to mean that this is approved
- 🟣 to mean that this is merged!

We can engage in discussions for code changes, especially on the pull request page on GitHub.

## CI

The CI should be green before merging a pull request. In the CI, we try to have a good coverage of the code with tests, as well as a linter and formatter to check the code style. We also of course compile the Coq proofs if there are some.
