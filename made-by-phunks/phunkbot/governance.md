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

# ➖ GOVERNANCE

#### Welcome to first actual, autonomous, self hosted DAO Service for Community Governance.

## <mark style="color:orange;">`Challenge`</mark>

Achieving consensus in Web3 is big challenge, decentralized nature of Communities around Crypto Projects brought up questions like how can decentralized Community come to consensus in decision making without being reliant on old centralised Solutions or single point of failure. \
\
Smart people came out with Solutions by offering Services to Communities like for example CollabLand (token Gated discord roles and management), GitCoin (bind Social accounts to your Web3 identity), SnapShot (transparent and certificated Voting system), EasyPoll (anonymous voting bot for Discord), TweetShift (Discord Sales Bot). \
\
While all those Services are of great benefit for whole Crypto Community, they come with the Price. Making it really complicated for onboarding and thus limiting participation, there is also risk involved with how user data is being processed/stored. Web3 is all about own you own Data, Simplicity, not to rely on third party Services and be self sufficient as individual and Community. \
How things are set currently is not only not optimal but also undermines basic principles of Web3: _Decentralised, Trustless and Transparent._&#x20;

{% hint style="info" %}
Web3 introduces four core principles that promise to reshape the digital landscape: ownership, commerce, identity, and governance.
{% endhint %}

## <mark style="color:orange;">`Solution`</mark>

With PhunkBot module called [`DAOService`](features.md) enabled, communities don't need to be dependent on third party Services for Governance anymore. In true Web3 fashion, PhunkBot makes third party Services like CollabLand, GitCoin, SnapShot, EasyPoll and TweetShift obsolete. \
\
PhunkBot is in house hosted, Self-Sufficient Service by the Community for the Community, safe and as simple to use as running Discord [application commands](tutorials.md).\
\
**Solution we found is, it all revolves around token ownership. PhunkBot elegantly eliminates possible sybil attacks with simple and configurable `minOwnedCount`&`minOwnedTime` safety checks and by binding discord account and/or social account with Web3 wallet(s) holding underlying asset.** \
**This enables individual to safely participate in community Governance and it guarantees provably fair process to achieve consensus.**&#x20;

```typescript
import { DAOService } from './extensions/dao/dao.extension.service';
```

## <mark style="color:orange;">Sybil Attack handling</mark>

<details>

<summary>ELEGANCE ACHIEVED</summary>

Hardly any Community in Crypto is immune to [Sybil Attack](https://en.wikipedia.org/wiki/Sybil\_attack) especially where individuals can exploit Governance system to their monetary advantage.

We at Phunks Community, while exploring best ways to Achieve consensus for Proposals came to conclusion that [current system](governance.md#challenge) if flawed and undermines basic Principles of Web3.&#x20;

We found a new, better way to Govern decentralized Community by utilising already available ideas and tools into Simple yet powerful way.

We enabled PhunkBot to serve as autonomous, trustless Bot that elegantly eliminates Sybil in dynamic and configurable setup. &#x20;

{% code title="config.ts" %}
```typescript
      minOwnedCount: 1,
      minOwnedTime: 15, // in days
```
{% endcode %}

Example Above is set off Parameters that writes a Simple Rule that if user has minimum of 1 Asset and owns that Asset for minimum of 15 days is allowed to Vote. Only if that user already [bounded](governance.md#bounded) his Discord and/or Twitter account to his Web3 wallet(s)..&#x20;

Example bellow is another (optional) set of rules where only [permitted](governance.md#createpoll) Discord Roles that PhunkBot granted to specific underlying Assets are allowed to Vote.

{% code title="dao.extention.service.ts" %}
```typescript
if (poll.discord_role_id && !member.roles.cache.has(poll.discord_role_id)) {
```
{% endcode %}

</details>

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

***

## <mark style="color:orange;">`DAOService Commands Explained`</mark>

<details>

<summary>/bindweb3</summary>



</details>

<details>

<summary>/bindtwitter</summary>



</details>

<details>

<summary>/bounded</summary>



</details>

<details>

<summary>/createpoll</summary>

This commands is reserved for Discord Admins only, executing this command with parameters set kicks off new Poll where community can vote on Active proposals and as a result achieve consensus.

* Voting itself is anonymous and final results get auto revealed only after set time expires.&#x20;
* Only Admins are [permitted](governance.md#pollresults) to see casted Votes and Voters for auditing purposes.
* If optional <mark style="color:blue;">\<role></mark> is set, only users with set Discord role can cast a Vote.
* With set parameters under <mark style="color:orange;">src/config.ts</mark> Sybil attacks are mitigated, read more [here](governance.md#sybil-attack-handling).

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