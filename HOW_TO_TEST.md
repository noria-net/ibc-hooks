# Testing

## Cosmos (source) -> Cosmos (destination, with ibc-hooks implemented)

1. Spin up a relayer between two chains over the transfer port (ICS20 - unordered)
2. Deploy a smart contract on the destination chain
3. Send an IBC transfer from the source chain to the destination chain, with the memo field formatted correctly for wasmhooks
4. Check that the smart contract on the destination chain was called with the correct arguments

### Example

```bash
CONTRACT_ADDR='chain1298fhj20f2' # contract deployed on destination chain
EXEC_MSG='{"increment":{}}' # execute message to be sent to contract
MEMO='{"wasm":{"contract":"'$CONTRACT_ADDR'","msg":'$EXEC_MSG'}}' # memo field formatted correctly for wasmhooks
CHANNEL="channel-893" # the channel for the relayer to use, from source chain to destination chain
SOURCE_CHAIN_BINARY="osmosisd" # binary for source chain

# send IBC transfer
SOURCE_CHAIN_BINARY tx ibc-transfer transfer $CHANNEL $CONTRACT_ADDR 1uosmo --from=me --memo="$MEMO"
```  

---

## EVM (source, let's say Avalanche Testnet Fuji) -> Cosmos (destination, with ibc-hooks implemented)

1. Deploy a smart contract on the destination chain
2. Follow the instructions [here](https://github.com/axelarnetwork/evm-cosmos-gmp-sample/blob/main/native-integration/onboard-devnet.md) to register and activate your destination chain with Axelar devnet  
3. Spin up a relayer between your destination chain and Axelar devnet over the transfer port (ICS20 - unordered)
4. Deploy a solidity smart contract on the source chain such as [this one](https://github.com/ori-wagmi/axelar_send_receive_example/tree/main/evm).  

> Params for deployment:
> - GATEWAY: 0x3724270405e60Fb25f99556Ad2104631f38b9b79 (from instructions at step 1 above)
> - GASRECEIVER: 0xbE406F0189A0B4cf3A05C286473D23791Dd44Cc6 
> - CHAINNAME: Avalanche

5. Execute the `send` function on the deployed contract with the following params:

> - destinationChain: _chain id of destination chain_ (e.g. `chain-ibc-hooks-1`)
> - destinationAddress: smart contract deployed on destination chain
> - message: your exec msg payload. If using example EVM contract above, this can be any string (e.g. `hello world`)

6. Check that the smart contract on the destination chain was called with the correct arguments  
