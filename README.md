Source by Solana Kit
<div align="center">

# Solana Agent Kit

![SAKCover2](https://github.com/user-attachments/assets/a6072421-8958-4cee-934a-a10ea32ae75e)

![NPM Downloads](https://img.shields.io/npm/dm/solana-agent-kit?style=for-the-badge)
![GitHub forks](https://img.shields.io/github/forks/sendaifun/solana-agent-kit?style=for-the-badge)
![GitHub License](https://img.shields.io/github/license/sendaifun/solana-agent-kit?style=for-the-badge)

</div>

An open-source toolkit for connecting AI agents to Solana protocols. Now, any agent, using any model can autonomously perform 60+ Solana actions:

- Trade tokens
- Launch new tokens
- Lend assets
- Send compressed airdrops
- Execute blinks
- Launch tokens on AMMs
- Bridge tokens across chains
- And more...

Anyone - whether an SF-based AI researcher or a crypto-native builder - can bring their AI agents trained with any model and seamlessly integrate with Solana.

[![Run on Repl.it](https://replit.com/badge/github/sendaifun/solana-agent-kit)](https://replit.com/@sendaifun/Solana-Agent-Kit)
> Replit template created by [Arpit Singh](https://github.com/The-x-35)

## 🔧 Core Blockchain Features

- **Token Operations**
  - Deploy SPL tokens by Metaplex
  - Transfer assets
  - Balance checks
  - Stake SOL
  - Zk compressed Airdrop by Light Protocol and Helius
  - Bridge tokens across chains using Wormhole
- **NFTs on 3.Land**
  - Create your own collection
  - NFT creation and automatic listing on 3.land
  - List your NFT for sale in any SPL token
- **NFT Management via Metaplex**
  - Collection deployment
  - NFT minting
  - Metadata management
  - Royalty configuration

- **DeFi Integration**
  - Jupiter Exchange swaps
  - Launch on Pump via PumpPortal
  - Raydium pool creation (CPMM, CLMM, AMMv4)
  - Orca Whirlpool integration
  - Manifest market creation, and limit orders
  - Meteora Dynamic AMM, DLMM Pool, and Alpha Vault
  - Openbook market creation
  - Register and Resolve SNS
  - Jito Bundles
  - Pyth Price feeds for fetching Asset Prices
  - Register/resolve Alldomains
  - Perpetuals Trading with Adrena Protocol
  - Drift Vaults, Perps, Lending and Borrowing
  - Cross-chain bridging via deBridge DLN
  - Cross chain bridging via Wormhole

- **Solana Blinks**
   - Lending by Lulo (Best APR for USDC)
   - Send Arcade Games
   - JupSOL staking
   - Solayer SOL (sSOL)staking

- **Non-Financial Actions**
  - Gib Work for registering bounties

- **Market Data Integration**
  - CoinGecko Pro API integration
  - Real-time token price data
  - Trending tokens and pools
  - Top gainers analysis
  - Token information lookup
  - Latest pool tracking

## 🤖 AI Integration Features

- **LangChain Integration**
  - Ready-to-use LangChain tools for blockchain operations
  - Autonomous agent support with React framework
  - Memory management for persistent interactions
  - Streaming responses for real-time feedback

- **Vercel AI SDK Integration**
  - Vercel AI SDK for AI agent integration
  - Framework agnostic support
  - Quick and easy toolkit setup

- **Autonomous Modes**
  - Interactive chat mode for guided operations
  - Autonomous mode for independent agent actions
  - Configurable action intervals
  - Built-in error handling and recovery

- **AI Tools**
  - DALL-E integration for NFT artwork generation
  - Natural language processing for blockchain commands
  - Price feed integration for market analysis
  - Automated decision-making capabilities

## 📃 Documentation
You can view the full documentation of the kit at [docs.sendai.fun](https://docs.sendai.fun/v0/introduction)

## 📦 Installation

```bash
npm install solana-agent-kit
```

## Quick Start

```typescript
import { SolanaAgentKit, createSolanaTools } from "solana-agent-kit";

// Initialize with private key and optional RPC URL
const agent = new SolanaAgentKit(
  "your-wallet-private-key-as-base58",
  "https://api.mainnet-beta.solana.com",
  { OPENAI_API_KEY: "your-openai-api-key" } // optional config
);

// Create LangChain tools
const tools = createSolanaTools(agent);
```

## Usage Examples

### Deploy a New Token

```typescript
const result = await agent.deployToken(
  "my ai token", // name
  "uri", // uri
  "token", // symbol
  9, // decimals
  {
    mintAuthority: null, // by default, deployer account
    freezeAuthority: null, // by default, deployer account
    updateAuthority: undefined, // by default, deployer account
    isMutable: false // by default, true
  },
  1000000 // initial supply
);

console.log("Token Mint Address:", result.mint.toString());
```

### Deploy a New Token2022

```typescript
const result = await agent.delpoyToken2022(
  "my ai token 2022", // name
  "uri", // uri
  "token2022", // symbol
  9, // decimals
  {
    mintAuthority: null, // by default, deployer account
    freezeAuthority: null, // by default, deployer account
    updateAuthority: undefined, // by default, deployer account
    isMutable: false // by default, true
  },
  1000000 // initial supply
);

console.log("Token2022 Mint Address:", result.mint.toString());
```



### Get all supported chains using Wormhole
```typescript
const chains = await agent.getWormholeSupportedChains();
console.log("Supported Chains:", chains);
```

### Create a Wrapped Token using Wormhole

```typescript

const result = await agent.createWrappedToken({
  destinationChain: "BaseSepolia", // Target chain
  tokenAddress: "4zMMC9srt5Ri5X14GAgXhaHii3GnPAEERYPJgZJDncDU", // Original token address
  network: "Testnet", // Network type (Testnet or Mainnet)
});
console.log("Wrapped Token Result:", result);
```


Note:
 When using Wormhole for cross-chain operations:
- Always verify the destination chain is supported before attempting transfers
- Use the correct network parameter ("Testnet" or "Mainnet") based on your environment
- Make sure the destination address wallet private key is presernt in the .env file as automatic transfer is not supported yet on Solana

### Perform a CCTP transfer using Wormhole
```typescript
const transfer = await agent.cctpTransfer({
  destinationChain: "Base Sepolia", // Target chain
  transferAmount: "1", // Amount to transfer
  network: "Testnet", // Network type (Testnet or Mainnet)
});
console.log("Transfer result:", transfer);
```

### Perform Token Transfer using Wormhole
```typescript
const transfer = await agent.tokenTransfer({
  destinationChain: "Base Sepolia", // Target chain
  tokenAddress: "4zMMC9srt5Ri5X14GAgXhaHii3GnPAEERYPJgZJDncDU", // Original token address or leave it empty to treansfer Native SOL
  network: "Testnet", // Network type (Testnet or Mainnet)
});
```


### Create NFT Collection on 3Land
```typescript
const isDevnet = false; // (Optional) if not present TX takes place in Mainnet
const priorityFeeParam = 1000000; // (Optional) if not present the default priority fee will be 50000

 const collectionOpts: CreateCollectionOptions = {
    collectionName: "",
    collectionSymbol: "",
    collectionDescription: "",
    mainImageUrl: ""
  };

const result = await agent.create3LandCollection(
      collectionOpts,
      isDevnet, // (Optional) if not present TX takes place in Mainnet
      priorityFeeParam, //(Optional)
    );
```

### Create NFT on 3Land
When creating an NFT using 3Land's tool, it automatically goes for sale on 3.land website
```typescript
const isDevnet = true; // (Optional) if not present TX takes place in Mainnet
const withPool = true; // (Optional) only present if NFT will be created with a Liquidity Pool for a specific SPL token
const priorityFeeParam = 1000000; // (Optional) if not present the default priority fee will be 50000
const collectionAccount = ""; //hash for the collection
const createItemOptions: CreateSingleOptions = {
  itemName: "",
  sellerFee: 500, //5%
  itemAmount: 100, //total items to be created
  itemSymbol: "",
  itemDescription: "",
  traits: [
    { trait_type: "", value: "" },
  ],
  price: 0, //100000000 == 0.1 sol, can be set to 0 for a free mint
  splHash: "", //present if listing is on a specific SPL token, if not present sale will be on $SOL, must be present if "withPool" is true
  poolName: "", // Only present if "withPool" is true
  mainImageUrl: "",
};
const result = await agent.create3LandNft(
  collectionAccount,
  createItemOptions,
  isDevnet, // (Optional) if not present TX takes place in Mainnet
  withPool
  priorityFeeParam, //(Optional)
);

```


### Create NFT Collection

```typescript
const collection = await agent.deployCollection({
  name: "My NFT Collection",
  uri: "https://arweave.net/metadata.json",
  royaltyBasisPoints: 500, // 5%
  creators: [
    {
      address: "creator-wallet-address",
      percentage: 100,
    },
  ],
});
```

### Swap Tokens

```typescript
import { PublicKey } from "@solana/web3.js";

const signature = await agent.trade(
  new PublicKey("target-token-mint"),
  100, // amount
  new PublicKey("source-token-mint"),
  300 // 3% slippage
);
```

### Lend Tokens

```typescript
import { PublicKey } from "@solana/web3.js";

const signature = await agent.lendAssets(
  100 // amount of USDC to lend
);
```

### Stake SOL

```typescript
const signature = await agent.stake(
  1 // amount in SOL to stake
);
```

### Stake SOL on Solayer

```typescript
const signature = await agent.restake(
  1 // amount in SOL to stake
);

```

### Send an SPL Token Airdrop via ZK Compression

```typescript
import { PublicKey } from "@solana/web3.js";

(async () => {
  console.log(
    "~Airdrop cost estimate:",
    getAirdropCostEstimate(
      1000, // recipients
      30_000 // priority fee in lamports
    )
  );

  const signature = await agent.sendCompressedAirdrop(
    new PublicKey("JUPyiwrYJFskUPiHa7hkeR8VUtAeFoSYbKedZNsDvCN"), // mint
    42, // amount per recipient
    [
      new PublicKey("1nc1nerator11111111111111111111111111111111"),
      // ... add more recipients
    ],
    30_000 // priority fee in lamports
  );
})();
```

### Fetch Price Data from Pyth

```typescript

const priceFeedID = await agent.getPythPriceFeedID("SOL");

const price = await agent.getPythPrice(priceFeedID);

console.log("Price of SOL/USD:", price);
```

### Open PERP Trade

```typescript
import { PublicKey } from "@solana/web3.js";

const signature = await agent.openPerpTradeLong({
  price: 300, // $300 SOL Max price
  collateralAmount: 10, // 10 jitoSOL in
  collateralMint: new PublicKey("J1toso1uCk3RLmjorhTtrVwY9HJ7X8V9yYac6Y7kGCPn"), // jitoSOL
  leverage: 50000, // x5
  tradeMint: new PublicKey("J1toso1uCk3RLmjorhTtrVwY9HJ7X8V9yYac6Y7kGCPn"), // jitoSOL
  slippage: 0.3, // 0.3%
});
```

### Close PERP Trade

```typescript
import { PublicKey } from "@solana/web3.js";

const signature = await agent.closePerpTradeLong({
  price: 200, // $200 SOL price
  tradeMint: new PublicKey("J1toso1uCk3RLmjorhTtrVwY9HJ7X8V9yYac6Y7kGCPn"), // jitoSOL
});
```

### Close Empty Token Accounts

``` typescript

const { signature } = await agent.closeEmptyTokenAccounts();
```

### Create a Drift account

Create a drift account with an initial token deposit.

```typescript
const result = await agent.createDriftUserAccount()
```

### Create a Drift Vault

Create a drift vault.

```typescript
const signature = await agent.createDriftVault({
  name: "my-drift-vault",
  marketName: "USDC-SPOT",
  redeemPeriod: 1, // in days
  maxTokens: 100000, // in token units e.g 100000 USDC
  minDepositAmount: 5, // in token units e.g 5 USDC
  managementFee: 1, // 1%
  profitShare: 10, // 10%
  hurdleRate: 5, // 5%
  permissioned: false, // public vault or whitelist
})
```

### Deposit into a Drift Vault

Deposit tokens into a drift vault.

```typescript
const signature = await agent.depositIntoDriftVault(100, "41Y8C4oxk4zgJT1KXyQr35UhZcfsp5mP86Z2G7UUzojU")
```

### Deposit into your Drift account

Deposit tokens into your drift account.

```typescript
const {txSig} = await agent.depositToDriftUserAccount(100, "USDC")
```

### Derive a Drift Vault address

Derive a drift vault address.

```typescript
const vaultPublicKey = await agent.deriveDriftVaultAddress("my-drift-vault")
```

### Do you have a Drift account

Check if agent has a drift account.

```typescript
const {hasAccount, account} = await agent.doesUserHaveDriftAccount()
```

### Get Drift account information

Get drift account information.

```typescript
const accountInfo = await agent.driftUserAccountInfo()
```

### Request withdrawal from Drift vault

Request withdrawal from drift vault.

```typescript
const signature = await agent.requestWithdrawalFromDriftVault(100, "41Y8C4oxk4zgJT1KXyQr35UhZcfsp5mP86Z2G7UUzojU")
```

### Carry out a perpetual trade using a Drift vault

Open a perpetual trade using a drift vault that is delegated to you.

```typescript
const signature = await agent.tradeUsingDelegatedDriftVault({
  vault: "41Y8C4oxk4zgJT1KXyQr35UhZcfsp5mP86Z2G7UUzojU",
  amount: 500,
  symbol: "SOL",
  action: "long",
  type: "limit",
  price: 180 // Please long limit order at $180/SOL
})
```

### Carry out a perpetual trade using your Drift account

Open a perpetual trade using your drift account.

```typescript
const signature = await agent.tradeUsingDriftPerpAccount({
  amount: 500,
  symbol: "SOL",
  action: "long",
  type: "limit",
  price: 180 // Please long limit order at $180/SOL
})
```

### Update Drift vault parameters

Update drift vault parameters.

```typescript
const signature = await agent.updateDriftVault({
  name: "my-drift-vault",
  marketName: "USDC-SPOT",
  redeemPeriod: 1, // in days
  maxTokens: 100000, // in token units e.g 100000 USDC
  minDepositAmount: 5, // in token units e.g 5 USDC
  managementFee: 1, // 1%
  profitShare: 10, // 10%
  hurdleRate: 5, // 5%
  permissioned: false, // public vault or whitelist
})
```

### Withdraw from Drift account

Withdraw tokens from your drift account.

```typescript
const {txSig} = await agent.withdrawFromDriftAccount(100, "USDC")
```

### Borrow from Drift

Borrow tokens from drift.

```typescript
const {txSig} = await agent.withdrawFromDriftAccount(1, "SOL", true)
```

### Repay Drift loan

Repay a loan from drift.

```typescript
const {txSig} = await agent.depositToDriftUserAccount(1, "SOL", true)
```

### Withdraw from Drift vault

Withdraw tokens from a drift vault after the redemption period has elapsed.

```typescript
const signature = await agent.withdrawFromDriftVault( "41Y8C4oxk4zgJT1KXyQr35UhZcfsp5mP86Z2G7UUzojU")
```

### Update the address a Drift vault is delegated to

Update the address a drift vault is delegated to.

```typescript
const signature = await agent.updateDriftVaultDelegate("41Y8C4oxk4zgJT1KXyQr35UhZcfsp5mP86Z2G7UUzojU", "new-address")
```

### Get Voltr Vault Position Values

Get the current position values and total value of assets in a Voltr vault.

```typescript
const values = await agent.voltrGetPositionValues("7opUkqYtxmQRriZvwZkPcg6LqmGjAh1RSEsVrdsGDx5K")
```

### Deposit into Voltr Strategy

Deposit assets into a specific strategy within a Voltr vault.

```typescript
const signature = await agent.voltrDepositStrategy(
  new BN("1000000000"), // amount in base units (e.g., 1 USDC = 1000000)
  "7opUkqYtxmQRriZvwZkPcg6LqmGjAh1RSEsVrdsGDx5K", // vault
  "9ZQQYvr4x7AMqd6abVa1f5duGjti5wk1MHsX6hogPsLk"  // strategy
)
```

### Withdraw from Voltr Strategy

Withdraw assets from a specific strategy within a Voltr vault.

```typescript
const signature = await agent.voltrWithdrawStrategy(
  new BN("1000000000"), // amount in base units (e.g., 1 USDC = 1000000)
  "7opUkqYtxmQRriZvwZkPcg6LqmGjAh1RSEsVrdsGDx5K", // vault
  "9ZQQYvr4x7AMqd6abVa1f5duGjti5wk1MHsX6hogPsLk"  // strategy
)
```

### Get a Solana asset by its ID

```typescript
const asset = await agent.getAsset("41Y8C4oxk4zgJT1KXyQr35UhZcfsp5mP86Z2G7UUzojU")
```

### Get a price inference from Allora

Get the price for a given token and timeframe from Allora's API

```typescript
const sol5mPrice = await agent.getPriceInference("SOL", "5m");
console.log("5m price inference of SOL/USD:", sol5mPrice);
```

### List all topics from Allora

```typescript
const topics = await agent.getAllTopics();
console.log("Allora topics:", topics);
```

### Get an inference for an specific topic from Allora

```typescript
const inference = await agent.getInferenceByTopicId(42);
console.log("Allora inference for topic 42:", inference);
```

### Simulate a Switchboard feed

Simulate a given Switchboard feed. Find or create feeds [here](https://ondemand.switchboard.xyz/solana/mainnet).

```typescript
const value = await agent.simulateSwitchboardFeed(
      "9wcBMATS8bGLQ2UcRuYjsRAD7TPqB1CMhqfueBx78Uj2", // TRUMP/USD
      "http://crossbar.switchboard.xyz");;
console.log("Simulation resulted in the following value:", value);

### Cross-Chain Swap

```typescript
import { PublicKey } from "@solana/web3.js";

const signature = await agent.swap(
  amount: "10",
  fromChain: "bsc",
  fromToken: "0x3c499c542cef5e3811e1192ce70d8cc03d5c3359",
  toChain: "solana",
  toToken: "0x0000000000000000000000000000000000000000",
  dstAddr: "0xc2d3024d64f27d85e05c40056674Fd18772dd922",
);

```

### Cross-Chain Bridge via deBridge

The Solana Agent Kit supports cross-chain token transfers using deBridge's DLN protocol. Here's how to use it:

1. Check supported chains:
```typescript
const chains = await agent.getDebridgeSupportedChains();
console.log("Available chains:", chains);
// Example output: { chains: [{ chainId: "1", chainName: "Ethereum" }, { chainId: "7565164", chainName: "Solana" }] }
```

2. Get available tokens (optional):
```typescript
const tokens = await agent.getDebridgeTokensInfo("1", "USDC"); // Search for USDC on Ethereum
console.log("Available tokens:", tokens);
// Shows tokens matching 'USDC' on the specified chain
```

3. Create bridge order (SOL -> ETH):
```typescript
const orderInput = {
  srcChainId: "7565164", // Solana
  srcChainTokenIn: "11111111111111111111111111111111", // Native SOL
  srcChainTokenInAmount: "1000000000", // 1 SOL (9 decimals)
  dstChainId: "1", // Ethereum
  dstChainTokenOut: "0x0000000000000000000000000000000000000000", // ETH
  dstChainTokenOutRecipient: "0x23C279e58ddF1018C3B9D0C224534fA2a83fb1d2" // ETH recipient
};

const order = await agent.createDebridgeOrder(orderInput);
console.log("Order created:", order);
// Contains transaction data and estimated amounts
```

4. Execute the bridge order:
```typescript
const signature = await agent.executeDebridgeOrder(order.tx.data);
console.log("Bridge transaction sent:", signature);
```

5. Check bridge status:
```typescript
const status = await agent.checkDebridgeTransactionStatus(signature);
console.log("Bridge status:", status);
// Shows current status: Created, Fulfilled, etc.
```

Note: When bridging between chains:
- To Solana: Use base58 addresses for recipients and token mints
- From Solana: Use EVM addresses for recipients and ERC-20 format for tokens
- Always verify addresses and amounts before executing bridge transactions

### Get Token Price Data from CoinGecko

```typescript
const priceData = await agent.getTokenPriceData([
  "So11111111111111111111111111111111111111112", // SOL
  "EPjFWdd5AufqSSqeM2qN1xzybapC8G4wEGGkZwyTDt1v"  // USDC
]);
console.log("Token prices:", priceData);
```

### Get Trending Tokens

```typescript
const trendingTokens = await agent.getTrendingTokens();
console.log("Trending tokens:", trendingTokens);
```

### Get Latest Pools

```typescript
const latestPools = await agent.getLatestPools();
console.log("Latest pools:", latestPools);
```

### Get Token Information

```typescript
const tokenInfo = await agent.getTokenInfo("EPjFWdd5AufqSSqeM2qN1xzybapC8G4wEGGkZwyTDt1v");
console.log("Token info:", tokenInfo);
```

### Get Top Gainers

```typescript
const topGainers = await agent.getTopGainers("24h", "all");
console.log("Top gainers:", topGainers);
```

### Get Trending Pools

```typescript
const trendingPools = await agent.getTrendingPools("24h");
console.log("Trending pools:", trendingPools);
```

## DEX API Tools

### OKX DEX Integration

The toolkit provides comprehensive integration with OKX DEX for Solana. Here's how to use the DEX API tools:

### Get Supported Tokens

```typescript
const tokens = await agent.getTokens();
console.log("Supported tokens:", tokens);
// Returns list of tokens available on OKX DEX
```

### Get DEX Quote

```typescript
const quote = await agent.getQuote(
  "So11111111111111111111111111111111111111112", // fromTokenAddress (SOL)
  "EPjFWdd5AufqSSqeM2qN1xzybapC8G4wEGGkZwyTDt1v", // toTokenAddress (USDC)
  "1000000000", // amount in base units
  "0.5" // slippage (optional, default 0.5%)
);
console.log("Swap quote:", quote);
// Returns quote data with price, fees, and slippage, token symbol, decimals
```

### Execute Token Swap

```typescript
const swapResult = await agent.executeSwap({
  fromTokenAddress: "So11111111111111111111111111111111111111112", // SOL
  toTokenAddress: "EPjFWdd5AufqSSqeM2qN1xzybapC8G4wEGGkZwyTDt1v", // USDC
  amount: "1000000000", // amount in base units
  autoSlippage: true, // optional, use auto slippage
  slippage: "0.1", // optional, custom slippage (0.1%)
  maxAutoSlippageBps: "100" // optional, max auto slippage in basis points
  userAddress: "signer-public-key" // optional, user wallet address
});
console.log("Swap executed:", swapResult);
```

### Parse Instruction Data

```typescript
const parsedData = await agent.parseInstruction(
  "<programId>",
  "<instructionData>" // base64
)

console.log("parsed data:", parsedData)
```

### Parse Instruction Data

```typescript
const parsedData = await agent.parseAccount(
  "<programId>",
  "<accountData>" // base64
)

console.log("parsed data:", parsedData)
```

### Get Chain Data

Note: To use OKX DEX integration, you need to set up the following environment variables: Get OKX API keys from the [OKX Developer Portal] (https://www.okx.com/web3/build/dev-portal)
- `OKX_API_KEY`
- `OKX_SECRET_KEY`
- `OKX_API_PASSPHRASE`
- `OKX_PROJECT_ID`
- `RPC_URL`
- `SOLANA_PRIVATE_KEY`
- `SOLANA_WALLET_ADDRESS`
## Examples

### LangGraph Multi-Agent System

The repository includes an advanced example of building a multi-agent system using LangGraph and Solana Agent Kit. Located in `examples/agent-kit-langgraph`, this example demonstrates:

- Multi-agent architecture using LangGraph's StateGraph
- Specialized agents for different tasks:
  - General purpose agent for basic queries
  - Transfer/Swap agent for transaction operations
  - Read agent for blockchain data queries
  - Manager agent for routing and orchestration
- Fully typed TypeScript implementation
- Environment-based configuration

Check out the [LangGraph example](examples/agent-kit-langgraph) for a complete implementation of an advanced Solana agent system.

## Dependencies

The toolkit relies on several key Solana and Metaplex libraries:

- @solana/web3.js
- @solana/spl-token
- @metaplex-foundation/digital-asset-standard-api
- @metaplex-foundation/mpl-token-metadata
- @metaplex-foundation/mpl-core
- @metaplex-foundation/umi
- @lightprotocol/compressed-token
- @lightprotocol/stateless.js
- @coingecko/sdk

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.
Refer to [CONTRIBUTING.md](CONTRIBUTING.md) for detailed guidelines on how to contribute to this project.

## Contributors

<a href="https://github.com/sendaifun/solana-agent-kit/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=sendaifun/solana-agent-kit" />
</a>

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=sendaifun/solana-agent-kit&type=Date)](https://star-history.com/#sendaifun/solana-agent-kit&Date)

## License

Apache-2 License

## Funding

If you wanna give back any tokens or donations to the OSS community -- The Public Solana Agent Kit Treasury Address:

Solana Network : EKHTbXpsm6YDgJzMkFxNU1LNXeWcUW7Ezf8mjUNQQ4Pa

## Security

This toolkit handles private keys and transactions. Always ensure you're using it in a secure environment and never share your private keys.

