# Privy + Solana `create-next-solana-app` Starter using Mobile Wallet Adapter (MWA)

This is a template for integrating Privy's Solana capabilities into a Next.js application. It provides a simple setup for wallet login, embedded wallets, and transaction signing using the [Privy React SDK](https://docs.privy.io/basics/react/installation).

This demo uses NextJS's [App Router](https://nextjs.org/docs/app).

## Mobile Wallet Adapter

In `components/providers.tsx`, the Mobile Wallet Adapter standard wallet is registered calling `registerMwa`.

With:

```tsx
// In providers.tsx

import { 
    createDefaultAuthorizationCache, 
    createDefaultChainSelector, 
    createDefaultWalletNotFoundHandler,
    registerMwa, 
} from '@solana-mobile/wallet-standard-mobile';

registerMwa({
    appIdentity: {
      name: 'My Example',
      uri: 'https://solanamobile.com',
      icon: 'favicon.ico', // resolves to https://solanamobile.com/favicon.ico
    },    
    authorizationCache: createDefaultAuthorizationCache(),
    chains: ['solana:devnet', 'solana:mainnet'],
    chainSelector: createDefaultChainSelector(),
    onWalletNotFound: createDefaultWalletNotFoundHandler(),
})
```

## Setup

1. Clone this repository and open it in your terminal.

```bash
git clone https://github.com/privy-io/create-next-solana-app.git && cd create-next-solana-app
```

2. Install the dependencies.

```bash
npm install
```

3. Define the environment variables in a `.env.local` file.

```bash
cp .env.local.example .env.local
```

## Building locally

In your project directory, run npm run dev. You can now visit [http://localhost:3000](http://localhost:3000) to see your app and login with Privy!

## Check out

- `components/providers.tsx` for how to use the `PrivyProvider` and initialize it with your Privy App ID.
- `app/page.tsx` for how to verify if a user is logged in from a server component.
- `components/loginButton.tsx` for how to use the `useLogin` Privy hook to log in a user and create an embedded wallet.
- `app/dashboard/page.tsx` for how to use the `usePrivy` hook to access the Privy SDK in a client component, and how to use the embedded and EOA wallets to sign a message and send a transaction.
