# Awesome Uniswap v4 Hooks

A curated list of awesome [Uniswap v4](https://github.com/Uniswap/v4-core) [hooks](https://github.com/Uniswap/v4-periphery/tree/main/contracts/hooks) resources.

## Hooks

- [saucepoint/median-oracles](https://github.com/saucepoint/median-oracles): Experimental variations for a Median Price Oracle with Uni v4.
- [trading-days](https://github.com/horsefacts/trading-days): A Uniswap v4 hook that reverts when markets are closed in New York.
- [saucepoint/v4-stoploss](https://github.com/saucepoint/v4-stoploss): Stop Loss Orders via Uniswap V4 Hooks.
- [jtriley-eth/huff-hooks](https://github.com/jtriley-eth/huff-hooks): Uniswap V4 Huff Hooks.
- [saucepoint/v4-hyperlane-LPTs](https://github.com/saucepoint/v4-hyperlane-LPTs): Automate LPTs on destination chains using Hyperlane in Uniswap v4 Hooks.
- [jamesbachini/Uniswap-V4-Torres-Token-Sale](https://github.com/jamesbachini/Uniswap-V4-Torres-Token-Sale): A Solidity ERC20 token using Uniswap v4 hooks to create a compliant token sale system following judge Torres ruling in the XRP case.
- [wagmiwiz/nft-owners-only-uniswap-hook](https://github.com/wagmiwiz/nft-owners-only-uniswap-hook): A Uniswap v4 hook that disallows a swap if sender doesn't own an ERC721 NFT.
- [antoniordf/impermanent-loss-hedge](https://github.com/antoniordf/impermanent-loss-hedge): Uniswap V4 hook to hedge against impermanent loss.

## Templates

- [saucepoint/v4-template](https://github.com/saucepoint/v4-template): Template repository for writing Uniswap V4 Hooks.
- [ArrakisFinance/uni-v4-playground](https://github.com/ArrakisFinance/uni-v4-playground): Uniswap v4 playground.
- [LucasMartinCalderon/Uniswap](https://github.com/LucasMartinCalderon/Uniswap): Uniswap V4 Hooks Template for ETHGlobal Hackathon.

## Tools

- [devtooligan/HookMineAndSinker](https://github.com/devtooligan/HookMineAndSinker): Mine addresses for UniswapV4 Hooks.
- [drgorillamd/uniV4-hook-deployer](https://github.com/drgorillamd/uniV4-hook-deployer), Uniswap V4 hook create2 deployer.
- [jamesbachini/Uniswap-v4-Tests](https://github.com/jamesbachini/Uniswap-v4-Tests), A test suite for working with Uniswap v4 Hooks.

## Tutorials

- [LearnWeb3/Uniswap v4 Hooks: Create a fully on-chain "take-profit" orders hook on Uniswap v4](https://learnweb3.io/lessons/uniswap-v4-hooks-create-a-fully-on-chain-take-profit-orders-hook-on-uniswap-v4/)


## Ideas

- A time-weighted average market maker ([TWAMM](https://github.com/Uniswap/v4-periphery/blob/main/contracts/hooks/examples/TWAMM.sol))
- Dynamic fees based on [volatility](https://github.com/Uniswap/v4-periphery/blob/main/contracts/hooks/examples/VolatilityOracle.sol) or other inputs
- [Onchain limit orders](https://github.com/Uniswap/v4-periphery/blob/main/contracts/hooks/examples/LimitOrder.sol)
- Depositing out-of-range liquidity into lending protocols
- Customized onchain oracles, such as [geomean oracles](https://github.com/Uniswap/v4-periphery/blob/main/contracts/hooks/examples/GeomeanOracle.sol)
- Autocompounded LP fees back into the LP positions
- Internalized MEV profits are distributed back to LPs
- [v4 hooks as keeper](https://twitter.com/saucepoint/status/1686070429503676416)
- [Oracleless lending protocol](https://blog.instadapp.io/oracleless-lending-protocol-on-uniswap-v4/)
