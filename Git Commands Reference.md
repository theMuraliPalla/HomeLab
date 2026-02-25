# Git Commands Reference

Complete reference for Git version control commands.

---

## Setup & Configuration
- `git config --global user.name "Your Name"` - Set your username
- `git config --global user.email "email@example.com"` - Set your email

## Repository Initialization
- `git init` - Initialize a new Git repository in current directory
- `git clone <url>` - Clone a remote repository to your local machine

## Basic Workflow
- `git status` - Show current branch and modified files
- `git add <file>` - Stage specific file for commit
- `git add .` - Stage all changed files
- `git commit -m "message"` - Commit staged changes with a message
- `git push` - Push commits to remote repository
- `git pull` - Fetch and merge changes from remote repository

## Branching
- `git branch` - List all local branches
- `git branch <name>` - Create new branch
- `git checkout <branch>` - Switch to specified branch
- `git checkout -b <branch>` - Create and switch to new branch
- `git merge <branch>` - Merge specified branch into current branch
- `git branch -d <branch>` - Delete a branch

## Viewing History
- `git log` - Show commit history
- `git log --oneline` - Show condensed commit history
- `git diff` - Show unstaged changes
- `git diff --staged` - Show staged changes

## Undoing Changes
- `git reset <file>` - Unstage a file
- `git reset --hard` - Discard all local changes
- `git revert <commit>` - Create new commit that undoes specified commit
- `git checkout -- <file>` - Discard changes in working directory

## Remote Operations
- `git remote -v` - List remote repositories
- `git remote add origin <url>` - Add a remote repository
- `git fetch` - Download changes without merging
- `git push -u origin <branch>` - Push branch and set upstream

---

**Last Updated:** February 25, 2026
