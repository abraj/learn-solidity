### Use environment variables

```shell
source .env
echo $RPC_URL
echo $KEYSTORE
echo $PWD_FILE
```

### Initialize project

```shell
forge init
```

### Build project

```shell
forge clean

forge build
# forge build --zksync
```

### Switch b/w `foundry` and `foundry-zksync`

```shell
foundryup
foundryup-zksync

forge --version
cast --version
anvil --version
chisel --version
```

### Add private key to keystore

```shell
cast wallet import test-account-1 --interactive
cast wallet list

mkdir -p ~/.my/passwords
bash -c 'read -p "Keystore password: " user_input && echo -n $user_input > ~/.my/passwords/test-account-1'

cat ~/.foundry/keystores/test-account-1
cat ~/.my/passwords/test-account-1

history -p && rm ~/.zsh_history
history -c && rm ~/.bash_history
```

### Deploy using `forge` CLI

```shell
forge create SimpleStorage --rpc-url $RPC_URL --keystore $KEYSTORE --password-file $PWD_FILE
forge create SimpleStorage --rpc-url $RPC_URL --interactive
forge create SimpleStorage --keystore $KEYSTORE --password-file $PWD_FILE
forge create SimpleStorage --interactive
forge create src/SimpleStorage.sol:SimpleStorage --keystore $KEYSTORE --password-file $PWD_FILE

# Deploy to Zksync (--zksync option required)
forge create SimpleStorage
  --rpc-url https://sepolia.era.zksync.dev
  # --chain 300
  --keystore $KEYSTORE --password-file $PWD_FILE
  # --legacy
  --zksync
```

### Deploy using `forge script`

```shell
forge script SimpleStorageScript --rpc-url $RPC_URL --broadcast --keystore $KEYSTORE --password-file $PWD_FILE
forge script script/SimpleStorage.s.sol --rpc-url $RPC_URL --broadcast --keystore $KEYSTORE --password-file $PWD_FILE
forge script script/SimpleStorage.s.sol:SimpleStorageScript --rpc-url $RPC_URL --broadcast --keystore $KEYSTORE --password-file $PWD_FILE

# Zksync (--zksync option required) [Not working currently]
  # --legacy
  --zksync
```

### Send transaction

```shell
cast send 0x5FbDB2315678afecb367f032d93F642f64180aa3 "store(uint256)" 123 --rpc-url $RPC_URL --keystore $KEYSTORE --password-file $PWD_FILE
```

### Call function

```shell
cast call 0x5FbDB2315678afecb367f032d93F642f64180aa3 "retrieve()" --rpc-url $RPC_URL
cast --to-dec 0x000000000000000000000000000000000000000000000000000000000000007b
cast --to-dec 0x7b
```

### Read storage

```shell
cast storage 0x5FbDB2315678afecb367f032d93F642f64180aa3 0
cast --to-dec 0x000000000000000000000000000000000000000000000000000000000000007b
```

### Inspect storage layout

```shell
forge inspect SimpleStorage storageLayout
```

### Format code

```shell
forge fmt
```

<!--
[Anvil] Contract Address: 0x5FbDB2315678afecb367f032d93F642f64180aa3
[Sepolia:eth] Contract Address: 0x912b91c6433C52350f736cB815c0D11c0a3f8434
[Sepolia:zksync] Contract Address: 0x5A162dB8eCB5A5e2912c3376F15604221a0f7c14
-->
