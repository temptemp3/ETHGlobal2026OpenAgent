# ETHGlobal2026OpenAgent

This repository holds our **ETHGlobal 2026** build: the product, related code repos, a running [Todo](#todo) list, a work log (including deferred payment-path notes by day), target prizes, team, and use-of-AI notes. **Work window:** all submission work was done **from 2026-04-24** through **before the official submission deadline** — see [Hackathon log](#hackathon-log).

## Project idea

**LendPay** lets a user **repay DeFi loans with USDC** across supported networks **in one workflow**, instead of juggling bridges, dApps, and per-chain steps by hand. Execution and automation run through [KeeperHub](https://app.keeperhub.com) (workflows, wallet, and follow-up in the app).

*Status:* UI prototype in progress.

## Repos

- [lendpay-app](https://github.com/NautilusOSS/lendpay-app) — LendPay UI (prototype)
- [lendpay-backend](https://github.com/NautilusOSS/lendpay-backend) — LendPay backend (API / server for app and x402 flows)
- [openagent-demo1](https://github.com/NautilusOSS/openagent-demo1) — pay-to-workflow demo; **microtip**–style paid run (Base: RainbowKit, wagmi, viem; see that repo for setup and env)

## Architecture

High-level flow: user and [lendpay-app](https://github.com/NautilusOSS/lendpay-app) → workflow config → x402 on Base → [lendpay-backend](https://github.com/NautilusOSS/lendpay-backend) → [KeeperHub](https://app.keeperhub.com) execution → protocols and receipts back to the UI.

```mermaid
flowchart TD
  U[User] --> UI[LendPay Web App]

  UI -->|Enter repayment target| CFG[Workflow Config]
  CFG -->|Select chain + protocol + loan| UI

  UI -->|x402 payment request| X402[x402 Payment Layer on Base]
  X402 -->|USDC payment proof| API[LendPay API]

  API --> AUTH[User / Org API Key]
  API --> PAY[Payment Verification]
  API --> WF[Workflow Builder]

  PAY -->|valid payment| WF
  WF --> KH[KeeperHub]

  KH --> EXEC[Workflow Execution Agent]

  EXEC --> AAVE[Aave / Lending Protocol]
  EXEC --> OTHER[Other DeFi Protocols]
  EXEC --> DEST[Target Chain Wallet / Contract]

  AAVE -->|Repay on behalf| LOAN[User Loan Position]
  OTHER -->|Repay / Close / Rebalance| LOAN

  API --> REFUND[Refund / Remainder Logic]
  REFUND --> U

  API --> LOGS[Execution Logs + Receipts]
  LOGS --> UI
```

## Todo

Active build tasks. Check `[x]` when done. Work deferred on the **LendPay workflow gateway** payment path (while **KeeperHub** still runs execution) is written under **2026-04-28** in the [Hackathon log](#hackathon-log), not as a separate README section.

- [ ] Demonstrate payer identity for the workflow execution
- [ ] Add Wallet Connection to the UI
- [ ] Demo: recorded walkthrough or link to a live deployment for judges
- [ ] Tighten submission materials (README, repo links, prize copy)

## Target prizes

- Top 10 finalist & partner prizes
- [KeeperHub](https://app.keeperhub.com) prizes
  - Best Use of KeeperHub
  - Builder Feedback Bounty

## Hackathon log

**Submission timing:** All work for this **ETHGlobal 2026** entry was completed **from 2026-04-24** (first log day, hackathon start) **through before the event’s official submission deadline** (per hackathon rules).

Running notes from the build: decisions, blockers, demos, and what changed when. Newest day on top. Keep entries short; link PRs, issues, or doc sections when they exist.

### 2026-04-24 — Start

- Exploratory research on KeeperHub workflow execution for agents including:
  - Workflow creation
  - Paid workflow execution using the KeeperHub wallet
  - Dev environment setup

### 2026-04-25 - 2026-04-26 — Project Ideas

- Consider project idea after exploratory research

### 2026-04-27 — Kickoff UI (prototype) + Project Idea

- Finalize project idea: **LendPay** (see [Project idea](#project-idea))
- Build UI prototype for LendPay

### 2026-04-28 — Backend, architecture, and payment path

- Linked **[lendpay-backend](https://github.com/NautilusOSS/lendpay-backend)** in [Repos](#repos) (API / x402 server alongside [lendpay-app](https://github.com/NautilusOSS/lendpay-app))
- Added [Architecture](#architecture) section with a **Mermaid** flowchart (web app → workflow config → x402 on Base → LendPay API → KeeperHub → execution → refunds / logs)
- **[Todo](#todo):** active list only — `[x]` **Browser x402** with [Base proof](https://basescan.org/tx/0x31de8c5ff8d66494805c11b7b0fcfde508d91aaf4a89cf06d755dbb8fa5ba946); open: payer identity, wallet, demo, submission
- **Deferred payment-path backlog** (recorded here instead of a separate README section): the exact **payment path** waits on the **LendPay workflow gateway**; **KeeperHub** still runs **workflow execution**. Until the gateway is clear, we are not tracking these in active Todo:
  - **End-to-end repay** through [KeeperHub](https://app.keeperhub.com) (workflow + wallet) — after gateway routes payments into runs
  - **x402 + LendPay** — **[KeeperHub](https://app.keeperhub.com) workflow fee** + **loan-repay** from the app (single 402, staged 402s, or batched—TBD). *Blocked* on **KeeperHub** (not LendPay-only); also gated on gateway
  - **x402 + LendPay (packs)** — LendPay (pack UX, optional refund rules) and KeeperHub org (list packs, org wallet for refund txs); not blocked on dynamic-402 in the call route; also gated on gateway
  - **KeeperHub workflows / packs** — workflow to demo **0.10 USDC** pack with x402; workflows or tiers **1, 2, 5, 10, 20, 50, 100 USDC**

### 2026-04-29 — Payment path and workflow gateway

## Team

- [temptemp3](https://github.com/temptemp3) — Lead developer

## Use of AI

How AI helped on this project; we update this as the build evolves.

**Tools**

- [ChatGPT](https://chatgpt.com) — project naming brainstorm, early UI spec notes, logo and branding exploration, architecture documentation
- [Lovable](https://lovable.dev) — UI prototype
- [Cursor](https://cursor.com) — coding assistance, workflow generation via KeeperHub MCP

**Verified by hand**

- Application logic, on-chain calls, product decisions
- Workflow changes and follow-up in [KeeperHub](https://app.keeperhub.com)

