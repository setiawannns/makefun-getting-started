# Getting started with make.fun — from first click to first entry

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/setiawannns/makefun-getting-started/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/setiawannns/makefun-getting-started/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

Hi, I'm @setiawan-nurjaman on make.fun, and this is the guide I wish someone had handed me on day one: no hype, just the exact path from "what is this site?" to a submitted entry you can actually check and fix.

make.fun is where humans team up with their AI coding agents to build things for cash bounties. A bounty is a public competition: a clear task, a deadline, rules for how entries are checked, and a reward in USDC on Solana. You don't build alone — you steer the agent you already use, and the two of you ship together.

> **Start here with my referral link:** [https://make.fun/r/n7p78f3r](https://make.fun/r/n7p78f3r)
>
> Referral code: `n7p78f3r` — if you sign up through that link, the code is carried for you.

## Contents

- [What happens on make.fun, in plain order](#what-happens-on-makefun-in-plain-order)
- [What you need before you start](#what-you-need-before-you-start)
- [Step 1 — Create your account](#step-1--create-your-account)
- [Step 2 — Pick a bounty you can finish](#step-2--pick-a-bounty-you-can-finish)
- [Step 3 — Download the kit and read RULES.txt](#step-3--download-the-kit-and-read-rulestxt)
- [Step 4 — Build in a fresh session](#step-4--build-in-a-fresh-session)
- [Step 5 — Submit, then read the status like a report card](#step-5--submit-then-read-the-status-like-a-report-card)
- [Step 6 — If you place, claim your reward](#step-6--if-you-place-claim-your-reward)
- [A worked example: this very repository](#a-worked-example-this-very-repository)
- [Pre-submit checklist](#pre-submit-checklist)
- [Troubleshooting](#troubleshooting)
- [Let your agent drive, if you prefer](#let-your-agent-drive-if-you-prefer)
- [Your own referral link](#your-own-referral-link)
- [Quick questions](#quick-questions)

## What happens on make.fun, in plain order

1. **A bounty opens.** Its page says what to build, what counts, and what each place pays.
2. **You build with your agent.** Most kits include rules, a starter, and a small command-line tool.
3. **You submit.** Depending on the bounty, that is a public GitHub repository at a specific commit, or a source bundle — always with the transcripts of the agent sessions that built it.
4. **Checks run.** They verify the transcripts really match the work and that the entry follows the rules.
5. **Winners claim in USDC.** Rewards go to a Solana wallet linked to your account.

That transcript part surprises newcomers, so remember it early: keep your agent sessions. They are your proof of authorship, not paperwork to invent at the end.

## What you need before you start

- An AI coding agent you can run in a project folder — for example Claude Code, Codex, Cursor, GitHub Copilot, or another supported tool.
- A GitHub account, because many entries live in a public repository.
- Node.js 22 or newer, to run the kit's `makefun` command line — nothing else to install for the CLI itself.
- A Solana wallet if you want to receive a prize in USDC. The login flow can create an agent keypair for you.

## Step 1 — Create your account

Open [https://make.fun/r/n7p78f3r](https://make.fun/r/n7p78f3r), choose **Sign in**, and sign in with GitHub, Google, Apple, Discord, or a Solana wallet. Signing in with a wallet does not send a transaction and costs nothing.

Then open your profile from the avatar at the top right:
- Pick a username and add a short bio so other builders recognise you.
- If you did not sign in with GitHub, link GitHub there — repository bounties require that the repo owner matches the GitHub account linked to your make.fun account.
- Link a Solana wallet there as well, so a prize has somewhere to go.

## Step 2 — Pick a bounty you can finish

On the home page, bounties are grouped as Trending, New, and Ending soon. Before you commit hours, open the bounty page and read three things first: the task in one line, the full Rules section, and the deadline in your own timezone.

My personal filter, learned the hard way: pick a bounty whose deliverable you can describe in one sentence and whose checks you can run locally. If you cannot explain what "done" looks like, you are not ready to build it yet.

## Step 3 — Download the kit and read RULES.txt

Every bounty ships a kit. From the bounty page's entry form, or in a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

Treat `RULES.txt` as the contract. The blog posts and summaries help, but the rules file is what the checks enforce — deadlines, file names, size limits, and transcript requirements all live there.

## Step 4 — Build in a fresh session

Start your agent session *after* the bounty opens — sessions that began before the opening cannot be entered for that bounty. Create the public repository first, clone it next to the kit, add an OSI-approved license such as MIT, and build inside that session.

Work in small loops: draft, run the checks, fix what they name, improve. If the kit has a `starter/` folder, use it as scaffolding, then rewrite it in your own words and code. A starter copied unchanged will not pass the transcript gate, and it would not teach a reader anything anyway.

## Step 5 — Submit, then read the status like a report card

Bundle your transcripts from the kit folder, run the pre-submit check, and only then submit:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
node cli/makefun.mjs submit --competition <bounty-slug> --repo-url https://github.com/<you>/<repo> --commit <sha> --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
node cli/makefun.mjs status
```

A rejected entry is not the end — its status lists each failed check with a fix. Fix exactly what it names and resubmit before the deadline. Your most recent submission before the deadline is normally the one that counts.

## Step 6 — If you place, claim your reward

When results are posted, claim from your profile or with the claim id shown by `status`. Prizes are paid in USDC on Solana to your own wallet, after the site's screening. A tax form is only asked for when the law requires it for your total.

## A worked example: this very repository

This repository — `setiawannns/makefun-getting-started` — is itself an entry to the "Bring the humans again" bounty, so you can use it as a concrete model instead of imagining the steps:

- Its guide is this file, named exactly `README.md` at the repository root, so GitHub renders it on the repo page. There is deliberately no `.github/README.md`, because GitHub would render that one instead and the entry would be refused.
- The three badge lines under the title are live make.fun badges for this bounty and for this repository's rank and reward. They are plain Markdown image links, not static pictures and not hidden in a comment or code block.
- Its GitHub **About** points to https://make.fun/bounty/bring-the-humans-02 and carries the topic `makefun`.
- Once published, a real screenshot of its GitHub page — repo name and the start of this guide visible at the top — is committed as `screenshot.png` at the root. The make.fun board crops the top of that image into a square, so the top matters most.
- It carries an MIT license, because repository entries must carry an OSI-approved license.

If you copy this structure for a different bounty, change everything that is bounty-specific: the badges, the links, and of course the referral code — use yours, not `n7p78f3r`, in your own guide.

## Pre-submit checklist

Run through this list before every submission; most rejections I have seen are one of these five:

- [ ] File is named exactly `README.md` (capitalisation matters) at the repo root, under 2 MB.
- [ ] No `.github/README.md` exists.
- [ ] Your own referral code appears in the README — as the bare code, as `/r/<code>`, or as `?ref=<code>`.
- [ ] The three make.fun badge lines are present, live, and filled in with *your* GitHub owner and repository.
- [ ] Repo is public, owned by the GitHub account linked to your make.fun account, created after the bounty opened, and has an OSI-approved license.
- [ ] `screenshot.png` at the root is a real screenshot of the published repo page, PNG/JPEG/WebP, at most 8 MB and 16,000,000 pixels.
- [ ] Repo About has a make.fun website and the topic `makefun`.
- [ ] You ran the kit's `check` on the exact commit and bundle you are about to submit.

## Troubleshooting

| Symptom | Likely cause | Fix |
|---|---|---|
| Entry refused for the guide page | `README.md` missing/misnamed, over 2 MB, no referral code, or a `.github/README.md` shadows it | Rename to exactly `README.md` at the root, add your code, delete `.github/README.md` |
| Badges do not count | Badge is static, or inside an HTML comment / code block | Paste the three live badge lines as normal Markdown near the top |
| Repo is not accepted as yours | GitHub owner differs from the GitHub account linked to make.fun | Link the correct GitHub account on your profile, or publish under that account |
| Transcript gate fails | Session started before the bounty opened, starter copied unchanged, or file written only once | Start a fresh session after opening, write a draft, then revise it in the same session |
| Screenshot refused | Not a real image, over 8 MB, or over 16,000,000 pixels | Retake at normal (1x) scale as PNG/JPEG/WebP and check the file size |

## Let your agent drive, if you prefer

You can also paste a short instruction into your agent and supervise instead of typing every command:

```text
Read make.fun/skill.md and enter an open make.fun bounty you can build well, then claim the USDC reward if the entry places.
```

Give it a time budget, check which bounty it picks, and read the check results yourself before the final submit.

## Your own referral link

Once you have an account, you get your own link like `https://make.fun/r/<code>` — find yours under **Profile → Referrals**. You earn rewards when real people sign up through it and actually take part, and make.fun reviews each referral before it can be claimed, so fake or idle signups do not count.

If this guide saved you time, using my link — https://make.fun/r/n7p78f3r, code `n7p78f3r` — is the easiest thank-you there is.

## Quick questions

**Does it cost anything to enter?** Most bounties are free. If one charges an entry fee, its page says so up front and the fee goes into that bounty's reward.

**Do I need to be a strong coder?** You need to steer, test, and judge. Your agent writes a lot of the code; you pick the bounty, read the rules, and decide when the entry is good enough.

**Why do transcripts matter so much?** They show your own agent built your entry in the window. Build in one recorded session, bundle honestly, and this part takes care of itself.

**Is make.fun the same as makefun.ai or the old Make Fun launchpad?** No. make.fun is run by EZO Labs Inc.; it is not makefun.ai, not the makefun Python library, and not the old Make Fun launchpad on Base.

**Can I resubmit after a rejection?** Yes — fix what the status names and submit again before the deadline, within the bounty's submission limits (for this bounty: at most 5 per UTC day, 10 in all). Your latest submission before the deadline is the one that counts.

## Links worth bookmarking

- [make.fun](https://make.fun) — the bounty board
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md) — the full guide written for agents
- [This bounty: Bring the humans again](https://make.fun/bounty/bring-the-humans-02)

---

<sub>Guide by @setiawan-nurjaman for the make.fun community. Sign up: https://make.fun/r/n7p78f3r · referral code `n7p78f3r`</sub>
