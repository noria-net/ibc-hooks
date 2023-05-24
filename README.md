# Noria Chain Boilerplate

## Overview

This is a cosmos-sdk chain boilerplate for creating custom modules. It is a fork from [CosmWasm/wasmd](https://github.com/CosmWasm/wasmd) that has been upgraded to be compatible with [ignite](https://github.com/ignite/cli).

## Wasm

The boilerplate is compatible with the CosmWasm smart contracts. Wasmd sync'd commit: [fc45b6d53136b20e0fb77643f2314d7f3d108e11](https://github.com/CosmWasm/wasmd/commit/fc45b6d53136b20e0fb77643f2314d7f3d108e11).

## Ignite

Current ignite compatible version: [0.26.1-dev](https://github.com/ignite/cli/commit/0cb89939d71f366a3e8a038e16015416de736ad6)

Ignite version:

```bash
Ignite CLI version:             v0.26.1-dev
Ignite CLI build date:          2023-05-10T16:49:12Z
Ignite CLI source hash:         0cb89939d71f366a3e8a038e16015416de736ad6
Ignite CLI config version:      v1
Cosmos SDK version:             v0.47.2
```

## Usage

Clone this repo:

```bash
git clone https://github.com/noria-net/ibc-hooks
```

Reinitialize the git repo:

```bash
rm -rf .git
git init
```

Add your custom module:

```bash
ignite scaffold module <module-name>
```

Run your chain:

```bash
ignite chain serve
```
