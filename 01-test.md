### Check wallet balance

```shell
cast balance 0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266
cast balance 0x8858eBF9a19bAf281624E571ef8309696D991Fde --rpc-url=$SEPOLIA_RPC_URL
```

### Install chainlink/contracts

```shell
forge install smartcontractkit/chainlink-brownie-contracts@0.6.1 --no-commit
```

### Install foundry-devops

```shell
forge install https://github.com/Cyfrin/foundry-devops --no-commit
```

### Run test suite

```shell
forge test
forge test -vv
forge test --mt test_PriceFeedVersionIsCorrect -vvv
forge test --mt test_PriceFeedVersionIsCorrect --fork-url $RPC_URL

forge test --fork-url $RPC_URL
forge test --fork-url $SEPOLIA_RPC_URL
forge test --fork-url $MAINNET_RPC_URL
```

### Run a test in _debug mode_

```shell
forge test --debug test_PriceFeedVersionIsCorrect
```

### Check test suite coverage

```shell
forge coverage
forge coverage --fork-url $RPC_URL

forge coverage --report debug
forge coverage --report debug > coverage.txt
```

### Check gas costs

```shell
forge snapshot
forge snapshot --mt test_WithdrawWithManyFunders
```

### Zksync Devops

https://github.com/Cyfrin/foundry-devops

### TODO: Gas cost exploration

https://github.com/Cyfrin/foundry-fund-me-cu/blob/main/script/DeployStorageFun.s.sol
https://github.com/Cyfrin/foundry-fund-me-cu/blob/main/src/exampleContracts/FunWithStorage.sol
