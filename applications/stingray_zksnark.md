# Open Grant Proposal

> This document is referenced in the terms and conditions and therefore needs to contain all the required information. Don't remove any of the mandatory parts presented in bold letters or as headlines! See the [Open Grants Program Process](https://github.com/w3f/Open-Grants-Program/blob/master/README_2.md) on how to submit a proposal.

* **Project:** Stingray zkSNARK
* **Proposer:** [Manta-Network](https://github.com/Manta-Network/Manta-Whitepaper/blob/main/manta-whitepaper.pdf)
* **Payment Address:** bc1qcnghrzsfwnnv5fuh8095a6g3cf820c9y7t432q


## Project Overview :page_facing_up: 
Stringray is a zero-knowledge proof framework for Polkadot. 

### Overview

zkSNARK (zero-knowledge Succinct Non-interactive Argument of Knowledge) has been adopted increasingly to protect privacy and speed up transactions in decentralized ledger systems. 

Stingray is zkSNARK framework developed by [Manta Network](www.manta.network) team to make ease of Polkadot developers to integrate zero-knowledge proof to their projects.

Stingray is based on the popular [Groth16](https://eprint.iacr.org/2016/260.pdf) scheme, which is the most efficient zkSNARK construction to date. Stringray will allow Polkadot developers to easily generate the prover and verifier (as a substrate) from standard gadgets that cover many popular applications.

Our own team will be the initial user of Stringray to create private assets and a decentralized exchange framework on Polkadot.

### Project Details 

Stringray will provide a Rust library that allows Polkadot developers to easily prototype and deploy zkSNARK-based parachain substrates. The Stringray framework will include:

* a series of gadgets including hash, signature, and authenticated dictionaries for common building blocks;
* a programming interface that allows developers to combine those gadgets to build the zkSNARK statement;
* generation of offline prover and verifier substrates from the zkSNARK statement;
* a working demo and documentation to explain how to use Stingray.

Currently, we plan to implement/adapt the following gadgets to Stingray:
* BLS signature
* Pedersen Hash
* Merkle Patricia Trie

Stringray will leverage the existing Web3 Foundation [BLS Curve](https://github.com/w3f/bls) and zkSNARK libraries such as 
[LibZexe](https://github.com/scipr-lab/zexe) as building blocks, and focus on building programming abstractions and libraries that lower the entry barrier of deploying zkSNARK to Polkadot.


### Ecosystem Fit 
One similar project to ours is [Stark Network](https://github.com/w3f/Open-Grants-Program/blob/master/applications/starks_network.md). The major difference is that Stingray will use the more efficient Groth16 scheme. There are pros and cons in both schemes. Below are the detailed comparisions:

|                                       | SNARKs                     | STARKs                        | 
| ------------------------------------: | -------------------------: | ----------------------------: | 
| Algorithmic complexity: prover        | O(N * log(N))              | O(N * poly-log(N))            | 
| Algorithmic complexity: verifier      | ~O(1)                      | O(poly-log(N))                | 
| Communication complexity (proof size) | ~O(1)                      | O(poly-log(N))                | 
| - size estimate for 1 TX              | Tx: 200 bytes, Key: 50 MB  | 45 kB                         | 
| - size estimate for 10.000 TX         | Tx: 200 bytes, Key: 500 GB | 135 kb                        | 
| Ethereum/EVM verification gas cost    | ~600k (Groth16)            | ~2.5M (estimate, no impl.)    | 
| Trusted setup required?               | YES :unamused:             | NO :smile:                    | 
| Post-quantum secure                   | NO :unamused:              | YES :smile:                   | 
| Crypto assumptions                    | Strong :unamused:          | Collision resistant hashes :smile: |

The major advantage of Groth16 is the very low verification cost and small proof size. Since the verification needs to be done on chain, that is a huge advantage both in terms of performance and gas cost. However, Groth16 requires a more expensive trusted setup while STARKs doesn't require setup. We think the trusted setup is a one-time cost and for most blockchain applications, it is worth paying. We have a future plan to add a ceremony library like the one used in ZCash to make the trusted setup easier.


## Team :busts_in_silhouette:

### Team members
* Shumo Chu: Assistant Professor at UCSB. He obtained his Ph.D. in Computer Science from University of Washington. He was a research scientist in Algorand working on smart contract runtime and verification. 
* Zhenfei Zhang: Zhenfei obtained his Ph.D. in computer at University of Wollongong, Australia. He was the director of cryptographic research at OnBoard Security, and a cryptographic engineer at Algorand.
* Qiudong  Xia: received the B.S. degree from the Department of Information Security, University of Science and Technology of China (USTC), in 2018. He is currently pursuing a master's degree in information security from the Department of Electronic Engineering and Information Science (EEIS), USTC. His research interests include architecture design and security protection.


### Team Website	
* https://github.com/Manta-Network/Manta-Whitepaper/blob/main/manta-whitepaper.pdf

### Legal Structure 
BVI company.

### Team's experience
All team members have extensive experience in distributed systems, cryptocurrencies and applied cryptography. Shumo had been working on distributed database systems, smart contract runtime and verification, and published more than 10 papers in database systems and formal methods. Zhenfei has published over 25 papers in cryptography; contributed to multiple proposals to the NIST post-quantum cryptography competition; and co-drafted the BLS IETF Internet-draft. Qiudong has been working actively on access control and security of networking systems.


### Team Code Repos
* https://github.com/Manta-Network/Stingray

### Team LinkedIn Profiles
* https://www.linkedin.com/in/shumo-chu-a1722416/
* https://www.linkedin.com/in/zhenfeizhang/
* https://www.linkedin.com/in/qiudong-xia-2935761aa

## Development Roadmap :nut_and_bolt: 


### Overview
* **Total Estimated Duration:** 2 months
* **Full-time equivalent (FTE):**  2 
* **Total Costs:** 2 BTC

### Milestone 1 — Stingray Framework Prototype
* **Estimated Duration:** 1 month
* **FTE:**  2
* **Costs:** 1.5 BTC

| Number | Deliverable | Specification |
| ------------- | ------------- | ------------- |
| 0a. | License | Apache 2.0 |
| 1. | Rust Crate: Stingray | We will create the Stingray Rust Crate that contains the programming interface, common gadgets and prover/verifier generation tool  |
| 2. | Substrate module: example verifier | We will create a Substrate module that is generated by our framework to demonstrate the effectiveness and efficiency of Stringray |
| 3. | Docker | We will provide a dockerfile to demonstrate the end-to-end pipeline of Stingray. |

### Milestone 2 — Wrapup, Documentation and Demonstration

* **Estimated Duration:** 1 month
* **FTE:**  1
* **Costs:** 0.5 BTC

| Number | Deliverable | Specification |
| ------------- | ------------- | ------------- |
| 0a. | License | Apache 2.0 |
| 0b. | Documentation | We will provide a detailed documentation of how to use stingray as a developer, including a documentation on the programming interface, how to generate a prover/verifier, how to perform trusted setup, and how to verify a package to a substrate module and deploy. |
| 0c. | Testing | We will add unit tests for Stingray that achieve at least 60% coverage and add them into the continuous integration process. | 
| 1. | Benchmark | We will provide a performance study of Stingray and a guide for developers on how to achieve the best performance using Stringray. We will also add the benchmark as part of the regression test suite. |
| 2. | Docker | We will provide a dockerfile to demonstrate the end-to-end pipeline of Stingray with 3 different use case examples. |

### Community engagement

As part of the Program, we plan to publish several Medium articles/tutorials:
* general introductions to zkSNARKs
* design/architecture of Stingray
* tutorial of using Stringray to develop a privacy-preserving app in Polkadot

## Future Plans

Stingray is part of the [Manta](https://manta.network) project. We plan to keep adding new features to Stingray, including:
* a ceremony tool to do decentralized trusted setup using SMPC (secure multi-party computation)
* gadgets covering more applications
* leading a community effort to create an open standard for DApps using zkSNARK on Polkadot

## Additional Information :heavy_plus_sign: 

Fun fact: all Manta projects are named after sea creatures.
