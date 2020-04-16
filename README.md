

## List of Komodo Platform Technologies

- Delayed Proof of Work (dPoW) - Additional security layer and Komodos own consensus algorithm  
- zk-SNARKs - Komodo Platform's privacy technology for shielded transactions  
- Tokens/Assets Technology - create "colored coins" on the Komodo Platform and use them as a layer for securites  
- Reward API - Komodo CC technology for securities  
- CC - Crypto Conditions to realize "smart contract" logic on top of the Komodo Platform  
- Jumblr - Decentralized tumbler for KMD and other cryptocurrencies  
- Assetchains - Create your own Blockchain that inherits all Komodo Platform functionalities and blockchain interoperability  
- Pegged Assets - Chains that maintain a peg to fiat currencies  
- Peerchains - Scalability solution where sibling chains form a network of blockchains  
- More in depth covered [here](https://docs.google.com/document/d/1AbhWrtagu4vYdkl-vsWz-HSNyNvK-W-ZasHCqe7CZy0)  
- Also note you receive 5% Active User Reward on your balance.  
[See this article for more details](https://support.komodoplatform.com/en/support/solutions/articles/29000024515-how-to-claim-the-kmd-active-user-reward-in-agama)

## About this Project
Komodo is based on Zcash and has been extended by our innovative consensus algorithm called dPoW which utilizes Bitcoin's hashrate to store Komodo blockchain information into the Bitcoin blockchain. Other new and native Komodo features are the privacy technology called JUMBLR, our assetchain capabilities (one click plug and play blockchain solutions) and a set of financial decentralization and interoperability technologies. More details are available under https://komodoplatform.com/ and https://blog.komodoplatform.com.

## Getting started

### Dependencies

```shell
#The following packages are needed:
sudo apt-get install build-essential pkg-config libc6-dev m4 g++-multilib autoconf libtool ncurses-dev unzip git python python-zmq zlib1g-dev wget libcurl4-gnutls-dev bsdmainutils automake curl libsodium-dev
```

### Build Komodo

This software is based on zcash and considered experimental and is continously undergoing heavy development.

The dev branch is considered the bleeding edge codebase while the master-branch is considered tested (unit tests, runtime tests, functionality). At no point of time do the Komodo Platform developers take any responsbility for any damage out of the usage of this software. 
Komodo builds for all operating systems out of the same codebase. Follow the OS specific instructions from below.

#### Linux
```shell
git clone https://github.com/komodoplatform/komodo --branch master --single-branch
cd komodo
./zcutil/fetch-params.sh
# -j8 = using 8 threads for the compilation - replace 8 with number of threads you want to use
./zcutil/build.sh -j8
#This can take some time.
```


#### OSX
Ensure you have [brew](https://brew.sh) and Command Line Tools installed.
```shell
# Install brew
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
# Install Xcode, opens a pop-up window to install CLT without installing the entire Xcode package
xcode-select --install 
# Update brew and install dependencies
brew update
brew upgrade
brew tap discoteq/discoteq; brew install flock
brew install autoconf autogen automake
brew update && brew install gcc@8
brew install binutils
brew install protobuf
brew install coreutils
brew install wget
# Clone the Komodo repo
git clone https://github.com/komodoplatform/komodo --branch master --single-branch
# Change master branch to other branch you wish to compile
cd komodo
./zcutil/fetch-params.sh
# -j8 = using 8 threads for the compilation - replace 8 with number of threads you want to use
./zcutil/build-mac.sh -j8
# This can take some time.
```

#### Windows
Use a debian cross-compilation setup with mingw for windows and run:
```shell
sudo apt-get install build-essential pkg-config libc6-dev m4 g++-multilib autoconf libtool ncurses-dev unzip git python python-zmq zlib1g-dev wget libcurl4-gnutls-dev bsdmainutils automake curl cmake mingw-w64 libsodium-dev libevent-dev
curl https://sh.rustup.rs -sSf | sh
source $HOME/.cargo/env
rustup target add x86_64-pc-windows-gnu
git clone https://github.com/jl777/komodo --branch master --single-branch
cd komodo
./zcutil/fetch-params.sh
# -j8 = using 8 threads for the compilation - replace 8 with number of threads you want to use
./zcutil/build-win.sh -j8
#This can take some time.
```
**komodo is experimental and a work-in-progress.** Use at your own risk.

To reset the Komodo blockchain change into the *~/.komodo* data directory and delete the corresponding files by running `rm -rf blocks chainstate debug.log komodostate db.log`

#### Create .komodo/OSN/OSN.conf

Create a komodo.conf file:

```
mkdir ~/.komodo/PSS
cd ~/.komodo/PSS
touch PSS.conf

#Add the following lines to the komodo.conf file:
rpcuser=yourrpcusername
rpcpassword=yoursecurerpcpassword
rpcbind=127.0.0.1
txindex=1
addnode=91.231.187.24
addnode=91.231.187.27
addnode=91.231.187.16
addnode=91.231.187.20
addnode=91.231.187.19
addnode=91.231.187.21
addnode=91.231.187.11
```

### Connect to PSS blockchain
### Command to run PSS blockchain and connect with the network:

./komodod -ac_name=PSS -ac_supply=20000000 -ac_sapling=1 -ac_reward=12000000000 -ac_staked=50 -ac_halving=525600 -ac_decay=65000000 -ac_cbmaturity=6 -ac_adaptivepow=1 -ac_cc=102 -ac_blocktime=150 -ac_public=1 -addnode=91.231.187.19 &


Wallet commands:
# Get (transparent) wallet and blockchain info
./komodo-cli -ac_name=PSS getinfo


# Get (transparent) wallet information
./komodo-cli -ac_name=PSS getwalletinfo
# Get mining information
./komodo-cli -ac_name=PSS getmininginfo
# Generate a new address
./komodo-cli -ac_name=PSS getnewaddress

# Example:
./komodo-cli -ac_name=PSS senfrom "" address

**Komodo is based on Zcash which is unfinished and highly experimental.** Use at your own risk.

License
-------
For license information see the file [COPYING](COPYING).




Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
