<template>
    <UHorizontalNavigation :links="links" class="border-b border-gray-200 dark:border-gray-800" />



    <slot />

</template>


<script setup >

import { createWeb3Modal, defaultConfig } from '@web3modal/ethers/vue'



// 1. Get projectId at https://cloud.walletconnect.com
const projectId = 'db617acd5482191b1d13b2875679e1e1'

// 2. Set chains
const mainnet = {
    chainId: 1,
    name: 'Ethereum',
    currency: 'ETH',
    explorerUrl: 'https://etherscan.io',
    rpcUrl: 'https://cloudflare-eth.com'
}

// 3. Create your application's metadata object
const metadata = {
    name: 'My Website',
    description: 'My Website description',
    url: 'https://mywebsite.com', // url must match your domain & subdomain
    icons: ['https://avatars.mywebsite.com/']
}

// 4. Create Ethers config
const ethersConfig = defaultConfig({
    /*Required*/
    metadata,
    auth: {
        socials: ['google', 'x', 'github'],
    },
    /*Optional*/
    enableEIP6963: true, // true by default
    enableInjected: true, // true by default
    enableCoinbase: true, // true by default
    rpcUrl: '...', // used for the Coinbase SDK
    defaultChainId: 1 // used for the Coinbase SDK
})

// 5. Create a Web3Modal instance
const modal = createWeb3Modal({
    ethersConfig,
    chains: [mainnet],
    projectId,
    enableAnalytics: true, // Optional - defaults to your Cloud configuration
    enableOnramp: true // Optional - false as default
})

//const modal = useWeb3Modal()


const links = [
    [{
        label: 'Home',
        icon: 'i-heroicons-home',
        to: '/'
    }, {
        label: '<w3m-button />',
        icon: 'i-heroicons-games',
    }], [{
        label: `${true ? 'Account' : 'Connect'}`,
        icon: `${true ? 'i-heroicons-wallet' : 'i-heroicons-user'}`,
        
    }]
]
</script>