---
icon: street-view
layout:
  width: default
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
---

# Concept

### What is To-paz?

Digitization of money is great, unless it makes your donations threaten your career, your friendships, or even your life. These days you can support almost anything online, but you can rarely be sure that no digital trace will later come back to harm you. [Read why it's important to keep your donations private.](#user-content-fn-1)[^1]

<mark style="color:blue;">To-paz is a donation protocol with customizable per-field privacy</mark>: now you decide where your support visibility starts and where it ends. Check the example below to understand the core idea:&#x20;

<details>

<summary>EXAMPLE</summary>

**Example 1 - A public stance, with the amount hidden.**

Maria wants to openly back an independent journalist. She keeps her name, the recipient, and her message public - _"I stand with independent journalism"_ - but hides the amount she sends.

* Name → public
* Recipient → public
* Message → public
* Amount → hidden

Everyone can see _that_ Maria supports this cause and _why_. No one can see how much she gave. The gesture is the point, not the size of the wallet behind it.

***

**Example 2 - An anonymous thank-you, even to the recipient.**

Alex wants to thank a creator whose videos helped him, but he doesn't want to be known - not even to the creator. He hides his name from everyone, including the recipient, and attaches a short message only the recipient can read: _"thank you for your work on YouTube, I appreciate it."_

* Name → hidden (even from the recipient)
* Message → private (only the recipient can read it)
* Recipient → private
* Amount → private

The creator receives the funds and a kind note - but never learns who sent them.

Moreover, as there is no public data at all, this donation is not indexed: nobody sees it in creators stats.

</details>

You can also download the file and throw it to your favorite AI to chat about To-paz:&#x20;

{% file src=".gitbook/assets/Frame 5(2).png" %}

Once you understand what it's all about, things just get interesting. Let's start!&#x20;

### Where To-paz will be launched?

The project is going to be launched on Ethereum Mainnet + on Aztec L2 (layer for true privacy). Such a combination will help to deliver:

* Ethereum Mainnet soundness;
* private transactions on Aztec;
* anonymous To-paz DAO voting; <mark style="color:$info;"><—</mark> [<mark style="color:$info;">what to vote for?</mark>](#user-content-fn-1)[^1]
* Ethereum Name System (ENS) integration;
* Easy connection to other protocols. <mark style="color:$info;"><—</mark> [<mark style="color:$info;">where it can be used?</mark>](#user-content-fn-1)[^1]

### Protocol Architecture

To-paz runs across three layers:

<figure><img src=".gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

Above you can see the flow of two processes: new paz-maker account registration, and paz-finder donation to paz-maker with later withdrawal.

<details>

<summary>Who are <mark style="color:blue;"><strong>paz-makers</strong></mark> and <mark style="color:blue;"><strong>paz-finders</strong></mark>?</summary>

To describe its core idea precisely, To-paz uses the following terms for its users:

* <mark style="color:blue;">**paz-makers**</mark> = recipients, creators, those who have public profiles and receive the donations.
* <mark style="color:blue;">**paz-finders**</mark> = donors, supporters, fans, those who send donations.

It may seem strange to coin special words for a single protocol, but we do it to make one thing clear from the very first minute: <mark style="color:blue;">To-paz exists to let people support ideas that change the world for the better.</mark>

</details>

### Protocol Access Model

Read how we connect paz-finders to paz-makers (SPOILER: not only via DApp):

<figure><img src=".gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

The dApp catalog of all registered paz-makers (public stats + ENS name), or the browser extension, which detects a paz-maker's website, socials or name anywhere on the web and flags that they can be supported anonymously via To-paz.

### Why To-paz differs from other donation options?

| On-chain & decentralized       |  ✅  |  ✅  |  ❌  |
| ------------------------------ | :-: | :-: | :-: |
| Non-custodial                  |  ✅  |  ✅  |  ❌  |
| Crypto-native                  |  ✅  |  ✅  |  ❌  |
| Hide donor identity            |  ✅  |  ❌  |  ❌  |
| Hide donation amount           |  ✅  |  ❌  |  ❌  |
| Hide recipient                 |  ✅  |  ❌  |  ❌  |
| Customizable per-field privacy |  ✅  |  ❌  |  ❌  |
| Commission-free                |  ✅  |  ✅  |  ❌  |
| Open source                    |  ✅  |  ❌  |  ❌  |
| Human-readable names (ENS)     |  ✅  |  ✅  |  ❌  |
| Quadratic funding              |  ✅  |  ❌  |  ❌  |
| Community / DAO governance     |  ✅  |  ❌  |  ❌  |

[^1]: 
