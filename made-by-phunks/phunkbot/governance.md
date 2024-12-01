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

Achieving consensus in Web3 is a big challenge, decentralized nature of Communities around Crypto Projects brought up questions like how can decentralized Community come to consensus in decision making without being reliant on old centralised Solutions or single point of failure. \
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
PhunkBot is in house, Self-Sufficient Service hosted by the Community for the Community, safe and as simple to use as running Discord [application commands](governance.md#daoservice-commands-explained) or pressing an emoji to vote.\
\
**Solution we found is, it all revolves around token ownership and identity in Web3. By binding those two Assets we can actually solve Governance for decentralized community.**\
**PhunkBot elegantly eliminates possible sybil attacks with simple and configurable `minOwnedCount`&`minOwnedTime` safety checks and by binding discord account and/or social account with Web3 wallet(s) holding underlying Assets or even Traits of underlying Assets.** \
**This enables individual to safely participate in community Governance and it guarantees provably fair process to achieve consensus.**&#x20;

{% code title="app.module.ts" %}
```typescript
import { DAOService } from './extensions/dao/dao.extension.service';
```
{% endcode %}

***

## <mark style="color:orange;">`Sybil Attack`</mark>

<details>

<summary>ELEGANCE ACHIEVED</summary>

Hardly any Community in Crypto is immune to [Sybil Attack](https://en.wikipedia.org/wiki/Sybil_attack) especially where individuals can exploit Governance system to their monetary advantage.

We at Phunks Community, while exploring best ways to Achieve consensus for Proposals came to conclusion that [current system](governance.md#challenge) if flawed and undermines basic Principles of Web3.&#x20;

We found a new, better way to Govern decentralized Community by utilising already available ideas and tools into Simple yet powerful way.

We enabled PhunkBot to serve as autonomous, trustless Bot that elegantly eliminates Sybil in dynamic and configurable setup. &#x20;

{% code title="config.ts" %}
```typescript
      minOwnedCount: 1,
      minOwnedTime: 15, // in days
```
{% endcode %}

Example Above is set off Parameters that writes a Simple Rule that if user has minimum of \
1 underlying Asset and owns that Asset for minimum of 15 days is allowed to Vote. Only works if that user already [bounded](governance.md#bounded) his Discord and/or Twitter account to his Web3 wallet(s).&#x20;

Example bellow is another (optional) set of rules where only [permitted](governance.md#createpoll) Discord Roles that PhunkBot granted to a specific underlying Assets/Traits are allowed to Vote.&#x20;

{% code title="dao.extention.service.ts" %}
```typescript
if (poll.discord_role_id && !member.roles.cache.has(poll.discord_role_id)) {
```
{% endcode %}

<mark style="background-color:orange;">Also here, First rule</mark> <mark style="background-color:orange;"></mark><mark style="background-color:orange;">**minOwnedCount & minOwnedTime**</mark> <mark style="background-color:orange;"></mark><mark style="background-color:orange;">always applies.</mark> \
<mark style="background-color:red;">Additional Rules like</mark> <mark style="background-color:red;"></mark><mark style="background-color:red;">**minDiscordActivity & minTwitterActivity**</mark> <mark style="background-color:red;"></mark><mark style="background-color:red;">can be added in the future.</mark>

</details>

***

## <mark style="color:orange;">`Voting Process Explained`</mark>

<details>

<summary>HARDCODED RULES</summary>

#### For users to participate in Voting Process, few simple conditions needs to be met.

* User holds underlying Asset, for example Phunk NFT.
* User holds underlying Asset for minimum [threshold](governance.md#sybil-attack) time set.
* User has Discord and optional Twitter Account.
* User [bounded](governance.md#daoservice-commands-explained) his Discord and optional Twitter Account.
* For Vote to be considered Success, min Vote count [threshold](governance.md#min-vote-count) needs to be reached.

<mark style="background-color:red;">1 bounded Identity even with multiple Wallets and Phunks NFTs equals 1 Vote.</mark>

<mark style="background-color:green;">That's it! Player one ready, go!</mark>&#x20;

</details>

<details>

<summary>START NEW POLL</summary>

This commands is reserved for Discord Admins only and is explained here:

-> [#createpoll](governance.md#createpoll "mention")

</details>

<details>

<summary>CAST YOUR VOTE</summary>

By default users have two options to Vote 👍 (Yes) and 👎 (No).

Note: your Vote is anonymous and is not visible to other users, however Admins are allowed to privately [audit](governance.md#pollresults) all the Voters/Votes for [security](governance.md#sybil-attack) purposes and if necessary to provide proof in case of a dispute.

Not&#x65;**:** once Voted, Vote can not be redacted! You can however change your Vote from yes to no or other way around during whole voting period without limitations.

#### If Vote was successfully recorded, user gets confirmation message from PhunkBot

![](<../../.gitbook/assets/image (83).png>)

#### If user is not allowed to Vote, user gets notification message from PhunkBot

![](<../../.gitbook/assets/image (84).png>)

<mark style="background-color:red;">To receive PhunkBot notifications you need to have your Discord DMs open.</mark>\ <mark style="background-color:orange;">To see all Active Polls to Vote, simply run /listpolls</mark> [<mark style="background-color:orange;">command</mark>](governance.md#daoservice-commands-explained) <mark style="background-color:orange;">on Discord or go to:</mark>\
[https://phunk.cc/polls/](https://phunk.cc/polls/)

#### DEMO

<img src="../../.gitbook/assets/2023-12-05_10-06-43 (1).gif" alt="" data-size="original">

Vote demo for custom Discord role powered by PhunkBot.

</details>

<details>

<summary>MIN VOTE COUNT</summary>

Optional Admins can set `minimumVotesRequired` for Poll to be considered Success or if minimum threshold was not Reached is marked as Failed, therefore consensus not reached.&#x20;

{% code title="dao.extention.service.ts" %}
```typescript
    if (minimumVotesRequired) {
      const reached = voteCount >= minimumVotesRequired ? '✅' : '❌'
      msg += `\nMinimum votes required: **${minimumVotesRequired}** (Reached: ${reached})`
    }
```
{% endcode %}

#### Input

<img src="../../.gitbook/assets/Bildschirmfoto 2023-12-03 um 10.15.49.png" alt="" data-size="original">

#### Output

<img src="../../.gitbook/assets/Bildschirmfoto 2023-12-03 um 10.15.21.png" alt="" data-size="original">

<mark style="background-color:orange;">Note: If min threshold of Votes is set too for example 30 and reached; Min votes required:</mark> <mark style="background-color:orange;"></mark><mark style="background-color:orange;">**30**</mark> <mark style="background-color:orange;"></mark><mark style="background-color:orange;">(Reached: ❌) will automatically change to Min votes required:</mark> <mark style="background-color:orange;"></mark><mark style="background-color:orange;">**30**</mark> <mark style="background-color:orange;"></mark><mark style="background-color:orange;">(Reached: ✅).</mark>

</details>

<details>

<summary>RESULTS</summary>

To avoid user being influenced by Vote weight going in one direction and to keep Voting process as fair as possible, it is not possible to see current results nor count of yes or no Votes/Voters. Only after [set time](governance.md#createpoll) for Poll expired, final results are automatically Revealed.

#### Output

![](<../../.gitbook/assets/Bildschirmfoto 2023-12-04 um 07.09.22.png>)

</details>

***

## <mark style="color:orange;">`Discord Roles Explained`</mark>

<details>

<summary>ROLES</summary>

By binding Discord Account with your Web3 wallet(s), PhunkBot automatically Grants you Discord roles depending on underlying Asset and parameters set under `src/config.ts`.&#x20;

This can be for example one Role for holding underlying Asset or Multiple Roles for holding Specific Traits of underlying Collection.

<img src="../../.gitbook/assets/Bildschirmfoto 2023-11-30 um 22.49.38.png" alt="" data-size="original">

#### Code Example of Role granted to Stringy Hair Trait Holders

{% code title="config.ts" %}
```typescript
    {
      guildId: '873564453227094078',
      roleId: '1174817463515500574',
      specificTrait: {
        traitType: 'Hair',
        traitValue: 'Stringy Hair'
      }
    },
```
{% endcode %}

#### Example of PhunkBot log when granting roles

{% code title="dao.extention.service.ts" %}
```typescript
[start:prod] [2023-11-30 22:58:57] [dao.extension.service] [info]: grantRoles()
[start:prod] --> granting PHUNK to avolalim.eth
[start:prod] --> granting PHUNK to MACHO 💥
[start:prod] --> granting PHUNK to .meuleman
[start:prod] --> granting PHUNK to dovebot <afk>
[start:prod] --> granting PHUNK to shalfean
[start:prod] --> granting PHUNK to qukuaiboyou
[start:prod] --> granting PHUNK to jacopoman
[start:prod] --> granting PHUNK to 9999999333
[start:prod] --> granting PHUNK to cadillion
[start:prod] --> granting PHUNK to doli0li
[start:prod] --> granting PHUNK to web_gnar
```
{% endcode %}

<mark style="background-color:orange;">grantRoles() is handled by PhunkBot automatically and if user at anytime or for any reason removes underlying Asset from his bounded Web3 wallet, Role(s) get redacted.</mark> \
<mark style="background-color:red;">**Grace period is set to 24h!**</mark>

</details>

<details>

<summary>MANAGE ROLES</summary>



</details>

***

## <mark style="color:orange;">`DAOService Commands Explained`</mark>

### <mark style="color:green;">`User Commands`</mark>

<details>

<summary><mark style="color:blue;">/</mark>bindweb3</summary>

User command to bind Discord Account with Web3 wallet(s).

#### User Command

```typescript
/bindweb3
```

#### Output

<img src="../../.gitbook/assets/Bildschirmfoto 2023-12-02 um 00.35.43.png" alt="" data-size="original">

</details>

<details>

<summary><mark style="color:blue;">/</mark>bindtwitter</summary>

User command to bind Twitter Account with Web3 wallet(s).

#### User Command

```typescript
/bindtwitter
```

#### Output

<img src="../../.gitbook/assets/Bildschirmfoto 2023-12-02 um 00.36.51.png" alt="" data-size="original">

</details>

<details>

<summary><mark style="color:blue;">/</mark>bounded</summary>

List bounded Web3 wallet(s) and Twitter Account to your Discord Account.&#x20;

#### User Command

```typescript
/bounded
```

#### Output

<img src="../../.gitbook/assets/Bildschirmfoto 2023-11-30 um 23.29.09.png" alt="" data-size="original">\
<mark style="background-color:orange;">To preserve privacy, command output is only Visible to user that called it.</mark>&#x20;

</details>

<details>

<summary><mark style="color:blue;">/</mark>listpolls</summary>

#### To make it easy for users to keep track of Active Polls, users can run this command at any time without limitations. Wen called, it will List all Active Polls and link to each Poll.

#### User Command

```typescript
/listpolls
```

![](<../../.gitbook/assets/image (81).png>)

#### Output

![](<../../.gitbook/assets/image (82).png>)

<mark style="background-color:orange;">For non Discord users, all Active and Finished Polls are visible at:</mark> [https://phunk.cc/polls/](https://phunk.cc/polls/)

</details>

### <mark style="color:red;">`Admin Commands`</mark>

<details>

<summary><mark style="color:blue;">/</mark>createpoll</summary>

This commands is reserved for Discord Admins only, executing this command with parameters set kicks off new Poll where community can vote on Active proposals and as a result achieve consensus.

* Voting itself is anonymous and final results get auto revealed only after set time expires.&#x20;
* Only Admins are [permitted](governance.md#pollresults) to see casted Votes and Voters for auditing purposes.
* If optional <mark style="color:blue;">\<role></mark> is set, only users with set Discord role can cast a Vote.
* With set parameters under src/config.ts Sybil attacks are mitigated, read more [here](governance.md#sybil-attack-handling).

#### Admin Command

```typescript
/createpoll <description> <duration> <role> <emoji> <link> <minimumvotes> 
```

![](<../../.gitbook/assets/Bildschirmfoto 2023-12-03 um 10.15.49 (1).png>)

#### Output

![](<../../.gitbook/assets/Bildschirmfoto 2023-12-03 um 10.15.21 (1).png>)

</details>

<details>

<summary><mark style="color:blue;">/</mark>pollresults</summary>

This commands is reserved for Discord Admins only. It will display SnapShot of Vote result and will list all the Voters for Current and Past Polls.

#### Admin Command

```typescript
/pollresults <poll id>
```

![](<../../.gitbook/assets/image (76).png>)

#### How to get Poll ID?

![](<../../.gitbook/assets/image (78).png>)

To see this option, on your Discord settings, you will need to have Developer mode turned ON.

<img src="../../.gitbook/assets/Bildschirmfoto 2023-12-02 um 00.11.25.png" alt="" data-size="original">

#### Output

![](<../../.gitbook/assets/image (77).png>)

<mark style="background-color:orange;">This is Visible to Admins only and it is on their own discretion if they will share this information with the Community.</mark>&#x20;

</details>

<details>

<summary><mark style="color:blue;">/</mark>closepoll</summary>

This commands is reserved for Discord Admins only. It will Force Close currently Active Poll.\
If used, PhunkBot will Print this interaction and it will be visible to users.&#x20;

#### Admin Command

```typescript
/closepoll <poll id>
```

![](<../../.gitbook/assets/image (79).png>)

#### Output

<img src="../../.gitbook/assets/Bildschirmfoto 2023-12-02 um 00.28.30.png" alt="" data-size="original">

</details>

<details>

<summary><mark style="color:blue;">/</mark>deletepoll</summary>

This commands is reserved for Discord Admins only. It will Force Delete currently Active Poll.\
If used, PhunkBot will Print this interaction and it will be visible to users.&#x20;

#### Admin Command

```typescript
/deletepoll <poll id>
```

![](<../../.gitbook/assets/image (80).png>)

#### Output

<img src="../../.gitbook/assets/Bildschirmfoto 2023-12-02 um 00.28.59.png" alt="" data-size="original">

</details>

***

## <mark style="color:orange;">`Encryption`</mark>

<details>

<summary>USER DATA</summary>

To protect user data in case of data breach, data is Encrypted using community owned Symetric key that is obtained from the discord server and [Explained here](https://discord.com/channels/873564453227094078/1148354544938528830/1162887458309029890).

#### Wen enabled, this is how Encrypted user data looks like on Host Server.

![](<../../.gitbook/assets/image (2) (1).png>)

#### Encryption is Optional, it can be Enabled by changing Boolean from `false` to `true`

{% code title="config.ts" %}
```typescript
  dao_requires_encryption_key: false,
```
{% endcode %}

#### Code Sample

{% code title="dao.extention.service.ts" %}
```typescript
if (config.dao_requires_encryption_key) {
  const guildsId = unique(config.dao_roles.map(r => r.guildId))
  for (const guildId of guildsId) {
    console.log(`fetching encryption key for ${guildId}`)
    
    const guild = this.discordClient.getClient().guilds.cache.get(guildId)
    const channels = await guild.channels.fetch()

    const channel = channels.find(channel => channel.name === 'setup-daoextension') as TextBasedChannel
    const lastMessage = await channel.messages.fetch(channel.lastMessageId)
    this.encryptionKeys.set(guildId, lastMessage.content)
    console.log(`fetched encryption key for ${guildId}`)
  }
}
```
{% endcode %}

<mark style="background-color:red;">Data saved is: Discord ID, Wallet(s) public Key(s).</mark>

</details>

<details>

<summary>DEPLOYMENT</summary>

Data is Encrypted using community owned Symetric key that is obtained from the discord server, but how does that work?

Ideally one of Discord Admins creates Private channel called `#setup-daoextension` \
on Discord containing a 32 bytes encryption key for example using this [generator](https://seanwasere.com/generate-random-hex/).

&#x20;![](<../../.gitbook/assets/Bildschirmfoto 2023-12-16 um 10.08.45.png>)

and places Encryption key as only message into this Private channel. PhunkBot needs to have access to channel to Decrypt data in PhunkBot memory using this key.

After seed (encryption key) is in place, bot host enables encryption by changing Boolean from `false` to `true` under config.ts.

{% code title="config.ts" %}
```typescript
 dao_requires_encryption_key: true,
```
{% endcode %}

<mark style="background-color:red;">Warning: enabling Encryption will wipe database containing user data collected before.</mark>



</details>
