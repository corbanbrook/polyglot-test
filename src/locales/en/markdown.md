---
sidebar_label: Checkout
---

# Overview
The checkout modal enables developers to easily facilitate cryptocurrency payments. Test 123

<div class="text--center">
  <img src="/img/kit/checkout-modal.png" />
</div>

# Integration
To integrate the checkout feature, follow these steps:
1. Install the `kit-checkout` module:

```bash
npm install @0xsequence/kit-checkout
# or
pnpm install @0xsequence/kit-checkout
# or
yarn add @0xsequence/kit-checkout
```

2. Place the KitCheckoutProvider below the Sequence Kit Core provider in your app:

```jsx
import { KitCheckoutProvider } from '@0xsequence/kit-checkout'


const App = () => {
  return (
    <WagmiConfig config={config}>
      <QueryClientProvider client={queryClient}> 
        <KitProvider>
          <KitCheckoutProvider>
            <Page />
          </KitCheckoutProvider>
        </KitProvider>
      </QueryClientProvider>
    </WagmiConfig>
  )
}
```
## Opening the Checkout modal
Use the `useCheckoutModal` hook to open the checkout modal and pass a settings object:


```jsx
  import { useCheckoutModal } from '@0xsequence/kit-checkout'


  const MyComponent = () => {
    const { triggerCheckout } = useCheckoutModal()
  
    const onClick = () => {
      const checkoutSettings = {...}
      triggerCheckout(checkoutSettings)
    }

    return (
      <button onClick={onClick}>checkout</button>
    )
  }
```


## Configuring the Checkout modal
Configure the checkout modal using the `checkoutSettings` object:


```jsx
const checkoutSettings = {
  cryptoCheckout: {...},
  orderSummaryItems: {...}
}
```

### Crypto Checkout Configuration (`cryptoCheckout`)
The `cryptoCheckout` field specifies settings for checking out with cryptocurrency, e.g., interacting with a minting contract or marketplace contract.

Example configuration:

```jsx
cons checkoutConfig = {
  // ...
  cryptoCheckout: {
    chainId: 137,
    triggerTransaction: async () => { console.log('triggered transaction') },
    coinQuantity: {
      contractAddress: '0x2791Bca1f2de4661ED88A30C99A7a9449Aa84174',
      amountRequiredRaw: '10000000000'
    },
  },
}
```

### Order Summary Configuration (`orderSummaryItems`)
The `orderSummaryItems` field specifies the list of collectibles shown in the order summary.

Example configuration:

```jsx
    orderSummaryItems: [
      {
        contractAddress: '0x631998e91476da5b870d741192fc5cbc55f5a52e',
        tokenId: '66597',
        quantityRaw: '100'
      },
    ]
```