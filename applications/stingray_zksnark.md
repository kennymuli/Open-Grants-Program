# Open Grant Proposal

> This document is referenced in the terms and conditions and therefore needs to contain all the required information. Don't remove any of the mandatory parts presented in bold letters or as headlines! See the [Open Grants Program Process](https://github.com/w3f/Open-Grants-Program/blob/master/README_2.md) on how to submit a proposal.

* **Project:** Stingray zkSNARK
* **Proposer:** [Manta-Network](https://github.com/Manta-Network)
* **Payment Address:** TBD. 



## Project Overview :page_facing_up: 
Stringray is a zero-knowledge proof framework for Polkadot. 

### Overview

zkSNARK (zero-knowledge Succinct Non-interactive Argument of Knowledge) has been adopted increasingly to protect privacy and speed up transactions in decentralized ledger systems. 

Stingray is zkSNARK framework developed by [Manta Network](www.manta.network) team to make ease of Polkadot developers to integate zero-knowldge proof to their projects.

Stingray will based on the popular [Groth16](https://eprint.iacr.org/2016/260.pdf) scheme, which is the most efficient zkSNARK constrcution to date. Stringray will allow Polkadot developers easily generate prover and the verifier (as a substrate) with from our standard gadgets that covers many popular applications.

Our own team will be the initial user of Stringray to create a private assets and decentralized exchange framework on Polkadot.  

### Project Details 

Stringray will provide a rust library that allows Polkadot developer could easily prototype and deploy zkSNARK based parachain substrates. Stringray framework include:

* a series of gadget including hash, signature, and authenticated dictionaries for common building blocks.
* a programming interface that allows developers to combine these gadgets to build the zkSNARK statement.
* generating a offline prover and verifier substrates from the zkSNARK statement.
* a working demo and documentation to illustrate how to use Stingray

Currently, we plan to implement/adapt the following gadget to Stignray:
* BLS signature
* Pedersen Hash
* Merkle Patricia trie

Stringray will leverage existing Web3 Foundation [BLS Curve](https://github.com/w3f/bls) and existing zkSNARK library such as 
[LibZexe](https://github.com/scipr-lab/zexe) as building blocks, focus on building programming abstractions and libraries that lower the entry barrier of deploying zkSNARK to Polkadot.


### Ecosystem Fit 
One similar project to ours is [Stark Network](https://github.com/w3f/Open-Grants-Program/blob/master/applications/starks_network.md). The major difference is that we use the more efficient Groth16 scheme. There are pros and cons in both scheme, below is the detailed comparision:

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

The major advantage of Groth16 is the low verification cost and small proof size. Since the verification need to be done on chain, 
this is a huge benefit both in terms of performance and gas cost. However, Groth16 requires a more expensive trusted setup. We think the trusted setup is a one-time cost and for most blockchain applications, it is worth paying this one-time cost. We have a future plan to add a ceremony library like the one used in ZCash to make the trusted setup easier.


## Team :busts_in_silhouette:

### Team members
* Shumo Chu: Assistant Professor at UCSB. He obtained his Ph.D. in Computer Science from University of Washington. He was an research scientist in Algorand working on smart contract runtime and verification. 
* Zhenfei Zhang: Independent Researcher. TBD.
* Qiudong Xia: Master student at University of Science and Technology of China. TBD.

### Team Website	
* https://manta.network

### Legal Structure 
BVI company.

### Team's experience
All team members have extensive experience in distributed systems, cryptocurrencies and applied cryptography. Shumo had been working on distributed database systems, smart contract runtime and verification, and published more than 10 papers in database systems, formal methods. Zhenfei has published more than XX papers in cryptography and was the co-author of NIST post-quantum signature competition. Qiudong Xia has been working on security in computer networking XXXX. 



### Team Code Repos
* https://github.com/Manta-Network/Stingray

### Team LinkedIn Profiles
* https://www.linkedin.com/in/shumo-chu-a1722416/
* https://www.linkedin.com/<person_2>

## Development Roadmap :nut_and_bolt: 



### Overview
* **Total Estimated Duration:** 2 month
* **Full-time equivalent (FTE):**  2 
* **Total Costs:** 2 BTC

### Milestone 1 — Stingray Framework Prototype
* **Estimated Duration:** 1 month
* **FTE:**  2
* **Costs:** 1.5 BTC

| Number | Deliverable | Specification |
| ------------- | ------------- | ------------- |
| 0a. | License | Apache 2.0 |
| 1. | Rust Crate: Stingray | We will create Stingray Rust crate that contains the programming interface, common gadget and prover/verifier generation tool  |
| 2. | Substrate module: example verifier | We will create a Substrate module that generated by our framework to demonstrate the effectiveness and efficiency of Stringray |
| 3. | Docker | We will provide a dockerfile to demonstrate the end to end pipeline of Stingray. |

### Milestone 2 — Wrapup, Documentation and Demonstration

* **Estimated Duration:** 1 month
* **FTE:**  1
* **Costs:** 0.5 BTC

| Number | Deliverable | Specification |
| ------------- | ------------- | ------------- |
| 0a. | License | Apache 2.0 |
| 0b. | Documentation | We will provide a detailed documentation of how to use stingray as a developer, including a documentation on the programming interface, how to generate prover/verifier, how to perform trusted setup, how to package verifier to a substrate module and deploy. |
| 0c. | Testing | We will add unit tests for stingray that achieves at least 60% coverage and integrate it into the continuous integration process. | 
| 1. | Benchmark | We will provide a performance study of Stingray and a guide for developer how to achieve best performance using Stringray. We will also add the benchmark as part of the regression test suite. |
| 2. | Docker | We will provide a dockerfile to demonstrate end to end pipeline of Stingray with 3 different use case examples. |

### Community engagement

As part of the Program, we plan to publish serveral medium articles/tutorials:
* general introductions to zkSNARKs
* design/architecture of Stingray
* tutorial of using Stringray to develop privacy preserving app in Polkadot

## Future Plans

Stingray is part of [Manta](https://manta.network) project. We plan to keep adding new features to Stingray, including:
* a ceremony tool to do decentralized trusted setup using MPC (secure multi-party computation)
* 

## Additional Information :heavy_plus_sign: 

Fun fact: all Manta projects are named after sea creatures.
