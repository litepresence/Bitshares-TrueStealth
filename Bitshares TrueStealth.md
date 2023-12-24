
# Bitshares Improvement Proposal

**BSIP:** TBD
**Title:** Bitshares TrueStealth
**Sub Title:** Enhancing Confidential Transactions with Ring Signatures, RSA Accumulators, Delayed Transfers, and Market-Driven Fee Incentive
**Authors:** litepresence, finitestate@tutamail.com
**Status:** [Draft]
**Type:** [Protocol]
**Created:** 2023-12-20
**Discussion:** TBD
**Worker:** TBD

## Abstract:

This proposal introduces Bitshares TrueStealth, a comprehensive enhancement to BitShares' confidential transactions. TrueStealth incorporates advanced cryptographic techniques such as Ring Signatures, RSA Accumulators, and Pedersen Commitments. It also introduces Delayed Transfers and Market-Driven Fee Incentives, aiming to revolutionize participant privacy. By strategically combining these elements, the proposal seeks to create a holistic and market-oriented approach to strengthen privacy within the BitShares ecosystem.

## Motivation:

While BitShares' current confidential transactions conceal amounts through blinded transfers, identified limitations in participant privacy and transaction traceability necessitate a significant leap. This proposal integrates advanced cryptographic methods to fortify BitShares' confidential transactions and introduces market-driven incentives for widespread adoption. The motivation is rooted in an unwavering commitment to user privacy and the desire for a secure and private digital experience.

Join us in reshaping the future of confidential transactions with a proposal that not only meets technological demands but taps into the fundamental desire for a secure and private digital experience.

## Rationale:

### Ring Signature:

Conceal sender identity and minimize blockchain bloat by integrating LSAG Ring Signatures, enabling configurable anonymity sets for confidential transfers.

### RSA Accumulator:

Safeguard transaction amount privacy using RSA cryptography, constructing an accumulator as a cryptographic proof while serving as a nullifier to prevent double-spending.

### Pedersen Commitments:

Enhance individual transaction amount privacy within the RSA Accumulator using homomorphic Pedersen Commitments, facilitated by zero-knowledge proofs and Cut-Through optimization.

### Delayed Blind Transfers:

Boost overall privacy by introducing a delay mechanism for blind transfers, strategically postponing transaction confirmation to increase entropy and hinder transaction linkage.

### Market-Driven Fee Structure Optimization:

Drive adoption of privacy features by adjusting fees to make blind transfers more cost-effective, encouraging users to embrace privacy-conscious transactions and enhancing overall blockchain entropy.

## Specification:

### 1. Ring Signatures:

#### 1.1 Implementation Details:

Building upon the success of Monero's Linkable Spontaneous Anonymous Group (LSAG) Ring Signatures, BitShares proposes their integration to significantly enhance participant privacy and minimize blockchain bloat. This involves implementing LSAG-based Ring Signatures to increase efficiency while maintaining a lean blockchain.

#### 1.2 Workflow:

- **Sender Anonymity Set Configuration:**
  Users initiating confidential transfers gain the ability to configure the size of the anonymity set, determining the number of potential senders within the ring.

- **Ring Signature Inclusion:**
  Upon initiation of a confidential transfer, the sender's signature, along with decoy signatures from the configured anonymity set, will be included in the ring. This computational approach introduces ambiguity, making it infeasible to determine the actual sender of a confidential transaction.

- **Dynamic Anonymity Set:**
  The dynamic nature of the anonymity set ensures continuous enhancement of participant privacy, as the potential sender pool evolves with each transaction.

### 2. RSA Accumulators:

#### 2.1 Implementation Details:

The integration of RSA Accumulators focuses on addressing the privacy of transaction amounts through the application of RSA cryptography.

- **RSA Accumulator Construction:**
  Utilizing the multiplicative property of RSA modulo \(N\), the accumulator is constructed as the product of prime numbers corresponding to individual transaction amounts. This cryptographic proof, represented as \(A\), ensures the confidentiality of the overall transaction amount.

#### 2.2 Workflow:

- **Amount Aggregation Process:**
  Upon initiation of a confidential transaction, individual amounts are mapped to unique prime numbers, and these primes are accumulated in the RSA Accumulator using the multiplicative property.

- **Single Representational Value:**
  The resulting value of the RSA Accumulator serves as a cryptographic proof of the overall transaction amount, maintaining unlinkability to specific transactions.

- **Verification without Disclosure:**
  Non-interactive zero-knowledge proofs or other cryptographic techniques can be employed to verify the accumulated amount without disclosing the individual components.

- **Preventing Double-Spending:**
  The RSA Accumulator is utilized as a nullifier, verifying that a specific prime factorization has not been included before, thus preventing double-spending.

### 3. Confidential Assets:

#### 3.1 Implementation Details:

Building upon successful implementations, Pedersen Commitments are integrated to enhance the privacy of individual transaction amounts within the RSA Accumulator. Pedersen Commitments leverage homomorphic properties, allowing the aggregation of commitments without revealing the actual values.

#### 3.2 Workflow:

- **Amount Aggregation Process:**
  Upon initiation of a confidential transaction, each individual amount is committed using Pedersen commitments, allowing for secure aggregation.

- **Zero-Knowledge Proofs:**
  Zero-knowledge proofs are implemented to ensure the commitment to zero, thereby maintaining the privacy and fungibility of the accumulated sum.

- **Cut-Through Optimization:**
  The Cut-Through optimization is applied to eliminate redundant transaction information, reducing the overall size of the transaction while preserving privacy and security.

- **Verification without Disclosure:**
  Verifiers can confirm the validity of the accumulated amount and the commitment to zero without revealing the individual components, ensuring transaction amount privacy.

### 4. Delayed Blind Transfers:

#### 4.1 Entropy Enhancement:

The proposed mechanism involves delaying the execution of blind transfers by a certain number of blocks, contributing to increased overall entropy.

#### 4.2 Workflow:

- **Delay Parameter Configuration:**
  The committee will vote on the appropriate delay parameter, measured in blocks, specifying the number of blocks transactions should be delayed before execution. This parameter enhances privacy by strategically postponing the confirmation of transfers.

- **Suggested Delay Parameter:**
  The suggested delay parameter is 100 blocks, equivalent to 5 minutes with a 3-second block time. This provides a balance between enhanced privacy and reasonable transaction confirmation times.

- **Entropy Accumulation:**
  By delaying transfers in terms of blocks, the system accumulates a higher number of pending transactions, increasing overall entropy. This makes it more challenging to link specific transactions and enhances the privacy of the blockchain.

### 5. Market-Driven Fee Structure Optimization:

Adjust the fee structure to incentivize the use of blind transfers over regular transfers. By making blind transfers more cost-effective, users may be encouraged to opt for privacy-enhancing features, thereby increasing the overall entropy in the stealth system.

#### 5.1. Cheaper Blind Transfers:

- Reduce the fees associated with blind transfers compared to regular transfers. This adjustment can motivate users to choose blind transfers as the more economical option, leading to a higher adoption rate of privacy features.

#### 5.2. Subsidizing Blind Transfers:

- Use the fees collected from regular transfers to subsidize the cost of blind transfers. This approach can make privacy features financially accessible to a broader user base, fostering a culture of privacy-conscious transactions.

#### 5.3. Entropy Increase:

- The increased usage of blind transfers due to lower fees can contribute to higher entropy in the stealth system. Higher entropy makes it more challenging for

 external observers to discern meaningful patterns or trace specific transactions, enhancing the overall privacy of the blockchain.

#### 5.4. Committee Vote:

- The committee should vote to increase transfer TX fees to heavily subsidize blind transfers.

#### 5.5 Suggest Fee Ratio

The cost of blind transfers should be set to 1/100 that of a regular transfer. Doing so encourages their use while the cost can be offset by regular transfers. Encouraged uses increases entropy.

## Implementation Timeline and Milestones:

### Phase 1: Foundation and Preparation

**Timeline:** Q1 2024

1. **Community Engagement and Feedback (2 weeks):**
   - Establish community forums and conduct introductory webinars.
   - Gather initial feedback on the TrueStealth proposal.

2. **Proposal Refinement (2 weeks):**
   - Review and incorporate community feedback.
   - Refine the TrueStealth proposal based on user insights.

3. **Security Audit Procurement (1 week):**
   - Identify and engage a third-party security audit firm.

### Phase 2: Cryptographic Implementations

**Timeline:** Q2 2024

4. **Ring Signatures Implementation (1 month):**
   - Develop and integrate LSAG-based Ring Signatures into the BitShares protocol.
   - Conduct testing and optimization for computational efficiency.

5. **RSA Accumulators Integration (1.5 months):**
   - Implement RSA Accumulators to address transaction amount privacy.
   - Collaborate with cryptography experts to ensure the security of the accumulator construction.

6. **Pedersen Commitments and Confidential Assets (1 month):**
   - Integrate Pedersen Commitments to enhance the privacy of individual transaction amounts.
   - Implement zero-knowledge proofs and Cut-Through optimization.

### Phase 3: Operational Enhancements

**Timeline:** Q3 2024

7. **Delayed Blind Transfers Implementation (2 weeks):**
   - Develop and integrate delayed blind transfers mechanism.
   - Allow for dynamic adjustment of delay parameters based on network conditions.

8. **Market-Driven Fee Structure Optimization (1.5 months):**
   - Implement the proposed fee adjustments for incentivizing blind transfers.
   - Conduct economic modeling and simulations to validate the impact of fee changes.

### Phase 4: Testing and Quality Assurance

**Timeline:** Q4 2024

9. **Comprehensive Testing (1 month):**
   - Conduct thorough testing of the entire TrueStealth implementation.
   - Perform unit testing, integration testing, and security testing.

10. **Bug Fixing and Optimization (2 weeks):**
    - Address any issues identified during testing.
    - Optimize code and enhance overall system performance.

### Phase 5: Deployment and Community Adoption

**Timeline:** Q1 2025

11. **Deployment on Testnet (2 weeks):**
    - Deploy TrueStealth on the BitShares testnet for community testing.
    - Gather additional feedback from users and developers.

12. **Mainnet Release (2 weeks):**
    - Release TrueStealth on the BitShares mainnet.
    - Launch awareness campaigns to promote TrueStealth features and benefits.

### Crude Estimate of Development Hours per Milestone:

1. **Community Engagement and Feedback:** 40 hours
2. **Proposal Refinement:** 30 hours
3. **Security Audit Procurement:** 10 hours
4. **Ring Signatures Implementation:** 120 hours
5. **RSA Accumulators Integration:** 160 hours
6. **Pedersen Commitments and Confidential Assets:** 120 hours
7. **Delayed Blind Transfers Implementation:** 80 hours
8. **Market-Driven Fee Structure Optimization:** 0 hours
9. **Comprehensive Testing:** 60 hours
10. **Bug Fixing and Optimization:** 30 hours
11. **Deployment on Testnet:** 20 hours
12. **Mainnet Release:** 20 hours

690 HOURS @ $100 = $69,000

## Discussion:

**Unlocking Value: The TrueStealth Advantage for BitShares Holders**

BitShares TrueStealth revolutionizes the landscape for token holders, bringing succinct and tangible benefits:

1. **Evaluation of Current System Weaknesses:**
   Peer into the shadows of the current BitShares' confidential transactions, revealing the weaknesses in participant privacy and transaction traceability. TrueStealth emerges as the luminary, addressing these issues with a comprehensive approach inspired by Monero.

2. **Combined Impact of Ring Signatures, RSA Accumulators, Delayed Transfers, and Fee Incentives:**
   TrueStealth is not just a proposal; it's a crescendo. The integration of Ring Signatures, RSA Accumulators, delayed blind transfers, and market-driven fee incentives forms a symphony—a holistic composition that transcends the technical into the realm of heightened participant privacy. Join the ensemble, where each mechanism harmonizes to bring BitShares TrueStealth to life.

3. **Privacy Propels Adoption:**
   TrueStealth's robust privacy features—Ring Signatures, RSA Accumulators, Pedersen Commitments, Delayed Transfers, and market-driven fees—position BitShares as a haven for confidential transactions. This not only satisfies existing users but attracts newcomers seeking a secure financial ecosystem, inherently boosting token demand.

4. **Incentives Drive Participation:**
   The market-driven fee structure strategically makes blind transfers cost-effective, incentivizing users to embrace privacy-conscious transactions. Reduced fees, subsidized by regular transfers, stimulate active participation and increase transaction volume within BitShares. This dynamic ecosystem enhances token value.

5. **Symphony of Security:**
   TrueStealth doesn't compromise on security. From Ring Signatures ensuring sender anonymity to RSA Accumulators guarding transaction amounts, each element harmonizes to create an impenetrable fortress. This heightened security instills trust, encouraging users to hold and transact with BitShares tokens more frequently, bolstering intrinsic value.

6. **Entropy as a Shield:**
   Delayed Blind Transfers and intentional entropy accumulation add complexity, making it challenging for external observers to discern patterns or trace transactions. This strategic move enhances privacy and strengthens BitShares tokens' position as valuable and secure assets.

7. **Market Responsiveness:**
   TrueStealth is adaptable to market dynamics. The introduction of market-driven fee incentives, with committee voting to adjust transfer fees, showcases a commitment to a flexible and responsive ecosystem. This adaptability ensures BitShares remains competitive and aligned with user preferences, safeguarding and enhancing token value.

**How You Can Contribute:**

- **Feedback and Suggestions:**
  Review the proposal and share your thoughts. Do you have suggestions for improvement, concerns, or additional insights? Your feedback will help us refine TrueStealth to meet the highest standards.

- **Spread the Word:**
  Knowledge is power. Spread awareness about TrueStealth within the BitShares community and beyond. Encourage fellow users to explore the proposal, understand its benefits, and participate in the conversation.

- **Community Forums:**
  Engage in community forums, discussion groups, and social media channels dedicated to BitShares. Your active participation will amplify the collective voice of the community and contribute to the success of TrueStealth.

- **Technical Expertise:**
  If you possess technical expertise in cryptography, blockchain development, or related fields, your insights are particularly valuable. Help us ensure the robustness of TrueStealth through your technical knowledge and experience.

Thank you for being a vital part of the BitShares revolution.

## Shareholder Summary

In conclusion, BitShares TrueStealth is a strategic move aligning technological innovation with user desires. Elevating privacy, incentivizing participation, fortifying security, introducing entropy, and remaining responsive to market needs, TrueStealth unlocks substantial value for BitShares holders. As users experience a more secure, private, and dynamic financial ecosystem, the inherent value of BitShares tokens becomes not just a promise but a reality. TrueStealth sets the stage for a future where BitShares holders not only preserve but significantly enhance the value of their - private - digital assets.
```
