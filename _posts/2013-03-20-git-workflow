---
layout: post
title: My new favorite Git workflow
published: false
---

## {{ page.title }}

I've been working on a long-lived feature branch for a project at work for a couple of months now. When the time came to finally merge back into our mainline branch, I had nearly 50 commits on hand - mostly small commits. I'm a big fan of SCM cleanliness and isolation of commits to a single logical change, so I wasn't too keen on simply merging all these commits as-is or doing a big ugly squash.

What I ended doing was what I like to think of as a "patch merge".

* I did main feature work on a feature branch
* When it came time to start merging back to mainline, I created an integration branch
* Clean up code/tests, keep rebasing from mainline until finished
* Once integration is ready, do a no-commit squash to mainline
* git-patch specific changes into a smaller number of nice self-contained commits

Or in git-ese

```
# On develop
git checkout -b my-feature

# Do some work on feature
git checkout -b integration
git rebase develop
# Fix conflicts, tests, etc

git checkout develop
git merge --squash --no-commit integration

# Create nice logically self-contained commits from the results of merge
git add -p
```
