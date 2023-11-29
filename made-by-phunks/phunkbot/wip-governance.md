---
description: COMMUNITY GOVERNANCE POWERED by PHUNKBOT
cover: ../../.gitbook/assets/Bildschirmfoto 2023-11-29 um 13.13.44.png
coverY: 0
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
    visible: false
  pagination:
    visible: true
---

# ➖ 🚧WIP🚧 GOVERNANCE

#### Welcome to first actual, autonomous, self hosted DAO Service for Community Governance.

## <mark style="color:orange;">`Challenge`</mark>

Coming to consensus in web3 is big challenge, decentralized nature of Communities around Crypto Projects brought up question like how can decentralized Community come to consensus in decision making without being reliant on old centralised Solutions or single point of failure. \
Smart people came out with Solutions by offering Services to Communities like for example CollabLand (token Gated discord roles and management), GitCoin (bind Social accounts to your web3 identity), SnapShot (transparent and certificated Voting system), EasyPoll (anonymous voting bot for Discord), TweetShift (Discord Sales Bot). While all those Services are of great benefit for whole Crypto Community, they come with the Price. Making it really complicated for onboarding and thus limiting participation there is also risk involved with how user data is being processed. Web3 is all about own you own Data, Simplicity, not to rely on third party Services and be self sufficient as individual and Community. How things are set now is not only not optimal but also undermines basic principles of Web3: _Decentralised, Trustless and Transparent._&#x20;

{% hint style="info" %}
Web3 introduces four core principles that promise to reshape the digital landscape: ownership, commerce, identity, and governance.
{% endhint %}

## <mark style="color:orange;">`Solution`</mark>

With PhunkBot module called [`DAOService`](features.md), communities don't need to be dependent on third party Services for Governance anymore. In true Web3 fashion, PhunkBot makes third party Services like CollabLand, GitCoin, SnapShot, EasyPoll and TweetShit obsolete. \
Its Self hosted, Self-Sufficient Service by the Community for the Community, safe to use and simple as running Discord [application commands](tutorials.md).\
**Solution we found is, it all revolves around token ownership. PhunkBot elegantly eliminate possible sybil attack with simple and configurable `minOwnedCount`&`minOwnedTime` safety checks and by binding discord account or social account with web3 wallet(s). This enables individual to safely participate in community Governance and it guarantees provably fair process to find consensus.**&#x20;

```typescript
import { DAOService } from './extensions/dao/dao.extension.service';
```

## <mark style="color:orange;">`Commands Explained`</mark>

<details>

<summary>/createpoll</summary>

#### ....

#### Admin Command

```typescript
/createpoll <description> <duration> <role> <emojis>
```

![](<../../.gitbook/assets/image (74).png>)

#### Output

![](<../../.gitbook/assets/image (75).png>)

</details>

<details>

<summary>/pollresults</summary>

#### ....

#### Admin Command

```typescript
/pollresults <poll id>
```

![](<../../.gitbook/assets/image (76).png>)

#### Gett Poll ID

![](<../../.gitbook/assets/image (78).png>)

#### Output

![](<../../.gitbook/assets/image (77).png>)



</details>

<details>

<summary>/closepoll</summary>

#### .....

#### Admin Command

```typescript
/closepoll <poll id>
```

![](<../../.gitbook/assets/image (79).png>)







</details>

<details>

<summary>/deletepoll</summary>

#### .....

#### Admin Command

```typescript
/deletepoll <poll id>
```

![](<../../.gitbook/assets/image (80).png>)





</details>

<details>

<summary>/listpolls</summary>

#### ....

#### User Command

![](<../../.gitbook/assets/image (81).png>)

#### Output

![](<../../.gitbook/assets/image (82).png>)



</details>

***

***

## <mark style="color:orange;">`Voting Process Explained`</mark>

<details>

<summary>CAST VOTE</summary>

.....

![](<../../.gitbook/assets/image (83).png>)

....

![](<../../.gitbook/assets/image (84).png>)





</details>

<details>

<summary>RESULTS</summary>

.....

![](<../../.gitbook/assets/image (85).png>)







</details>

***

## <mark style="color:orange;">`Discord Roles Explained`</mark>

<details>

<summary>ROLES</summary>

....

</details>
