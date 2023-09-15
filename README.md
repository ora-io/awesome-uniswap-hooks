# 🦄️ Awesome Uniswap v4 Hooks

A curated list of awesome [Uniswap v4](https://github.com/Uniswap/v4-core) [hooks](https://github.com/Uniswap/v4-periphery/tree/main/contracts/hooks) resources.

Special thanks to Uniswap Foundation for [including this resource in the official doc](https://web.archive.org/web/20230915081852/https://docs.uniswapfoundation.org/hooks/hook-examples)!

## 📑 Table of Contents

- [🦄️ Awesome Uniswap v4 Hooks](#️-awesome-uniswap-v4-hooks)
  - [📑 Table of Contents](#-table-of-contents)
  - [🤔 Introduction](#-introduction)
  - [🔄 Lifecycle](#-lifecycle)
  - [🔧 Functionalities](#-functionalities)
  - [📜 Examples](#-examples)
    - [From Uniswap](#from-uniswap)
    - [From the Community](#from-the-community)
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

- [Uniswap's V4 Announcement](https://blog.uniswap.org/uniswap-v4): Official announcement article from Uniswap detailing their vision for v4, including the introduction of hooks.
- [Uniswap V4: A New Era For Defi](https://uniswapfoundation.mirror.xyz/5elfLDeU-AMehTtnwAswhc3p2NjF3_BWDtji6BEzh_0): Article from Uniswap discussing their excitement for the developing of the ecosystem -- highlighting hooks' ability to attract liquidity, design new interfaces, and bridge DeFi into the mainstream.
- [Core smart contracts of Uniswap v4](https://github.com/Uniswap/v4-core): The core smart contracts of Uniswap v4, highlighting `v4-core`'s singleton-style architecture, the management of all pool state in `PoolManager.sol`, and use of hook contracts to implement callbacks in the lifecycle of pool actions.
- [Peripheral smart contracts for interacting with Uniswap v4](https://github.com/Uniswap/v4-periphery): `v4-periphery` hosts the logic that builds on top of the core pool logic like hook contracts, position managers, and even possibly libraries needed for integrations. It is still under development and is being updated as the v4 ecosystem matures. Includes the `BaseHook` contract that can be used as a base for creating custom hooks.
- [Draft Technical Whitepaper for Uniswap v4 Core](https://github.com/Uniswap/v4-core/blob/main/whitepaper-v4-draft.pdf): Covers an introduction to Uniswap v4, hooks, singleton and flash accounting, native ETH, and other notable features.
- [Contribution Guidelines for Uniswap v4 Core](https://github.com/Uniswap/v4-core/blob/main/CONTRIBUTING.md): Uniswap has released the draft code so that v4 can be built in public with community contribution. You may contribute by opening an issue, resolving an issue, and reviewing open PRs.

## 🔄 Lifecycle

During the course of a pool action's lifecycle, a hook invokes custom logic primarily at four critical phases:

1. **Initialize**: Activated when the pool is deployed.
2. **Modify Position**: Used to add or remove liquidity.
3. **Swap**: Engages a swap between tokens within the V4 ecosystem.
4. **Donate**: Facilitates the donation of liquidity to a V4 pool.
   Upon initialization, a pool can be associated with a hook contract. Such a contract has the ability to execute any of the callback functions during the pool action's lifecycle:

- `{before,after}Initialize`
- `{before,after}ModifyPosition`
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

### From Uniswap

- [Full Range](https://github.com/Uniswap/v4-periphery/blob/main/contracts/hooks/examples/FullRange.sol): A hook that allows a Uniswap pool to provide liquidity for a range of prices. This can be used to create a market maker for a volatile asset or to provide more liquidity for a thin market.
- [Geomean Oracle](https://github.com/Uniswap/v4-periphery/blob/main/contracts/hooks/examples/GeomeanOracle.sol): A unique hook making a Uniswap pool function as an oracle. The geomean price is calculated using the prices of the assets in the pool. This can be used to get a more accurate price for an asset than a single oracle.
- [Limit Order](https://github.com/Uniswap/v4-periphery/blob/main/contracts/hooks/examples/LimitOrder.sol): A hook that allows users to place limit orders. This means that they can specify the price at which they are willing to buy or sell an asset. If the market price reaches the limit price, the order will be executed.
- [TWAMM](https://github.com/Uniswap/v4-periphery/blob/main/contracts/hooks/examples/TWAMM.sol): A TWAMM (Time Weighted Average Market Maker) is a type of market maker that uses time-weighted averages to calculate the prices of assets. This can be used to reduce the volatility of the market and to provide more accurate prices for assets.
- [Volatility Oracle](https://github.com/Uniswap/v4-periphery/blob/main/contracts/hooks/examples/VolatilityOracle.sol): A volatility oracle is a contract that provides information about the volatility of an asset. This information can be used to price options and other derivatives.

### From the Community

- [Multi-Sig](https://github.com/atj3097/mfa-multisig-hook-v4/tree/main): Requires multiple signatures for certain pool actions, such as adding or removing liquidity. This can be used to add an extra layer of security to a pool.
- [Whitelist](https://github.com/atj3097/whitelist-hook): Restricts pool participation to a whitelist of approved addresses. This can be used to prevent certain people from participating in a pool, such as people who have been banned from the platform or people who are considered to be high-risk traders.
- [Old Account](https://github.com/jdubpark/Uniswap-Hooks/blob/main/contracts/OldAccountHook.sol): Allows only old accounts to use the pool. Old is subjective; it's the hook owner's job to define "old".
- [KYC](https://github.com/jdubpark/Uniswap-Hooks/blob/main/contracts/KYCHook.sol): Allows for Know Your Customer (KYC) checks to be performed on users before they are allowed to trade on a pool. This can be used to prevent fraud and ensure that only legitimate users are able to trade.
- [Trading Hours](https://github.com/bennoprice/univ4/blob/main/src/TradingHours.sol): Allows trading to only occur between defined trading hours. This can be used to prevent trading during certain times of day, such as when the market is illiquid or when there is a high risk of price volatility.
- [New York Trading Hours](https://github.com/horsefacts/trading-days): Reverts when markets are closed in New York. This can be used to prevent trading during certain times of the day, such as when the New York Stock Exchange is closed.
- [Hedging Mechanism](https://github.com/vanillaHill/hedge): Allows users to hedge their positions against market volatility. This can be done by using a variety of techniques, such as buying options or futures contracts.
- [Impermanent Loss Hedge (Antonio Furtado)](https://github.com/antoniordf/impermanent-loss-hedge): A hook to hedge against impermanent loss. This can be used to protect liquidity providers from losing money due to price fluctuations.
- [Impermanent Loss Hedge (Makemake)](https://github.com/makemake-kbo/sdhasidhas): Another hook to automatically hedge impermanent loss with options.
- [Median Price Oracle](https://github.com/saucepoint/median-oracles): Provides a more accurate price feed. This can be done by using a variety of techniques, such as aggregating prices from multiple sources or using a median price calculation.
- [Stop Loss Order](https://github.com/saucepoint/v4-stoploss): Allows users to place stop loss orders on their positions. This means that the position will be automatically closed if the price reaches a certain level.
- [Liquidity Provider Fee Rebate](https://github.com/jdubpark/Uniswap-Hooks/blob/main/contracts/LPFeeRebateHook.sol): Allows liquidity providers (LPs) to receive a rebate on the fees they pay when swapping tokens on a pool. This can be used to incentivize LPs to provide liquidity to the pool.
- [On-Chain Take Profit Order](https://github.com/LearnWeb3DAO/uniswap-v4-take-profits-hook): Allows users to place automatically executing on-chain "take-profit" orders. This means that the position will be automatically closed if the price reaches a certain level.
- [Hyperlane LPTs](https://github.com/saucepoint/v4-hyperlane-LPTs): Automates LPTs on destination chains using Hyperlane in hooks. This can be used to provide liquidity to new tokens on new chains in a more efficient and secure way.
- [Torres Token Sale](https://github.com/jamesbachini/Uniswap-V4-Torres-Token-Sale): A Solidity ERC20 token using hooks to create a compliant token sale system following judge Torres ruling in the XRP case. This can be used to ensure that token sales are conducted in a fair and transparent way.
- [NFT Owners Only](https://github.com/wagmiwiz/nft-owners-only-uniswap-hook): Disallows a swap if sender doesn't own an ERC721 NFT. This can be used to prevent people from selling tokens that they don't own.
- [Curve Style Voting Escrow - veLP](https://github.com/kadenzipfel/veLP): A Curve-style voting escrow (ve) hook. This can be used to create a more democratic and efficient way to vote on changes to a liquidity pool.
- [Huff Hooks](https://github.com/jtriley-eth/huff-hooks): Allows developers to add custom functionality to pools. This can be used to create a variety of new features, such as limit orders or margin trading.
- [Magna Carta](https://github.com/tarunsintern/magna-carta): A hook for enforcing a verifiable sequencing rule. This can be used to prevent front-running and other types of manipulation.

## 🛠 Tools

_Utilize these tools to boost your development process._

- [Hook Mine And Sinker](https://github.com/devtooligan/HookMineAndSinker): Mine addresses for UniswapV4 Hooks. This tool can be used to generate random addresses that are eligible to become hooks. This can be useful for testing or for deploying your own Hooks.
- [Hook Deployer](https://github.com/drgorillamd/uniV4-hook-deployer): Hook create2 deployer. This tool can be used to deploy hooks to Ethereum.
- [Uniswap v4 Tests](https://github.com/jamesbachini/Uniswap-v4-Tests): A test suite for working with Uniswap v4 hooks. This test suite can be used to verify that your hooks are working correctly.

## 📐 Templates

_These are templates for writing Uniswap V4 Hooks._

- [Saucepoint's Template](https://github.com/saucepoint/v4-template): This template repository provides a starting point for writing Uniswap V4 hooks. It includes the necessary files and contracts to get started. This template can be used to create a custom hook that can be used to execute arbitrary code on every swap.
- [SolidityLabs' Template](https://github.com/soliditylabs/uniswap-v4-custom-pool): Foundry-based template for developing custom pool in Uniswap v4 with hooks.
- [Arrakis' Playground](https://github.com/ArrakisFinance/uni-v4-playground): This playground is a web-based application that allows you to interact with hooks. You can use this playground to test your own hooks or to learn more about how hooks work. This playground can be used to test the functionality of your hooks by simulating swaps.
- [Lucas Martin Calderon's Template](https://github.com/LucasMartinCalderon/Uniswap): This repository contains a template for a hook that was created for the ETHGlobal Hackathon. This template can be used to create a custom hook that can be used to provide liquidity to a particular pool.
- [Nick Addison's Template](https://github.com/naddison36/uniswap-v4-hooks): This repository contains a template for a hook that includes a factory to mine addresses and trace diagrams. This template can be used to create a custom hook that can be used to mine addresses and generate trace diagrams.

## 🎓 Tutorials

_Empower your learning curve with these insightful tutorials._

- [LearnWeb3: On-chain "take-profit" orders hook](https://learnweb3.io/lessons/uniswap-v4-hooks-create-a-fully-on-chain-take-profit-orders-hook-on-uniswap-v4/): This tutorial from LearnWeb3 delves into the intricacies of Uniswap v4 hooks. The lesson guides users through building a hook for placing 'take-profit' positions, exemplified by the scenario where a user in an ETH/DAI pool can set an automatic order to sell all their ETH when the price reaches a determined price.
- [Solidity Developer: Integrate Uniswap v4 and create a custom hook](https://soliditydeveloper.com/uniswap4): This tutorial provides a deep dive, showcasing the nuanced mechanisms for executing fees, the importance of the Ethereum address prefix for the hooks contract, and use of the CREATE2 opcode to deploy contracts with deterministic addresses. A tangible example of using hooks to enable limit orders is presented.
- [James Bachini: Introduction to Hooks](https://jamesbachini.com/uniswap-v4-hooks/): This tutorial showcases using the "beforeSwap" hook function to introduce custom actions during a swap.

## 💡 Articles

_Read these articles to gain a deeper understanding of Uniswap v4 hooks._

- [A Saga of Hooks, Bidding Farewell to Fork Swap](https://medium.com/ybbcapital/uniswap-v4-a-saga-of-hooks-bidding-farewell-to-fork-swap-c653ba9ffce4): The v4 innovation, introduction to hooks, action hooks, and enabling custom oracle and distribution of internalized MEV to LPs.
- [Threat modeling for secure integration](https://composable-security.com/blog/uniswap-v-4-threat-modeling-for-secure-integration/): Learn what to watch out for and what to take care of when integrating with Uniswap v4. Section 4.4.1 reviews potential issues with hooks, including upgradeable hooks, denial of service attacks, sandwich attacks, and access control.
- [SharkTeam's Best Security Practices for UniswapV4 Hooks](https://app.chainaegis.com/home/news/detail?contentId=347): Covers differences between v4 and v3 with examples of best security practices for hooks.

## 🍿 Videos

_Watch these videos to learn more about Uniswap v4 hooks._

- [Hayden Adams announcing the release of Uniswap V4 (Bankless)](https://www.youtube.com/watch?v=ZmhdNiGOMRU): 90-minute video covering the release of Uniswap v4, including the hook centric roadmap at [43:29](https://youtu.be/ZmhdNiGOMRU?si=Txqbp0wLnU8gdQn4&t=2609).
- [Hayden Adams on what makes v4 special (Unchained Podcast)](https://www.youtube.com/watch?v=KNK-W8JDuWg): 80-minute video highlighting v4 including an explanation of hooks, their most common uses, and security concerns starting at [21:05](https://youtu.be/KNK-W8JDuWg?si=a4RIqonO1Bj-DpCf&t=1265).
- [Uniswap V4 Deep Dive with Head of Protocols Sara Reynolds (The Defiant)](https://www.youtube.com/watch?v=6e8n_GedrMY): 75-minute video discussing v4 including an overview of hooks and attack vectors starting at [4:30](https://www.youtube.com/live/6e8n_GedrMY?si=l5lSMSUOvZ54w4HP&t=270).
- [Uniswap v4: Hooks, Singletons and Controversy (Blockcast)](https://www.youtube.com/watch?v=cu5S87U2dXs): 22-minute video exploring v4 including a discussion of hooks starting at [1:21](https://youtu.be/cu5S87U2dXs?si=7TaaqhjZ4WmpOjb_&t=81).

## 💡 Creative Ideas

_Hooks open doors to limitless innovations. Check out some of these inspiring ideas._

- [Loss Versus Rebalancing Minimization](https://ethresear.ch/t/lvr-minimization-in-uniswap-v4/15900): Research funded from the Uniswap Foundation Grants Program regarding cross-domain MEV sources within the DEX ecosystem, specifically on loss-versus-rebalancing (LVR).
- [Oracleless Lending Protocol](https://blog.instadapp.io/oracleless-lending-protocol-on-uniswap-v4/): Creating a new lending protocol offering features like flexible liquidation thresholds, oracle-free operations, and enhanced earnings for liquidity providers.
- [Torando Cash on Hooks](https://twitter.com/witconomist/status/1694859874080076180?s=20): A Tornado-like system, utilizing all of Uniswap's liquidity as its pool.
- [Hook Safety as a Service](https://twitter.com/xin__wan/status/1695258362298933499): Insuring safety of a hook up to a certain amount.
- [Gasless Swaps](https://twitter.com/dhruvinparikh_/status/1691441830410461184?s=20): Incentivizing traders via a non-toxic MEV executer with gasless swaps.

## 👀 See Also

_Check out these related resources._

- [Uniswap Hooks Discussion Board](https://hooks.uniswapfoundation.org): A location to share skills, knowledge, and interests through ongoing conversation regarding Uniswap v4 hooks.
- [StackExchange: Hooks, returning the function selector](https://ethereum.stackexchange.com/questions/151985/why-do-we-need-to-check-function-return-right-selector): Explanation of why we return the function selector to signal successful function call with hooks (for example, deciding not to accept a donation).
- [Uniswap Twitter thread on the first ever Hookathon](https://twitter.com/UniswapFND/status/1683983199872122881?s=20): Highlights of the hookathon (hackthon for Uniswap hooks) including the r hackers (hookers) and the hooks the built.
- [Uniswap Twitter thread on TWAMM](https://twitter.com/Uniswap/status/1674452938683473921?s=20): 6-tweet thread on the use case for time weighted automatic market makers.

## 🙏 Thanks

_Thanks to these contributors for making this list possible._

- [fewwwww](https://github.com/fewwwww)
- [naddison36](https://github.com/naddison36)
- [0xV4L3NT1N3](https://github.com/0xV4L3NT1N3)
- [johnsonstephan](https://github.com/johnsonstephan)
