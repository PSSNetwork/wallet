[![gitstars](https://img.shields.io/github/stars/PSSNetwork/wallet?style=social)](https://github.com/PSSNetwork/wallet/stargazers)
[![discord](https://img.shields.io/discord/701937565929963581)](https://discord.gg/DYZHmgF)

## PSS

PSS is based on Komodo (Zcash fork). You should install Komodo with all dependencies and then run PSS blockchain and connect with the network.

## Resources

- Website: [https://psscoin.online](https://psscoin.online)
- Block Explorer: [https://explorer.psscoin.online](https://explorer.psscoin.online)
- Discord: [PSS PROJECT](https://discord.gg/DYZHmgF)

## Tech Specification
- Max Supply: 5,898,454,281 PSS
- Block Time: 30 seconds
- Block Reward: 36 SPACE (currently)
- Block Generation: 50% PoW | 50% PoS
- Mining Algorithm: Equihash (200, 9)

## Getting started

### Dependencies

```shell
#The following packages are needed:
sudo apt-get install build-essential pkg-config libc6-dev m4 g++-multilib autoconf libtool ncurses-dev unzip git python python-zmq zlib1g-dev wget libcurl4-gnutls-dev bsdmainutils automake curl libsodium-dev
```

### Build Komodo

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

#### Create .komodo/PSS/PSS.conf

Create a komodo.conf file:

```shell
mkdir ~/.komodo/PSS
cd ~/.komodo/PSS
touch PSS.conf

#Add the following lines to the komodo.conf file:
rpcuser=yourrpcusername
rpcpassword=yoursecurerpcpassword
rpcbind=127.0.0.1
txindex=1
addnode=91.231.187.24
addnode=91.231.187.36
addnode=91.231.187.15
addnode=91.231.187.48
```

#### Connect to PSS blockchain
#### Command to run PSS blockchain and connect with the network:

```shell
./komodod -ac_name=PSS -ac_supply=0 -ac_eras=6 -ac_reward=3600000000,2700000000,1800000000,900000000,600000000,300000000 -ac_end=939393,3757572,12212109,325343422,638474735,951606048 -ac_blocktime=30 -ac_staked=50 -ac_cbmaturity=1 -ac_cc=939 -ac_sapling=1 -addnode=91.231.187.36 -addnode=91.231.187.48 &
```

# Wallet commands:
#### Get (transparent) wallet and blockchain info
./komodo-cli -ac_name=PSS getinfo


#### Get (transparent) wallet information
./komodo-cli -ac_name=PSS getwalletinfo
#### Get mining information
./komodo-cli -ac_name=PSS getmininginfo
#### Generate a new address
./komodo-cli -ac_name=PSS getnewaddress

#### Send an amount from account to address
./komodo-cli -ac_name=PSS sendfrom "account" "address" amount


**PSS and Komodo is based on Zcash which is unfinished and highly experimental.** Use at your own risk.

License
-------
For license information see the file [COPYING](COPYING).

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
