# torresm
**torresm** is a two-part cross-chain proof-of-concept that combines permissioned access control via Arbitrum Stylus with encrypted computation powered by Fully Homomorphic Encryption (FHE).  
Why “torresm”?
No one really knows. But like your data — it’s protected by default.


## Team
- Name: Thiago Rocha [site](https://thiagorochatr.com/)
- GitHub Handle: [@thiagorochatr](https://github.com/thiagorochatr)
- Devfolio Handle: thiagorochatr  

- Name: Pedro Rosalba
- GitHub Handle: [@PedroRosalba](https://github.com/PedroRosalba)

## Project Description
### 🔒 What It Does

The project implements a confidential token vesting system across two chains.

#### 1. ZK-Verified Vesting Control (Stylus - Arbitrum Sepolia)
Companies create vesting schedules with encrypted amounts, submitting Zero-Knowledge proofs to validate vesting parameters.
A Rust smart contract (running on Arbitrum Stylus) verifies Groth16 ZK proofs using native Rust cryptography libraries, ensuring gas-efficient verification.
If the proof is valid, the vesting metadata is stored on-chain, and a CCIP message is sent to Ethereum.

#### 2. Encrypted Vesting Computation (Ethereum Sepolia)
Vesting amounts are encrypted off-chain using Zama's FHE toolkit and stored on Ethereum.
OpenZeppelin's VestingWalletConfidential library handles encrypted calculations — computing releasable amounts without ever decrypting the total allocation.
When beneficiaries request token release, calculations happen homomorphically, and only the final transfer amount is decrypted.

#### 3. Cross-Chain Communication (Chainlink CCIP)
Vesting creation triggers on Arbitrum are relayed to Ethereum via CCIP.
Release requests flow from Arbitrum to Ethereum, where encrypted tokens are released to beneficiaries.

### 🧠 Why It Matters

Stylus enables high-performance ZK proof verification in Rust — making cryptographic operations that would be prohibitively expensive in Solidity practical and cost-effective.
FHE allows secure computation on encrypted vesting amounts, protecting sensitive compensation data from competitors, investors, and even blockchain observers.
CCIP bridges the gap between L2 efficiency (Arbitrum) and L1 security/FHE capability (Ethereum).

Together, they enable practical workflows for:
- Private financial interactions
- Selective access to sensitive data
- Confidential identity checks
- Anonymous surveys
- Cross-chain token distribution with privacy guarantees
- Transparent vesting timelines with encrypted amounts
- and many more



## Tech Stack
- **Smart Contracts:** Rust (Arbitrum Stylus for ZK verification), Solidity (Ethereum for FHE operations)
- **Zero-Knowledge Proofs**: Circom circuits, SnarkJS, Groth16
- **Cross-Chain**: Chainlink CCIP (Arbitrum ↔ Ethereum)
- **Encryption Engine:** Zama TFHE
- **Vesting Logic**: OpenZeppelin Confidential Contracts
- **Front-End:** React + Wagmi + Zama Relayer SDK
- **Dev Tools:** Stylus CLI, Docker, Hardhat



## Objectives
_What are the specific outcomes you aim to achieve by the end of ARG25?_
- Create this MVP flow for signing and then compute encrypted data
- Deploy a Rust-based Stylus contract that verifies Groth16 ZK proofs
- Implement cross-chain interaction using CCIP (Arbitrum → Ethereum)
- Store and compute encrypted data using Zama FHE on Ethereum
- Integrate OpenZeppelin's library
- Create end-to-end MVP


## Weekly Progress

### Week 1 (ends Oct 31)
**Goals:**
- Define architecture and flow
- Set up Stylus environment
- Write README and submit initial PR for Invisible Garden.


### Week 2 (ends Nov 7)
**Goals:**  
- Finalize and test Stylus contract
- Build simple frontend
- Encrypt test data with Zama and submit it
- Complete the most simple MVP with the entire flow working
- Design cross-chain confidential vesting architecture
- Set up Circom circuit for vesting validity proofs
- Research OpenZeppelin Confidential Contracts and Zama FHE integration
- Plan CCIP message flow between Arbitrum and Ethereum
- Define encryption strategy (off-chain encrypt, on-chain compute)
 
**Progress Summary:**  
- ✅ Finalized architecture: Arbitrum (ZK + metadata) → CCIP → Ethereum (FHE + tokens)
- ✅ Identified required libraries and contracts
- ✅ Created technical specification
- ✅ Confirmed FHE only works on Ethereum Sepolia, CCIP only in Solidity
- ✅ Designed Circom circuit with 4 constraints (amount > 0, cliff ≤ duration, beneficiary valid, commitment matches)

**Here's the link of the demo**: https://youtu.be/Mf-Bw1QYPyA  

### 🗓️ Week 3 (ends Nov 14)
**Goals:**
- Create a more complex flow
- Run encrypted computation
- Show full end-to-end flow
- Document usage and design
- Implement circom circuit and generate proving/verification keys
- Deploy ZKVerifier contract (Rust/Stylus) on Arbitrum Sepolia
- Deploy VestingController (Solidity) on Arbitrum with CCIP sender
- Deploy VestingWalletCCIPReceiver (Solidity + FHE) on Ethereum Sepolia
- Integrate OpenZeppelin VestingWalletCliffConfidential
- Build frontend flows: Create vesting & Request release
- Test full end-to-end flow with cliff for demo

**Progress Summary:**  
- Complex Open Zeppelin/Zama libs are not yet stable. Implementing them in just a few days is not so simple.
- ✅ Successfully completed the ZK part: User generates the proof, then calls the Stylus contract to verify the proof. If the proof is verified, it calls the sendMessage function of the CCIP sender contract, which is deployed on Arbitrum. The message is sent containing the address, nullifier, and timestamp.
- ⚠️ ConfidentialVesting still has some issues under investigation. It worked successfully 30% of the time.
- ❌ CCIP Receiver has not yet been implemented in the flow.


## Final Wrap-Up
- **Main Repository Link:**  https://github.com/thiagorochatr/torresm-fhe-vesting
- **Demo / Deployment Link (if any):**  
- **Slides / Presentation (if any):**



## 🧾 Learnings
_What did you learn or improve during ARG25?_
soon...


## Next Steps
_If you plan to continue development beyond ARG25, what’s next?_
soon...


_This template is part of the [ARG25 Projects Repository](https://github.com/invisible-garden/arg25-projects)._  
_Update this file weekly by committing and pushing to your fork, then raising a PR at the end of each week._
