# torresm
**torresm** is a two-part proof-of-concept that combines permissioned access control via Arbitrum Stylus with encrypted computation powered by Fully Homomorphic Encryption (FHE).  
Why “torresm”?
No one really knows. But like your data — it’s protected by default.


## Team
- Name: Thiago Rocha
- GitHub Handle: [@thiagorochatr](https://github.com/thiagorochatr)
- Devfolio Handle: thiagorochatr

## Project Description
### 🔒 What It Does

The project is split into two cleanly separated components:

#### 1. Stylus-Based Access Control (On-chain)
Users must prove they are authorized by submitting a valid Ed25519 digital signature.  
A Rust smart contract (running on Arbitrum Stylus) verifies this signature using native Rust cryptography libraries.  
If the signature is valid, the user is marked as authorized to proceed.

#### 2. Encrypted Computation with Zama (Off-chain)
Once authorized, users submit sensitive data (e.g. a vote, score, or value), which is encrypted using Zama’s FHE toolkit.  
The data is processed *without ever being decrypted*, ensuring complete privacy.  
Example: encrypted values are summed homomorphically, then the final result is decrypted by an authorized party or oracle.

### 🧠 Why It Matters

Stylus enables high-performance, low-cost smart contracts in Rust — unlocking signature schemes and cryptographic logic not feasible in Solidity.  
FHE allows secure computation on encrypted data, without ever revealing the inputs.

Together, they enable practical workflows for:
- Private financial interactions
- Selective access to sensitive data
- Confidential identity checks
- Anonymous surveys
- and many more



## Tech Stack
- **Smart Contracts:** Rust (Arbitrum Stylus), and Solidity (FHE)
- **Signature Scheme:** Ed25519 (`ed25519-dalek`)
- **Encryption Engine:** Zama TFHE
- **Front-End:** React + Wagmi
- **Dev Tools:** Stylus CLI, Docker, Hardhat



## Objectives
_What are the specific outcomes you aim to achieve by the end of ARG25?_
- Deploy a Rust-based Stylus contract that verifies signatures
- Create this MVP flow for signing and then compute encrypted data




## Weekly Progress

### Week 1 (ends Oct 31)
**Goals:**
- Define architecture and flow
- Set up Stylus environment
- Write README and submit initial PR for Invisible Garden.


### Week 2 (ends Nov 7)
**Goals:**  
- Implement signature verification with `ed25519-dalek`
- Finalize and test Stylus contract
- Build simple frontend
- Encrypt test data with Zama and submit it
- Complete the most simple MVP with the entire flow working
 
**Progress Summary:**  


### 🗓️ Week 3 (ends Nov 14)
**Goals:**
- Create a more complex flow
- Run encrypted computation (sum or validation)
- Show full end-to-end flow
- Document usage and design

**Progress Summary:**  



## Final Wrap-Up
_After Week 3, summarize your final state: deliverables, repo links, and outcomes._

- **Main Repository Link:**  
- **Demo / Deployment Link (if any):**  
- **Slides / Presentation (if any):**



## 🧾 Learnings
_What did you learn or improve during ARG25?_



## Next Steps
_If you plan to continue development beyond ARG25, what’s next?_



_This template is part of the [ARG25 Projects Repository](https://github.com/invisible-garden/arg25-projects)._  
_Update this file weekly by committing and pushing to your fork, then raising a PR at the end of each week._
