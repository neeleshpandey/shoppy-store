## Shoppy Store
### An online Ecommerce store
![Medusa Hackathon 2022](https://user-images.githubusercontent.com/87470414/197345784-b166d85e-d65f-4c73-b56d-1dfc31008dff.jpg)

# About

### Participants
`Neelesh Pandey` - [@neeleshpandey](https://github.com/neeleshpandey/)

`Krish Rathod` - [@KrishRathod](https://github.com/KrishRathod/)

`Ashutosh Singh`- [@Ashutosh5786](https://github.com/Ashutosh5786/)

`Ritesh Singh` - [@rootritesh](https://github.com/rootritesh/)

`Anurag Singh` - [@Anu2arc](https://github.com/Anu2arc/)

### Description


A Single place E-commerce Store where you can list multiple products to be purchased by customers
This Project is built using Medusa, Next.js and Typescript. It includes products screen, cart, checkout and payment.




### Preview

![Project Preview](https://user-images.githubusercontent.com/87470414/197344880-8366e6c8-0a28-44eb-90c4-30a1bf9322aa.png)

## Set up Project

### Prerequisites
Before you start with the tutorial make sure you have

- [Node.js](https://nodejs.org/en/) v14 or greater installed on your machine
- [Expo CLI](https://expo.dev/) 
- [Medusa server](https://docs.medusajs.com/quickstart/quick-start/) v14 or greater installed on your machine
- Stripe account

### Install Project

- Clone the repository:

```bash
git clone git@github.com:neeleshpandey/shoppy-store.git
```
- Navigate into your projects directory and get your enviroment variables ready:

```shell
cd nextjs-starter-medusa/
mv .env.template .env.local
```

### Install required dependencies

Use Yarn to install all dependencies.

```shell
yarn
```

### Start the Project

You are now ready to host your project

```shell
yarn dev
```

# Payment integrations

By default the this starter supports the following payment integrations

- [Stripe](https://stripe.com/)

- [Paypal](https://www.paypal.com/)

To enable the integrations you need to add the following to your `.env.local` file:

```shell

MEDUSA_PAYMENT_STRIPE_PUBLIC_KEY=<your-stripe-public-key>

MEDUSA_PUBLIC_PAYPAL_CLIENT_ID=<your-paypal-client-id>

```

You will also need to setup the integrations in your Medusa server. See the [Medusa documentation](https://docs.medusajs.com) for more information on how to configure [Stripe](https://docs.medusajs.com/add-plugins/stripe) and [PayPal](https://docs.medusajs.com/add-plugins/paypal) in your Medusa project.

# Search integration

This starter is configured to support using the `medusa-search-meilisearch` plugin out of the box. To enable search you will need to enable the feature flag in `./store-config.json`, which you do by changing the config to this:

```json

{

  "features": {

    "search": true

  }

}

```

Before you can search you will need to install the plugin in your Medusa server, for a written guide on how to do this – [see our documentation](https://docs.medusajs.com/add-plugins/meilisearch).

The search components in this starter are developed with Algolia's `react-instant-search-hooks-web` library which should make it possible for you to seemlesly change your search provider to Algoli instead of MeiliSearch.

To do this you will need to add `algoliasearch` to the project, by running

```shell

yarn add algoliasearch

```

After this you will need to switch the current MeiliSearch `SearchClient` out with a Alogolia client. To do this update `@lib/search-client`.

```ts

import algoliasearch from "algoliasearch/lite"

const appId = process.env.NEXT_PUBLIC_SEARCH_APP_ID | "" // You should add this to your environment variables

const apiKey = process.env.NEXT_PUBLIC_SEARCH_API_KEY || "test_key"

const searchClient = algoliasearch(appId, apiKey)

export const SEARCH_INDEX_NAME =

  process.env.NEXT_PUBLIC_INDEX_NAME || "products"

```

After this you will need to set up Algolia with your Medusa server, and then you should be good to go. For a more thorough walkthrough of using Algolia with Medusa – [see our documentation](https://docs.medusajs.com/add-plugins/algolia), and the [doucmentation for using `react-instantsearch-hooks-web`](https://www.algolia.com/doc/guides/building-search-ui/getting-started/react-hooks/).

## Resources
- [Next js Documentation](https://nextjs.org/docs)
- [Medusa Documentation](https://docs.medusajs.com/)
