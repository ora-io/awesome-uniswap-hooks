# 🦄️ Awesome Uniswap v4 Hooks

> Check out [Uniswap v4 Launch Announcement](https://uniswapfoundation.mirror.xyz/MHmGXC9KZOL1VkKERF2ZwrR6RuYzLLoBV3eM67cMjXY) for more contents.

A curated list of awesome [Uniswap v4](https://github.com/Uniswap/v4-core) [hooks](https://github.com/Uniswap/v4-periphery/tree/main/contracts/hooks) resources.

Special thanks to Uniswap Foundation for [including this resource in the official doc](https://web.archive.org/web/20230915081852/https://docs.uniswapfoundation.org/hooks/hook-examples) and [mentioning this work in the blog](https://web.archive.org/web/20231019143600/https://blog.uniswap.org/uniswap-v4-community-contributions)!

## 📑 Table of Contents

- [🦄️ Awesome Uniswap v4 Hooks](#️-awesome-uniswap-v4-hooks)
  - [📑 Table of Contents](#-table-of-contents)
  - [🤔 Introduction](#-introduction)
  - [🔄 Lifecycle](#-lifecycle)
  - [🔧 Functionalities](#-functionalities)
  - [📜 Examples](#-examples)
    - [Projects](#projects)
    - [From Uniswap](#from-uniswap)
    - [From Community](#from-community)
    - [From Hackathon](#from-hackathon)
  - [🛠 Tools](#-tools)
  - [📐 Templates](#-templates)
  - [🎓 Tutorials](#-tutorials)
  - [💡 Articles](#-articles)
  - [🍿 Videos](#-videos)
  - [💡 Creative Ideas](#-creative-ideas)
  - [👀 See Also](#-see-also)
  - [🙏 Thanks](#-thanks)

## 🤔 Introduction

Uniswap v4 Hooks -- also known simply as hooks -- are specially designed contracts that run at distinct points throughout a pool action's lifecycle. They serve as plugins allowing developers to tailor how pools, swaps, fees, and LP positions interact. This enables innovation atop Uniswap v4's core features, thereby supporting the development of custom AMM pools.

_These resources will help you get started with Uniswap v4 hooks._

- [Uniswap's v4 Announcement](https://blog.uniswap.org/uniswap-v4): Official announcement article from Uniswap detailing their vision for v4, including the introduction of hooks.
- [Uniswap v4 Developer Documents](https://docs.uniswapfoundation.org/): Official V4 Developer Documents from Uniswap Foundation, covering topics including how developer would begin to start building out hooks on local testnets in order to start testing out hook designs.
- [Core smart contracts of Uniswap v4](https://github.com/Uniswap/v4-core): The core smart contracts of Uniswap v4, highlighting `v4-core`'s singleton-style architecture, the management of all pool state in `PoolManager.sol`, and use of hook contracts to implement callbacks in the lifecycle of pool actions.
- [Peripheral smart contracts for interacting with Uniswap v4](https://github.com/Uniswap/v4-periphery): `v4-periphery` hosts the logic that builds on top of the core pool logic like hook contracts, position managers, and even possibly libraries needed for integrations. It is still under development and is being updated as the v4 ecosystem matures. Includes the `BaseHook` contract that can be used as a base for creating custom hooks.
- [Technical Whitepaper for Uniswap v4 Core](https://github.com/Uniswap/v4-core/blob/main/docs/whitepaper/whitepaper-v4.pdf): Covers an introduction to Uniswap v4, hooks, singleton and flash accounting, native ETH, and other notable features.

## 🔄 Lifecycle

During the course of a pool action's lifecycle, a hook invokes custom logic primarily at four critical phases:

1. **Initialize**: Activated when the pool is deployed.
2. **Modify Position**: Used to add or remove liquidity.
3. **Swap**: Engages a swap between tokens within the V4 ecosystem.
4. **Donate**: Facilitates the donation of liquidity to a V4 pool.
   Upon initialization, a pool can be associated with a hook contract. Such a contract has the ability to execute any of the callback functions during the pool action's lifecycle:

- `{before,after}Initialize`
- `{before,after}AddLiquidity`
- `{before,after}RemoveLiquidity`
- `{before,after}Swap`
- `{before,after}Donate`

Moreover, hooks can determine fees on swaps and liquidity withdrawals through callback functions. The flexibility lies in updating the fee values or callback logic based on the hook's design. Nevertheless, the callbacks activated on a pool, including the fee type, remain constant post pool initialization.

## 🔧 Functionalities

_Hooks foster creativity. Here are some interesting functionalities that could be implemented with hooks._

- Onchain limit orders that fill at tick prices
- Dynamic fees rooted in volatility or other determinants
- Channeling out-of-range liquidity into lending platforms
- Autocompounding LP fees reintegrated into the LP positions
- MEV profits being internally distributed back to liquidity providers
- A time-weighted average market maker TWAMM to execute large orders over time
- Creation of bespoke onchain oracles (i.e., median, truncated), like geomean oracles

## 📜 Examples

_A collection of hooks from Uniswap and community developers._

### Projects

- [Angstrom](https://x.com/angstromxyz): The first DEX that defends LPs. Angstrom utlizes Uniswap v4 hook for ensuring only staked Angstrom validators can execute swaps to realize onchain DEX based on decentralized node network.
- [Flaunch](https://flaunch.gg/): Meme coin launchpad that enables 100% of trading fees go to creators and buybacks. Flaunch utilizes Uniswap v4 hook for enabling fair price launch of token, and distributing swap fees automatically.
- [Bunni](https://bunni.pro/): The shapeshifting exchange that maximizes liquidity provider profits in all market conditions. Bunni utilizes Uniswap v4 hook for rehypothecation that boosts LP returns by pairing steady APYs from lending vaults with swap fees.
- [Unimon](https://www.unimon.app/): NFT battle game contained and managed inside of a Uniswap V4 hook. Unimon utilizes Uniswap v4 hook to mint NFT after swapping with specfic pool.

### From Uniswap

- [Full Range](https://github.com/Uniswap/v4-periphery/tree/example-contracts/contracts/hooks/examples/FullRange.sol): A hook that allows a Uniswap pool to provide liquidity for a range of prices. This can be used to create a market maker for a volatile asset or to provide more liquidity for a thin market.
- [Geomean Oracle](https://github.com/Uniswap/v4-periphery/tree/example-contracts/contracts/hooks/examples/GeomeanOracle.sol): A unique hook making a Uniswap pool function as an oracle. The geomean price is calculated using the prices of the assets in the pool. This can be used to get a more accurate price for an asset than a single oracle.
- [Limit Order](https://github.com/Uniswap/v4-periphery/tree/example-contracts/contracts/hooks/examples/LimitOrder.sol): A hook that allows users to place limit orders. This means that they can specify the price at which they are willing to buy or sell an asset. If the market price reaches the limit price, the order will be executed.
- [TWAMM](https://github.com/Uniswap/v4-periphery/tree/example-contracts/contracts/hooks/examples/TWAMM.sol): A TWAMM (Time Weighted Average Market Maker) is a type of market maker that uses time-weighted averages to calculate the prices of assets. This can be used to reduce the volatility of the market and to provide more accurate prices for assets. See also [Uniswap's research blog post on TWAMM](https://blog.uniswap.org/v4-twamm-hook).
- [Volatility Oracle](https://github.com/Uniswap/v4-periphery/tree/example-contracts/contracts/hooks/examples/VolatilityOracle.sol): A volatility oracle is a contract that provides information about the volatility of an asset. This information can be used to price options and other derivatives.
- [Truncated Oracle](https://github.com/Uniswap/v4-periphery/blob/trunc-oracle/contracts/hooks/TruncGeoOracle.sol): A truncated oracle is an onchain price oracle that records the price of an asset in a Uniswap liquidity pool using the geometric mean formula. See also [Uniswap's research blog post on truncated oracles](https://blog.uniswap.org/uniswap-v4-truncated-oracle-hook).

### From Community

- [Multi-Sig](https://github.com/atj3097/mfa-multisig-hook-v4/tree/main): Requires multiple signatures for certain pool actions, such as adding or removing liquidity. This can be used to add an extra layer of security to a pool.
- [Whitelist](https://github.com/atj3097/whitelist-hook): Restricts pool participation to a whitelist of approved addresses. This can be used to prevent certain people from participating in a pool, such as people who have been banned from the platform or people who are considered to be high-risk traders.
- [Old Account](https://github.com/jdubpark/Uniswap-Hooks/blob/main/contracts/OldAccountHook.sol): Allows only old accounts to use the pool. Old is subjective; it's the hook owner's job to define "old".
- [KYC](https://github.com/jdubpark/Uniswap-Hooks/blob/main/contracts/KYCHook.sol): Allows for Know Your Customer (KYC) checks to be performed on users before they are allowed to trade on a pool. This can be used to prevent fraud and ensure that only legitimate users are able to trade.
- [New York Trading Hours](https://github.com/horsefacts/trading-days): Reverts when markets are closed in New York. This can be used to prevent trading during certain times of the day, such as when the New York Stock Exchange is closed.
- [Impermanent Loss Hedge (Antonio Furtado)](https://github.com/antoniordf/impermanent-loss-hedge): A hook to hedge against impermanent loss. This can be used to protect liquidity providers from losing money due to price fluctuations.
- [Stop Loss Order](https://github.com/saucepoint/v4-stoploss): Allows users to place stop loss orders on their positions. This means that the position will be automatically closed if the price reaches a certain level.
- [Liquidity Provider Fee Rebate](https://github.com/jdubpark/Uniswap-Hooks/blob/main/contracts/LPFeeRebateHook.sol): Allows liquidity providers (LPs) to receive a rebate on the fees they pay when swapping tokens on a pool. This can be used to incentivize LPs to provide liquidity to the pool.
- [On-Chain Take Profit Order](https://github.com/LearnWeb3DAO/uniswap-v4-take-profits-hook): Allows users to place automatically executing on-chain "take-profit" orders. This means that the position will be automatically closed if the price reaches a certain level.
- [Hyperlane LPTs](https://github.com/saucepoint/v4-hyperlane-LPTs): Automates LPTs on destination chains using Hyperlane in hooks. This can be used to provide liquidity to new tokens on new chains in a more efficient and secure way.
- [Torres Token Sale](https://github.com/jamesbachini/Uniswap-V4-Torres-Token-Sale): A Solidity ERC20 token using hooks to create a compliant token sale system following judge Torres ruling in the XRP case. This can be used to ensure that token sales are conducted in a fair and transparent way.
- [NFT Owners Only](https://github.com/wagmiwiz/nft-owners-only-uniswap-hook): Disallows a swap if sender doesn't own an ERC721 NFT. This can be used to prevent people from selling tokens that they don't own.
- [Curve Style Voting Escrow - veLP](https://github.com/kadenzipfel/veLP): A Curve-style voting escrow (ve) hook. This can be used to create a more democratic and efficient way to vote on changes to a liquidity pool.
- [Huff Hooks](https://github.com/jtriley-eth/huff-hooks): Allows developers to add custom functionality to pools. This can be used to create a variety of new features, such as limit orders or margin trading.
- [Magna Carta](https://github.com/tarunsintern/magna-carta): A hook for enforcing a verifiable sequencing rule. This can be used to prevent front-running and other types of manipulation.
- [Uni LBP](https://github.com/kadenzipfel/uni-lbp): A capital-efficient Uniswap v4 liquidity bootstrapping pool (LBP) hooks contract. This can be used to allow tokens to be sold at a linearly decreasing price.
- [UniKits Hooks](https://github.com/UniKits-Dev/uniswap-v4-unikits-hooks): A series of hooks and tools to enhance the functionality of Uniswap v4 Hooks. These can be used to provide v4 pools with basic functions such as auth to swap, and swap to share.
- [Automated Buyback](https://github.com/atj3097/buyback-hook): A hook that enables protocols to implement automated token buybacks from their treasury when price drops below a target threshold in a Uniswap Pool. This enables automated price support during declines and volatility.
- [Privacy Enhancing Hook](https://github.com/atj3097/privacy-hook-univ4): A hook for Uniswap v4 that combines the privacy features of Tornado Cash with the efficiency and verifiability of Merkle trees/ZK Snarks. This can enhance the privacy and security of Uniswap v4 pools by breaking the on-chain link between depositors and withdrawal addresses, while also providing a verifiable proof of inclusion.
- [Minimize LVR Hook](https://github.com/ArrakisFinance/minimize-lvr-hook-poc): A hook for implementing the POC of research idea on loss-versus-rebalancing. This can reduce LVR and increase LP returns.
- [Bungi](https://github.com/saucepoint/bungi): An experimental Liquidity Position Manager for Uniswap v4. This can be an advanced LP router with more features than the baseline [PoolModifyPositionTest](https://github.com/Uniswap/v4-core/blob/main/contracts/test/PoolModifyPositionTest.sol).
- [Captain Hooks](https://github.com/mrhouzlane/CaptainHooks): A series of Uniswap v4 custom hooks built with Scaffold ETH 2. This can be used for targeting traditional finance entities, offering custom pools with dynamic fee options and other functionalities.
- [Anti-KYC](https://github.com/thegeronimo/Uniswap-Hooks/blob/main/contracts/AntiKYCHook.sol): A hook that bans KYC-ed users. This can be used to provide alternative liquidity pools for users who do not want to go through KYC.
- [WID KYC](https://github.com/Shivamycodee/WID-KYC-Hook): A hook that uses World ID to perform KYC checks. This can be used to provide specific liquidity pools for users who have registered on the World ID of World Coin.
- [Volatility Fee Hook](https://github.com/0xrhsmt/uniswapv4-volatility-fee-hook): A dynamic fee hook based on volatility to mitigate large impermanent losses on high volatility assets. This can be used to increase liquidity, which also benefits users.
- [Ref Fee Hook](https://github.com/mergd/ref-fee-hook): A hook that takes referral fees for swaps and liquidity adds (if specified). This can be used to incentivize users to refer others to the pool.
- [Identity with Civic](https://github.com/civicteam/uniswap-v4-hook): A hook that allows traders with a [Civic Pass](https://www.civic.com/). This can be used for KYC, compliance, sybil resistance and more.
- [Locking Liquidity Hook](https://github.com/BrokkrFinance/hooks-poc/blob/main/src/LiquidityLocking.sol): A hook that gives pool deployers a way to ensure consistent liquidity levels. This can let pool deployers create advanced features that are possible through locking liquidity. See also its [design choices](https://brokkrfinance.medium.com/locking-liquidity-hook-for-univ4-builders-perspective-44e192eefe1f).
- [Attestation Hook](https://github.com/CliqueOfficial/attestation-hooks): A hook that allows for the querying of attestations from various attestation protocols. Check returned responses against preset criteria in any of the hook functions.
- [Constant-sum Swap](https://github.com/saucepoint/v4-constant-sum): A hook that implements constant-sum swaps (x + y = k), allowing for an exact 1:1 swap everytime.
- [Violet Hooks](https://github.com/violetprotocol/uniswap-v4-violet-hooks): A hook that uses VioletID registry to perform identity checks. This can be used for permissioned pools for compliance.
- [Dynamic Fee Hook](https://github.com/umbrellaresearch/uni-v4-hooks-tutorial/blob/main/src/2-dynamic-fees/VolatilityFeeHook.sol): A hook that adjusts the pool fee based on the realized volatility of the pair, using a Volatility Fee oracle.
- [WBTC Hook](https://github.com/tyllenb/v4-btc-hook): A hook that only allows WBTC pools to be created. This is built for celebrating the Bitcoin ETF was approved on 2024-01-10.
- [v2 on v4](https://github.com/hensha256/v2-on-v4): A hook that implements Uniswap v2 on Uniswap v4 with hook.
- [Base v4 Hook](https://github.com/cairoeth/base-v4-hook): A hook that implements v4-like liquidity logic.
- [Backrunning Oracle](https://github.com/RigoBlock/back-geo-oracle/blob/main/src/BackGeoOracle.sol): A backrunning oracle is an onchain PoS resistant price oracle that records the price of an asset in a Uniswap liquidity pool using the geometric mean formula. See also [Rigoblock's research blog post on backrunning oracles](https://mirror.xyz/rigoblock.eth/yKAD5uYyH0KwfdsOxzt0MyppkFJZzXkxAFeufPGVA2M).
- [Slippage Fee Hook](https://github.com/dennnis0204/slippage-fee-hook): A hook protects swappers from slippage exceeding 5% based on two prices including the pool's current price and the simulated post-swap price that reflects slippage.

### From Hackathon

**[ETHGlobal Brussels 2024](https://x.com/UniswapFND/status/1813647336427647474)**

- [Malbec Finance](https://ethglobal.com/showcase/malbec-finance-7pjoz): Liquidity lent out for additional yield. With a synthetic pool, the hook claws back the minimum liquidity to swap (as if it wasn't lent out)..
- [LaunchFi](https://ethglobal.com/showcase/launchfi-o5iiq): Token launchpad with the choice of exponential bonding curve or gradual dutch auction. With dynamic LP fees, the hook rewards buyers & disincentives sellers.
- [All my 🦄 Read on L1](https://ethglobal.com/showcase/all-my-unicorn-read-on-l1-1v7jk): A hook which uses Scroll's L1SLOAD to read L1 spot price and prevent cross-chain arbitrage (LVR) on Scroll pools.
- [HookRank](https://ethglobal.com/showcase/hookrank-ym97n): An analytics app to surface data & safety of hooks and their corresponding pools. The dashboard includes transaction volume, swap success rate, earnings, gas spent, safety score, and user ratings.
- [X-DataAggregator](https://ethglobal.com/showcase/x-dataaggregator-dji5w): An onchain & crosschain data aggregation contract, including Uniswap v3 and v4 TWAP oracles.
- [Liquid Delegation](https://ethglobal.com/showcase/liquid-delegation-wqp0m): A marketplace for buying ARB delegation, allowing revenue-sharing with wrapped-ARB liquidity providers.
- [liqu1tent](https://ethglobal.com/showcase/liqu1tent-5mctm): Cross-chain swaps w/ ERC-7683 settlement contract & solver. Experimented with bytes32 accounts & compatibility with non-EVM chains.
- [Cook Some Hooks](https://ethglobal.com/showcase/cook-some-hooks-ehuy8): A prompt-style hook generator using LLMs to produce compiling and deployed hooks.
- [IntegrumSwap](https://ethglobal.com/showcase/integrumswap-7d99r): A cross-chain exchange using NoOp hooks for asynchronous RFQ swap fulfillment, with fallbacks to v4 liquidity.

**[Hookathon C1](https://uniswap.atrium.academy/hackathons/hookathon-c1/projects/)**

- [Vortex Protocol](https://uniswap.atrium.academy/hackathons/hookathon-c1/projects/0288ead9-9208-49ae-acb0-df5832a17c94/): Tornado Cash using Uniswap V4 Hooks + Legal Compliance.
- [DiamondX](https://uniswap.atrium.academy/hackathons/hookathon-c1/projects/0cb33efc-c4aa-4b12-abb7-130478f25de4/): Innovative Liquidity Solutions for Diamonds.
- [V4-orderbook](https://uniswap.atrium.academy/hackathons/hookathon-c1/projects/10b527ed-6d86-4eec-9444-38f4a0eb05c9/): limit order hook for Uniswap with intent-based orderbook.
- [FlexFee](https://uniswap.atrium.academy/hackathons/hookathon-c1/projects/1456547e-c635-408b-ac89-615b6c6b9a80/): Protecting LPs from impermanent loss using dynamic fees based on volatility (calculated with Brevis) and swap size.
- [Squared](https://uniswap.atrium.academy/hackathons/hookathon-c1/projects/18970626-eb1a-4722-bbce-6e31ade9ce0f/): Access leverage on any token.
- [AutoMate](https://uniswap.atrium.academy/hackathons/hookathon-c1/projects/20f9dd48-d366-42be-91b8-7ad09692725f/): Foodpanda for your on-chain tasks.
- [Oolong.xyz](https://uniswap.atrium.academy/hackathons/hookathon-c1/projects/24c54840-fe7c-44df-b986-2d2a01414eee/): Margin trading by recycling LP liquidity with auto-rebalancing.
- [Ampli](https://uniswap.atrium.academy/hackathons/hookathon-c1/projects/26838945-52ac-4797-a69e-a39c53f7d268/): A permissionless, self-custodial margin protocol with protocol provided liquidity built on top of Uniswap v4.
- [UniCast](https://uniswap.atrium.academy/hackathons/hookathon-c1/projects/372c9d9a-4ab1-49d1-92ea-7edded52928f/): A forward-look event hook for LSTs and yield-bearing tokens.
- [Advanced Orders](https://uniswap.atrium.academy/hackathons/hookathon-c1/projects/37ad66ab-97d5-4b00-8478-df45a7612977/): Advanced Orders Hook to create Stop Loss, Buy Stop, Buy Limit and Take Profit Orders.
- [Timelock Addition to the Points Loyalty Repo](https://uniswap.atrium.academy/hackathons/hookathon-c1/projects/3995df19-b709-46a2-9339-766603ca74ce/): Lock-down Incentivized Liquidity using a beforeRemoveLiquidity hook to ensure sufficient time has passed.
- [StableSwap](https://uniswap.atrium.academy/hackathons/hookathon-c1/projects/3a428d05-98a2-4246-afb8-e0e17ca4b21b/): NoOp hook with full functionality of Curve-liked AMM.
- [Concentrated Incentives Hook](https://uniswap.atrium.academy/hackathons/hookathon-c1/projects/40a37f97-819b-4458-81aa-a071cb0df5f0/): Transparent & Optimal Incentives in V4 by incentivizing only the active tick.
- [LBP Hook](https://uniswap.atrium.academy/hackathons/hookathon-c1/projects/41281dc7-d510-4409-a85d-17b608d14627/): Permissionless LBP sales for everyone.
- [Auto Compound](https://uniswap.atrium.academy/hackathons/hookathon-c1/projects/434f434d-212c-4036-a6fd-ccd1332464ea/): A hook which is designed to reinvest the earned fee back to LP position using uniswap's v4 hooks.
- [Degen Options](https://uniswap.atrium.academy/hackathons/hookathon-c1/projects/4c0f3abd-e74e-4ff1-bd07-0d37521c9147/): Reward your traders like the good ol' days of DeFi Summer.
- [LiquidityLock](https://uniswap.atrium.academy/hackathons/hookathon-c1/projects/51bbf237-01bf-48d0-a586-9b36df2feb47/): Incentivize Liquidity Locks for any Uniswapv4 pool.
- [Liquidity Mining on V4](https://uniswap.atrium.academy/hackathons/hookathon-c1/projects/5a610ca0-780b-44ee-a11a-7ef760b13ea6/): Enables any token rewards based on price in the range and liquidity amount.
- [LiquidityLock](https://uniswap.atrium.academy/hackathons/hookathon-c1/projects/65f4f590-edd7-42f8-befc-38e21109b4cd/): Incentivize Liquidity Locks for any Uniswapv4 pool.
- [Fidelity Hook](https://uniswap.atrium.academy/hackathons/hookathon-c1/projects/74320761-4ed9-4a01-9248-29c17e7aca77/): Market competitive pools withfee reductions.
- [Lumis](https://uniswap.atrium.academy/hackathons/hookathon-c1/projects/7d2c649c-b521-40b3-9120-c188f64c2cbc/): Hook-based options & Liquidity-as-a-service.
- [LoyalSwap](https://uniswap.atrium.academy/hackathons/hookathon-c1/projects/7f3f6221-0979-47c2-a1c6-e1f9d39ad1e4/): Loyal fees for loyal users.
- [FairLaunchoor](https://uniswap.atrium.academy/hackathons/hookathon-c1/projects/80e58e36-4506-44d6-8cf9-04934aa8c416/): Launch your token in a permissionless trustless cyberpunk and most importantly fair way.
- [Dortfolio](https://uniswap.atrium.academy/hackathons/hookathon-c1/projects/81c638c5-edc4-421c-b40f-e2bf1c4cad49/): Turn any portfolio into a token.
- [UniMarket](https://uniswap.atrium.academy/hackathons/hookathon-c1/projects/823a4b3f-af7f-4130-912f-d80ce9e913ae/): Prediction Market built on a hook.
- [Levery](https://uniswap.atrium.academy/hackathons/hookathon-c1/projects/8c0ce7cf-dde8-4814-90c9-b4f3b07f8428/): Regulatory compliant DEX infrastructure oriented on toxic arbitrage mitigation.
- [Mev Auction Hook](https://uniswap.atrium.academy/hackathons/hookathon-c1/projects/95127f15-30a0-4231-947e-8c73fed7be1c/): Reduce MEV spreads and impermanent loss natively through swaps.
- [Internal Swap Pool Hook](https://uniswap.atrium.academy/hackathons/hookathon-c1/projects/984a6c34-e073-42bf-8614-409659a103ee/): Convert accumulated token fees before `donate`, whilst avoiding slippage and pool price change.
- [Liquidity Bet Hook](https://uniswap.atrium.academy/hackathons/hookathon-c1/projects/9f8a73e2-dfb5-4b2f-bc03-8d34d5680e73/): Allows users to bet on whether the liquidity of a specific pool (Token0/Token1) will be higher.
- [Simple LP Rebalancer](https://uniswap.atrium.academy/hackathons/hookathon-c1/projects/a6da420d-7034-4111-af4c-8b5d2623227f/): 100% capital efficiency for LPs.
- [Trailing Hook](https://uniswap.atrium.academy/hackathons/hookathon-c1/projects/a9e4dd2d-3b06-4ea7-aac9-8569e13242b3/): Create a trailing stop directly in a hook.
- [am-AMM hook](https://uniswap.atrium.academy/hackathons/hookathon-c1/projects/ae6965c8-8e5d-43f1-b74e-6bf63f2455d9/): An auction-managed AMM that enhance price discovery, reduce impermanent loss, and offer more liquidity in equilibrium than any standard, fixed-fee AMM.
- [Realized Volatility Based Dynamic Fee Hook](https://uniswap.atrium.academy/hackathons/hookathon-c1/projects/c4e966cd-4203-402d-b7c4-cb60ad9fb60d/): A Uniswap V4 Hook taking SNARK Verified Realized Volatility data of ETH/USDC acrosses DEXes to determine real time fee.
- [Auction-managed perpetual options](https://uniswap.atrium.academy/hackathons/hookathon-c1/projects/de00e67a-e04c-4144-a1cf-039027fb3c31/): Perpetual options offering leverage on any token.
- [Catapoolt](https://uniswap.atrium.academy/hackathons/hookathon-c1/projects/df4b6a25-6b97-4312-933b-b7771a6d125a/): Gamified Liquidity Mining.
- [Fungi Hook](https://uniswap.atrium.academy/hackathons/hookathon-c1/projects/f8c5386c-8bcd-4c58-8f8c-b261070fd7d0/): Make ranges fungible.

**[ETHGlobal London 2024](https://ethglobal.com/showcase/page/1?events=london2024)**

- [Apeful](https://ethglobal.com/showcase/apeful-5avb8) ([source](https://github.com/joergkiesewetter/2024-ethglobal-london)): A hook that enables user incentives on Uniswap V4 pools by automatically generating AI-based NFTs when the user does specific action with ApeCoins, everything completely onchain.
- [The Incredible Hook](https://ethglobal.com/showcase/the-incredible-hook-g635j) ([source](https://github.com/youtpout/the-incredible-hook)): A hook that enables user to get their transaction sponsored in exchange for a discount on swap fees for the sponsor, a win-win deal.
- [SuckerPunch](https://ethglobal.com/showcase/suckerpunch-tp4yo) ([source](https://github.com/popfendi/suckerpunch)): A dynamic fee hook, which adjusts fees based on how long you've been a holder.
- [Dynamic AMM Fees](https://ethglobal.com/showcase/dynamic-amm-fees-x3x1v) ([source](https://github.com/jpw993/ethlondon_dynamicfeehook)): A hook with impermanent loss protection using dynamic fees based on market volatility.
- [TokenTown](https://github.com/Gnome101/UniswapV4HardhatAgain) ([source](https://ethglobal.com/showcase/tokentown-7a1hp)): A Monopoly-inspired, onchain board game where in-game properties are purchased with a stepwise price via a custom-curve v4 pool.
- [0xEstate](https://github.com/ahmedali8/0xestate-contracts) ([source](https://ethglobal.com/showcase/0xestate-gmqr0)): A marketplace that leverages v4 hooks to provide liquidity to fractional real estate. Hooks enabled constraints for purchases of onchain assets.
- [Royalty Swap](https://github.com/Keinberger/royalty-swap) ([source](https://ethglobal.com/showcase/royalty-swap-n8y1i)): A hook to provide discounted swap fees for high volume traders
- [FairArbooors](https://github.com/LVooooors/ETHGlobalLondon) ([source](https://ethglobal.com/showcase/fairarbooors-uq81v)): SUAVE auctions for the right to perform top-of-block swaps, with auction proceeds being donated to LPs.

**[ETHGlobal Istanbul 2023](https://ethglobal.com/showcase/page/1?events=istanbul)**

- [SUClave](https://ethglobal.com/showcase/suclave-dwh4f) ([source](https://github.com/getclave/suclave-ethglobal-istanbul/)): A hook that controls initial swap access. This democratizes MEV and ensures equitable swap opportunities in liquidity pools.
- [Toxic Fl-no](https://ethglobal.com/showcase/toxic-fl-no-qsog4) ([source](https://github.com/tredfern0/toxic-fl-no)): A dynamic fee hook, rewarding valuable participants in the ecosystem by adjusting Uniswap pool fees based on user behavior within a Suave contract, promoting equitability.
- [Aggeragator Hook](https://ethglobal.com/showcase/aggeragator-hook-rfy6g) ([source](https://github.com/Attens1423/Aggregator-Hook)): A hook enables LPs in other DEXes to optimize their Uniswap V4 positions, streamlining liquidity management. It facilitates JIT activation for profitable ranges.

**[ETHOnline 2023](https://ethglobal.com/showcase/page/1?events=ethonline2023)**

- [Perks](https://ethglobal.com/showcase/perks-gv9d1) ([source](https://github.com/aloksahay/perksApp)): A mobile app that redefines brand loyalty. Users earn rewards across various brands while token pools are shielded from market dumps via a Uniswap hook.
- [Delegated Liquidity](https://ethglobal.com/showcase/delegated-liquidity-pas1o) ([source](https://github.com/ScopeLift/delegated-liquidity)): Empowers token delegates to vote on governance proposals without missing out on providing liquidity.
- [HOOK Finance](https://ethglobal.com/showcase/hook-finance-w29rb) ([source](https://github.com/hook-finance/hook-finance-hook)) : A hook that enables perpetual trading as a Uniswap V4 Hook! An innovative way to introduce perpetual markets to V4.
- [Protecc](https://ethglobal.com/showcase/protecc-w9gak) ([source](https://github.com/batoulalkarim/protecc)): Allows developers and builders to create liquidity pools that automatically leverage Spark Protocol's sDAI and SparkLend.
- [Orderbook Hook](https://ethglobal.com/showcase/orderbook-hook-vsmt9) ([source](https://github.com/standardweb3/standard-2.0-contracts/tree/main/contracts/uniswapv4)): A Uniswap v4 hook blending the immediacy of AMM systems with the detail-oriented nature of orderbooks.

**[ETHGlobal New York 2023](https://ethglobal.com/showcase?events=newyork2023)**

- [MEVictim Rebate](https://ethglobal.com/showcase/mevictim-rebate-qsxak) ([source](https://github.com/mliuuu/ETHNYC23/)): Allows you to identify MEV victims using historical onchain data which then airdrops the victim a token to use in a Uniswap v4 gated pool on where they can get a rebate when providing liquidity.
- [Fair Trade](https://ethglobal.com/showcase/fair-trade-yrg2f) ([source](https://github.com/batoulalkarim/copy-trade-nyc-mb)): A Uniswap v4 pool that launches tokens with safety guarantees for future token holders and traders. Designed to be a hook to be added to pools to protect against shit-coin ruggings.
- [NFT Pool Party](https://ethglobal.com/showcase/nft-pool-party-snybc) ([source](https://github.com/nftpoolparty/monorepo)): Enables you to launch your NFT collection on Uniswap & earn ongoing income streams from royalties (again). Used v4 Hooks to create NFT IDOs and gave the power back to the creators to control their royalties.
- [ReCentFi](https://ethglobal.com/showcase/recentifi-k7jan) ([source](https://github.com/KaiStryker/ReCentiFi)): An AI-powered platform to reward eco-friendly action. Users pick up trash, upload videos for verification, and gain exclusive access to ‘clean’ Uniswap pools with verification gated hooks added to them.
- [0xY](https://ethglobal.com/showcase/0xy-bjtsk) ([source](https://github.com/NPrada/oxy-hack-fe)): Borrowing protocol offering put-protected term loans that protect against price liquidation. A Uniswap V4 pool implements custom hooks that lends to the protocol whenever the price moves out of range for a user's LP.
- [Axiom LP Mgmt](https://ethglobal.com/showcase/axiom-lp-mgmt-1h3z2) ([source](https://github.com/saucepoint/v4-axiom-rebalancing/)): A Uniswap v4 hook and position manager to enable trustless LP modification with Axiom. Modifies positions on Uniswap pools automatically so that LPs can passively make better returns.
- [UniV4 CCLP Hook](https://ethglobal.com/showcase/univ4-cclp-hook-zd3st) ([source](https://github.com/cesarhuret/ethglobalnyc)): Uses Uniswap V4 to create a hook that seamlessly transfers the user's LP to another chain, without them having to worry about bridging or anything else.
- [TimeConcentrate](https://ethglobal.com/showcase/timeconcentrate-c58h4) ([source](https://github.com/MarcusWentz/time_concentrate)): Concentrates liquidity along price, and now time, with Uni v4 hooks to mitigate the times MEV bots attack. Hook that modifies positions based on time of MEV attacks.
- [Arb Controller](https://ethglobal.com/showcase/arb-controller-dw3so) ([source](https://github.com/ziyincody/arbitrage-controller-ETHNYC)): A Uniswap v4 hook that sets dynamic fee for a pool based on the price movements. The dynamic fee partially discriminates informed order flow from arbitrageurs.
- [NYCV4Hermit](https://ethglobal.com/showcase/nycv4hermit-dj0um) ([source](https://github.com/djm07073/ETHNewYork-Hook-LAB)): Three libraries of tooling developed for Liquidity Sniping (Liquidity Snipping Blocking Hook), V4 Math, and a V4 Quoter Library.
- [Lime](https://ethglobal.com/showcase/lime-qczie) ([source](https://github.com/kohshiba/univ4-offchain-pricing)): An active Uniswap V4 hook manager which allows fillers or market makers to set price and fill Intent / RFQ based swap requests.

**[EthCC Paris Hookathon 2023](https://twitter.com/UniswapFND/status/1683983199872122881)**

- [Median Price Oracle](https://github.com/saucepoint/median-oracles): An initial exploration of a median price oracle that is more resistant to manipulation than TWAP. It includes an approximation algorithm where a running median can provide substantial gas efficiency on both read and write.
- [Impermanent Loss Hedge (Makemake)](https://github.com/makemake-kbo/sdhasidhas): A hook to explore ways to hedge impermanent loss for LPs by buying out of the money call options on the underlying asset. When liquidity is added to the pool, the hook is called & executes a purchase of the req. amount of calls in Lyra options protocol.
- [Hedge](https://github.com/vanillaHill/hedge): Risk management strategies using hooks. The project showcases how hedging mechanisms can mitigate price volatility risks in a trader's portfolio.
- [Trading Hours](https://github.com/bennoprice/univ4/blob/main/src/TradingHours.sol): Traditional market opening/closing hours to a Uniswap v4 pool using a beforeSwap hook. Users are only able to trade between 8am and 4pm.
- [Dynamic Fee](https://github.com/ArrakisFinance/uni-v4-playground/blob/main/contracts/ArrakisHookV1.sol): Adjusts with the goal of cutting LP losses to arbitrageurs, and an implementation of a shared fungible liquidity position (similar to a vault).

## 🛠 Tools

_Utilize these tools to boost your development process._

- [Scaffold Hook](https://github.com/uniswapfoundation/scaffold-hook): Uniswap v4 Hook development stack, complete with testnet deployment and UI. This tool can help builder develop and test Uniswap v4 Hooks with minimal interfaces for the swap lifecycle (pool creation, liquidity provision, and swapping).
- [Hook Mine And Sinker](https://github.com/devtooligan/HookMineAndSinker): Mine addresses for UniswapV4 Hooks. This tool can be used to generate random addresses that are eligible to become hooks. This can be useful for testing or for deploying your own Hooks.
- [Hook Deployer](https://github.com/drgorillamd/uniV4-hook-deployer): Hook create2 deployer. This tool can be used to deploy hooks to Ethereum.
- [Uniswap v4 Tests](https://github.com/jamesbachini/Uniswap-v4-Tests): A test suite for working with Uniswap v4 hooks. This test suite can be used to verify that your hooks are working correctly.
- [Uniswap v4 Hook Test Framework](https://github.com/khegeman/uniswapv4-hook-test-framework): A fuzz testing framework for Uniswap V4 Hooks, built during ETHGlobal 2023. This framework can be used to test the security of your hooks.
- [Hookmate](https://github.com/saucepoint/hookmate): Experimental Solidity components and utilities for Uniswap v4 Hook development. This can help developers leverage extsload and access fee info for hooks.
- [Uniswap v4 Minimal](https://github.com/0xaaiden/uniswap-v4-minimal): Minimal subgraph for Uniswap v4.
- [Uniswap V4 Hook Address Miner](https://v4hookaddressminer.xyz/): Fast multithreaded Uniswap V4 hook vanity address miner online tool


## 📐 Templates

_These are templates for writing Uniswap V4 Hooks._

- [Uniswap Foundation's Template](https://github.com/uniswapfoundation/v4-template): This template repository provides a starting point for writing Uniswap V4 hooks. It includes the necessary files and contracts to get started. This template can be used to create a custom hook that can be used to execute arbitrary code on every swap. Previously built by [saucepoint](https://github.com/saucepoint).
- [SolidityLabs' Template](https://github.com/soliditylabs/uniswap-v4-custom-pool): Foundry-based template for developing custom pool in Uniswap v4 with hooks.
- [Arrakis' Playground](https://github.com/ArrakisFinance/uni-v4-playground): This playground is a web-based application that allows you to interact with hooks. You can use this playground to test your own hooks or to learn more about how hooks work. This playground can be used to test the functionality of your hooks by simulating swaps.
- [Lucas Martin Calderon's Template](https://github.com/LucasMartinCalderon/Uniswap): This repository contains a template for a hook that was created for the ETHGlobal Hackathon. This template can be used to create a custom hook that can be used to provide liquidity to a particular pool.
- [Nick Addison's Template](https://github.com/naddison36/uniswap-v4-hooks): This repository contains a template for a hook that includes a factory to mine addresses and trace diagrams. This template can be used to create a custom hook that can be used to mine addresses and generate trace diagrams.
- [Quantum3 Labs's Scaffold](https://github.com/Quantum3-Labs/Scaffold-UniswapV4): A boilerplate to use Uniswap v4 hooks with scaffold eth.
- [Gnome101's Hardhat Template](https://github.com/Gnome101/UniswapV4Hardhat): A template and playground that uses hardhat. This can be used to create and test custom hooks.
- [OpenZeppelin's Hooks Library](https://github.com/OpenZeppelin/uniswap-hooks): Solidity library for secure and modular Uniswap hooks.

## 🎓 Tutorials

_Empower your learning curve with these insightful tutorials._

- [Uniswap Foundation: v4 by Example](https://www.v4-by-example.org/): This website shows Solidity snippets for integrating and using Uniswap v4. This is an introduction to integrating and using Uniswap v4 through simple examples.
- [LearnWeb3: On-chain "take-profit" orders hook](https://learnweb3.io/lessons/uniswap-v4-hooks-create-a-fully-on-chain-take-profit-orders-hook-on-uniswap-v4/): This tutorial from LearnWeb3 delves into the intricacies of Uniswap v4 hooks. The lesson guides users through building a hook for placing 'take-profit' positions, exemplified by the scenario where a user in an ETH/DAI pool can set an automatic order to sell all their ETH when the price reaches a determined price.
- [Solidity Developer: Integrate Uniswap v4 and create a custom hook](https://soliditydeveloper.com/uniswap4): This tutorial provides a deep dive, showcasing the nuanced mechanisms for executing fees, the importance of the Ethereum address prefix for the hooks contract, and use of the CREATE2 opcode to deploy contracts with deterministic addresses. A tangible example of using hooks to enable limit orders is presented.
- [James Bachini: Introduction to Hooks](https://jame11sbachini.com/uniswap-v4-hooks/): This tutorial showcases using the "beforeSwap" hook function to introduce custom actions during a swap.
- [Saucepoint: Getting Started with the `v4-template`](https://uniswaphooks.com/blog/getting-started-with-v4-template): This tutorial provides a step-by-step guide to using the `v4-template` to create a custom hook, with testing and trouble-shooting tips.
- [Captain Hook: Uniswap Hooks Tutorial](https://github.com/umbrellaresearch/uni-v4-hooks-tutorial): This tutorial contains 3 different proofs of concept hooks, accompanied by a tutorial blog post.
- [Umbrella Research: A Deep Dive With Captain Hook (I)](https://medium.com/@umbrellaresearch/uniswap-v4-hooks-a-deep-dive-with-captain-hook-i-6be5d1677539): This tutorial shows how developers can implement role-based features within the Uniswap v4 protocol.
- [Umbrella Research: Uniswap v4 Hooks Guide (II) Dynamic Fees Hook](https://medium.com/@umbrellaresearch/uniswap-v4-hooks-a-deep-dive-with-captain-hook-ii-44b0efc84e45): This article talks about how Dynamic Fees work and their impact on Uniswap V4.
- [Rahat: Exploring Hooks on Uniswap V4](https://www.youtube.com/watch?v=4n8yAtnwxBI): This stream shows how developer learns about hooks on Uniswap V4 with SaucePoint - Developer Relations Engineer at Uniswap.

## 💡 Articles

_Read these articles to gain a deeper understanding of Uniswap v4 hooks._

- [A Saga of Hooks, Bidding Farewell to Fork Swap](https://medium.com/ybbcapital/uniswap-v4-a-saga-of-hooks-bidding-farewell-to-fork-swap-c653ba9ffce4): The v4 innovation, introduction to hooks, action hooks, and enabling custom oracle and distribution of internalized MEV to LPs.
- [Threat modeling for secure integration](https://composable-security.com/blog/uniswap-v-4-threat-modeling-for-secure-integration/): Learn what to watch out for and what to take care of when integrating with Uniswap v4. Section 4.4.1 reviews potential issues with hooks, including upgradeable hooks, denial of service attacks, sandwich attacks, and access control.
- [SharkTeam's Best Security Practices for UniswapV4 Hooks](https://app.chainaegis.com/home/news/detail?contentId=347): Covers differences between v4 and v3 with examples of best security practices for hooks.
- [Community Contributions to Uniswap v4](https://blog.uniswap.org/uniswap-v4-community-contributions): Talks about the community contributions to Uniswap v4, including ideas, implementations, commits, and so on.
- [Uniswap V4: Exploring Hooks, KYC, and Enhanced Features](https://medium.com/@diamondprotocol/uniswap-v4-exploring-hooks-kyc-and-enhanced-features-d53e77af850b): Explores the buzz around Uniswap V4, and the reason why this development is intriguing.
- [Thorns in the Rose: Exploring Security Risks in Uniswap v4's Novel Hook Mechanism](https://phalcon.xyz/blog/thorns-in-the-rose-exploring-security-risks-in-uniswap-v4-s-novel-hook-mechanism): Explores the threat models of Uniswap v4 hook, and discovers that 36% of the hooks in [this repository in one specific commit hash](https://github.com/fewwwww/awesome-uniswap-hooks/commit/3a0a444922f26605ec27a41929f3ced924af6075) may be vulnerable to attacks.
- [Lethal Integration: Vulnerabilities in Hooks Due to Risky Interactions](https://phalcon.xyz/blog/lethal-integration-vulnerabilities-in-hooks-due-to-risky-interactions): Scrutinizes secure hook interaction logic from flawed access control and improper input validation perspectives.
- [Threats for UniswapV4 hooks](https://composable-security.com/blog/threats-for-uniswap-v-4-hooks/): Focuses on the potential threats, risks and vulnerabilities associated with bad hooks in Uniswap v4.
- [Uniswap V4: Re-Initialization Leading to Funds Locked](https://composable-security.com/blog/uniswap-v-4-re-initialization-leading-to-funds-locked/): Presents present implementations of "Bad hooks" of "Re-Initialization Leading to Funds Locked".
- [Uniswap V4: Liquidity Theft via Hook Fee](https://composable-security.com/blog/uniswap-v-4-liquidity-theft-via-hook-fee/): Covers "Liquidity theft" using the scenario of "Hook sets high withdrawal fee".
- [Uniswap V4: Oracle hook with malicious owner](https://composable-security.com/blog/uniswap-v-4-oracle-hook-with-malicious-owner/): Presents the potential risks of Oracle hook with malicious backdoor for owner.
- [UniswapV4: Further research to improve hooks security](https://composable-security.com/blog/uniswap-v-4-further-research-to-improve-hooks-security/): Focuses on the current state and the ideas on how to change Uniswap v4 security by further research.
- [Protecting Uniswap v4 Against Unknown Attacks](https://www.certora.com/blog/protecting-uniswap-v4-against-unknown-attacks-part-one-a-threat-model): Explores the threat model for Uniswap v4, analyzes potential attack vectors, and evaluates how the protocol's test suite addresses them.
- [Establishing Hook Data Standards in Uni v4: A Guide for Developers and Analysts](https://uniswapfoundation.mirror.xyz/KGKMZ2Gbc_I8IqySVUMrEenZxPnVnH9-Qe4BlN1qn0g): Aims to establish a standard for hook developers, hook data indexers, and analysts, such that all users, from developers and LPs to analysts, can use the same shared framework when it comes to hook data.

## 🍿 Videos

_Watch these videos to learn more about Uniswap v4 hooks._

- [Hayden Adams announcing the release of Uniswap V4 (Bankless)](https://www.youtube.com/watch?v=ZmhdNiGOMRU): 90-minute video covering the release of Uniswap v4, including the hook centric roadmap at [43:29](https://youtu.be/ZmhdNiGOMRU?si=Txqbp0wLnU8gdQn4&t=2609).
- [Hayden Adams on what makes v4 special (Unchained Podcast)](https://www.youtube.com/watch?v=KNK-W8JDuWg): 80-minute video highlighting v4 including an explanation of hooks, their most common uses, and security concerns starting at [21:05](https://youtu.be/KNK-W8JDuWg?si=a4RIqonO1Bj-DpCf&t=1265).
- [Uniswap V4 Deep Dive with Head of Protocols Sara Reynolds (The Defiant)](https://www.youtube.com/watch?v=6e8n_GedrMY): 75-minute video discussing v4 including an overview of hooks and attack vectors starting at [4:30](https://www.youtube.com/live/6e8n_GedrMY?si=l5lSMSUOvZ54w4HP&t=270).
- [Uniswap v4: Hooks, Singletons and Controversy (Blockcast)](https://www.youtube.com/watch?v=cu5S87U2dXs): 22-minute video exploring v4 including a discussion of hooks starting at [1:21](https://youtu.be/cu5S87U2dXs?si=7TaaqhjZ4WmpOjb_&t=81).

## 💡 Creative Ideas

_Hooks open doors to limitless innovations. Check out some of these inspiring ideas._

- [Loss Versus Rebalancing Minimization](https://ethresear.ch/t/lvr-minimization-in-uniswap-v4/15900): Research funded by the Uniswap Foundation Grants Program regarding cross-domain MEV sources within the DEX ecosystem, specifically on loss-versus-rebalancing (LVR).
- [Oracleless Lending Protocol](https://blog.instadapp.io/oracleless-lending-protocol-on-uniswap-v4/): Creating a new lending protocol offering features like flexible liquidation thresholds, oracle-free operations, and enhanced earnings for liquidity providers.
- [Torando Cash on Hooks](https://twitter.com/witconomist/status/1694859874080076180): A Tornado-like system, utilizing all of Uniswap's liquidity as its pool.
- [Hook Safety as a Service](https://twitter.com/xin__wan/status/1695258362298933499): Insuring safety of a hook up to a certain amount.
- [Gasless Swaps](https://twitter.com/dhruvinparikh_/status/1691441830410461184): Incentivizing traders via a non-toxic MEV executer with gasless swaps.
- [Hook to Facilitate Keeper Activity](https://twitter.com/saucepoint/status/1686070429503676416): An intuition on using v4 hooks to facilitate keeper activity.
- [What bad hooks look like](https://uniswap.notion.site/Research-What-bad-hooks-look-like-b10256c445904111914eb3b01fb4ec53): An RFP by Uniswap Foundation inviting for proposals from academic researchers and/or solidity auditors to explore the "malicious design space" of hooks in solidity, especially how they can compromise systems and create safety failures.
- [UniBrain Hook](https://hackmd.io/@kames/unibrain-hook): The UniBrain hook is designed to automatically trigger onchain actions using an automated Dutch Auction via a Uniswap V4 Pool. It can turn Uniswap v4 into a hub for triggering onchain function calls.
- [Tips to make pool aggregator/searcher-friendly](https://twitter.com/fulminmaxi/status/1733500528607600946): 6 dos and don'ts to make v4 customized pools aggregator/searcher-friendly, to attract more volume from aggregators/searchers.
- [Value accrual designs for hook developers](https://twitter.com/saucepoint/status/1744385686621372723): A simple hook fee introduces vampire/fork risk. Retaining LPs will be crucial to justifying hook fees.
- [auction-managed AMM](https://twitter.com/danrobinson/status/1765773423090012433): An auction-managed AMM that shows the design space of v4.
- [Sandwich-resistant Hook](https://x.com/cairoeth/status/1825593789492375925): A sandwich-resistant Uniswap v4 hook based on "A SANDWICH-RESISTANT AMM" from Umbra Research.
- [The Null Fee Idea](https://github.com/subtrahend-labs/research/blob/main/the-null-fee.pdf): A novel type of indicator called the null fee that may be a useful ingredient in the design of a dynamic fee algorithms for concentrated liquidity and constant product AMMs.
- [Doppler](https://x.com/AustinAdams10/status/1833505856056660026): A liquidity-bootstrapping hook design on top of Uniswap v4.

## 👀 See Also

_Check out these related resources._

- [Uniswap v4: A New Era For Defi](https://uniswapfoundation.mirror.xyz/5elfLDeU-AMehTtnwAswhc3p2NjF3_BWDtji6BEzh_0): Article from Uniswap discussing their excitement for the developing of the ecosystem -- highlighting hooks' ability to attract liquidity, design new interfaces, and bridge DeFi into the mainstream.
- [Contribution Guidelines for Uniswap v4 Core](https://github.com/Uniswap/v4-core/blob/main/CONTRIBUTING.md): Uniswap has released the draft code so that v4 can be built in public with community contribution. You may contribute by opening an issue, resolving an issue, and reviewing open PRs.
- [The Uniswap Hook Incubator](https://atrium.academy/uniswap): An 8-week program to help advanced DeFi devs build hooks.
- [What are you building with Uniswap v4 hooks?](https://x.com/haydenzadams/status/1885786932438823252): A discussion tweet from Hayden Adams.

## 🙏 Thanks

_Thanks to these contributors for making this list possible._

- [fewwwww](https://github.com/fewwwww)
- [naddison36](https://github.com/naddison36)
- [0xV4L3NT1N3](https://github.com/0xV4L3NT1N3)
- [johnsonstephan](https://github.com/johnsonstephan)
- [UniswapHooks](https://uniswaphooks.vercel.app/)
- [UniV4 Hook Dojo](https://t.me/+m35oO7qzqu02NTgx)
- [0xaaiden](https://github.com/0xaaiden)
- [dankelleher](https://github.com/dankelleher)
- [Gnome101](https://github.com/Gnome101)
- [buendiadas](https://github.com/buendiadas)
- [LiRiu](https://github.com/LiRiu)
- [omahs](https://github.com/omahs)
