---
slug: /
sidebar_position: 1
---

# Getting started

### Spacetime is a decentralized database that lets developers build decentralized apps with trustless automation at 1000x lower cost than on-chain storage.

:::info
Spacetime is better than a web2 DB like Firebase 🔥 or Postgres 🐘 because you can encrypt data using wallets 💳 for "user owned data" and verifiably query Spacetime from smart contracts 📜 (coming soon).

Spacetime is also better than storing data on-chain ⛓ because it's 1000 to a million times cheaper than on-chain storage. For example, storing 1mb on Ethereum costs around $64,000 💸. 
:::

Blockchains are not built for scalable structured data storage so we built Spacetime to combine the best attributes of web2 databases and blockchains 🤗.

## Install Spacetime JS client

```bash
npm install @spacetimexyz/client
```
```bash
yarn add @spacetimexyz/client
```

## Initialize the library

```ts
import { Spacetime } from '@spacetimexyz/client'

const db = new Spacetime()
```

## Create a collection

You can create a collection using the library.

:::info
Creating a collection via the [Spacetime Explorer](https://explorer.testnet.spacetime.xyz) is coming soon.
:::

```ts
const metadata: CollectionMeta = {
    id: 'your-namespace/cities',
    schema: {
        type: 'object',
        properties: {
            name: {
                type: 'string'
            },
            country: {
                type: 'string'
            }
        }
    },
    indexes: [{
      fields: [{ field: 'name' }],
    }],
}

const response = await db.createCollection(metadata)
```

:::note
`id`s must be globally unique across all Spacetime collections. We suggest using a namespace (we use `test` here) for your organization.
:::

For more details on creating collections, see the [collection](/collections) overview.

## Write data to a collection

```ts
await db.collection('your-namespace/cities').doc('new-york').set({ 
  name: 'New York',
  country: 'USA'
})
```

:::note
Now go view the collection in the [Explorer](https://explorer.testnet.spacetime.xyz).
:::

## Read a document

```ts
const data = await db.collection('your-namespace/cities').doc('new-york').get()
```

## Next steps

* Read the [Spacetime whitepaper](https://bit.ly/spctmwp)
* [Understand collections](/read)
* [Known issues](/known-issues)