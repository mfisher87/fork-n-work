# fork-n-work

Skip all the steps to making small contributions to public software. Forks a repo, clones it to a local workspace, and changes directory to that workspace.

_This project doesn't exist. It's just an idea for now._


## Rationale

I'm tired of finding a repository I want to contribute to and having to choose between two imperfect workflows (there are of course others, but these two are the most straightforward I know of):

1. Use the GitHub GUI, instead of my usual toolset, to quickly change some text.
   This handles automatically creating a fork, branch, and opening a PR.
   Works well for _very_ small changes, but if line length, linting, testing, etc. are important, does not work.
2. Forking the repository in the GitHub UI, then cloning the fork from my namespace to my local machine, creating a branch, and working on it.
   When done, push the branch to my fork in GitHub and open a PR.

So, why not a hybrid of both?
Automatically create the fork for me, clone, and set my terminal in the correct directory to begin working.
From there, I can leverage tooling used by the repository (e.g. `pre-commit`), and use my development environment of choice.


## How it works

I have no idea. Goal is to minimize clicks and commands. In my head, it looks like:

* Take a repo URL (or `user/repo` string) at the CLI
* Hit the GitHub API to fork that repo to the user namespace.
  If a conflicting repo exists, postpend a string, maybe a sequential number, until an open name is found.
  Consider timestamping or something?
* Once forked, clone the fork to a temporary directory.
  Maybe ask the user where to clone to, and default to tempdir?
  If tempdir, caution the user that it must be re-located to avoid being potentially cleaned up.
* Tell the user where the clone is.
* Prompt the user for a branch name and create a branch?
  Default to `patch-{seq}` like GitHub does?
* Move the user's terminal to the cloned repository worktree.
* User can edit files with `vim` or `code` or `nano` or whatever,
  use repository tooling (e.g. `pre-commit`),
  execute tests or other checks (e.g. with `act`).

Is it best to implement this as an extension to `gh` CLI? Maybe prototype it as a `bash` script first.


## Is this a solved problem?

I don't know... I tried searching in various ways to try and find a tool that automated these little steps, but turned up nothing.
Maybe it's because I searched poorly. Help me out here! :)
