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
<img width="694" height="463" alt="image" src="https://github.com/user-attachments/assets/3153bd11-1396-45bc-995b-e240dca004c3" />

## Features

- **Rebasing Mechanism**: Token balances automatically increase based on per-user interest rates
- **Cross-Chain Bridging**: Seamlessly transfer tokens between supported chains via Chainlink CCIP
- **Interest Rate Preservation**: User interest rates are encoded and transferred with tokens
- **Burn & Mint Model**: Tokens are burned on source chain and minted on destination chain
