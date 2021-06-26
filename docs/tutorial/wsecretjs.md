# wSecretJS

Now that have a wallet connected, and you see how easy that is to get setup, the next step is to start interacting with the blockchain directly. For that we will need a SecretJS client.

SecretJS, itself a wrapper of cosmjs, is a really powerful library. It handles all sorts of tricky stuff like connecting to a wallet, signing transactions, and importantly for Secret Network, client-side encryption. But this power and complexity comes with a trade-off, it is quite difficult to use, at least at first. In addition SecretJS is mainly focused on interacting with contracts, not with core Secret Network modules like staking or governance. Meaning anything you want to do on that front gets done seperately. Wouldn't it be great if their was a way to bundle all that, every interaction you will have with the blockchain in an app, into one clean, easy to use wrapper? We thought so too, so we have added wSecretJS to the stack.

Well, lets use it shall we.

The first thing we are going to need is to import two fuctions from Core Griptape: `createScrtCLient` and  `useWallet`. This may seem a little strange, didn't we already import `useWalletStore` in the last section? What is `useWallet` and why do we need it? Remember how Griptape.js comes in two levels. There is Core Griptape, which we used so directly only to get the `coinConvert` utility, and there's griptape-vue, which we have seen a little more. Well Griptape-vue is in charge of, among other things, managing state, which it uses Pinia to do. So what we actually imported, with `useWalletStore`, was a Pinia store that lives in the griptape-vue layer. Underneath that, is `usewallet` itself (Which useWalletStore uses), and that lives in core griptape. `useWallet` will be used to get a core griptape wallet object. This object is not a store, its the connective tissue needed to interact with, in this case, Keplr. I hope that wasn't too confusing, lets just move forward for now an hopefully everything starts making sense.

**/src/App.vue**
```html
...

<script>
  import { coinConvert, createScrtClient, useWallet } from '@stakeordie/griptape.js'
  export default {

  }
</script>

...
```