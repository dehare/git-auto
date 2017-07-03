# Git auto brancher

Automated branch creator aimed at issue trackers - asserting 'Git Flow'

## Basics
Issue trackers generally use prefixes to their projects to ease development.
E.G. AcmeCatLauncher = ACL, PancakeBossJester = PBJ.

Git-auto will automatically add this prefix to your branches - by configuration.

## Why?
Because creating branches sometimes just isn't fast enough with your favorite IDE, let alone Git CLI.
Think of the following situation:

Jamie is working on a hotfix for 'Epic WebApp'. After editing 15 files he discovers he's still on his previous issue's branch. Now Jamie has to go back into git and stash his changes, create his branch and re-apply the stash he just made. Now, what was the project prefix again?

Git-auto provides the solution! Simply typing `git-auto -h 676` and EA-676* is automatically created with all changes made, ready to be committed. Simply adding the argument `-p <commit message>` would even commit and push the changes made.


## Options

__Branching options__

| Option  | Meaning   | Parent branch | Arguments | Status |
|---------|-----------|---------------|-----------|--------|
| -f      | _feature_ | develop       | name      | Done   |
| -h      | hotfix    | master        | name      | Done   |
| -r      | release   | develop       |           | Done   |
| -t      | tag       | master        |           | WIP    |
| -b      | branch    | -             | name      | Done   |
| --patch | patch     | develop       | name      | WIP    |

__Default__: Create feature

Supplying `-b <name>` will create a separate branch. Temporarily setting a custom prefix is no problem.

__Other options__

| Option    | Meaning                                  | Arguments | Status  |
|-----------|------------------------------------------|-----------|---------|
| -p        | commit & push changes with supplied msg  | message   | Done    |
| --dirty   | don't pull changes before applying stash | -         | Done    |
| --verbose | print debug messages                     | -         | Done    |
| --config  | reconfigure project prefix               | prefix    | Done    |

## What it doesn't do
Solve merge conflicts. Well, sorry, I'm not a wizard.

Pushing changes to a non-existing remote branch is not supported (yet).

## Technical details
__Requirements__: Bash, GIT (+ GIT Flow), write access to $HOME/.config/git-auto.conf (file)

## Milestones
 - [x] Branch creation
 - [x] Automatic checkout & pull before feature/hotfix
 - [x] Reconfiguration of active project
 - [ ] Automated tagging. __Status__: finds latest tag and shows incremented version. Work in progress.
 - [ ] Creating patches. __Status__: Just creates a new branch `patch/<name>`
 - [ ] Creating releases by setting version numbers. __Status__: Just creates a new branch `release/<name>`.
