---
icon: map
---

# Roadmap

I work solo (more about it here - [team.md](team.md "mention")) so I prefer to have not a date-detailed roadmap but the pack of ideas I want to implement one day. Here it is, structured in the best possible way:

<details>

<summary><mark style="color:$info;">#DOCUMENTATION -</mark> <mark style="color:$success;">complete docs and website</mark> <mark style="color:$primary;">- will be done by May 2026</mark> </summary>

To begin with, I wanted to complete the entry point of my project early on - partly to motivate myself, and partly to expand my vision of what it could eventually become. Consider these early version docs as a form of brainstorming.

</details>

<details>

<summary><mark style="color:$info;">#CODE -</mark> <mark style="color:$success;">basic Noir smart contract</mark> <mark style="color:$primary;">- will be done by July 2026</mark></summary>

My first goal after completing the docs and website is definitely the basic smart contract. I want to write it in Noir and prepare it for deployment on Aztec.

The contract will work as follows:

1. Users can register themselves as a paz-maker, which stores their account address under a unique name.
2. Anyone can then send a transaction to the contract using that name, and once the name is resolved, the funds are directed to the corresponding address.

At the point of transaction creation, the balance between privacy and publicity is decided. Users will be able to choose special visibility flags for the message, amount, sender address, and receiver address. Once the transaction is sent, all selected public data will be published so that off-chain listening nodes can capture it and store it for display in the dApp.

</details>

<details>

<summary><mark style="color:$info;">#COMMUNITY</mark> <mark style="color:$info;">#OPEN-SOURCE -</mark> <mark style="color:$success;">CONTRIBUTE.md</mark> <mark style="color:$primary;">- will be done by July 2026</mark></summary>

`CONTRIBUTE.md` will be the first step toward making this project community-built. It will lay the foundation for anyone to join the project, solve existing issues, and create new issues in the right way.

At this stage, I also plan to write several AI prompts that can be used to generate properly structured issue descriptions and contribution requests.

</details>

<details>

<summary><mark style="color:$info;">#CODE #DAPP -</mark> <mark style="color:$success;">simple UI for direct donations</mark></summary>

“Simple UI” refers to the MVP version of the dApp. My goal is to build the lightest possible interface for interacting with the protocol, and then expand it with extensions around a modular structure. This approach will make it possible for alternative interfaces or community-built add-ons to be developed on top of it as well.

</details>

<details>

<summary><mark style="color:$info;">#CODE #DAPP -</mark> <mark style="color:$success;">catalog of paz-makers broken into categories</mark></summary>

Catalogization and a lightweight search engine would fit the dApp perfectly. I do not plan to include them in the MVP, but they are definitely needed.&#x20;

Once this milestone is reached, users will be able to discover all paz-makers through the website, read their bios, view their donation statistics (only public parts go to stats), and explore similar paz-makers based on shared categories.

</details>

<details>

<summary><mark style="color:$info;">#COMMUNITY #OPEN-SOURCE -</mark> <mark style="color:$success;">friendly GitHub issues</mark> <mark style="color:$primary;">- will be done by August 2026</mark></summary>

“friendly GitHub issues” will be a collection of tasks that I could probably solve myself, but intentionally leave open for people who want to try contributing to open source.

</details>

<details>

<summary><mark style="color:$info;">#CODE  #PROTOCOL #DAPP -</mark> <mark style="color:$success;">extension for crowd-funding</mark></summary>

It's one of the first add-ons that I would love to see as a part of to-paz. It will bring traditional crowd-funding mechanism: it means that you can use private donations to support not the person but the goal + receive your donation back if the goal is not reached by certain date.

</details>

