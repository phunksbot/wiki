---
description: IN FEW EASY STEPS YOU WILL BE ABLE TO DEPLOY VERY POWERFUL BOT
cover: ../../.gitbook/assets/Bildschirmfoto 2023-11-28 um 21.58.22 (1).png
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

# ➖ TUTORIALS

## <mark style="color:orange;">`Getting started`</mark>

<details>

<summary>THINGS YOU WILL NEED</summary>

* Linux Server ([ubuntu 20.04](https://www.vultr.com/products/cloud-compute/)).
* Twitter [v2 API access](https://developer.twitter.com/en/docs/twitter-api/getting-started/about-twitter-api).
* Alchemy [API Key](https://auth.alchemy.com/signup).
* [Node.js](https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-20-04) v18.x
* Discord [APP token](https://discord.com/developers).
* Discord Server **Admin** access.
* Some Basic coding/editing knowledge.

</details>

***

## <mark style="color:orange;">`Prerequisite`</mark>

<details>

<summary>ACCOUNTS AND ACCESS TOKENS</summary>

#### TWITTER

* To get your twitter API keys, follow this [tutorial](https://developer.talkwalker.com/guides/rehydrating-tweet/getting-started).
* Now you need Access keys with **read and write** permission, follow this [tutorial](https://docs.tibco.com/pub/activematrix\_businessworks\_plugin\_for\_twitter/6.1.0/doc/html/GUID-3FAC9352-94BE-4D21-9DAC-7AE79E24BECA.html).
* Save both, your API and Access keys for [deployment](tutorials.md#deployment).

DISCORD

* To get Discord bot token, follow this [tutorial](https://www.writebots.com/discord-bot-token/).
* Save your Discord token for [deployment](tutorials.md#deployment).
* Now you will need to generate link with proper permissions to invite your Discord bot to your Server. In your [developer portal](https://discord.com/developers) under `0Auth2/URL Generator` check this boxes:

<img src="../../.gitbook/assets/image (73).png" alt="" data-size="original">

This will generate URL that you can use to invite Bot to your Discord server with proper permissions for it to post sales and other [Application Commands](tutorials.md#stats-commands).

Discord bot should now be ready to post sales, if you get stuck dm me on twitter @iape\_

</details>

***

## <mark style="color:orange;">`Deployment`</mark>

<details>

<summary>INSTALLATION</summary>

On your ubuntu server first clone PhunkBot repository

```bash
git clone https://github.com/Crypto-Phunks/nft-sales-twitter-bot.git
```

Go to Bots directory

```bash
cd nft-sales-twitter-bot
```

#### Run installation

```bash
npm install
```

#### Create `.env` file

```bash
nano .env
```

Add content from `example.env` and enter your [API](tutorials.md#prerequisite) credentials

{% code title=".env" overflow="wrap" %}
```bash
TWITTER_ACCESS_TOKEN_KEY=""
TWITTER_ACCESS_TOKEN_SECRET=""
TWITTER_API_KEY=""
TWITTER_API_KEY_SECRET=""

ALCHEMY_API_KEY=""
DISCORD_TOKEN=""

GETH_NODE_ENDPOINT=""
GETH_NODE_ENDPOINT_HTTP=""
```
{% endcode %}

\---

#### Edit the `src/config.ts` file

```bash
nano src/config.ts
```

Add your Smart Contract and Discord IDs

{% code title="config.ts" %}
```typescript
  // Contract Address ======================================== //
  contract_address: 'your-NFT-smart-contract',
  nftx_vault_contract_address: '',
  // Enter the block where your contract has been created
  statistic_initial_block: 13035326,
  //
  discord_channels: 'your-discord-channel-ID-where-bot-posts-sales',
  discord_client_id: 'your-discord-APP-ID',
  discord_guild_ids: 'your-discord-Server-ID',
```
{% endcode %}

Customise the Tweet and Discord Stats parameters

{% code title="config.ts" %}
```typescript
  ownedTokensMessageDiscord: '<wallet> owns <count> Phunks!\n———\n',
  graphStatisticsMessageDiscord: 'Here is the graph you requested for [<wallet>]!\n———\n',
  userStatisticsMessageDiscord: 'Stats for <wallet>!\n———\n\n⏳ Flipped to Phunk for the first time [<holder_since>] days ago.\n💰 Flipped Phunks [<tx_count>] times with a total volume of [Ξ<volume>]\n💎 Is currently holding [<owned_tokens>] Phunks.',
  globalStatisticsMessageDiscord: 'Here are volume stats for [<window>]! 💰\n\n<per_platform_stats>\n\nlast tx fetched [<last_event>]',
  saleMessageDiscord: '[Phunk #<tokenId>](<tweetLink>) was flipped for [<ethPrice> (<fiatPrice>)](<https://etherscan.io/tx/<txHash>>)\nfrom: [<from>](<https://notlarvalabs.com/cryptophunks/phunkbox?address=<initialFrom>>)\nto: [<to>](<https://notlarvalabs.com/cryptophunks/phunkbox?address=<initialTo>>)',
  saleMessage: 'Phunk #<tokenId> was flipped for <ethPrice> (<fiatPrice>) by <to>\n| https://notlarvalabs.com/cryptophunks/details/<tokenId>\n',
  bidMessageDiscord: '[Phunk #<tokenId>](<tweetLink>) has a bid for [<ethPrice> (<fiatPrice>)](https://notlarvalabs.com/cryptophunks/details/<tokenId>)\nfrom: [<from>](<https://notlarvalabs.com/cryptophunks/phunkbox?address=<initialFrom>>)',
  bidMessage: 'Phunk #<tokenId> has a bid for <ethPrice> (<fiatPrice>) from <from>\n| https://notlarvalabs.com/cryptophunks/details/<tokenId>\n',
  flywheelMessageDiscord: '[Phunk #<tokenId>](<tweetLink>) was flipped to FlyWheel for [<ethPrice> (<fiatPrice>)](<https://etherscan.io/tx/<txHash>>)\nby: [<to>](<https://notlarvalabs.com/cryptophunks/phunkbox?address=<initialTo>>)',
  flywheelMessage: 'Phunk #<tokenId> was flipped to FlyWheel for <ethPrice> (<fiatPrice>) by <to>\n| https://notlarvalabs.com/cryptophunks/details/<tokenId>\n| https://phunks.pro',
  auctionMessageDiscord: '[Phunk #<tokenId>](<tweetLink>) was Auctioned for [<ethPrice> (<fiatPrice>)](<additionalText>)\nto: [<to>](<https://notlarvalabs.com/cryptophunks/phunkbox?address=<initialTo>>)',
  auctionMessage: 'Phunk #<tokenId> was Auctioned for <ethPrice> (<fiatPrice>) to <to>\n| https://notlarvalabs.com/cryptophunks/details/<tokenId>\n| <additionalText>',
  loanMessage: 'Phunk #<tokenId> was flipped for <ethPrice> (<fiatPrice>) by <to>\n| https://notlarvalabs.com/cryptophunks/details/<tokenId>\n',
```
{% endcode %}

(Optional) Use Local images and Local metadata

{% code title="config.ts" %}
```typescript
  use_local_images: true,
  local_image_path: './token_images/phunk',
  use_forced_remote_image_path: false,
  forced_remote_image_path: '',
  enable_flashbot_detection: false,
  // 
  // this is a configuration for the phunk bid demo extension
  local_bids_image_path: './bids_images/Phunk_',
  discord_owned_tokens_image_path: '',
  discord_footer_text: 'FLIP!',
  // this is a configuration for the phunk auction house demo extension
  local_auction_image_path: './token_images/phunk',
  token_metadata_cache_path: './token_metadatas_cache',
```
{% endcode %}

The `local_image_path` will be suffixed with the token number, ie, here, it will seek for an image named `./token_images/tokens0034.png` if the token #34 is sold.

\---

(Optional) Edit `src/app.module.ts`file and activate/deactivate services (providers) //&#x20;

<pre class="language-typescript" data-title="app.module.ts"><code class="lang-typescript">@Module({
  imports: [
    HttpModule,
    ServeStaticModule.forRoot({
      rootPath: join(__dirname, '..', 'client'),
    })],
    providers: [
      Erc721SalesService,
      <a data-footnote-ref href="#user-content-fn-1">// DAOService, -> This is DAO Service </a>
      <a data-footnote-ref href="#user-content-fn-2">// StatisticsService, -> This is Statistics Service</a>
      ////
      // Below is a simple example of how to create and plug a custom 
      // extension to the bot
      ////
      //
      PhunksBidService,
      PhunksAuctionHouseService,
      PhunksAuctionFlywheelService, 
      StatisticsService
    ],
    controllers: [
      DAOController
    ],
})

export class AppModule {

}
</code></pre>

\---

#### Build and Deploy

```bash
npm run build
```

Installation should be ready now, proceed to [next step](tutorials.md#running-bot).

</details>

***

## <mark style="color:orange;">`Running Bot`</mark>

<details>

<summary>START</summary>

#### From experience i recommend you run screen instance for your Bot, in installation directory start a new screen Session

```bash
screen -S yourbotsname
```

#### Now you can finally Start a bot

#### development

```bash
npm run start
```

#### watch mode

```bash
npm run start:dev
```

#### production mode

```bash
npm run start:prod
```

#### with watchdog (<mark style="color:green;">recommended</mark>)

```bash
npm run start:prod-with-watchdog
```

#### Detach from screen Session

```bash
ctrl a + d
```

#### Enter the screen Session back

```bash
screen -r yourbotsname
```

</details>

***

## <mark style="color:orange;">`Stats Commands`</mark>

<details>

<summary>FOR DISCORD</summary>

#### If you have [Statistics module](features.md) in src/app.module.ts enabled your Discord bot will gain some super powers. Here is the list of available commands:

#### Display a list of the owned tokens by a wallet

```typescript
/owned <wallet>
```

#### Display some interesting stats by wallet

```typescript
/userstats <wallet>
```

#### Display collection volume across all markets for given time frame

```typescript
/volume <time frame> 
```

#### Display a graph showing the average price and the volume of Collection over time

```typescript
/graph
```

#### Display the top 20 traders of your Collection for given time frame

```typescript
/traders <time frame>
```

#### Displays indexed informations about a given transaction, useful for debugging purpose

```typescript
/transaction <tx>
```

#### Force indexation by the statistic module of the given transaction within the given block

```typescript
/index <block> <tx>
```

</details>

***

## <mark style="color:orange;">`CLI Commands`</mark>

<details>

<summary>FOR SERVER ONLY</summary>

WIP

</details>

***

## <mark style="color:orange;">`DAO Commands`</mark>

<details>

<summary>FOR DISCORD</summary>

WIP

</details>

[^1]: Check [Features](features.md) to understand this module.

[^2]: [Check Features to understand this module.](features.md)
