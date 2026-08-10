# Recoil is deprecated. Should we migrate to Jotai, Redux Toolkit, or use both?

> A practical React architecture case study about replacing Recoil without turning a dependency migration into an uncontrolled rewrite

![Promotion and Couponing team mascot](./images/promotion-and-couponing-logo.png)

## About the article

Recoil had to be replaced, but choosing its successor was only part of the problem. The more important question was: **who should own each kind of state?**

This article follows a real architecture discussion around a React application using Apollo Client, React Hook Form and Recoil. It explains why a safe one-to-one migration to Jotai is a sensible first step, and where Redux Toolkit can later provide clearer process modelling, debugging and tests.

## The decision

| State type | Recommended owner |
| --- | --- |
| Backend and cached server data | Apollo Client |
| Edited form values and validation | React Hook Form |
| Lightweight shared UI state | Jotai |
| Explicit async processes and application flows | Redux Toolkit |
| Component-only state | Local React state |
| Shareable navigation and search state | URL |

The proposed direction is intentionally hybrid:

```text
Jotai = lightweight atom layer
Redux Toolkit = explicit process and flow layer
```

## What the article covers

- why replacing Recoil is not only a library-choice problem;
- how to identify state ownership boundaries;
- why promotion data should not have three competing sources of truth;
- when boolean state becomes a hidden command;
- how coupon-job polling could evolve into an explicit Redux Toolkit flow;
- why `rerenderFilters` needs an ownership refactor rather than a library swap;
- a phased, low-risk migration plan from Recoil to Jotai and selected Redux Toolkit flows.

## Main takeaway

The first migration should be deliberately boring: remove Recoil with minimal behavioural change. Architectural improvements should follow separately, only where explicit process state provides a concrete benefit.

## Technologies and concepts

`React` · `Recoil` · `Jotai` · `Redux Toolkit` · `Apollo Client` · `React Hook Form` · `state ownership` · `polling` · `async lifecycle`

## Read the articles

The repository contains a static GitHub Pages version of the case study:

- **Part 1:** [`index.html`](./index.html) → `https://gkromkowski.github.io/recoil-jotai-redux-case-study/`
- **Part 2:** [`part2/index.html`](./part2/index.html) → `https://gkromkowski.github.io/recoil-jotai-redux-case-study/part2/`

## Author

Grzegorz Kromkowski
