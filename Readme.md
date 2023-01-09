### Deploy OWN `Factory` and `Router`

- Access: https://remix.ethereum.org/#optimize=false&runs=200&evmVersion=null&version=soljson-v0.5.16+commit.9c3226ce.js

#### Deploy WBNB

+ New File: `WBNB.sol` => Copy source from https://github.com/ngocbd/pancanswap/blob/master/WBNB.sol
+ Compiler tab => Select compiler: `v0.8.3+commit.8d00100c`
+ Deploy tab => Select `WBNB` -> Deploy

#### Deploy RancakeFactory

+ New File: `RancakeFactory.sol` => Copy source from `/RancakeFactory.sol`
+ Name changed: Find `Rancake` And `Ran-LP` Replace by yours.
+ Compiler tab => Select compiler: `v0.5.16+commit.9c3226ce`
+ Deploy tab => Select `RancakeFactory` -> Fill your address as `feeToSetter` in constructor -> Deploy

#### Deploy RancakeRouter01

+ New File: `RancakeRouter01.sol` => Copy source from `/RancakeRouter01.sol`
+ Name changed: Find `Rancake` And `Ran-LP` Replace by yours.

+ Expand `RancakeFactory` deployed above -> Read `INIT_CODE_PAIR_HASH` -> Copy this hash without prefix `0x`. Ex: `bf80e745c6b3562b80b9c6f5819ba91c44b56ca9eee331bda76f32827f1ea403`
+ Edit `RancakeRouter01`: Find `RancakeLibrary` -> `pairFor` function => Replace new hex by `INIT_CODE_PAIR_HASH` above. Ex: `hex'bf80e745c6b3562b80b9c6f5819ba91c44b56ca9eee331bda76f32827f1ea403'` -> `hex'bf80e745c6b3562b80b9c6f5819ba91c44b56ca9eee331bda76f32827f1ea403'`
+ Compiler tab => Select compiler: `v0.6.6+commit.6c089d02`
+ Deploy tab => Select `RancakeRouter01` -> Fill `RancakeFactory` address and `WBNB` address as constructor params -> Deploy

#### Deploy RancakeRouter (Main Router)
+ New File: `RancakeRouter.sol` => Copy source from `/RancakeRouter.sol`
+ Name changed: Find `Rancake` And `Ran-LP` Replace by yours.
+ Expand `RancakeFactory` deployed above -> Read `INIT_CODE_PAIR_HASH` -> Copy this hash without prefix `0x`. Ex: `bf80e745c6b3562b80b9c6f5819ba91c44b56ca9eee331bda76f32827f1ea403`
+ Edit `RancakeRouter`: Find `RancakeLibrary` -> `pairFor` function => Replace new hex by `INIT_CODE_PAIR_HASH` above. Ex: `hex'bf80e745c6b3562b80b9c6f5819ba91c44b56ca9eee331bda76f32827f1ea403'` -> `hex'bf80e745c6b3562b80b9c6f5819ba91c44b56ca9eee331bda76f32827f1ea403'`
+ Compiler tab => Select compiler: `v0.6.6+commit.6c089d02`; Check on `Enable optimization: 200` to avoid `Contract code size limit` issue
+ Deploy tab => Select `RancakeRouter` -> Fill `RancakeFactory` address and `WBNB` address as constructor params -> Deploy