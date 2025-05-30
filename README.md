# Compound DeFi

A practical solution repository for developing, testing, and demonstrating decentralized finance (DeFi) smart contracts using Solidity and Vyper. This project is intended for developers who want to experiment with DeFi protocols such as Compound, Chainlink, and flash minting on Ethereum mainnet forks.

---

## Features

- **Integration with DeFi Protocols**: 
  - Interacts with major protocols including Compound and Chainlink.
  - Demonstrates borrowing, lending, liquidation, and long/short strategies with ERC20 tokens and ETH.
  - Provides flash minting/wrapping solutions (e.g., WETH flash mint).

- **Test Environment**:
  - Forks Ethereum mainnet using Infura or ArchiveNode for realistic contract testing.
  - Unlocks token whale accounts to provide deep liquidity for testing.
  - Includes comprehensive tests for Compound (ETH, ERC20, liquidation, leverage/long), Vyper contracts, Chainlink price feeds, and flash minting.

- **Multi-language Support**:
  - Supports both Solidity and Vyper contract development.
  - Truffle and Vyper environment setup instructions included.

---

## Install

### Linux/MacOS

```bash
# install vyper
virtualenv -p python3 venv
source venv/bin/activate
pip install vyper

cp .env.sample .env
```

### Windows

```bash
virtualenv -p python3 venv
venv\Scripts\activate
pip install vyper
```

---

## To Run

```bash
# Activate environment
source venv/bin/activate  # or `venv\Scripts\activate` on Windows

# Compile smart contracts
truffle compile
```

---

## Testing

Before running tests, source your `.env` file with the required whale addresses and API keys.

Fork mainnet with Ganache using Infura:

```bash
source .env

npx ganache-cli \
--fork https://mainnet.infura.io/v3/$WEB3_INFURA_PROJECT_ID \
--unlock $WETH_WHALE \
--unlock $DAI_WHALE \
--unlock $USDC_WHALE \
--unlock $USDT_WHALE \
--unlock $WBTC_WHALE \
--networkId 999
```

Or using ArchiveNode:

```bash
BLOCK=11597142
ARCHIVE_NODE_URL=https://api.archivenode.io/$ARCHIVE_NODE_API_KEY@$BLOCK

ganache-cli \
--fork $ARCHIVE_NODE_URL \
--unlock $WETH_WHALE \
--unlock $DAI_WHALE \
--unlock $USDC_WHALE \
--unlock $USDT_WHALE \
--unlock $WBTC_WHALE \
--networkId 999
```

Run tests:

```bash
env $(cat .env) npx truffle test --network mainnet_fork test/test-erc20.js
env $(cat .env) npx truffle test --network mainnet_fork test/test-dydx-solo-margin.js
```


---

## License

MIT License

---

## Author

TartarusDevtech
