# BioChain DataVault: Secure Genomic Research Marketplace

## Overview

BioChain DataVault is an advanced decentralized platform built on the Stacks blockchain that facilitates secure trading of genomic datasets between data contributors and research institutions. The platform provides comprehensive privacy protection, automated quality assurance, transparent pricing mechanisms, and reputation-based trust systems for accelerating genomic research collaboration.

## Key Features

- **Secure Genomic Data Trading**: Decentralized marketplace for buying and selling genomic datasets
- **Privacy Protection**: Cryptographic hashing ensures data security and privacy
- **Quality Assurance**: Peer review system with quality ratings (1-5 scale)
- **Reputation System**: Track contributor and researcher reputation scores
- **Automated Payments**: Smart contract handles payments and commission distribution
- **Access Control**: Fine-grained permissions for dataset access
- **Market Analytics**: Performance tracking and popularity rankings

## Architecture

### Core Components

1. **Dataset Management**: Registration, pricing, and availability control
2. **Access Control**: Purchase verification and permission management  
3. **Quality System**: Peer reviews and ratings from verified researchers
4. **Profile Management**: Researcher and contributor reputation tracking
5. **Administrative Functions**: Platform governance and verification

### Data Structures

- **Genomic Dataset Repository**: Stores dataset metadata, pricing, and access information
- **Research Participant Registry**: Manages user profiles and reputation
- **Access Authorization Records**: Tracks dataset purchases and permissions
- **Quality Evaluation Records**: Stores peer reviews and ratings
- **Market Performance Analytics**: Aggregates dataset statistics and popularity

## Installation & Deployment

### Prerequisites

- Stacks blockchain environment
- Clarity smart contract deployment tools
- STX tokens for transactions

### Deployment Steps

1. Deploy the smart contract to Stacks blockchain
2. The deployer automatically becomes the platform administrator
3. Configure initial commission rate (default: 8%)
4. Set operational status to active

## Usage Guide

### For Data Contributors

#### Contributing a Dataset

```clarity
(contribute-genomic-dataset-to-marketplace
  genetic-data-hash           ;; 32-byte cryptographic fingerprint
  metadata-location          ;; URI to dataset metadata (max 512 chars)
  access-price              ;; Price in microSTX (min 1000)
  research-category         ;; Classification category (max 100 chars)
  access-tier              ;; Permission level (max 30 chars)
  sample-size              ;; Number of participants
  sequencing-technology    ;; Technology used (max 150 chars)
  research-purpose        ;; Intended use (max 300 chars)
)
```

#### Managing Your Datasets

- **Update Pricing**: `modify-dataset-access-pricing`
- **Toggle Availability**: `toggle-dataset-marketplace-availability-status`

### For Researchers

#### Purchasing Dataset Access

```clarity
(acquire-genomic-dataset-research-access
  dataset-identifier        ;; Target dataset ID
  research-purpose         ;; Scientific purpose declaration (max 300 chars)
)
```

#### Reviewing Dataset Quality

```clarity
(contribute-dataset-quality-evaluation
  dataset-identifier       ;; Dataset to review
  quality-rating          ;; Score 1-5
  review-text            ;; Detailed review (max 1000 chars)
)
```

### Query Functions

#### Dataset Information
- `retrieve-comprehensive-dataset-information`
- `retrieve-dataset-market-performance-analytics`

#### User Profiles  
- `retrieve-research-participant-profile-data`
- `verify-dataset-access-authorization`

#### Platform Status
- `verify-marketplace-operational-status`
- `retrieve-current-platform-commission-percentage`

## Configuration

### Platform Settings

- **Commission Rate**: 8% default, max 25%
- **Minimum Dataset Price**: 1,000 microSTX
- **Quality Rating Scale**: 1-5 (lowest to highest)
- **Maximum Dataset ID**: 99,999,999

### Text Length Limits

- Metadata URI: 1-512 characters
- Research Category: 1-100 characters  
- Access Permission Level: 1-30 characters
- Sequencing Technology: 1-150 characters
- Research Purpose: 1-300 characters
- Quality Review: 1-1000 characters

## Administrative Functions

### Platform Management (Admin Only)

- **User Verification**: `authorize-participant-institutional-verification`
- **Commission Settings**: `configure-platform-commission-percentage`
- **Platform Control**: `toggle-biochain-marketplace-operational-status`
- **Quality Verification**: `authorize-dataset-quality-verification`

## Error Codes

| Code | Error | Description |
|------|--------|-------------|
| 200 | ERR-ADMINISTRATOR-AUTHORIZATION-REQUIRED | Admin privileges required |
| 201 | ERR-GENOMIC-DATASET-RECORD-NOT-LOCATED | Dataset not found |
| 202 | ERR-INSUFFICIENT-ACCESS-PRIVILEGES | Insufficient permissions |
| 203 | ERR-PAYMENT-AMOUNT-BELOW-REQUIREMENT | Payment too low |
| 204 | ERR-DATASET-IDENTIFIER-ALREADY-REGISTERED | Dataset ID in use |
| 205 | ERR-DATASET-PRICING-VALIDATION-FAILED | Invalid pricing |
| 206 | ERR-DATASET-TEMPORARILY-UNAVAILABLE | Dataset unavailable |
| 207 | ERR-EXISTING-ACCESS-PERMISSION-DETECTED | Access already granted |
| 208 | ERR-FUNCTION-PARAMETER-VALIDATION-FAILED | Invalid parameters |
| 209 | ERR-MARKETPLACE-OPERATIONS-SUSPENDED | Platform suspended |
| 210 | ERR-QUALITY-RATING-EXCEEDS-VALID-RANGE | Invalid rating score |
| 211 | ERR-REVIEW-SUBMISSION-NOT-AUTHORIZED | Cannot review without access |
| 212 | ERR-DATASET-IDENTIFIER-FORMAT-INVALID | Invalid dataset ID |
| 213 | ERR-TEXT-CONTENT-LENGTH-REQUIREMENTS-VIOLATED | Text length violation |
| 214 | ERR-GENETIC-DATA-HASH-STRUCTURE-INVALID | Invalid hash format |
| 215 | ERR-WALLET-ADDRESS-FORMAT-VERIFICATION-FAILED | Invalid wallet address |

## Security Features

### Data Protection
- Cryptographic hashing of genetic data
- No raw genomic data stored on-chain
- Metadata stored off-chain with URI references

### Access Control
- Purchase verification before dataset access
- Time-based access permissions
- Contributor cannot purchase own datasets

### Financial Security
- Automatic payment splitting (contributor + platform commission)
- Transparent fee structure
- Protection against double-spending

## Economics

### Revenue Model
- Platform takes configurable commission (default 8%)
- Contributors receive majority of purchase price
- Transparent fee structure

### Reputation System
- Contributors earn reputation from dataset sales
- Researchers build reputation through purchases and reviews
- Institutional verification available