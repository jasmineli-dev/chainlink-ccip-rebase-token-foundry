# CCIP Cross-Chain Rebase Token

A cross-chain rebase token built with Chainlink CCIP (Cross-Chain Interoperability Protocol). This token earns interest over time and can be bridged across supported chains while preserving its rebasing properties.

## Overview

This project implements a rebase token that:
- **Earns interest over time** — User balances grow automatically based on an interest rate
- **Bridges cross-chain** — Uses Chainlink CCIP for secure cross-chain transfers
- **Preserves interest rates** — User interest rates are maintained when bridging between chains

# Cross-Chain Transfer Flow
User initiates bridge → Calls router.ccipSend()
Source pool burns tokens → lockOrBurn() called by OnRamp
CCIP delivers message → Message sent to destination chain
Destination pool mints tokens → releaseOrMint() called by OffRamp
User receives tokens → With preserved interest rate

# Visual: Complete chainlink CCIP Setup Checklist
CHAIN A (e.g., Sepolia)                 CHAIN B (e.g., zkSync Sepolia)
═══════════════════════                 ═══════════════════════════════

□ 1. Deploy Token                       □ 1. Deploy Token
      ↓                                       ↓
□ 2. Deploy Pool                        □ 2. Deploy Pool
      ↓                                       ↓
□ 3. Token.grantMintAndBurnRole(pool)   □ 3. Token.grantMintAndBurnRole(pool)
      ↓                                       ↓
□ 4a. RegistryModule.registerAdminViaOwner(token)    □ 4a. Same
      ↓                                       ↓
□ 4b. TokenAdminRegistry.acceptAdminRole(token)      □ 4b. Same
      ↓                                       ↓
□ 4c. TokenAdminRegistry.setPool(token, pool)        □ 4c. Same
      ↓                                       ↓
□ 5. Pool.applyChainUpdates(chainB info)             □ 5. Pool.applyChainUpdates(chainA info)
      ↓                                       ↓
═══════════════════════════════════════════════════════════════
      │                                       │
      └───────────── CCIP READY ──────────────┘
                         │
                         ▼
               □ 6. Bridge tokens!

## Features

- **Rebasing Mechanism**: Token balances automatically increase based on per-user interest rates
- **Cross-Chain Bridging**: Seamlessly transfer tokens between supported chains via Chainlink CCIP
- **Interest Rate Preservation**: User interest rates are encoded and transferred with tokens
- **Burn & Mint Model**: Tokens are burned on source chain and minted on destination chain
