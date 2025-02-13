# walletlibb



Unified interface to programmatically open and extract data from cryptocurrency wallet backup files

## Quick Start with Docker - Start here if you simply need to dump the contents of a wallet file

### Make sure that the files you are trying to open are in one directory.

```bash
$ docker pull jimzhou/walletlib:latest
$ docker run -v /path/to/your/wallet/folder:/app jimzhou/walletlib:latest wallet.dat -o wallet_output.txt --keys -p password
```
Output file will be in the directory with the wallet. --keys and -p are optional



## Quick Start with installation

This module requires Python 3.7+

Note: prior to installation, make sure that BerkeleyDB 4.8+ is installed.

With Homebrew:
```bash
$ brew install berkeley-db@4
```

On Ubuntu
```
$ sudo apt-get install libdb++-dev python3-bsddb3
```

```bash
$ pip install walletlib
```
A convenient cli script is available after installation.
```bash
$ python -m dumpwallet wallet.dat -o output.txt
```
or
```bash
$ dumpwallet wallet.dat -o output.txt
$ dumpwallet wallet-protobuf -o output.txt --keys
```

## Features
- Automatic reading of version byte and WIF prefix from default keys
- Dumping just keys or all data
- Read only access of wallet files

## Installation
The simplest way to install walletlib is using pip.
```bash
$ pip install walletlib
```
You can also clone this repo and then run
```bash
$ python setup.py install
```
## Usage
```python
import walletlib

wallet = walletlib.Walletdat.load("path/to/wallet.dat")
wallet.parse(passphrase="password")
wallet.dump_all(filepath="output.txt")
wallet.dump_keys(filepath="output_keys.txt")

```
Bitcoinj wallets:

```python
import walletlib

wallet = walletlib.ProtobufWallet.load("path/to/wallet-protobuf")
wallet.parse()
wallet.dump_all(filepath="output.txt")
wallet.dump_keys(filepath="output_keys.txt")
```

