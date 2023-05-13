---
theme: eloc
title: "`Ethereum and Its Rabbitholes`"
---

## `Ethereum and Its Rabbitholes`

@libevm

---

# Sponsors

<img width="512" src="https://images.squarespace-cdn.com/content/v1/61ee5a6c04b4a81efde07fa3/7737d0e7-c4ef-45b7-8fed-f357188de30e/Untitled.jpg"/>
<br/>
<img width="512" src="https://i.imgur.com/IL6W7AF.png"/>

---

`No dumb questions`

Got a question? Ask away!

---

# Ethereum?

---

> Ethereum is a public computer that lets people create

> `anything`

> **without intermediaries**

---

## Anything?

<v-clicks>

- Assets (Stablecoins / ETFs)
- Protocols (Finance / Commerce)

</v-clicks>

<!--
You can create:
- Digital assets, such as stablecoins, gold-backed assets, or stablecoin derivatives (will get onto that later)
- Digital protocols that lets you do something with said assets (exchange, lending/protocol)

And in the process of digital asset creation and usage, markets pop up, inefficiency arrises and value is left to be extracted

And to faciliate all that, we need infrastructure, so lets talk about a few of the rabbitholes that exists on ethereum
-->

---

## Rabbitholes

- Infrastructure (Beaconchains / Light clients)
- Computer Science / Math (Data structures / Languages)
- Decentralized Finance (DeFi)
- Maximum Extractable Value (MEV)

<!--
Infrastructure
- Mention ETH 1.0 -> ETH 2.0 transition, how they modularize the consensus layer from the exeuction engine
- How the manage to handle random numbers
  - random numbers are used to make sure that no one can predict the future and game the system
- It IS a hard problem, how do you generate a random number in a deterministic machine?

Computer Science
- Efficient store data? Hashmap? Merkle Tree? Sparse Merkle Tree?
- Programming Languages - Solidity, Vyper, Huff, Yul/Yul+
- Zero Knowledge Proofs -  ZKSnarks/ZKStarks, Polynomial Commitments

DeFi
- Talk about ERC20 assets ('just a standard on how something is define, e.g. Tree is something that has root, trunk, branch')
- Mention the fact that ERC20s are infinitely composable (bring up Aave/Compound, and their interest bearing version)
- Bring up Alchemix
- Bring up flashloans, say it'll be used for the last slide

MEV
- Talk about DAI/USDC arb
- Talk about flashbots
- Talk about samonella
-->

---

## Rabbitholes

- ~~Infrastructure (Beaconchains / Light clients)~~
- ~~Computer Science / Math (Data structures / Languages)~~
- Decentralized Finance (DeFi)
- Maximum Extractable Value (MEV)

---

## Speaker Interest

<QRCode :value="'https://forms.gle/xnDi99er2e4W4SVv9'"/>

<a>ethmelbourne.co</a>

---

## Decentralized Finance (DeFi)

---

### Beating Heart of DeFi

[`ERC20 Standard`](https://ethereum.org/en/developers/docs/standards/tokens/erc-20/)

---

[`ERC20 Standard`](https://ethereum.org/en/developers/docs/standards/tokens/erc-20/)

> Set of rules for digital assets to behave on Ethereum

```solidity
function name() public view returns (string)
function symbol() public view returns (string)
function decimals() public view returns (uint8)
function totalSupply() public view returns (uint256)
function balanceOf(address _owner) public view returns (uint256 balance)
function transfer(address _to, uint256 _value) public returns (bool success)
function transferFrom(address _from, address _to, uint256 _value) public returns (bool success)
function approve(address _spender, uint256 _value) public returns (bool success)
function allowance(address _owner, address _spender) public view returns (uint256 remaining)
```

---

[`ERC20 Standard`](https://ethereum.org/en/developers/docs/standards/tokens/erc-20/)

> Set of rules for digital assets to behave on Ethereum

```bash
name                    -> "USD Coin"
symbol                  -> "USDC"
totalSupply             -> Supply of USDC Coin
balanceOf "vitalik.eth" -> Vitalik's USDC Supply
transfer "10" "abc.eth" -> Transfer 10 of my tokens to abc.eth
```

<!--
key note: erc20 standard is up to the implementators vision
-->

---

Why do I care about some digital asset standard?

---

### `Infinite Composability`

Infinite Possibilities

---

### Borrowing / Lending Protocols

<p>
<img width=420 src="https://assets-global.website-files.com/606f63778ec431ec1b930f1f/633ee3b889712fca0b43da1d_aave.jpg"/>
<br/>
<img width=420 src="https://assets-global.website-files.com/606f63778ec431ec1b930f1f/633eb43a34a875737944c7a3_Compound-Review-A-Beginner-Guide-to-Compound-Finance.png"/>
</p>

<!--
What do I mean by that? Lets take a step back and talk about one of the DeFi primitives, borrowing and lending protocols
-->

---

### Simplistic Bank

- Lenders: Earn interest on asset
- Borrowers: Line of credit (!!)

<!--
Theses lending and borrowing protocols are akin to simplistic versions of banking

Of course there's a lot of things going on behind the scenes like risk management, asset due diligence, and so on

Line of credit, its digital, and atomic (stress atomic)
-->

---

Real World Example: Mortgage

1. Put house up as collateral
2. Loan $$ from bank

- a: You repay loan, get back collateral
- b: Fail to repay loan, bank seizes house

<!--
Lets make it more concrete and draw some parallels to the real world
-->

---

DeFi Land

1. Put USDC up as collateral
2. Loan ETH from Aave

- a: You repay loan, get back collateral
- b: Fail to repay loan, get liquidated

---

DeFi Land

1. `Put USDC up as collateral`
2. Loan ETH from Aave

- a: You repay loan, get back collateral
- b: Fail to repay loan, get liquidated

<!--
I would like to focus on the first part, where you put USDC up as collateral
-->

---

## Process

<v-clicks>

1. Deposit `ERC20: USDC` into Aave
2. Receive `ERC20: aUSDC` (Aave-USDC)

</v-clicks>

<!--
The deposit process roughly looks something like this, you have a digital asset USDC that you deposit into Aave,
You get back aUSDC from Aave
-->

---

`ERC20: aUSDC`

- Get back your original deposit
- ...and any interest it accrued

<!--
Seems like it hasn't hit anyone yet, so let me reiterate, aUSDC entitles you to:
- You original deposit, and any interests it accrued
- AND it adheres to the ERC20 standard
-->

---

Whats so special about `ERC20: aUSDC`?

<!--
How is it different from any other digital asset
-->

---

## `ERC20: aUSDC` = Liquid Collateral

<!--
Liquid collateral, it represents you deposit in the biggest defi 'bank' Aave

You, as a protocol developer, or payment on/off ramp personal because of the nature of composability
can accept aUSDC for whatever purpose you see fit, WITHOUT asking for permission from the bank of Aave
-->

---

What good is `ERC20: aUSDC`?

<v-click>

#### Enter: `Self Re-paying Loans`

<img width=512 src="https://techstory.in/wp-content/uploads/2022/01/alchemix-defi-1024x501-1.jpg"/>

</v-click>

---

Self Re-paying Loans

1. Deposit {x} `ERC20: aUSDC` as collateral
2. Loan {y} `ERC20: AUDC`
3. Reclaim `ERC20: aUSDC` when {i >= y}

```bash
x = aUSDC amount
i = Interest from aUSDC
y = AUDC amount
```

<!--
That is liquid collateral. We can go a step further... but we need to talk about something else: decentralized exchanges
-->

---

## Decentralized Exchanges (DEXes)

> Allows you to swap between `ERC20` tokens, permissionlessly

<!--
I don't need to be an 'accreddited investor' just to be able to invest in some company's IPO

Note that I'm not going to go into the Math of these Decentralized exchanges, as that topic itself can be a whole meetup discussion
-->

---

User

1. Has `ERC20: A`
2. Swaps `ERC20: A` -> `ERC20: B`
3. Now has `ERC20: B`

---

Market Maker / Liquidity Provider (LPs)

1. Has {x} `ERC20: A` and {y} `ERC20: B` at time {t}
2. Supply {x} and {y} liquidity to DEX
3. Time passes: `ERC20: A` and `ERC20: B` price changed
4. Remove {i} `ERC20: A` and {j} `ERC20: B` liquidity from DEX

---

Why are the **amounts in** and **amounts out** different?

> `x y = k` formula

---

> 2. Supply {x} and {y} liquidity to DEX

<img width=1024 src="https://i.imgur.com/VB019pP.png"/>

---

> 3. Time passes: `ERC20: A` and `ERC20: B` price changed

<img width=1024 src="https://i.imgur.com/fo0UsGj.png"/>

---

> 4. Remove {i} `ERC20: A` and {j} `ERC20: B` liquidity from DEX

<img width=1024 src="https://i.imgur.com/D4JNzUe.png"/>

---

`Impermanent Loss (IL)`

> (Temporary) value loss experienced by LPs in a DEX due to token price changes

---

Market Maker / Liquidity Provider (LPs)

2. `Supply {x} and {y} liquidity to DEX`

<v-click>

How to represent receipt for liquidity provided?

</v-click>

---

`ERC-20 Tokens`

<p>

- LP for `ERC20: A` and `ERC20: B`
- Receive `ERC20: LP(A:B)`

</p>

- Burn `ERC20: LP(A:B)`
- Receive `ERC20: A` and `ERC20: B`

<v-click>

Liquid Collateral!!

</v-click>

---

What if...?

<v-clicks>

- Rewards users who **stake** `ERC20: LP(A:B)`

</v-clicks>

<!--
What if we reward users who stake (which means lock up tokens for a set about of time) LP (A:B)
You just created an incentive for people to market make tokens A and B, which is really handy if
you're launching a new token and you need liquidity

Or... you could be a competitor to the platform
-->

---

Short Tangent: Vampire Attacks

> Origins of Sushiswap 🍣

---

In the beginning was `Uniswap 🦄`

- Receive `UNI-LP` for providing liquidity on `Uniswap 🦄`

---

Then came `Sushiswap 🍣`

- Had a token `$SUSHI`
- Incentivized people to stake `UNI-LP SUSHI/ETH`
- And also... `UNI-LP ETH-USDC`, `UNI-LP ETH-USDT`...

---

<img src="https://i.imgur.com/aUJMtra.png"/>

---

What `Sushiswap 🍣` did:

1. Cloned `Uniswap 🦄`'s DEX code
2. Burn staked `UNI-LP` from `Uniswap 🦄`
3. Provided liquidity on `Sushiswap 🍣`
4. Credited staked users with identical `SUSHI-LP`

<v-click>

(How to get $830m in deposits in 4 simple steps)

</v-click>

---

So much more to DeFi: explore it yourself!

- Flashloans
- NFTs (represent collateral + debt positions)
- Other DEXes (Curve.fi, Balancer)
- Yield aggregators
- Liquid Staking Derivatives (LSD)
- ...

---

## Maximum Extractable Value (MEV)

<v-clicks>

> Printing money from thin air

> Adversarial PVP

</v-clicks>

<!--
TLDR is to gain tips and tricks
-->

---

Printing money from thin air?

---

Early days there was `MakerDAO`

- Stablecoin ([DAI]()) issuer
- Provide collateral to mint [DAI]()

---

`MakerDAO`'s collateral system

- Collateral Ratio of [USDC](): `110%`
- Need `1.10` [USDC]() to mint `1` [DAI]()

---

<img src="https://i.imgur.com/8ima2TI.png"/>

<!--
Trading on the open market for >1 dollar
-->

---

Stablecoins should be stable!

---

`MakerDAO`'s proposal:

- Lower collateral Ratio of [USDC]() to: `101%`
- Need `1.01` [USDC]() to mint `1` [DAI]()
- **While [DAI]() was trading on the open market for `1.06` [USDC]()**

<v-click>

(Spoiler: The proposal passed after a few days)

</v-click>

<!--
Does anyone see the opportunity here?
-->

---

> How to print money in March 2020

Lets say: `1` [DAI]() = `1.05` [USDC]()

1. Start with `1.01` [USDC]()
2. Collateralize `1.01` [USDC]() into `1` [DAI]()
3. Sell `1` [DAI]() into `1.05` [USDC]()

---

<img src="https://i.imgur.com/HiQmfyV.png"/>

---

Adversarial PVP

---

When you trade on Ethereum

- Your trades are **public**

---

> Abusing that information with a Bot

1. Victim: submits buy order for `ERC20: A`
2. Bot: Sees order, immediately buys `ERC20: A`
3. Victim: Order goes through, receives less `ERC20: A`
4. Bot: Sells `ERC20: A` at higher price

---

> Early days bots were rudimentary with `minimal` security checks

Bots assumed `ERC20` tokens would be implemented correctly

---

> Assumptions

```solidity
function transfer(address to, uint256 amount) public {
  balances[msg.sender] -= amount;
  balances[to] += amount;
}
```

---

What if...?

We had a `ERC20` token that `diverged` from the standard?

---

> Its a trap!

```solidity
function transfer(address to, uint256 amount) public {
  if (whitelisted[msg.sender]) {
    balances[msg.sender] -= amount;
    balances[to] += amount;
  }
}
```

---

<img src="https://i.imgur.com/jpDkFrf.png/">

---

So much more in MEV

- Sandwiching
- Backrunning
- Long/short tail arbitrages
- https://eigenphi.io/

---

> Thank You! Questions?

Speaker: @libevm

`Ethereum Melbourne looking for more sponsors!`

---