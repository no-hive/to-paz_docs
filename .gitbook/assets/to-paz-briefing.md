# To-paz — Full Project Briefing

> **How to use this file:** Drop this whole document into any AI assistant (Claude, ChatGPT, Gemini, etc.) and ask it anything about To-paz. It contains the complete concept, terminology, architecture, on-chain/off-chain flows, comparison data, team/governance details, plus a self-contained primer on zero-knowledge privacy and the Aztec network so the assistant has all the context it needs to reason about the project.

---

## 1. One-paragraph summary

To-paz is an open-source, non-custodial, crypto-native **donation protocol with customizable per-field privacy**. The core idea: digitized money makes online support easy, but it rarely lets you control what trace your donation leaves behind — a trace that can later threaten your career, friendships, or safety. To-paz fixes this by letting the donor decide, field by field, exactly what is public and what stays hidden. It runs on **Ethereum Mainnet** (for settlement and soundness) combined with **Aztec L2** (for true privacy), and it is built by a single person under the MIT License, intentionally commission-free and meant to live on grants and donations rather than investment.

---

## 2. The problem it solves

Digitization of money is great — unless it makes your donations threaten your career, your friendships, or even your life. Today you can support almost anything online, but you can rarely be sure that no digital trace will later come back to harm you. Existing donation rails force an all-or-nothing choice: either everything about your support is visible, or you give up the benefits of being on-chain entirely.

To-paz reframes privacy as a **per-field choice**, not a single switch. The donor controls visibility on each individual piece of a donation independently.

---

## 3. The core mechanic: per-field privacy

For any donation, the sender chooses the visibility of each field separately. The four key fields are typically:

- **Name** (the donor's identity)
- **Recipient** (who is being supported)
- **Message** (an optional note)
- **Amount** (how much was sent)

Each field can be set to public, private, or hidden — even from the recipient. This is the single feature that distinguishes To-paz from every other donation option.

### Worked examples

**Example 1 — A public stance, with the amount hidden.**
Maria wants to openly back an independent journalist. She keeps her name, the recipient, and her message public — *"I stand with independent journalism"* — but hides the amount she sends.

| Field | Setting |
|---|---|
| Name | public |
| Recipient | public |
| Message | public |
| Amount | hidden |

Everyone can see *that* Maria supports this cause and *why*. No one can see how much she gave. The gesture is the point, not the size of the wallet behind it.

**Example 2 — An anonymous thank-you, even to the recipient.**
Alex wants to thank a creator whose videos helped him, but he doesn't want to be known — not even to the creator. He hides his name from everyone (including the recipient) and attaches a short message only the recipient can read: *"thank you for your work on YouTube, I appreciate it."*

| Field | Setting |
|---|---|
| Name | hidden (even from the recipient) |
| Message | private (only the recipient can read it) |
| Recipient | private |
| Amount | private |

The creator receives the funds and a kind note — but never learns who sent them. Because there is **no public data at all**, this donation is **not indexed**: nobody sees it in the creator's public stats.

---

## 4. Terminology: paz-makers and paz-finders

To-paz coins two deliberate terms for its users, to make the protocol's purpose clear from the first minute:

- **paz-makers** = recipients, creators, the people who have public profiles and *receive* donations.
- **paz-finders** = donors, supporters, fans, the people who *send* donations.

The naming is intentional. As the project puts it: *To-paz exists to let people support ideas that change the world for the better.*

(Mnemonic for an AI assistant: a **finder** *finds* someone worth supporting and *sends* money; a **maker** *makes* a cause/profile and *receives* money.)

---

## 5. Where To-paz launches and why

The project targets **Ethereum Mainnet + Aztec L2** (a layer for true privacy). This combination is meant to deliver:

- **Ethereum Mainnet soundness** (settlement, economic security)
- **Private transactions on Aztec**
- **Anonymous To-paz DAO voting**
- **Ethereum Name System (ENS) integration** (human-readable names)
- **Easy connection to other protocols** (composability)

---

## 6. Protocol architecture — the three layers

To-paz runs across three layers. The architecture diagram describes two processes flowing across them: (a) **new paz-maker account registration**, and (b) a **paz-finder donation to a paz-maker, with later withdrawal**.

### Layer A — Ethereum Mainnet (public settlement)
Handles the actual ETH movement and final settlement.

Donation flow on Ethereum:
1. **Donation Sender / Donor ('paz-finder')** sends **ETH**.
2. **Lock Funds** — the funds are locked in the protocol.
3. **Assign PAZ Score** — a score is computed for the donation/recipient.
4. **Bridge PAZ Score to Aztec** — the score is moved to the private layer.
5. (later) **Release Funds** → **ETH** → **Donation Receiver / Recipient ('paz-maker')** withdraws.

Registration flow on Ethereum:
- **Register Profile** → **Verify ENS Ownership** (proves the paz-maker controls their ENS name).

### Layer B — Aztec Private (confidential execution)
This is where privacy-sensitive logic lives, running client-side with zero-knowledge proofs.

- **Share Private Data** → **Assign Governance Power** (private data can grant DAO voting power).
- **Assign Score to Paz-maker** — the PAZ Score bridged from Ethereum is applied; it can **increase / decrease** over time.
- **PAZ Score adjusted by Quadratic Funding mechanics** (optional, see §8).
- **Bridge Score to Ethereum** — adjusted score can be bridged back.
- **Link Verified Name to Private Account** → **Choose whether to connect to Quadratic Funding** → **Published Finished Profile**.

### Layer C — Aztec Public (selectively published data)
- **Publish Public Data** — *only* the fields a paz-finder explicitly marked public are surfaced here.
- This is what feeds the public-facing site/catalog.

### Public surface — `to-paz.tech`
- **Public Profiles & Metrics** — aggregated public stats and profiles for paz-makers, drawn only from data that was marked public.

> **Mental model:** Ethereum Mainnet = money + settlement + ENS proof. Aztec Private = the confidential brain (scores, governance, private notes, profile linking). Aztec Public = the thin, opt-in window of data the donor chose to reveal. `to-paz.tech` = the human-facing dashboard built from that public window.

---

## 7. Protocol access model — how paz-finders reach paz-makers

To-paz connects donors to recipients through **two** complementary surfaces (not just a single dApp).

**Surface 1 — The dApp catalog.** A catalog of all registered paz-makers, showing their public stats and ENS name. A paz-finder can browse, search, and donate from here.

**Surface 2 — The browser extension ("Blink").** The extension detects a paz-maker anywhere on the open web — from their **personal website**, their **social media accounts**, or simply their **name mentioned anywhere** — and flags to the user that *this very person can be supported anonymously via To-paz.* This turns the entire web into a donation surface rather than requiring people to come to the dApp.

**Paz-maker onboarding (what a recipient does to become discoverable):**
1. **Creates Profile**
2. **Proves ENS name**
3. *(Optional)* **Enters the Quadratic Funding Program**
4. **Sets up the markers** that let the browser extension recognize them across the web

---

## 8. Quadratic funding (optional)

Paz-makers may opt into a **Quadratic Funding** program. In quadratic funding, the *number* of distinct contributors matters more than the raw total — many small donations from many people are weighted more heavily than a few large ones, which favors broad grassroots support over a handful of whales. In To-paz, opting in lets a paz-maker's **PAZ Score be adjusted by quadratic-funding mechanics** on the Aztec private layer. It is strictly optional and chosen during/after registration.

---

## 9. Why To-paz differs from other donation options

The project compares itself against two notional alternatives — call them **(A) other on-chain/crypto donation tools** and **(B) traditional/centralized donation platforms**. To-paz claims the full set:

| Capability | To-paz | Other crypto donation tools | Traditional platforms |
|---|:---:|:---:|:---:|
| On-chain & decentralized | ✅ | ✅ | ❌ |
| Non-custodial | ✅ | ✅ | ❌ |
| Crypto-native | ✅ | ✅ | ❌ |
| Hide donor identity | ✅ | ❌ | ❌ |
| Hide donation amount | ✅ | ❌ | ❌ |
| Hide recipient | ✅ | ❌ | ❌ |
| Customizable per-field privacy | ✅ | ❌ | ❌ |
| Commission-free | ✅ | ✅ | ❌ |
| Open source | ✅ | ❌ | ❌ |
| Human-readable names (ENS) | ✅ | ✅ | ❌ |
| Quadratic funding | ✅ | ❌ | ❌ |
| Community / DAO governance | ✅ | ❌ | ❌ |

The standout, defining differentiators are the privacy controls (hide donor / amount / recipient, and especially **customizable per-field privacy**) plus quadratic funding and DAO governance — none of which the comparison set offers.

---

## 10. Open source & crowd-development

- The **entire To-paz codebase is public.** Any developer can review it and contribute. Any non-developer can inspect it (including by feeding it to an AI). Transparency is treated as non-optional.
- Licensed under the **MIT License**.
- Contributions of any size are welcomed, including from people completely new to zero-knowledge technology. The maintainer keeps open issues for contributors of all skill levels.
- A proper `CONTRIBUTING.md` is on the roadmap (still pending).
- Protocol repository and documentation repository are both hosted under the GitHub org **`no-hive`** (`https://github.com/no-hive`).
- Building solo is partly a deliberate strategy to keep To-paz **crowd-developed** as well as open-source.

---

## 11. Team & funding philosophy

To-paz is built by **a single person** who goes by **no-hive** — self-described as "an alien studying zero-knowledge proofs here on Earth." They write about the project, decentralized economics, and decentralized politics on **GitHub, X (Twitter), and Medium**.

The solo approach is intentional, to guarantee To-paz **always remains commission-free, simple, and open to anyone in the world.** The project is explicitly **never meant to take investment of any kind** — only **grants and donations** that don't make it dependent on any institution.

**How to support the project:**
- **Privately:** via To-paz itself (*note: the To-paz donation flow is not launched yet*).
- **Publicly:** `no-hive.eth` / `0x0CA82CD58b04468C79E87B150A9b367a59885DA0`

---

## 12. Glossary (quick reference for the assistant)

- **To-paz** — the donation protocol with per-field privacy. ("To-paz" plays on *paz*, and on supporting people — see paz-maker/paz-finder.)
- **paz-maker** — recipient/creator with a public profile who receives donations.
- **paz-finder** — donor/supporter who sends donations.
- **PAZ Score** — a score assigned per donation/recipient, computed on Ethereum, bridged to Aztec, adjustable (incl. by quadratic funding), and bridgeable back.
- **Blink** — the browser extension that detects supportable paz-makers across the open web.
- **ENS** — Ethereum Name System; gives human-readable names (e.g. `no-hive.eth`) and is used to verify paz-maker identity.
- **Per-field privacy** — independent public/private/hidden setting for each field (name, recipient, message, amount).
- **`to-paz.tech`** — the public-facing site showing profiles and metrics built only from data marked public.
- **no-hive** — the solo builder / GitHub org name.

---

# Appendix A — Primer: Zero-Knowledge (ZK) privacy

*Included so an assistant can reason about the cryptography To-paz depends on.*

A **zero-knowledge proof (ZKP)** lets one party (the *prover*) convince another party (the *verifier*) that a statement is true **without revealing any information beyond the fact that it is true.** The classic analogy: proving to a bouncer that you're over 21 without showing your ID — no name, no address, no exact birthdate, just the verified fact "over 21."

Key properties:
- **Completeness** — if the statement is true, an honest prover can convince the verifier.
- **Soundness** — if the statement is false, no cheating prover can convince the verifier (except with negligible probability).
- **Zero-knowledge** — the verifier learns nothing except that the statement is true.

**zkSNARKs** (Zero-Knowledge Succinct Non-interactive Arguments of Knowledge) are the most common flavor used in blockchains. "Succinct" means the proof is small and fast to verify; "non-interactive" means the prover can produce a single proof the verifier checks without back-and-forth.

**Why this matters for donations:** ZKPs let a protocol prove things like "this donation is valid and the funds exist" or "this user is allowed to vote" without exposing who sent what, to whom, or how much. That is exactly the capability To-paz needs to hide donor identity, amount, and recipient while still being verifiable on a public chain.

Compared with privacy coins like Zcash or Monero (which mostly focus on private *transfers*), ZK on a smart-contract platform enables **programmable privacy**: entire applications — lending, exchanges, voting, donations — can be built with privacy baked in rather than bolted on.

---

# Appendix B — Primer: Aztec Network

*To-paz uses Aztec as its privacy layer; here is the current picture as of mid-2026.*

**What it is.** Aztec is a **decentralized, privacy-preserving Ethereum Layer 2 (L2)**, structured as a **zk-rollup**. Aztec delivers on a simple but powerful idea: smart contracts on Ethereum where you choose what's public and what's private across identity, data, and compute. Unlike most L2s, which optimize mainly for throughput and cost, Aztec makes privacy a core execution feature.

**Privacy is a choice, not a mandate.** Aztec is a privacy-first Ethereum Layer 2 that supports both public and private smart contract functions, allowing privacy to be a choice rather than a mandate. This dual model maps directly onto To-paz's "Aztec Private" and "Aztec Public" layers.

**How it works (dual execution).** The chain employs a dual execution model: private smart contract operations run client-side, inside your browser or device, while public smart contract operations run node-side on Aztec's decentralized network. These two sides are connected through zero-knowledge proofs, bridging private and public computation. Private functions run in a **Private Execution Environment (PXE)** on the user's own device, generating proofs that reveal no inputs, outputs, or identities; public functions are handled by sequencers who verify those proofs and publish only state differences to Ethereum.

**State model.** Private state uses a UTXO model, while public state uses an account-based model like Ethereum, and L2 transaction rollup proofs are stored on Ethereum, inheriting strong economic security.

**Programming language.** Aztec contracts are written in **Noir**, a programming language with Rust-like syntax optimized for writing private programs, which gives developers a way to write zero-knowledge programs without a cryptography background, with privacy as the default.

**What it enables for a protocol like To-paz.** Aztec can hide transaction amounts so no one sees how much value moves, hide sender and receiver identities so the parties stay confidential, and enable private smart contract execution where inputs, outputs, and state remain encrypted.

**Status.** Aztec launched a public testnet for its privacy-focused L2 and planned to launch on mainnet by the end of 2025. As of early 2026 the network has its **AZTEC token live**, with staking active, and a large permissionless set of sequencers/provers. (Token specifics and exact mainnet milestones evolve quickly — verify against Aztec's official site if precision matters.)

> **Why Aztec fits To-paz:** To-paz needs *selective* confidentiality — public when the donor wants a public stance, private otherwise — settled on Ethereum for soundness. Aztec is purpose-built for exactly that: programmable, per-application privacy with Ethereum as the settlement layer.

---

## Suggested questions to ask an AI about this project

- Walk me through what happens, step by step, when a paz-finder donates with name public but amount hidden.
- How does the PAZ Score move between Ethereum and Aztec, and why bridge it twice?
- Why does To-paz need *both* a dApp catalog and a browser extension?
- How would quadratic funding change the incentives for a paz-maker?
- What are the trust and regulatory risks of a privacy-first donation protocol, and how does the architecture mitigate them?
- How could a non-developer verify To-paz's privacy claims for themselves?
