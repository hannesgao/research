
# Orderly-LayerZero-AggLayer-Silicon Chain Interconnection Feasibility Study

## Executive Summary

**Core Conclusion**: 

Connecting Orderly to Polygon via LayerZero, and then to Silicon Chain through AggLayer is technically feasible but requires phased new implementation of relay contracts and strict cost analyse, since zk-proof and multi-hops chain-crossing cause extra costs. Orderly has already integrated LayerZero's omnichain functionality, while Silicon Network (https://silicon.network/) has only confirmed its Polygon CDK compatibility and connectivity via AggLayer.

**Key Findings**:
- Orderly Network has successfully integrated LayerZero for cross-chain interoperability to Polygon.
- Polygon AggLayer can provide a unified bridge solution for cross-chain interconnection among Polygon CDK Chains.
- Polygon AggLayer can provide unified liquidity and message passing among Polygon CDK Chains.
- Silicon Network is confirmed as one of AggLayer's core contributors
- Silicon Chain is not yet supported by LayerZero.
- It is technically possible to use Polygon as a relay to go through Polygon AggLayer to achieve cross-chain message passing between the Silicon Chain and Orderly Network (Orderly Network ⟷ LayerZero ⟷ Polygon ⟷ AggLayer ⟷ Silicon Network).
- The development complexity, latency and cost-effectiveness of this connection path above are not necessarily and conclusively better than direct connection via LayerZero.

---

## 1. Technical Architecture Analysis

### 1.1 Current Infrastructure Status

#### 1.1.2 Orderly Network
- **Architecture**: Layer 2 solution built on OP Stack
- **LayerZero Integration Status**: Complete, supporting omnichain functionality
- **Supported Polygon CDK-compatible Chain**: Polygon, which is possible to be used as a relay to go through Polygon AggLayer to connect to the Silicon Chain


#### 1.1.3 LayerZero Protocol
- **Supported Polygon CDK Chains**: 
  - Polygon
  - xLayer (by OKX) 
  - Merlin 

> **Notice:** Silicon Chain is not yet (2025.05.16) supported by LayerZero. 

- **Core Advantages for Orderly**: 
  - Native asset transfers (no wrapped tokens)
  - Message passing and smart contract calls
  - Configurable security model

> **Notice:** Currently, our cross-chain infrastructure and related smart contracts are all based on LayerZero. Considering the convenience of upgrading and migrating, as well as the consistency of our project, it is best for us to use LayerZero for cross-chain messaging with Silicon Chain (if LayerZero can provide support for it in the near future).


### 1.2 Polygon AggLayer Technical Overview

#### 1.2.1 Core Components
1. **Unified Bridge**
   - All connected chains share a single bridge contract
   - Supports native asset cross-chain transfers without wrapping
   - Provides two key mechanisms: Token Bridging and Message Bridging

2. **Zero-Knowledge Proof**
   - Zero-knowledge proof ensuring cross-chain security
   - Prevents any single chain from withdrawing more than deposited from the bridge
   - Generated using SP1 zkVM, built with Polygon Plonky3

3. **Aggregation Mechanism**
   - Aggregates ZK proofs from multiple chains into a single proof
   - Reduces cost of submitting proofs to Ethereum
   - Supports fast asynchronous cross-chain transactions

#### 1.2.2 Security Guarantees
- **Chain-level Accounting**: Ensures asset balance for each chain
- **Cryptographic Security**: ZK proofs provide mathematical guarantees
- **Sovereignty Preservation**: Connected chains maintain independent consensus mechanisms

> **Notice:** For the technical details of Polygon AggLayer, a special technical share for BD and Contract Team is being prepared. We'll cover more technical aspects and cross-chain workflows of Polygon CDK chains via AggLayer in this tech share.

### 1.3 Silicon Network Overview

#### 1.3.1 Project Positioning
- **Positioning**: Hyper-personalized social network backed by [Korbit Exchange](https://www.korbit.co.kr/) based in South Korea
- **Tech Stack**: ZK-based Ethereum Layer 2, built on Polygon CDK
- **AggLayer Status**: Confirmed as core contributor, aggregated via AggLayer

#### 1.3.2 Technical Characteristics
- **Chain ID**: 2355 (Silicon zkEVM)
- **Native Token**: ETH
- **EVM-Compatibility**: zkEVM compatible
- **Cross-Chain Connectivity**: Through AggLayer from/to other Polygon CDK chains

---

## 2. Connection Path Design

### 2.1 Possible Connection Paths

#### 2.1.1 Option 1: Direct Connection via LayerZero
```
[Orderly Network] 
        ⇅ (LayerZero)
[Silicon Chain]
```

#### 2.1.2 Option 2: Indirect Connection via LayerZero, Polygon and Agglayer
```
[Orderly Network] 
        ⇅ (LayerZero)
[Polygon Network] 
        ⇅ (AggLayer)
[Silicon Chain (and any other Polygon CDK chains)]
```

### 2.2 Possible Implementation Steps for Option 2

#### 2.2.1 Phase 1: Orderly to Polygon Connection
- **Status**: Already implemented and in production
- **Mechanism**: LayerZero omnichain protocol
- **Features**: 
  - Asset cross-chain transfers
  - Orderbook liquidity sharing
  - Message passing

#### 2.2.2 Phase 2: Polygon to Silicon Connection
- **Status**: Could consider
- **Mechanism**: AggLayer unified bridge
- **Features**:
  - Native asset transfers
  - State sharing
  - Unified liquidity pools

> **Notice:** AggLayer v1 is already deployed on Polygon and Silicon. If we choose the 2nd option, then we need to develop and deploy our own special relay contracts on Polygon and Silicon Chain to achieve message passing through AggLayer.

#### 2.2.3 Phase 3: Complete Integration Optimization
- **Status**: Could consider
- **Target**: Achieve end-to-end seamless cross-chain connection between Orderly Network and Silicon Chain
- **Optimization Points**:
  - Reduce cross-chain latency
  - Lower transaction fees
  - Improve user experience

---

## 3. Feasibility Analysis

### 3.1 Technical Feasibility ✅

#### 3.1.1 Advantages
1. **Existing Integration**: Orderly has already integrated LayerZero
2. **Official Support**: Silicon officially confirmed AggLayer integration
3. **Mature Protocols**: Both LayerZero and AggLayer are proven protocols
4. **Compatibility**: All components are based on EVM-compatible architecture

#### 3.1.2 Technical Challenges
1. **Multi-hop Latency**: Going through two relay layers may increase confirmation time
2. **Fee Accumulation**: Multiple cross-chain operations lead to fee stacking
3. **Complexity Management**: Need to coordinate state synchronization across multiple protocols

### 3.2 Economic Feasibility ⚠️

#### 3.2.1 Cost Factors
- **LayerZero Fees**: Gas fees + protocol fees
- **AggLayer Fees**: ZK proof verification costs
- **Liquidity Costs**: Liquidity distribution across chains

#### 3.2.2 Revenue Analysis
- **Unified Liquidity**: Improved capital efficiency
- **Expanded User Base**: Access to multi-chain ecosystems
- **Development Costs**: Paritcial reuse of existing infrastructure, but new developments, deployments and audits for our own special relay contracts on Polygon and Silicon Chain are needed

### 3.3 Security Assessment ✅

#### 3.3.1 Security Guarantees
1. **LayerZero**: Decentralized Verifier Networks (DVNs)
2. **AggLayer**: Pessimistic proofs ensure asset security
3. **Multiple Verification**: Each hop has independent verification mechanisms

#### 3.3.2 Risk Factors
- **Contract Risk**: Smart contract vulnerability risks
- **Bridge Risk**: Inherent cross-chain bridge risks
- **Liquidity Risk**: Insufficient liquidity on certain chains may affect experience

---

## 4. Recommended Implementation Plan

### 4.1 Phased Implementation

#### 4.1.1 Phase 1: Basic Connection Establishment (1-2 months)
- **Target**: Achieve basic asset cross-chain transfers
- **Scope**: Orderly ↔ Polygon ↔ Silicon
- **Priority**: High
- **TO DO**: Implement and deploy our own special relay contracts on Polygon and Silicon Chain to achieve message passing through AggLayer

#### 4.1.2 Phase 2: Functional Optimization Integration (1-2 months)
- **Target**: Achieve unified liquidity and state sharing
- **Scope**: Smart contract calls, message passing
- **Priority**: Medium

#### 4.1.3 Phase 3: User Experience Optimization (1-2 months)
- **Target**: Achieve better cross-chain experience
- **Scope**: Fee and UX optimization
- **Priority**: Medium

### 4.2 Technical Implementation Recommendations

#### 4.2.1 Possible Smart Contract Architecture
```solidity
contract OrderlyAggLayerRelay {
    // LayerZero endpoint interface
    ILayerZeroEndpoint public layerZeroEndpoint;
    
    // AggLayer bridge interface
    IAggLayerBridge public aggLayerBridge;
    
    // Cross-chain message routing
    function routeToSilicon(
        bytes calldata message,
        address recipient
    ) external payable {
        // 1. Send to Polygon via LayerZero
        // 2. Trigger AggLayer bridge to Silicon
        ...
    }
}
```

#### 4.2.2 Message Flow Design
1. **Orderly → Polygon**: LayerZero OApp message
2. **Polygon → Silicon**: AggLayer Bridge & Call
3. **State Sync**: Bidirectional message confirmation mechanism

---

## 5. Conclusions & Recommendations

### 5.1 Overall Conclusion

Currently, our cross-chain infrastructure and related smart contracts are all based on LayerZero. Considering the convenience of upgrading and migrating, as well as the consistency of our project, it is best for us to use LayerZero for cross-chain messaging with Silicon Chain (if LayerZero can provide support for it in the near future).

If LayerZero does not consider supporting Silicon Chain, and we decide that we must connect to Silicon Chain to expand our South Korean users, we can consider using the 2nd option of connecting to Silicon Chain, which is described in [[2.1.2 Option 2: Indirect Connection via LayerZero, Polygon and Agglayer]](#212-option-2-indirect-connection-via-layerzero-polygon-and-agglayer).

---

## 6. Appendix

### 6.1 Technical References

- [Orderly Network Documentation](https://docs.orderly.network/)
- [LayerZero V2 Documentation](https://docs.layerzero.network/v2)
- [Polygon AggLayer Documentation](https://docs.polygon.technology/agglayer/)
- [Silicon Network Official Site](https://silicon.network/)

### 6.2 Update Log of this Rearch Report

- **2024-05-16**: Initial report completed by Hannes Gao (hannes@orderly.network)

> **Notice:** Subsequent versions will be updated based on research and the decision-making progress of our team.

---

*This report is compiled based on publicly available information as of May 2024. It is recommended to conduct the latest technical verification and risk assessment before implementation.*