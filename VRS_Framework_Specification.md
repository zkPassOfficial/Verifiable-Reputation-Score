# Verifiable Reputation Score (VRS)
## A Coverage-Penalized Multi-Source Reputation Scoring Framework

---

## About VRS

The **Verifiable Reputation Score (VRS)** was first introduced as a proof-based mechanism to recognize authenticity, contribution, and engagement across the zkPass ecosystem. It quantifies how complete and credible your digital identity is across multiple verified data sources, while preserving privacy through zero-knowledge proofs.

### Key Principles

**🔒 Privacy-Preserving Verification**
VRS leverages zkPass technology to verify your reputation across platforms without exposing sensitive personal data. Zero-knowledge proofs enable validation of achievements and credentials while keeping actual values private.

**📊 Multi-Dimensional Assessment**
Rather than a single metric, VRS evaluates six distinct dimensions of your digital presence, each measuring different aspects of your online identity and contributions.

**⚖️ Coverage-Penalty Mechanism**
The framework encourages diversity by applying a mathematical penalty when users provide incomplete coverage across data sources. This prevents gaming the system through single-platform optimization.

**🌐 Cross-Platform Aggregation**
VRS aggregates verified credentials from 25+ platforms across social media, financial services, professional networks, learning platforms, and content creation sites.

---

## VRS Framework Overview

The Verifiable Reputation Score consists of **six core dimensions** plus a **social reputation component** (Yapper), totaling seven scoring components:

| Dimension | Full Name | Weight* | Data Sources | Focus Area |
|-----------|-----------|---------|--------------|------------|
| **POA** | Proof of Attention | ~14% | 3 platforms | Engagement with zkPass community |
| **POH** | Proof of Humanity | ~14% | 5 platforms | Identity verification & authenticity |
| **POSL** | Proof of Skill | ~14% | 5 platforms | Technical competence & learning |
| **POSY** | Proof of Society | ~14% | 5 platforms | Social influence & network reach |
| **POR** | Proof of Reach | ~14% | 4 platforms | Financial solvency & asset holdings |
| **POC** | Proof of Creation | ~14% | 5 platforms | Content creation & contributions |
| **Yapper** | Social Reputation | ~16% | Twitter/X API | Community engagement score |

**Total Verifiable Reputation Score Range:** 0 - 100 points

_*Weights are dynamically calculated as `ceil(100 / 7)` per component, ensuring balanced contribution._

---

## Table of Contents

1. [Understanding the Two-Level Weighting System](#understanding-the-two-level-weighting-system)
2. [Dimension Specifications](#dimension-specifications)
   - [POA - Proof of Attention](#poa---proof-of-attention)
   - [POH - Proof of Humanity](#poh---proof-of-humanity)
   - [POSL - Proof of Skill](#posl---proof-of-skill)
   - [POSY - Proof of Society](#posy---proof-of-society)
   - [POR - Proof of Reach](#por---proof-of-reach)
   - [POC - Proof of Creation](#poc---proof-of-creation)
3. [Scoring Methodology](#scoring-methodology)
   - [Property Scoring Types](#property-scoring-types)
   - [Dimension Scoring Process](#dimension-scoring-process)
4. [Platform Reference](#platform-reference)
5. [Final VRS Calculation](#final-vrs-calculation)
   - [Component Weights](#component-weights)
   - [Yapper Social Score](#yapper-social-score)
   - [VRS Score Interpretation](#vrs-score-interpretation)
   - [Privacy & Zero-Knowledge Proofs](#privacy--zero-knowledge-proofs)
6. [Summary](#summary)

---

## Understanding the Two-Level Weighting System

Each dimension uses **two types of weights** to calculate the final score:

### 1. Internal Weights (Property Level)
- **Purpose:** Combine multiple properties within the same platform
- **Scope:** Within a single platform/datasource
- **Must sum to:** 100% per platform
- **Example:** Binance in POH has KYC Level (70%) + Account Age (30%) = 100%

### 2. Cross-Datasource Weights (Platform Level)
- **Purpose:** Combine multiple platforms within the same dimension
- **Scope:** Across all platforms in a dimension
- **Must sum to:** 100% per dimension
- **Example:** POH has Binance (30%) + OKX (10%) + Coinbase (20%) + LinkedIn (20%) + Facebook (20%) = 100%

### Calculation Flow
```
Property Value → [Property Scoring] → Property Score
                                         ↓
Multiple Properties → [Internal Weights] → Platform Score
                                              ↓
Multiple Platforms → [Cross-Datasource Weights + Coverage Penalty] → Dimension Score
```

---

## Dimension Specifications

Each dimension has a unique **alpha value** that determines the strength of the coverage penalty. Lower alpha values encourage broader platform diversity, while higher alpha values place stronger emphasis on completeness.

| Dimension | Alpha | Penalty Strength | Strategic Implication |
|-----------|-------|------------------|----------------------|
| POA | 1.6 | Highest | Strong incentive to engage across all zkPass channels |
| POH | 1.2 | Lower | Flexibility in identity verification methods |
| POSL | 1.5 | Moderate | Balance between breadth and depth of skills |
| POSY | 1.5 | Moderate | Diverse social presence valued |
| POR | 1.2 | Lower | Encourages financial platform diversification |
| POC | 1.3 | Moderate-Low | Creative diversity across content types |

---

### POA - Proof of Attention

**Alpha:** 1.6 (higher penalty for missing data sources)

**Purpose:** Verifies user attention and engagement with zkPass by checking if users follow or join zkPass official channels.

### Cross-Datasource Weights

| Platform | Dimension Weight | Feature Count |
|----------|-----------------|---------------|
| Twitter (X) | 40% | 1 |
| Discord | 40% | 1 |
| Instagram | 20% | 1 |

### Platform-Specific Properties & Internal Weights

#### Twitter (X) - 40% of POA
| Property | Type | Internal Weight | Cap/Gamma | Description |
|----------|------|----------------|-----------|-------------|
| Following zkPass official account | Boolean | 100% | - | User is following @zkPass on Twitter |

#### Discord - 40% of POA
| Property | Type | Internal Weight | Cap/Gamma | Description |
|----------|------|----------------|-----------|-------------|
| Member of zkPass server | Boolean | 100% | - | User has joined the zkPass Discord server |

#### Instagram - 20% of POA
| Property | Type | Internal Weight | Cap/Gamma | Description |
|----------|------|----------------|-----------|-------------|
| Following zkPass official account | Boolean | 100% | - | User is following zkPass on Instagram |

---

## POH - Proof of Humanity

**Alpha:** 1.2 (lower penalty encourages diverse verification methods)

**Purpose:** Validates that the user is a real human through KYC-verified accounts and established social media profiles with account history.

### Cross-Datasource Weights

| Platform | Dimension Weight | Feature Count |
|----------|-----------------|---------------|
| Binance | 30% | 2 |
| OKX | 10% | 2 |
| Coinbase | 20% | 1 |
| LinkedIn | 20% | 2 |
| Facebook | 20% | 2 |

### Platform-Specific Properties & Internal Weights

#### Binance - 30% of POH
| Property | Type | Internal Weight | Cap/Gamma | Description |
|----------|------|----------------|-----------|-------------|
| KYC Verification Level | Number | 70% | Cap: 3 | User's KYC verification level (0-3) |
| Account Age | Time | 30% | Gamma: 1 | Registration date (early adopters score higher) |

#### OKX - 10% of POH
| Property | Type | Internal Weight | Cap/Gamma | Description |
|----------|------|----------------|-----------|-------------|
| KYC Verification Level | Number | 70% | Cap: 3 | User's KYC verification level (0-3) |
| Account Age | Time | 30% | Gamma: 1 | Registration date (early adopters score higher) |

#### Coinbase - 20% of POH
| Property | Type | Internal Weight | Cap/Gamma | Description |
|----------|------|----------------|-----------|-------------|
| Date of Birth Verified | Boolean | 100% | - | Account has verified birth year information |

#### LinkedIn - 20% of POH
| Property | Type | Internal Weight | Cap/Gamma | Description |
|----------|------|----------------|-----------|-------------|
| Verified Profile | Boolean | 70% | - | Account has a valid profile ID |
| Account Age | Time | 30% | Gamma: 1.5 | Profile creation date (slower maturity curve) |

#### Facebook - 20% of POH
| Property | Type | Internal Weight | Cap/Gamma | Description |
|----------|------|----------------|-----------|-------------|
| Verified Account | Boolean | 70% | - | Account has a valid user ID |
| Account History | Time | 30% | Gamma: 1.5 | Account metadata timestamp (slower maturity curve) |

---

## POSL - Proof of Skill

**Alpha:** 1.5 (moderate penalty balances breadth and depth)

**Purpose:** Evaluates technical skills, learning achievements, and contributions to professional and educational platforms.

### Cross-Datasource Weights

| Platform | Dimension Weight | Feature Count |
|----------|-----------------|---------------|
| GitHub | 40% | 1 |
| Duolingo | 20% | 1 |
| Stack Overflow | 20% | 1 |
| Kaggle | 10% | 2 |
| LeetCode | 10% | 1 |

### Platform-Specific Properties & Internal Weights

#### GitHub - 40% of POSL
| Property | Type | Internal Weight | Cap/Gamma | Description |
|----------|------|----------------|-----------|-------------|
| Annual Contributions | Number | 100% | Cap: 300 | Total contributions in the past year |

#### Duolingo - 20% of POSL
| Property | Type | Internal Weight | Cap/Gamma | Description |
|----------|------|----------------|-----------|-------------|
| Current Streak | Number | 100% | Cap: 14 | Consecutive days of learning activity |

#### Stack Overflow - 20% of POSL
| Property | Type | Internal Weight | Cap/Gamma | Description |
|----------|------|----------------|-----------|-------------|
| Reputation Score | Number | 100% | Cap: 1000 | Community-earned reputation points |

#### Kaggle - 10% of POSL
| Property | Type | Internal Weight | Cap/Gamma/Map | Description |
|----------|------|----------------|---------------|-------------|
| Performance Tier | Tiered | 70% | Contributor: 25%<br>Expert: 50%<br>Master: 75%<br>Grandmaster: 100% | Competition performance ranking |
| Max Day Streak | Number | 30% | Cap: 14 | Longest consecutive activity streak |

#### LeetCode - 10% of POSL
| Property | Type | Internal Weight | Cap/Gamma | Description |
|----------|------|----------------|-----------|-------------|
| Total Points | Number | 100% | Cap: 300 | Points earned from solving problems |

---

## POSY - Proof of Society

**Alpha:** 1.5 (moderate penalty balances breadth and depth)

**Purpose:** Measures social influence, network size, and community engagement across various social media platforms.

### Cross-Datasource Weights

| Platform | Dimension Weight | Feature Count |
|----------|-----------------|---------------|
| Twitter (X) | 60% | 1 |
| Instagram | 10% | 1 |
| TikTok | 10% | 1 |
| LinkedIn | 10% | 1 |
| YouTube | 10% | 3 |

### Platform-Specific Properties & Internal Weights

#### Twitter (X) - 60% of POSY
| Property | Type | Internal Weight | Cap | Description |
|----------|------|----------------|-----|-------------|
| Follower Count | Number | 100% | 1000 | Number of followers on Twitter/X |

#### Instagram - 10% of POSY
| Property | Type | Internal Weight | Cap | Description |
|----------|------|----------------|-----|-------------|
| Follower Count | Number | 100% | 1000 | Number of Instagram followers |

#### TikTok - 10% of POSY
| Property | Type | Internal Weight | Cap | Description |
|----------|------|----------------|-----|-------------|
| Follower Count | Number | 100% | 1000 | Number of TikTok followers |

#### LinkedIn - 10% of POSY
| Property | Type | Internal Weight | Cap | Description |
|----------|------|----------------|-----|-------------|
| Total Connections | Number | 100% | 500 | Number of professional connections |

#### YouTube - 10% of POSY
| Property | Type | Internal Weight | Cap | Description |
|----------|------|----------------|-----|-------------|
| Subscriber Count | Number | 40% | 200 | Channel subscribers |
| Video Count | Number | 20% | 20 | Total videos published |
| Total Views | Number | 40% | 10000 | Cumulative video view count |

---

## POR - Proof of Reach

**Alpha:** 1.2 (lower penalty encourages financial diversification)

**Purpose:** Validates financial solvency and asset holdings across cryptocurrency exchanges and payment platforms. Note: Actual amounts are privacy-preserved; only proof of meeting thresholds is verified.

### Cross-Datasource Weights

| Platform | Dimension Weight | Feature Count |
|----------|-----------------|---------------|
| Binance | 25% | 1 |
| OKX | 25% | 1 |
| PayPal | 25% | 1 |
| Kraken | 25% | 1 |

### Platform-Specific Properties & Internal Weights

#### Binance - 25% of POR
| Property | Type | Internal Weight | Cap (USD) | Description |
|----------|------|----------------|-----------|-------------|
| Total Asset Value | Number | 100% | 20,000 | Total portfolio value in USD equivalent |

#### OKX - 25% of POR
| Property | Type | Internal Weight | Cap (USD) | Description |
|----------|------|----------------|-----------|-------------|
| Total Valuation | Number | 100% | 10,000 | Total account valuation in USD |

#### PayPal - 25% of POR
| Property | Type | Internal Weight | Cap (USD) | Description |
|----------|------|----------------|-----------|-------------|
| Available Balance | Number | 100% | 3,000 | Current available balance in account |

#### Kraken - 25% of POR
| Property | Type | Internal Weight | Cap (USD) | Description |
|----------|------|----------------|-----------|-------------|
| Available Balance | Number | 100% | 10,000 | Available balance ready for trading |

---

## POC - Proof of Creation

**Alpha:** 1.3 (moderate-low penalty rewards creative diversity)

**Purpose:** Rewards content creation and meaningful community contributions across blogging, Q&A, and creative platforms.

### Cross-Datasource Weights

| Platform | Dimension Weight | Feature Count |
|----------|-----------------|---------------|
| Medium | 20% | 1 |
| Reddit | 20% | 2 |
| Quora | 20% | 3 |
| Tumblr | 20% | 2 |
| Unsplash | 20% | 2 |

### Platform-Specific Properties & Internal Weights

#### Medium - 20% of POC
| Property | Type | Internal Weight | Cap | Description |
|----------|------|----------------|-----|-------------|
| Published Articles | Number | 100% | 10 | Number of published stories/articles |

#### Reddit - 20% of POC
| Property | Type | Internal Weight | Cap | Description |
|----------|------|----------------|-----|-------------|
| Karma Points | Number | 40% | 1000 | Community upvotes earned (quality signal) |
| Total Contributions | Number | 60% | 300 | Posts and comments made |

#### Quora - 20% of POC
| Property | Type | Internal Weight | Cap | Description |
|----------|------|----------------|-----|-------------|
| Public Answers | Number | 50% | 100 | Number of public answers provided |
| Posts Published | Number | 20% | 50 | Total posts created |
| Follower Count | Number | 30% | 100 | Number of followers |

#### Tumblr - 20% of POC
| Property | Type | Internal Weight | Cap | Description |
|----------|------|----------------|-----|-------------|
| Posts Published | Number | 70% | 30 | Total blog posts created |
| Follower Count | Number | 30% | 100 | Blog followers |

#### Unsplash - 20% of POC
| Property | Type | Internal Weight | Cap | Description |
|----------|------|----------------|-----|-------------|
| Total Photo Views | Number | 30% | 1000 | All-time views of uploaded photos |
| Photo Downloads | Number | 70% | 100 | Times photos were downloaded (quality signal) |

---

## Scoring Methodology

### Property Scoring Types

### Number (Logarithmic with Cap)
Numerical values are scored using logarithmic scaling with a saturation point:
- **Formula:** `log(min(value, cap) + 1) / log(cap + 1)`
- **Behavior:** Provides diminishing returns as values increase
- **Cap:** Maximum value that contributes to the score (values above are capped)
- **Example:** With cap=1000, having 500 followers scores ~70%, while 1000 followers scores 100%

### Boolean (Yes/No)
Binary verification of property existence or condition:
- **Score:** 1.0 (100%) if true/exists, 0.0 (0%) if false/missing
- **Use Case:** Verifying account ownership, following status, KYC completion

### Time (Account Age)
Rewards older accounts with temporal maturity scoring:
- **Base Date:** October 1, 2025
- **Formula:** `accountAge / (accountAge + gamma)`
- **Gamma Parameter:** Controls how quickly accounts mature:
  - **Low gamma (1.0):** Fast maturity - newer accounts can score high quickly
  - **High gamma (1.5):** Slow maturity - favors significantly older accounts
- **Example:** 2-year-old account with gamma=1.0 scores 67%, with gamma=1.5 scores 57%

### Tiered (Categorical Levels)
Maps categorical achievement levels to predefined scores:
- **Use Case:** Performance tiers, ranking levels, achievement badges
- **Example:** Kaggle tiers - Contributor: 25%, Expert: 50%, Master: 75%, Grandmaster: 100%
- **Default:** 0% for unrecognized values

---

### Dimension Scoring Process

Dimension scoring uses a **two-level weighting system**: internal weights and cross-datasource weights.

### Step 1: Individual Property Scoring
Each property within a platform is scored individually using its type-specific formula (Number, Boolean, Time, or Tiered).

**Example:** GitHub's "Annual Contributions" with value 150:
- Type: Number with Cap: 300
- Score = log(150 + 1) / log(300 + 1) ≈ 0.86 (86%)

### Step 2: Platform Scoring (Internal Weights)
Properties within the same platform are combined using **internal weights** to produce a single platform score.

**Formula:** `Platform Score = Σ(Property Score × Internal Weight)`

**Example - Binance in POH:**
- KYC Level = 2 → Score ≈ 90% (internal weight: 70%)
- Account Age = 1.5 years → Score ≈ 60% (internal weight: 30%)
- **Binance Platform Score = (0.90 × 0.70) + (0.60 × 0.30) = 0.81 (81%)**

> **Internal weights** must sum to 100% within each platform.

### Step 3: Dimension Scoring (Cross-Datasource Weights)
Platforms within a dimension are aggregated using **cross-datasource weights** with a completeness penalty:

```
Dimension Score = Aggregated Score × (Coverage Penalty) × 100
```

**Formula:** `Aggregated Score = Σ(Platform Score × Cross-Datasource Weight)` for all platforms with attestations

**Where:**
- **Cross-Datasource Weight** = The dimension weight assigned to each platform
- **Coverage Penalty** = (Weighted Coverage)^(alpha - 1)
- **Weighted Coverage** = Sum of cross-datasource weights for platforms with attestations
- **Alpha** = Penalty exponent (dimension-specific, ranges from 1.2 to 1.6)

> **Cross-datasource weights** must sum to 100% within each dimension.

### Why the Penalty Matters
The penalty encourages users to provide attestations across **multiple platforms** rather than focusing on just one. Higher alpha = stronger penalty for incomplete coverage.

### Complete Example: POA Dimension

**Scenario:** User attests Twitter and Discord, but not Instagram

**Step 1 - Platform Scores (using internal weights):**
- Twitter: Following = Yes → Score = 100% (internal weight: 100%)
  - Twitter Platform Score = 100%
- Discord: Member = Yes → Score = 100% (internal weight: 100%)
  - Discord Platform Score = 100%
- Instagram: Not attested

**Step 2 - Dimension Scoring (using cross-datasource weights):**
- Twitter Platform Score: 100% × Cross-Datasource Weight: 40% = 0.40
- Discord Platform Score: 100% × Cross-Datasource Weight: 40% = 0.40
- Instagram: Not attested (would be 20%)

**Step 3 - Apply Coverage Penalty:**
- Aggregated Score = 0.40 + 0.40 = 0.80
- Weighted Coverage = 40% + 40% = 80% (missing Instagram's 20%)
- Coverage Penalty = 0.8^(1.6-1) = 0.8^0.6 ≈ 0.87
- **Final POA Score = 0.80 × 0.87 × 100 = 70 points**

**If all three platforms were attested:**
- Aggregated Score = 0.40 + 0.40 + 0.20 = 1.00
- Weighted Coverage = 100%
- Coverage Penalty = 1.0^0.6 = 1.0 (no penalty)
- **Final POA Score = 1.00 × 1.0 × 100 = 100 points**

---

## Platform Reference

### Platform-to-Dimension Mapping

| Platform | Used In Dimensions | Notes |
|----------|-------------------|-------|
| **Twitter (X)** | POA, POSY | High weight in both - primary social platform |
| **Discord** | POA | Community engagement verification |
| **Instagram** | POA, POSY | Following zkPass (POA), Follower count (POSY) |
| **Binance** | POH, POR | KYC + account age (POH), Asset value (POR) |
| **OKX** | POH, POR | KYC + account age (POH), Asset value (POR) |
| **Coinbase** | POH | KYC verification only |
| **Kraken** | POR | Financial solvency only |
| **PayPal** | POR | Traditional finance solvency |
| **LinkedIn** | POH, POSY | Account verification (POH), Connections (POSY) |
| **Facebook** | POH | Identity verification only |
| **GitHub** | POSL | Highest weight in skill dimension |
| **Duolingo** | POSL | Learning consistency |
| **Kaggle** | POSL | Data science expertise |
| **Stack Overflow** | POSL | Technical community reputation |
| **LeetCode** | POSL | Algorithm problem-solving |
| **TikTok** | POSY | Social media presence |
| **YouTube** | POSY | Content creator metrics |
| **Medium** | POC | Long-form content creation |
| **Reddit** | POC | Community contributions |
| **Quora** | POC | Q&A contributions |
| **Tumblr** | POC | Blogging and creative expression |
| **Unsplash** | POC | Photography and visual content |

---

## Final VRS Calculation

### Aggregating Dimensions into Your Verifiable Reputation Score

The final **Verifiable Reputation Score (VRS)** combines all six dimensions plus the Yapper social score into a single 0-100 metric:

```
VRS = Σ(Dimension Score × Dimension Weight) + (Yapper Score × Yapper Weight)
```

### Component Weights

| Component | Weight Formula | Typical Weight | Contribution Range |
|-----------|----------------|----------------|-------------------|
| POA Score | `ceil(100 / 7)` | ~14-15% | 0-15 points |
| POH Score | `ceil(100 / 7)` | ~14-15% | 0-15 points |
| POSL Score | `ceil(100 / 7)` | ~14-15% | 0-15 points |
| POSY Score | `ceil(100 / 7)` | ~14-15% | 0-15 points |
| POR Score | `ceil(100 / 7)` | ~14-15% | 0-15 points |
| POC Score | `ceil(100 / 7)` | ~14-15% | 0-15 points |
| Yapper Score | Remainder | ~15-16% | 0-16 points |
| **Total VRS** | **100%** | **100%** | **0-100 points** |

### Yapper Social Score

**Yapper** is an external social reputation metric from the Yapper platform that measures engagement and influence on Twitter/X. It's integrated into VRS as the seventh component:

- **Data Source:** Yapper API (yapper.io)
- **Metric:** Total Yapper points earned
- **Cap:** Configurable via `yap.yaml` (typically ~1000-10000)
- **Scoring:** Logarithmic scaling similar to numerical properties
- **Update Frequency:** Automatically refreshed every 4 hours via scheduled job

### Example VRS Calculation

**User Profile:**
- POA: 70 points (missing Instagram) × 14% = 9.8
- POH: 85 points (has 4/5 platforms) × 14% = 11.9
- POSL: 45 points (GitHub only) × 14% = 6.3
- POSY: 60 points (Twitter + LinkedIn) × 14% = 8.4
- POR: 0 points (no financial attestations) × 14% = 0
- POC: 55 points (Reddit + Medium) × 14% = 7.7
- Yapper: 80 points × 16% = 12.8

**Total VRS = 9.8 + 11.9 + 6.3 + 8.4 + 0 + 7.7 + 12.8 = 56.9 points**

### VRS Score Interpretation

| VRS Range | Tier | Interpretation |
|-----------|------|----------------|
| 80-100 | Elite | Highly verified across all dimensions with strong coverage |
| 60-79 | Advanced | Well-established presence with good multi-platform verification |
| 40-59 | Intermediate | Moderate verification with room for expansion |
| 20-39 | Emerging | Limited verification, early stage participation |
| 0-19 | Minimal | Very limited or single-dimension verification |

### Privacy & Zero-Knowledge Proofs

**What VRS Reveals:**
- Your aggregate score across dimensions (0-100)
- Which platforms you've verified (schema IDs)
- Your relative ranking position

**What VRS Keeps Private:**
- Exact values (follower counts, account balances, etc.)
- Personal identifiable information (names, emails, addresses)
- Specific transaction details or private account data

All attestations use **zkPass zero-knowledge proof technology**, meaning validators can verify claims without accessing underlying private data. For example, a POR attestation proves "user has >$5000 in Binance" without revealing the exact amount.

---

## Summary

The **Verifiable Reputation Score (VRS)** is a comprehensive, privacy-preserving framework that:

✅ **Measures multi-dimensional reputation** across 6 core areas of digital identity
✅ **Incentivizes platform diversity** through coverage-penalty mechanisms
✅ **Preserves user privacy** via zero-knowledge proof attestations
✅ **Prevents gaming** by requiring balanced contributions across dimensions
✅ **Provides verifiable credentials** for zkPass Pre-TGE reputation campaign

By participating in VRS, users build a holistic, verifiable reputation that reflects their authenticity, contributions, and engagement across the broader digital ecosystem—all while maintaining control over their private data.
