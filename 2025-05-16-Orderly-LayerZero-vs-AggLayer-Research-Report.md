# LayerZero vs AggLayer Cross-Chain Interoperability Analysis Report for Orderly Network

## Executive Summary

This report analyzes the technical characteristics and advantages/disadvantages of two major cross-chain interoperability protocols - LayerZero and AggLayer, with a specific focus on evaluating the feasibility of Orderly Network using these solutions. The research finds that AggLayer has advantages in technical sophistication, while LayerZero leads in ecosystem maturity.

---

## 1. Comparative Analysis of LayerZero and AggLayer

### 1.1 Similarities

Both protocols aim to solve blockchain fragmentation issues:

- **Core Functionality**: Both are omnichain interoperability protocols designed to connect the fragmented blockchain world¹
- **Cross-chain Messaging**: Both support cross-chain asset transfers and message passing
- **User Experience Optimization**: Both strive to provide users with a single-chain-like experience
- **Multi-chain Ecosystem Support**: Both can connect multiple blockchain networks

### 1.2 Key Differences

#### 1.2.1 Architecture Design

**LayerZero**:
- Adopts an improved version of external verification, converting the trust source for verification into two independent entities - oracles and relayers¹
- More like an engineering company that builds bridges everywhere, designing and constructing bridges for different chains

**AggLayer**:
- More like a "local area network" composed of switches, where connecting chains only need to plug in a "network cable" (ZK proof) to access the "LAN" and exchange data¹

#### 1.2.2 Technical Mechanisms

**LayerZero**:
- Uses a 2/2 consensus mechanism requiring both oracle and relayer agreement²
- Risk of collusion between oracle and relayer²
- Gas fees borne by message sender²

**AggLayer**:
- Uses pessimistic proof, a novel ZK proof mechanism that assumes all access chains are insecure, ultimately using zero-knowledge proofs to ensure correctness of cross-chain operations³
- Works without fee-extracting intermediaries, with ZK proof verification costs amortized among connected chains³
- Supports atomic cross-chain interactions and optimistic confirmation⁴

#### 1.2.3 Performance Comparison

**LayerZero**:
- Supports 70+ blockchains with broader ecosystem⁷
- Relatively traditional experience requiring confirmation waits
- Faces gas price fluctuation risks²

**AggLayer**:
- Supports ultra-low latency and asynchronous interoperability, more like the internet we use daily¹
- Can process transactions optimistically, offering faster cross-chain experience⁴
- Assets on AggLayer are always native and never wrapped³

---

## 2. Orderly Network Integration Analysis

### 2.1 Feasibility Assessment

**Conclusion**: Orderly Network can theoretically implement cross-chain messaging through AggLayer, but with conditional limitations.

#### 2.1.1 Technical Compatibility
- Orderly Network is already part of the LayerZero ecosystem, with its native ORDER token being an OFT (Omnichain Fungible Token)⁵
- Orderly's ecosystem partners include Polygon, indicating existing collaboration with Polygon tech stack⁶

#### 2.1.2 Integration Conditions
- AggLayer primarily connects chains built using Polygon CDK⁷
- If Orderly Network migrates to or deploys on chains using Polygon CDK, it can directly utilize AggLayer
- 16+ chains are already in the AggLayer ecosystem⁸

#### 2.1.3 Current Status
- Orderly Network has launched Orderly Omnichain on mainnet, utilizing LayerZero's cross-chain interoperability, developed with OP-Stack⁹

---

## 3. Solution Selection Recommendations

### 3.1 LayerZero Advantages
- **Ecosystem Maturity**: Supports 70+ blockchains, 200+ applications, over $50B value transferred⁷
- **Broad Compatibility**: Supports both EVM and non-EVM chains
- **Existing Integration**: Orderly Network already integrated with LayerZero⁵
- **Developer Ecosystem**: More development tools and documentation support

### 3.2 AggLayer Advantages
- **Technical Sophistication**: Uses ZK technology for better security and performance³⁴
- **User Experience**: Optimistic transaction processing, faster cross-chain experience⁴
- **Cost Efficiency**: No fee-extracting intermediaries³
- **Unified Liquidity**: Shared TVL across all connected chains³

### 3.3 Final Recommendations

**For Orderly Network:**

1. **Short-term Strategy**: Continue using LayerZero
   - Mature existing integration
   - Broader ecosystem
   - Lower technical risks

2. **Long-term Planning**: Explore AggLayer
   - More advanced technology, pessimistic proofs launched on mainnet in Q1 2025¹⁰
   - Better performance and user experience
   - Suitable for Polygon CDK ecosystem

3. **Optimal Strategy**: Adopt multi-protocol approach
   - LayerZero for broad multi-chain support
   - AggLayer for high-performance interactions within Polygon ecosystem (if Orderly consider to become Polygon CDK compatible)

---

## References

1. [From modularity to aggregation: Exploring the Agglayer core of Polygon 2.0](https://www.bitget.com/news/detail/12560604072877)
2. [In-depth comparison of cross-chain protocols LayerZero and deBridge](https://www.bitget.com/news/detail/12560604170086)
3. [Polygon Agglayer Official Documentation](https://polygon.technology/agglayer)
4. [Polygon AggLayer: Innovating Multi-chain UX](https://4pillars.io/en/articles/polygon-agglayer)
5. [LayerZero Ecosystem - Orderly Network](https://layerzero.network/ecosystem)
6. [Orderly Network Partners](https://orderly.network/partners/)
7. [Mapping Rollup Interoperability for Cross-chain Connectivity](https://www.zeeve.io/blog/mapping-rollup-interoperability-for-cross-chain-connectivity/)
8. [Why Polygon CDK's 2025 Comeback Could Silence the Doubters](https://www.zeeve.io/blog/why-polygon-cdks-2025-comeback-could-silence-the-doubters/)
9. [Orderly Network Launches Orderly Omnichain on Mainnet](https://www.coinlive.com/news-flash/308448)
10. [Polygon Q1 2025 Update: Agglayer Powers Cross-Chain Growth](https://www.tronweekly.com/agglayer-powers-cross-chain-growth-in-polygon/)

---

**Report Date**: May 16, 2025  
**Analyst**: Hannes Gao (hannes@orderly.network)