# Workaround for etherjs

## Issue: `Error: failed to meet quorum`
You might have came across this issue once in a while using ethersjs. This usually happens when you use multiple provider to initialise the provder.

## Solution 1
When you initialise the provider, set `quorum` to `1`.
``` JS
const provider = await ethers.getDefaultProvider(network, {
        etherscan: <ETHERSCAN_API_KEY>,
        infura:  {projectId: <INFURA_PROJECT_ID>, projectSecret: <INFURA_PROJECT_SECRET> },
        alchemy: <ALCHEMY_API>,
        quorum:1
      });
```

## Solution 2 
Initialising with one provider. Though, if the node goes down due to some reason, your application may not work properly.
```JS
const provider = await ethers.getDefaultProvider(network, {
        infura:  {projectId: <INFURA_PROJECT_ID>, projectSecret: <INFURA_PROJECT_SECRET> },
      });
```
