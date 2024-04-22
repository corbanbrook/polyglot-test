# Quickstart

You can quickly try out a Sequence Embedded Wallet integration before doing a complete configuration specific to your application. There are several ways to test out the features:

- Try out [Sequence WaaS demo](https://waas-demo.sequence.xyz/), showcasing a sample authentication and transaction flow leveraging Sequence Kit for web applications
- Play with [Aviator](https://0xsequence.github.io/waas-airplane-demo/), a complete WebGL game built using the Embedded Wallet, leveraging [Sequence Marketplace API](/solutions/marketplaces/orderbook/overview) as well as [serverless Cloudflare Worker](/guides/mint-collectibles-serverless) for minting
- Browse [Jelly Forest source code](https://github.com/0xsequence-demos/jelly-forest), our Unity WaaS SDK demo implementation that natively runs on iOS and Android

You can also do a quick integration of Embedded Wallet into your own application by using the following test configuration keys:

- Project Access Key: `AQAAAAAAAEGvyZiWA9FMslYeG_yayXaHnSI`
- WaaS Configuration Key: `eyJwcm9qZWN0SWQiOjE2ODE1LCJycGNTZXJ2ZXIiOiJodHRwczovL3dhYXMuc2VxdWVuY2UuYXBwIn0=`

These will leverage Sequence's own Google and Apple test authentication configurations and are whitelisted for `localhost` usage only. They cannot be used in a production setup.

To see how to integrate these keys into a sample demo application, you can browse the [Demo WaaS repository](https://github.com/0xsequence/demo-waas-auth).

You can also view SDK-specific guides here:

- [TypeScript SDK](/solutions/wallets/embedded-wallet/quickstart)
- [Unity SDK](/sdk/unity/overview)
- [Unreal SDK](/sdk/unreal/overview)

When you are ready to configure your own Embedded Wallet, you can [follow the Builder guide here](/solutions/builder/embedded-wallet).

## Getting Started with TypeScript SDK

::::steps

### SDK Installation
You can install the TypeScript SDK with:

```bash
pnpm install @0xsequence/waas
```

### Project Setup
You can test out the library with the Project Access Key and WaaS Configuration Key provided above. Once you are ready to configure your own Embedded Wallet, follow [the Builder guide here](/solutions/builder/embedded-wallet).

### Library Setup
To start using Sequence Embedded Wallet SDK, you'll need to create a new instance of the `waas` class:

```typescript
import { SequenceWaaS } from '@0xsequence/waas'

const waas = new SequenceWaaS({
  projectAccessKey: `${process.env.PROJECT_ACCESS_KEY}`,
  waasConfigKey: `${process.env.WAAS_CONFIG_KEY}`,
  network: 'arbitrum-nova'
})
```
::::

Note that the library is operational, but it can't be used to interact with any wallet until you have authenticated **as a user**.