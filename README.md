# ETHGlobal2026OpenAgent

This repository holds our **ETHGlobal 2026** build: the product, related code repos, a running task list, a work log, target prizes, team, and use-of-AI notes.

## Project idea

**LendPay** lets a user **repay DeFi loans with USDC** across supported networks **in one workflow**, instead of juggling bridges, dApps, and per-chain steps by hand. Execution and automation run through [KeeperHub](https://app.keeperhub.com) (workflows, wallet, and follow-up in the app).

*Status:* UI prototype in progress.

## Repos

- [lendpay-app](https://github.com/NautilusOSS/lendpay-app) — LendPay UI (prototype)
- [openagent-demo1](https://github.com/NautilusOSS/openagent-demo1) — pay-to-workflow demo; **microtip**–style paid run (Base: RainbowKit, wagmi, viem; see that repo for setup and env)

## Todo

Next steps for the build. Check items off in GitHub as you finish; add or remove lines as scope changes.

- [ ] Add Wallet Connection to the UI
- [ ] End-to-end repay path exercised through [KeeperHub](https://app.keeperhub.com) (workflow + wallet)
  - [ ] User can pay for microtip workflow execution in the app
- [x] **Browser x402 (end-to-end):** full **client-side** x402 flow — 402 from the API, user pays in-wallet, retry the request with payment and complete the call (see [openagent-demo1](https://github.com/NautilusOSS/openagent-demo1) for wiring toward x402 in a Base dapp)
  - <https://basescan.org/tx/0x31de8c5ff8d66494805c11b7b0fcfde508d91aaf4a89cf06d755dbb8fa5ba946>
- [ ] Demo: recorded walkthrough or link to a live deployment for judges
- [ ] Tighten submission materials (README, repo links, prize copy)

## Target prizes

- Top 10 finalist & partner prizes
- [KeeperHub](https://app.keeperhub.com) prizes
  - Best Use of KeeperHub
  - Builder Feedback Bounty

## Hackathon log

Running notes from the build: decisions, blockers, demos, and what changed when. Newest day on top. Keep entries short; link PRs, issues, or doc sections when they exist.

### 2026-04-24 — Start

- Exploratory research on KeeperHub workflow execution for agents including:
  - Workflow creation
  - Paid workflow execution using the KeeperHub wallet
  - Dev environment setup

### 2026-04-25 — Project Ideas

- Consider project idea after exploratory research

### 2026-04-26 — Kickoff UI (prototype) + Project Idea

- Finalize project idea: **LendPay** (see [Project idea](#project-idea))
- Build UI prototype for LendPay

## Team

- [temptemp3](https://github.com/temptemp3) — Lead developer

## Use of AI

How AI helped on this project; we update this as the build evolves.

**Tools**

- [ChatGPT](https://chatgpt.com) — project naming brainstorm, early UI spec notes, logo and branding exploration
- [Lovable](https://lovable.dev) — UI prototype
- [Cursor](https://cursor.com) — coding assistance, workflow generation via KeeperHub MCP

**Verified by hand**

- Application logic, on-chain calls, product decisions
- Workflow changes and follow-up in [KeeperHub](https://app.keeperhub.com)
