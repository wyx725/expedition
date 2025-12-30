# Expedition

<!-- project logo w/ quick links -->
<p align="center">
  <img src="https://github.com/etclabscore/jade-media-assets/blob/master/j-explorer/j-explorer(PNG)/128x128.png?raw=true" />
</p>
<center>
  <h3 align="center">Expedition</h3>

  <p align="center">
    A block explorer for the Ethereum Stack.
    <br />
    <a href="https://expedition.dev">View Demo</a>
    ·
    <a href="https://github.com/etclabscore/expedition/issues/new?assignees=&labels=&template=bug_report.md&title=">Report Bug</a>
    ·
    <a href="https://github.com/etclabscore/expedition/issues/new?assignees=&labels=&template=feature_request.md&title=">Request Feature</a>
  </p>
</center>

![expedition_gif](https://user-images.githubusercontent.com/364566/94349388-d17fb000-fff8-11ea-92ae-71c002474a65.gif)

<!-- table of contents -->
## Table of Contents
  - [About The Project](#about-the-project)
  - [Getting Started](#getting-started)
      - [Prerequisites](#prerequisites)
      - [Installation](#installation)
- [Usage](#usage)
  - [Start explorer](#start-the-explorer)
  - [Configurations](#configurations)
- [Contributing](#contributing)
- [Resources](#resources)

<!-- about the project -->
## About The Project

[Expedition](https://expedition.dev) is a minimal block explorer for Ethereum Stack. It does not use a database, and can be configured to point at any remote RPC node for any EVM-based network. The goal of the Explorer is to provide a resource for network information and block exploration with only an Ethereum EPC endpoint.

Explorer Features:
- Display chain id
- Syncing status
- Runtime configuration for endpoints
- Search by Block, Transaction, Address
- Charts for hash, transaction count, gas used, uncles
- Preview latest blocks with pagination
- Multi-language support

<!-- getting started with the project -->
## Getting Started
### Prerequisites
- node `v10.15.3` or later
- npm `v6.4.1` or later

### Installation
Clone/ download the project, and install dependencies.
```bash
git clone https://github.com/xops/expedition.git && cd expedition && npm install
```

<!-- example usage, screen shots, demos -->

#### Modify built-in chain node configurations (useChainList.ts) [新增]

To customize the built-in chain nodes displayed in the explorer, modify the useChainList.ts file. This file contains configurations for node display and connection, including three key fields:
name: The display name of the node in the browser (customizable, e.g., "My Ethereum Node")
network: The network type of the node (customizable, e.g., "private-mainnet")
rpc: The RPC port access address of the node (ensure the port is accessible to the client terminal, e.g., "http://192.168.1.100:8545")

##### Steps to modify:

- Locate the useChainList.ts file in the project source code.
- Find the chain configuration object (usually an array of chain items).
- Update the name, network, and rpc fields according to your needs.
- Save the file and restart the explorer with npm start for changes to take effect.

#### Compatibility Fix: Node.js v17+ Encryption Error [新增]

When running the project with Node.js v17 or higher, you may encounter the error digital envelope routines:unsupported (caused by incompatible encryption algorithms between Node.js v17+ and old webpack/React scaffolding).
**Solution**: Modify the scripts section in the project's package.json file to add legacy OpenSSL provider configuration:

```json
"start": "set NODE_OPTIONS=--openssl-legacy-provider && react-scripts start", 
"build": "set NODE_OPTIONS=--openssl-legacy-provider && react-scripts build"
```

- Note for Mac/Linux users: Replace set with **export** (e.g., "start": "export NODE_OPTIONS=--openssl-legacy-provider && react-scripts start")
- After modification, re-run npm start to launch the project normally.

## Usage

### Start the explorer
```bash
npm start
```
*The explorer will run at http://localhost:3000/.*

### Configurations

#### Set rpc via url

`?rpcUrl=` Set custom rpc url.

Example: 

http://localhost:3000/?rpcUrl=https://www.ethercluster.com/kotti

#### Configure default urls via environment variables

Override eth url

```
REACT_APP_ETH_RPC_URL=https://www.ethercluster.com/kotti npm start
```

<!-- template just leave alone  -->

## Roadmap
See the [open issues](https://github.com/etclabscore/xops/issues) for a list of proposed features (and known issues).

<!-- template just leave alone  -->
## Contributing
How to contribute, build and release are outlined in [CONTRIBUTING.md](CONTRIBUTING.md), [BUILDING.md](BUILDING.md) and [RELEASING.md](RELEASING.md) respectively. Commits in this repository follow the [CONVENTIONAL_COMMITS.md](CONVENTIONAL_COMMITS.md) specification.

## License
Apache License 2.0

<!-- references and additional resources  -->
## Resources
- [OpenRPC](https://open-rpc.org)

---
*This repo originally forked from [ETCDEVTeam/emerald-explorer](https://github.com/ETCDEVTeam/emerald-explorer).*
