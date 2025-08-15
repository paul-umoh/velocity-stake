# VelocityStake Protocol

**Next-generation DeFi staking platform with intelligent reward optimization, tiered governance, and adaptive risk management.**

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Clarity Version](https://img.shields.io/badge/clarity-v3-brightgreen.svg)](https://docs.stacks.co/clarity)
[![Tests](https://img.shields.io/badge/tests-passing-brightgreen.svg)](#testing)

## Overview

VelocityStake revolutionizes DeFi staking by combining algorithmic reward distribution with dynamic governance mechanisms. Users benefit from multi-tiered staking rewards that scale with commitment levels, participate in protocol evolution through weighted voting systems, and enjoy robust risk management with emergency safeguards.

### Key Features

- **🚀 Multi-Tiered Staking System**: Progressive reward multipliers based on stake amounts
- **⏰ Time-Locked Commitments**: Enhanced rewards for longer staking periods
- **🏛️ Decentralized Governance**: Weighted voting system for protocol decisions
- **🛡️ Security Mechanisms**: Cooldown periods and emergency pause functionality
- **📊 Real-Time Analytics**: Comprehensive position tracking and health monitoring
- **⚡ Algorithmic Rewards**: Dynamic reward calculation based on multiple factors

## Architecture

### Tier System

| Tier | Minimum Stake | Reward Multiplier | Features |
|------|---------------|-------------------|----------|
| **Entry (Tier 1)** | 1 STX | 1.0x | Basic staking |
| **Advanced (Tier 2)** | 5 STX | 1.5x | Governance participation |
| **Elite (Tier 3)** | 10 STX | 2.0x | Full protocol access |

### Time-Lock Bonuses

- **No Lock**: Base rewards (1.0x multiplier)
- **1 Month Lock**: 1.25x reward boost
- **2 Month Lock**: 1.5x reward boost

## Smart Contract Functions

### Public Functions

#### Core Staking Operations

- `stake-stx(amount, lock-period)` - Stake STX with optional time-lock commitment
- `initiate-unstake(amount)` - Begin unstaking process with security cooldown
- `complete-unstake()` - Complete unstaking after cooldown period

#### Governance System

- `create-proposal(description, voting-period)` - Create governance proposals
- `vote-on-proposal(proposal-id, vote-for)` - Cast weighted votes

#### Administrative Functions

- `initialize-contract()` - Initialize protocol configuration
- `pause-contract()` - Emergency protocol pause
- `resume-contract()` - Resume protocol operations

### Read-Only Functions

- `get-contract-owner()` - Get protocol owner address
- `get-stx-pool()` - Get total STX pool value
- `get-proposal-count()` - Get current proposal count

## Installation & Setup

### Prerequisites

- [Clarinet](https://github.com/hirosystems/clarinet) v2.0+
- [Node.js](https://nodejs.org/) v18+
- [Git](https://git-scm.com/)

### Quick Start

1. **Clone the repository**

   ```bash
   git clone https://github.com/paul-umoh/velocity-stake.git
   cd velocity-stake
   ```

2. **Install dependencies**

   ```bash
   npm install
   ```

3. **Run contract checks**

   ```bash
   clarinet check
   ```

4. **Execute tests**

   ```bash
   npm test
   ```

### Development Workflow

```bash
# Format contracts
clarinet fmt

# Run static analysis
clarinet check

# Launch Clarinet console
clarinet console

# Run tests with coverage
npm run test:report

# Watch mode for continuous testing
npm run test:watch
```

## Testing

The protocol includes comprehensive test coverage using Vitest and Clarinet SDK:

```bash
# Run all tests
npm test

# Run tests with detailed reporting
npm run test:report

# Continuous testing during development
npm run test:watch
```

### Test Coverage

- ✅ Staking functionality
- ✅ Unstaking with cooldown periods
- ✅ Tier-based reward calculations
- ✅ Governance proposal creation and voting
- ✅ Emergency pause mechanisms
- ✅ Edge cases and error handling

## Security Features

### Multi-Layer Protection

1. **Cooldown Periods**: 24-hour security delay for unstaking operations
2. **Emergency Pause**: Protocol-wide pause capability for critical situations
3. **Input Validation**: Comprehensive validation for all user inputs
4. **Access Controls**: Role-based permissions for administrative functions

### Audit Considerations

- Arithmetic overflow protection
- Reentrancy attack prevention
- Proper error handling and validation
- Time-based attack mitigation

## Governance

### Proposal System

The protocol features a decentralized governance system where:

- **Proposal Creation**: Minimum 1 STX voting power required
- **Weighted Voting**: Vote power proportional to staked amount
- **Time Limits**: Configurable voting periods (100-2880 blocks)
- **Execution**: Automated proposal execution after successful voting

### Governance Parameters

| Parameter | Value | Description |
|-----------|-------|-------------|
| Minimum Voting Power | 1 STX | Required to create proposals |
| Min Voting Period | 100 blocks | Shortest voting duration |
| Max Voting Period | 2880 blocks | Longest voting duration (~1 day) |
| Proposal Description | 10-256 chars | Valid description length |

## API Reference

### Error Codes

```clarity
ERR-NOT-AUTHORIZED (u1000)     - Insufficient permissions
ERR-INVALID-PROTOCOL (u1001)   - Protocol validation failure
ERR-INVALID-AMOUNT (u1002)     - Invalid amount specified
ERR-INSUFFICIENT-STX (u1003)   - Insufficient STX balance
ERR-COOLDOWN-ACTIVE (u1004)    - Cooldown period active
ERR-NO-STAKE (u1005)           - No active stake found
ERR-BELOW-MINIMUM (u1006)      - Below minimum stake threshold
ERR-PAUSED (u1007)             - Protocol is paused
```

### Data Structures

#### UserPositions

```clarity
{
  total-collateral: uint,
  total-debt: uint,
  health-factor: uint,
  last-updated: uint,
  stx-staked: uint,
  analytics-tokens: uint,
  voting-power: uint,
  tier-level: uint,
  rewards-multiplier: uint
}
```

#### StakingPositions

```clarity
{
  amount: uint,
  start-block: uint,
  last-claim: uint,
  lock-period: uint,
  cooldown-start: (optional uint),
  accumulated-rewards: uint
}
```

## Contributing

We welcome contributions to the VelocityStake Protocol! Please follow these guidelines:

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/amazing-feature`)
3. **Commit** your changes (`git commit -m 'Add amazing feature'`)
4. **Push** to the branch (`git push origin feature/amazing-feature`)
5. **Open** a Pull Request

### Development Standards

- Follow Clarity best practices
- Maintain comprehensive test coverage
- Add detailed documentation for new features
- Ensure all tests pass before submitting PRs

## Roadmap

### Phase 1: Core Protocol ✅

- [x] Multi-tier staking system
- [x] Time-lock mechanisms
- [x] Basic governance framework
- [x] Security features

### Phase 2: Enhanced Features 🚧

- [ ] Liquid staking tokens
- [ ] Cross-protocol integrations
- [ ] Advanced analytics dashboard
- [ ] Mobile wallet integration

### Phase 3: Ecosystem Expansion 📅

- [ ] Multi-asset staking support
- [ ] DeFi yield farming
- [ ] DAO treasury management
- [ ] Institutional features

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Built on the [Stacks](https://www.stacks.co/) blockchain
- Powered by [Clarity](https://clarity-lang.org/) smart contracts
- Testing framework by [Clarinet](https://github.com/hirosystems/clarinet)
