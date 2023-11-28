---
description: PHUNKBOT IS MODULAR AND CAN EVOLVE EVEN FURTHER IN THE FUTURE
cover: ../../.gitbook/assets/Bildschirmfoto 2023-11-28 um 16.28.58.png
coverY: -32.508017960230916
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

# ➖ FEATURES

## <mark style="color:orange;">`SALES SERVICE`</mark>

This module is called `Erc721SalesService` and enables PhunkBot to post all Sales to Twitter and Discord simultaneously. To customise, just edit `/src/config.ts` file and let PhunkBot do his magic.

<details>

<summary>MODULE</summary>

```typescript
import { Erc721SalesService } from './erc721sales.service';
```

</details>

<details>

<summary>FOR TWITTER</summary>

#### Sample of PhunkBot Log for successfully processed Sales event:

```log
2023-11-28 00:43:15] [base.service] [info]: Successfully tweeted: 1729299877790662770 -> Phunk #2949 was flipped for Ξ0.202 ($411) by servo.eth
| https://t.co/0MvKrg7ULB https://t.co/26upLUEDHu 
```

#### Output:

[https://x.com/PhunkBot/status/1729299877790662770](https://x.com/PhunkBot/status/1729299877790662770?s=20)

</details>

<details>

<summary>FOR DISCORD</summary>

#### Discord Output for tweet above:

<img src="../../.gitbook/assets/Bildschirmfoto 2023-11-28 um 15.34.02 (1).png" alt="" data-size="original">

</details>

***

## <mark style="color:orange;">`STATS SERVICE`</mark>

This module is called `StatisticsService` and enables PhunkBot to fetch all transactions for collection set under `/src/config.ts`.  With this information saved locally and synced in real time, discord users get access to useful informations like Volume stats, Trader stats and Token ownership. It enables discord Application Commands like `/volume` or `/graph` and much more.

<details>

<summary>MODULE</summary>

```typescript
import { StatisticsService } from './extensions/statistics.extension.service';
```

</details>

<details>

<summary>FOR DISCORD</summary>

#### Sample of PhunkBot Log for command /owned \<wallet>

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
For all `StatisticsService` Commands available check out [tutorials.md](tutorials.md "mention")&#x20;
{% endhint %}

***

## <mark style="color:orange;">`DAO SERVICE`</mark>

This module is called DAOService and enables PhunkBot to autonomously govern custom Discord roles and provably fair token gated Voting system. in depth explanation and functions can be found under [wip-governance.md](wip-governance.md "mention").&#x20;

<details>

<summary>MODULE</summary>

```typescript
import { DAOService } from './extensions/dao/dao.extension.service';
import { DAOController } from './extensions/dao/dao.controller';
```

</details>

<details>

<summary>FOR DISCORD</summary>

#### Sample of PhunkBot command /createpoll

<img src="../../.gitbook/assets/image (12).png" alt="" data-size="original">

#### Output:

![](<../../.gitbook/assets/image (53).png>)

</details>

{% hint style="info" %}
For all `DAOService` Commands available check out [wip-governance.md](wip-governance.md "mention")
{% endhint %}

***
