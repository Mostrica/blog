+++
title = "Sustainable Funding for Mostro’s Development"
date = "2026-01-08T12:00:00Z"

[extra]
author = "catrya"
img = "/img/dev-fee.jpg"
summary = "Mostro introduces an automatic and transparent funding mechanism for its development: each Mostro instance operator automatically allocates a configurable percentage of the fees they earn to a development fund, at no additional cost to users. The entire process is publicly verifiable through events published on Nostr, aligning incentives and ensuring the long-term sustainability of the project."
+++

The development of free and decentralized software inevitably runs into an uncomfortable but unavoidable question:  
**how do you fund it without sacrificing independence, privacy, or decentralization?**

At Mostro, we chose not to dodge that question. Instead of relying on sporadic donations, sponsors, or centralized structures, we designed a system that integrates naturally into how the network already works—and sustains itself.

## The challenge of decentralized funding

Building and maintaining a peer-to-peer exchange platform like Mostro requires continuous resources: new features, bug fixes, security improvements, code audits, and documentation. Traditionally, projects like this depend on voluntary donations or external funding. The problem is that these models tend to be **unpredictable**, hard to sustain over time, or they create dependencies that run counter to the decentralized ethos.

We needed something different. A system that was:

- **Automatic**, without relying on goodwill, reminders, or fundraising campaigns  
- **Transparent**: fully auditable by anyone  
- **Fair**: without adding extra costs for end users  
- **Decentralized**: without introducing centralized points of control  

## The core idea: contribute from earnings, not from usage

The solution we implemented is conceptually simple, but technically sophisticated.

Each Mostro instance operator can configure a percentage (minimum 10%, default 30%) of the fees **they personally earn** to be automatically donated to the development fund.

### A concrete example

Let’s look at a typical trade:

- **Trade amount**: 100,000 sats  
- **Total fee**: 1,000 sats (1%, split between buyer and seller, although each instance operator defines their own fee)  
- **Configured dev fee**: 30%  
- **Contribution to development**: 300 sats  

**The key point**: those 300 sats are paid by the Mostro instance out of its own earnings—**they are not charged to the user**. The buyer still pays exactly the same 500 sats in fees, the seller pays the other 500 sats, and the instance donates 300 sats from the 1,000 it received.

## Full transparency through Nostr

A system like this only works if it can be audited without asking for permission. That’s why every contribution to the development fund automatically generates a public event on **Nostr**.

Each event includes:

- The contributed amount  
- The destination Lightning address
- The Lightning payment hash  
- The exact timestamp  
- A reference to the order that generated it  

These events are published using a specific event type (`kind 8383`), allowing anyone to reconstruct the full history of contributions and verify that the system works exactly as described.

No internal reports. No promises. **Just verifiable data.**

## A system that runs in the background

Once configured, the mechanism is entirely automatic:

1. The operator sets their percentage (between 10% and 100%)  
2. Each successful trade generates a contribution  
3. An internal scheduler processes payments every 60 seconds  
4. Events are published to Nostr  
5. If anything fails, trading continues as normal  

None of this interferes with the user experience or the exchange flow.

## Aligned incentives for everyone

This model creates benefits for all participants.

### Mostro operators
- Contribute to the development of the tool that generates their income  
- Retain full control over their contribution percentage  
- Enjoy complete transparency over their contributions  

### Users
- Pay no additional fees  
- Use a platform that continuously improves  
- Can publicly verify how the project is funded  

### The project
- Gains predictable funding  
- Aligned incentives: more usage means more funding  
- Maintains independence and transparency  

## Technical implementation with no surprises

For those who want to dive deeper, the system includes:

- Unified fee calculation across different order types  
- Asynchronous payments that do not block operations  
- Proper handling of race conditions  
- Automatic recovery of abandoned orders  
- Robust validations and well-defined timeouts  

All the code is public, part of Mostro’s main repository, and the technical documentation explains every aspect of the implementation in detail.

## More than a dev fee: a sustainability model

This system is not just a way to fund development. It is a practical demonstration that decentralized projects can be sustainable without compromising their principles.

- **No external dependencies**: funds come from within the ecosystem itself  
- **No centralized points of failure**: each operator chooses their level of contribution  
- **No cost to end users**: contributions come from earnings, not new fees  
- **Complete transparency**: all information is publicly auditable  

## Conclusion

Mostro’s dev fee system shows that economic sustainability and decentralized principles can coexist. By automating contributions and making the entire process transparent through Nostr, we created a model where the platform’s growth directly funds its own development.

Operators get a stronger tool, users keep their costs low, and the project secures the resources it needs to keep innovating. It’s a concrete example of how technology can align incentives to create sustainable value within the Bitcoin ecosystem.

## More information

- **Technical documentation**: [https://github.com/MostroP2P/mostro/blob/main/docs/DEV_FEE.md](https://github.com/MostroP2P/mostro/blob/main/docs/DEV_FEE.md)  

Development sustainability is no longer a concern—it’s an automatic feature of the system!
