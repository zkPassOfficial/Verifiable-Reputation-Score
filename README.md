# 🧩 Verifiable Reputation Score (VRS)
### A Coverage-Penalized Multi-Source Reputation Scoring Framework

<br>

## Repository status

This repository contains this overview and the [framework specification](./VRS_Framework_Specification.md). It contains no scoring implementation, API client, `yap.yaml`, scheduler, build configuration, tests, or CI workflow. Features, privacy properties, integrations, and campaign use described below are design goals, not verified deployment behavior.

The component weights remain an unresolved design decision: the tables/example use six 14% components plus 16% Yapper, while the original `ceil(100 / 7)` rule implies six 15% components plus a 10% remainder. Both sum to 100%; this documentation does not select a production policy.

## 📘 Overview

The **Verifiable Reputation Score (VRS)** is a proposed **proof-based reputation scoring framework** for the **zkPass ecosystem**.
It is intended to measure signals of user authenticity, engagement, and contributions across multiple verified data sources with a goal of limiting sensitive-data disclosure through **zero-knowledge proofs (ZKPs)**.

Unlike traditional single-metric systems, VRS evaluates reputation across several independent dimensions, encouraging a well-rounded and verifiable digital identity.

<br>

## 🔑 Core Principles

- **Privacy-Preserving Verification** — Aims to validate selected claims using ZK proofs; disclosure depends on the eventual proof inputs, public outputs, and data handling.
- **Multi-Dimensional Reputation** — Considers identity, skills, engagement, and influence for a more holistic assessment.
- **Coverage-Penalty Mechanism** — Rewards users for balanced participation across different platforms.
- **Cross-Platform Aggregation** — The specification lists 22 distinct platforms across the six core dimensions; repeated appearances produce 27 dimension/platform entries. Integration code is not included.

<br>

## 🧩 Framework Structure

VRS is composed of six major dimensions plus one external social component:

| Code | Dimension | Description | Illustrative Weight |
|------|------------|-------------|----------------|
| **POA** | Proof of Attention | Engagement within zkPass ecosystem | ~14% |
| **POH** | Proof of Humanity | KYC and identity verification | ~14% |
| **POSL** | Proof of Skill | Technical ability and learning progress | ~14% |
| **POSY** | Proof of Society | Network size and community influence | ~14% |
| **POR** | Proof of Reach | Financial solvency and diversification | ~14% |
| **POC** | Proof of Creation | Content creation and creative contributions | ~14% |
| **Yapper** | Social Reputation | Twitter/X engagement score | ~16% |

**Total Score Range:** 0–100 points

<br>

## ⚙️ How It Works

VRS aggregates verified credentials from different platforms and evaluates them within each dimension.
Each dimension is designed with its own weighting and penalty settings to balance depth (within one area) and diversity (across multiple areas).
Users who maintain activity and verification across several dimensions achieve higher overall credibility scores.

The coverage penalty discourages narrow participation mathematically. It does not establish resistance to fabricated credentials, duplicate identities, collusion, or other manipulation; those require implementation and evaluation.

<br>

## 🧮 Scoring Dimensions Summary

- **Proof of Attention (POA):** Measures engagement with zkPass through verified follow, join, or participation actions.
- **Proof of Humanity (POH):** Confirms authenticity via KYC-verified and age-established accounts.
- **Proof of Skill (POSL):** Assesses technical proficiency and consistent learning activity.
- **Proof of Society (POSY):** Evaluates social influence and community presence.
- **Proof of Reach (POR):** Validates asset ownership and financial credibility without revealing amounts.
- **Proof of Creation (POC):** Recognizes creators for publishing meaningful content across multiple platforms.
- **Yapper (Social Reputation):** Proposed external engagement input for Twitter/X influence; no live API integration is included.

<br>

## 📊 Reputation Tiers

| Score Range | Tier | Description |
|--------------|------|-------------|
| **80 ≤ score ≤ 100** | Elite | High aggregate score; coverage still needs separate inspection |
| **60 ≤ score < 80** | Advanced | Strong presence with broad coverage |
| **40 ≤ score < 60** | Intermediate | Verified in several areas, some gaps remain |
| **20 ≤ score < 40** | Emerging | Early participation or limited coverage |
| **0 ≤ score < 20** | Minimal | Few or single attestations verified |

<br>

## 🔐 Privacy & Verifiability

The proposed disclosure boundary is to publish aggregate reputation/coverage while keeping raw credentials and values private. The specification also proposes public schema IDs and relative ranking; the exact public-output contract is still to be defined.

A proof can establish a selected predicate such as a balance threshold, but no proof circuit, verifier, storage policy, or privacy evaluation is supplied here. Scores and coverage can themselves reveal information. No guarantee that private inputs cannot be inferred is established by these documents; numeric scoring and threshold-only proofs also need a defined relationship before implementation.

<br>

## 🚀 Why VRS Matters

- **Verifiable:** Aim to bind scoring inputs and outputs to verifiable claims.
- **Coverage-aware:** Explicit weighting and penalties make participation incentives inspectable; fairness is not established.
- **Private by design goal:** Minimize disclosure; implementation and privacy review are still required.
- **Interoperable:** Built for zkPass, but extendable across other Web3 ecosystems.
- **Future-Ready:** Enables decentralized reputation for identity, governance, and credit systems.

<br>

## 💡 Summary

The **Verifiable Reputation Score (VRS)** introduces a new standard for digital trust —
combining **multi-source reputation**, **verifiable computation**, and **privacy-by-design** principles.

For formulas, dimension tables, worked examples, and unresolved decisions, continue to the [framework specification](./VRS_Framework_Specification.md). No executable setup or test command exists in this repository.

---
