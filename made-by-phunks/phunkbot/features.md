---
icon: conveyor-belt-boxes
description: PHUNKBOT IS MODULAR AND CAN AiVOLVE EVEN FURTHER IN THE FUTURE
cover: ../../.gitbook/assets/Bildschirmfoto 2023-11-28 um 16.34.06.png
coverY: 44
layout:
  cover:
    visible: true
    size: full
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# FEATURES

## <mark style="color:blue;">`SALES MODULE`</mark>

This module is called `Erc721SalesService` and enables PhunkBot to post all Sales to Twitter and Discord simultaneously. To customise, just edit `/src/config.ts` file and let PhunkBot do its magic.

<details>

<summary>MODULE</summary>

{% code title="app.module.ts" %}
```typescript
import { Erc721SalesService } from './erc721sales.service';
```
{% endcode %}

</details>

<details>

<summary>ON TWITTER</summary>

#### Sample of PhunkBot Log for successfully processed Sales event

```log
2023-11-28 00:43:15] [base.service] [info]: Successfully tweeted: 1729299877790662770 -> Phunk #2949 was flipped for Ξ0.202 ($411) by servo.eth
| https://t.co/0MvKrg7ULB https://t.co/26upLUEDHu 
```

#### Output:

[https://x.com/PhunkBot/status/1729299877790662770](https://x.com/PhunkBot/status/1729299877790662770?s=20)

<img src="../../.gitbook/assets/Bildschirmfoto 2023-11-29 um 08.02.44.png" alt="" data-size="original">

</details>

<details>

<summary>ON DISCORD</summary>

#### Discord Output for tweet above

<img src="../../.gitbook/assets/Bildschirmfoto 2023-11-28 um 15.34.02 (1).png" alt="" data-size="original">

</details>

<details>

<summary>SUPPORTED</summary>

* [NotLarvaLabs](../notlarvalabs/) marketplace - Support for Bids, Buys and Sells.
* BLUR.io - Sweeps, Buys and Sells & support for **ERC20** "blurio pool" wrapped ETH.
* OpenSea marketplace (inkl. SeaPort) - Sweeps, Buys and Sells.
* LooksRare v2 - Sweeps, Buys and Sells.
* NFTX - Sweeps, Buys and Sells.
* X2Y2 - Sweeps, Buys and Sells.
* **MEV** sniping bot exotic transactions.
* <mark style="background-color:orange;">**CLI mode feature:**</mark> [<mark style="background-color:orange;">**CLI**</mark>](tutorials.md) <mark style="background-color:orange;">command implemented to replay transaction.</mark>
* Integrated **flywheel** (phunks.pro) sales into bot with custom Message.
* Integrated **Auctions** (phunks.auction) **sales only** with custom Message.
* **Embedded** discord bot design implemented with dynamic smart exchange **ICON** support.

</details>

{% hint style="info" %}
For all Sales Service functionalities and tutorials go to [tutorials.md](tutorials.md "mention")
{% endhint %}

***

## <mark style="color:blue;">`STATS MODULE`</mark>

This module is called `StatisticsService` and enables PhunkBot to index all transactions for your collection set under `/src/config.ts`.  With this indexed information, saved locally and synced in real time, your discord users get access to Volume stats, Trader stats and Token ownership info. \
It enables discord Application Commands like <mark style="color:blue;">`/volume`</mark> or <mark style="color:blue;">`/graph`</mark> and so much more.

<details>

<summary>MODULE</summary>

{% code title="app.module.ts" %}
```typescript
import { StatisticsService } from './extensions/statistics.extension.service';
```
{% endcode %}

</details>

<details>

<summary>ON DISCORD</summary>

#### Sample of PhunkBot Log for command <mark style="color:blue;">/owned \<wallet></mark>

```log
[2023-11-26 17:18:54] [statistics.service] [info]: ./token_images/phunk1313.png 
[2023-11-26 17:18:54] [statistics.service] [info]: ./token_images/phunk3301.png 
[2023-11-26 17:18:54] [statistics.service] [info]: ./token_images/phunk5799.png 
[2023-11-26 17:18:54] [statistics.service] [info]: ./token_images/phunk6128.png
```

#### Output:

<img src="../../.gitbook/assets/Bildschirmfoto 2023-11-28 um 15.54.57.png" alt="" data-size="original">

</details>

{% hint style="info" %}
For all Statistics Service Commands available check out [tutorials.md](tutorials.md "mention")&#x20;
{% endhint %}

***

## <mark style="color:blue;">`DAO MODULE`</mark>

This module is called `DAOService` and enables PhunkBot to autonomously govern custom Discord roles and provably fair token gated Voting system. \
In depth explanation and functions can be found under [governance.md](governance.md "mention").&#x20;

<details>

<summary>MODULE</summary>

{% code title="app.module.ts" %}
```typescript
import { DAOService } from './extensions/dao/dao.extension.service';
import { DAOController } from './extensions/dao/dao.controller';
```
{% endcode %}

</details>

<details>

<summary>ON DISCORD</summary>

#### Sample of PhunkBot command <mark style="color:blue;">/createpoll</mark>

<img src="../../.gitbook/assets/image (12) (3).png" alt="" data-size="original">

#### Output:

![](<../../.gitbook/assets/image (53).png>)

</details>

{% hint style="info" %}
For all DAO Service Commands available check out [tutorials.md](tutorials.md "mention")
{% endhint %}

***
