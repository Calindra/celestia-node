# How to install

Clone the git repository

```sh
git fetch --all --tags
git checkout tags/v0.13.6
make build
sudo make install
```

```sh
make cel-key
```

```sh
celestia version
```

Output

```sh
Semantic version: v0.13.6
Commit: e40a10990142b443f62a1e71b7923ab993b91303
Build Date: Mon Jun 10 05:08:27 PM UTC 2024
System version: amd64/linux
Golang version: go1.22.2
```

```sh
celestia light init --p2p.network arabica
```

Delete the key if you need to recover an old account

```sh
./cel-key delete my_celes_key --node.type light --p2p.network arabica

# recover
./cel-key add my_celes_key --recover --keyring-backend test \
  --node.type light --p2p.network arabica
```

Start the celestia node

```sh
celestia light start --core.ip validator-1.celestia-arabica-11.com --p2p.network arabica
```


```sh
celestia state balance-for-address celestia1ejgmnkvtv5k58vtj5avq8c00yz2j4ejx49phkr --token $AUTH_TOKEN
```

Output:

```sh
{
  "result": {
    "denom": "utia",
    "amount": "99872320"
  }
}
```

Listing the accounts you have:

```sh
./cel-key list --node.type light --p2p.network arabica
```
Output:
```sh
using directory:  /home/gitpod/.celestia-light-arabica-11/keys
- address: celestia1yau775hcpt0q8qye339c76u65xuzekfxv8hyqa
  name: my_celes_key
  pubkey: '{"@type":"/cosmos.crypto.secp256k1.PubKey","key":"AlnDGc2bUKc8kE2Di+ZbuUd8ID2gaQNWnpn90O+qroxD"}'
  type: local
- address: celestia1ejgmnkvtv5k58vtj5avq8c00yz2j4ejx49phkr
  name: my_celes_key1
  pubkey: '{"@type":"/cosmos.crypto.secp256k1.PubKey","key":"ArBxytBFPJuFmEFlO2wjTmhZiSBrHM/U9cP/X7jm6WLW"}'
  type: local
```

Generate the token:

```sh
export AUTH_TOKEN=$(celestia light auth admin --p2p.network arabica)
```
