+++
author = "Ekow Baah-Nyarkoh"
title = "Monorepos: what's the deal with it? 😋"
date = "2022-06-20"
description = "What monorepos are, their pros and cons"
tags = [
    "monorepos"
]
+++

## Introduction

If you're reading this, it's because you've heard about monorepos. If you're a developer, there's a good chance that the idea of having to manage several repositories is something that makes your skin crawl. After all, managing those projects can't be easy! So let's examine what monorepos they do and why people use them.

## What is a monorepo?

A monorepo is a version-controlled code repository that holds many projects. While these projects may be related, they are often logically independent and run by different teams.
Some companies host all their code in a single repository, shared among everyone. However, Monorepos can reach colossal sizes. Google, for example, is theorized to have the most significant code repository ever, with tens of hundreds of daily commits and over 80 TBs large. Other companies known to run large monorepos are Microsoft, Facebook, and Twitter.
Monorepos are sometimes called monolithic repositories, but they should not be confused with monolithic architecture, a software development practice for writing self-contained applications. An example is a Ruby on Rails monolith handling websites, API endpoints, and background jobs.

Why are people using them?

- Make it easier to work on multiple projects. Having your code in one place allows you to focus on the task without worrying about where it came from or how your code might use elsewhere. You also won't have to worry about whether your colleagues have read a particular file before because then they'll know what changes were made and what new information was added since the last time they looked at the code base---allowing them to contribute more easily with their ideas and suggestions (which is good).

- Make it easier for everyone involved in a project to find their way around when needed (or if there are any questions). Having everything stored together makes finding what someone needs easier than having everything scattered across different places on disk or, even worse, your entire hard drive! Monorepos will save both times spent searching through files looking for what one wants/needs vs just typing something out directly into Google Docs, or whatever platform may be available today."

## What problems do monorepos solve?

At first glance, the choice between monorepos and multirepos may not seem like a big deal, but it’s a decision that will profoundly influence your company’s development workflow. As for their benefits, we can list a few:

- **Visibility**: everyone can see everyone else’s code. This property leads to better collaboration and cross-team contributions — a developer in a different team, can fix a bug in your code you didn’t even know existed.
- **Simpler dependency management**: sharing dependencies is trivial. There’s little need for a package manager as all modules are hosted in the same repository.
- **Single source of truth**: one version of every dependency means no versioning conflicts and no dependency hell.
- **Consistency**: enforcing code quality standards and a unified style is more effortless when you have all your codebase in one place.
- **Shared timeline**: breaking changes in APIs or shared libraries are exposed immediately, forcing different teams to communicate ahead and join forces. Everyone is invested in keeping up with changes.
- **Atomic commits**: atomic commits make large-scale refactoring easier. A developer can update several packages or projects in a single commit.
- **Implicit CI**: [continuous integration](https://semaphoreci.com/continuous-integration) is guaranteed as all the code is already unified in one place.
- **Unified CI/CD**: you can use the same [CI/CD](https://semaphoreci.com/cicd) deployment process for every project in the repo.
- **Unified build process**: we can use a shared [build process](https://semaphoreci.com/blog/build-stage) for every application in the repo.

## What problems do monorepos cause?

As monorepos grow, we reach design limits in version control tools, build systems, and continuous integration pipelines. These problems can make a company go the multi-repo route:

- **Lousy performance**: monorepos are challenging to scale up. Commands like git blame may take unreasonably long times, IDEs begin to lag, productivity suffers, and testing the whole repo on every commit becomes infeasible.
- **Broken main/master**: a broken master affects everyone working in the monorepo. This can be seen as either disastrous or an excellent motivation to keep tests clean and up to date.
- **Learning curve**: the learning curve for new developers is steeper if the repository spans many tightly-coupled projects.
- **Large volumes of data**: monorepos can reach unwieldy volumes of data and daily commits.
- **Ownership**: maintaining ownership of files is more challenging, as systems like Git or Mercurial don’t feature built-in directory permissions.
- **Code reviews**: notifications can get very noisy. For instance, GitHub has limited notification settings that are not best suited for a snow slide of pull requests and code reviews.

## Do I need one a monorepo for my projects?

The first thing to know about monorepos is that they aren't a silver bullet. They're not replacements for exhaustive testing, continuous integration, or code design.

As you'll see in this article and the next few ones coming up on this blog, I think that monorepos can help us build better software by making our lives easier in some ways while making them harder in others. That said, are you already doing things like TDD or CI/CD? Then maybe it will be worth looking at how monorepos might fit into your current workflow!

## Takeaway:

- Monorepos are an excellent choice for large projects, but they can be challenging to manage.

- Monorepos are not a good choice for small projects; they make it harder to keep your code organized and easy to find things in the project.
