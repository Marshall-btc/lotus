# lotus
```
NAME:
   lotus - Filecoin decentralized storage network client

USAGE:
   lotus [global options] command [command options] [arguments...]

VERSION:
   1.23.4-dev

COMMANDS:
   daemon   Start a lotus daemon process
   backup   Create node metadata backup
   config   Manage node config
   version  Print version
   help, h  Shows a list of commands or help for one command
   BASIC:
     send     Send funds between accounts
     wallet   Manage wallet
     info     Print node info
     client   Make deals, store data, retrieve data
     msig     Interact with a multisig wallet
     filplus  Interact with the verified registry actor used by Filplus
     paych    Manage payment channels
   DEVELOPER:
     auth          Manage RPC permissions
     mpool         Manage message pool
     state         Interact with and query filecoin chain state
     chain         Interact with filecoin blockchain
     log           Manage logging
     wait-api      Wait for lotus api to come online
     fetch-params  Fetch proving parameters
     evm           Commands related to the Filecoin EVM runtime
   NETWORK:
     net   Manage P2P Network
     sync  Inspect or interact with the chain syncer
   STATUS:
     status  Check node status

GLOBAL OPTIONS:
   --color        use color in display output (default: depends on output being a TTY)
   --interactive  setting to false will disable interactive functionality of commands (default: false)
   --force-send   if true, will ignore pre-send checks (default: false)
   --vv           enables very verbose mode, useful for debugging the CLI (default: false)
   --help, -h     show help
   --version, -v  print the version
```

## lotus daemon
```
NAME:
   lotus daemon - Start a lotus daemon process

USAGE:
   lotus daemon command [command options] [arguments...]

COMMANDS:
   stop     Stop a running lotus daemon
   help, h  Shows a list of commands or help for one command

OPTIONS:
   --api value               (default: "1234")
   --genesis value           genesis file to use for first node run
   --bootstrap               (default: true)
   --import-chain value      on first run, load chain from given file or url and validate
   --import-snapshot value   import chain state from a given chain export file or url
   --remove-existing-chain   remove existing chain and splitstore data on a snapshot-import (default: false)
   --halt-after-import       halt the process after importing chain from file (default: false)
   --lite                    start lotus in lite mode (default: false)
   --pprof value             specify name of file for writing cpu profile to
   --profile value           specify type of node
   --manage-fdlimit          manage open file limit (default: true)
   --config value            specify path of config file to use
   --api-max-req-size value  maximum API request size accepted by the JSON RPC server (default: 0)
   --restore value           restore from backup file
   --restore-config value    config file to use when restoring from backup
   --help, -h                show help
```

### lotus daemon stop
```
NAME:
   lotus daemon stop - Stop a running lotus daemon

USAGE:
   lotus daemon stop [command options] [arguments...]

OPTIONS:
   --help, -h  show help
```

## lotus backup
```
NAME:
   lotus backup - Create node metadata backup

USAGE:
   lotus backup [command options] [backup file path]

DESCRIPTION:
   The backup command writes a copy of node metadata under the specified path

   Online backups:
   For security reasons, the daemon must be have LOTUS_BACKUP_BASE_PATH env var set
   to a path where backup files are supposed to be saved, and the path specified in
   this command must be within this base path

OPTIONS:
   --offline   create backup without the node running (default: false)
   --help, -h  show help
```

## lotus config
```
NAME:
   lotus config - Manage node config

USAGE:
   lotus config command [command options] [arguments...]

COMMANDS:
   default  Print default node config
   updated  Print updated node config
   help, h  Shows a list of commands or help for one command

OPTIONS:
   --help, -h  show help
```

### lotus config default
```
NAME:
   lotus config default - Print default node config

USAGE:
   lotus config default [command options] [arguments...]

OPTIONS:
   --no-comment  don't comment default values (default: false)
   --help, -h    show help
```

### lotus config updated
```
NAME:
   lotus config updated - Print updated node config

USAGE:
   lotus config updated [command options] [arguments...]

OPTIONS:
   --no-comment  don't comment default values (default: false)
   --help, -h    show help
```

## lotus version
```
NAME:
   lotus version - Print version

USAGE:
   lotus version [command options] [arguments...]

OPTIONS:
   --help, -h  show help
```

## lotus send
```
NAME:
   lotus send - Send funds between accounts

USAGE:
   lotus send [command options] [targetAddress] [amount]

CATEGORY:
   BASIC

OPTIONS:
   --from value           optionally specify the account to send funds from
   --from-eth-addr value  optionally specify the eth addr to send funds from
   --gas-premium value    specify gas price to use in AttoFIL (default: "0")
   --gas-feecap value     specify gas fee cap to use in AttoFIL (default: "0")
   --gas-limit value      specify gas limit (default: 0)
   --nonce value          specify the nonce to use (default: 0)
   --method value         specify method to invoke (default: 0)
   --params-json value    specify invocation parameters in json
   --params-hex value     specify invocation parameters in hex
   --force                Deprecated: use global 'force-send' (default: false)
   --help, -h             show help
```

## lotus wallet
```
NAME:
   lotus wallet - Manage wallet

USAGE:
   lotus wallet command [command options] [arguments...]

COMMANDS:
   new          Generate a new key of the given type
   list         List wallet address
   balance      Get account balance
   export       export keys
   import       import keys
   default      Get default wallet address
   set-default  Set default wallet address
   sign         sign a message
   verify       verify the signature of a message
   delete       Soft delete an address from the wallet - hard deletion needed for permanent removal
   market       Interact with market balances
   help, h      Shows a list of commands or help for one command

OPTIONS:
   --help, -h  show help
```

### lotus wallet new
```
NAME:
   lotus wallet new - Generate a new key of the given type

USAGE:
   lotus wallet new [command options] [bls|secp256k1 (default secp256k1)]

OPTIONS:
   --help, -h  show help
```

### lotus wallet list
```
NAME:
   lotus wallet list - List wallet address

USAGE:
   lotus wallet list [command options] [arguments...]

OPTIONS:
   --addr-only, -a  Only print addresses (default: false)
   --id, -i         Output ID addresses (default: false)
   --market, -m     Output market balances (default: false)
   --help, -h       show help
```

### lotus wallet balance
```
NAME:
   lotus wallet balance - Get account balance

USAGE:
   lotus wallet balance [command options] [address]

OPTIONS:
   --help, -h  show help
```

### lotus wallet export
```
NAME:
   lotus wallet export - export keys

USAGE:
   lotus wallet export [command options] [address]

OPTIONS:
   --help, -h  show help
```

### lotus wallet import
```
NAME:
   lotus wallet import - import keys

USAGE:
   lotus wallet import [command options] [<path> (optional, will read from stdin if omitted)]

OPTIONS:
   --format value  specify input format for key (default: "hex-lotus")
   --as-default    import the given key as your new default key (default: false)
   --help, -h      show help
```

### lotus wallet default
```
NAME:
   lotus wallet default - Get default wallet address

USAGE:
   lotus wallet default [command options] [arguments...]

OPTIONS:
   --help, -h  show help
```

### lotus wallet set-default
```
NAME:
   lotus wallet set-default - Set default wallet address

USAGE:
   lotus wallet set-default [command options] [address]

OPTIONS:
   --help, -h  show help
```

### lotus wallet sign
```
NAME:
   lotus wallet sign - sign a message

USAGE:
   lotus wallet sign [command options] <signing address> <hexMessage>

OPTIONS:
   --help, -h  show help
```

### lotus wallet verify
```
NAME:
   lotus wallet verify - verify the signature of a message

USAGE:
   lotus wallet verify [command options] <signing address> <hexMessage> <signature>

OPTIONS:
   --help, -h  show help
```

### lotus wallet delete
```
NAME:
   lotus wallet delete - Soft delete an address from the wallet - hard deletion needed for permanent removal

USAGE:
   lotus wallet delete [command options] <address> 

OPTIONS:
   --help, -h  show help
```

### lotus wallet market
```
NAME:
   lotus wallet market - Interact with market balances

USAGE:
   lotus wallet market command [command options] [arguments...]

COMMANDS:
   withdraw  Withdraw funds from the Storage Market Actor
   add       Add funds to the Storage Market Actor
   help, h   Shows a list of commands or help for one command

OPTIONS:
   --help, -h  show help
```

#### lotus wallet market withdraw
```
NAME:
   lotus wallet market withdraw - Withdraw funds from the Storage Market Actor

USAGE:
   lotus wallet market withdraw [command options] [amount (FIL) optional, otherwise will withdraw max available]

OPTIONS:
   --wallet value, -w value   Specify address to withdraw funds to, otherwise it will use the default wallet address
   --address value, -a value  Market address to withdraw from (account or miner actor address, defaults to --wallet address)
   --confidence value         number of block confirmations to wait for (default: 5)
   --help, -h                 show help
```

#### lotus wallet market add
```
NAME:
   lotus wallet market add - Add funds to the Storage Market Actor

USAGE:
   lotus wallet market add [command options] <amount>

OPTIONS:
   --from value, -f value     Specify address to move funds from, otherwise it will use the default wallet address
   --address value, -a value  Market address to move funds to (account or miner actor address, defaults to --from address)
   --help, -h                 show help
```

## lotus info
```
NAME:
   lotus info - Print node info

USAGE:
   lotus info [command options] [arguments...]

CATEGORY:
   BASIC

OPTIONS:
   --help, -h  show help
```

## lotus client
```
NAME:
   lotus client - Make deals, store data, retrieve data

USAGE:
   lotus client command [command options] [arguments...]

COMMANDS:
   help, h  Shows a list of commands or help for one command
   DATA:
     import  Import data
     drop    Remove import
     local   List locally imported data
     stat    Print information about a locally stored file (piece size, etc)
   RETRIEVAL:
     find              Find data in the network
     retrieval-ask     Get a miner's retrieval ask
     retrieve          Retrieve data from network
     cat               Show data from network
     ls                List object links
     cancel-retrieval  Cancel a retrieval deal by deal ID; this also cancels the associated transfer
     list-retrievals   List retrieval market deals
   STORAGE:
     deal          Initialize storage deal with a miner
     query-ask     Find a miners ask
     list-deals    List storage market deals
     get-deal      Print detailed deal information
     list-asks     List asks for top miners
     deal-stats    Print statistics about local storage deals
     inspect-deal  Inspect detailed information about deal's lifecycle and the various stages it goes through
   UTIL:
     commP             Calculate the piece-cid (commP) of a CAR file
     generate-car      Generate a car file from input
     balances          Print storage market client balances
     list-transfers    List ongoing data transfers for deals
     restart-transfer  Force restart a stalled data transfer
     cancel-transfer   Force cancel a data transfer

OPTIONS:
   --help, -h  show help
```

### lotus client import
```
NAME:
   lotus client import - Import data

USAGE:
   lotus client import [command options] [inputPath]

CATEGORY:
   DATA

OPTIONS:
   --car        import from a car file instead of a regular file (default: false)
   --quiet, -q  Output root CID only (default: false)
   --help, -h   show help
```

### lotus client drop
```
NAME:
   lotus client drop - Remove import

USAGE:
   lotus client drop [command options] [import ID...]

CATEGORY:
   DATA

OPTIONS:
   --help, -h  show help
```

### lotus client local
```
NAME:
   lotus client local - List locally imported data

USAGE:
   lotus client local [command options] [arguments...]

CATEGORY:
   DATA

OPTIONS:
   --help, -h  show help
```

### lotus client stat
```
NAME:
   lotus client stat - Print information about a locally stored file (piece size, etc)

USAGE:
   lotus client stat [command options] <cid>

CATEGORY:
   DATA

OPTIONS:
   --help, -h  show help
```

### lotus client find
```
NAME:
   lotus client find - Find data in the network

USAGE:
   lotus client find [command options] [dataCid]

CATEGORY:
   RETRIEVAL

OPTIONS:
   --pieceCid value  require data to be retrieved from a specific Piece CID
   --help, -h        show help
```

### lotus client retrieval-ask
```
NAME:
   lotus client retrieval-ask - Get a miner's retrieval ask

USAGE:
   lotus client retrieval-ask [command options] [minerAddress] [data CID]

CATEGORY:
   RETRIEVAL

OPTIONS:
   --size value  data size in bytes (default: 0)
   --help, -h    show help
```

### lotus client retrieve
```
NAME:
   lotus client retrieve - Retrieve data from network

USAGE:
   lotus client retrieve [command options] [dataCid outputPath]

CATEGORY:
   RETRIEVAL

DESCRIPTION:
   Retrieve data from the Filecoin network.

   The retrieve command will attempt to find a provider make a retrieval deal with
   them. In case a provider can't be found, it can be specified with the --provider
   flag.

   By default the data will be interpreted as DAG-PB UnixFSv1 File. Alternatively
   a CAR file containing the raw IPLD graph can be exported by setting the --car
   flag.

   Partial Retrieval:

   The --data-selector flag can be used to specify a sub-graph to fetch. The
   selector can be specified as either IPLD datamodel text-path selector, or IPLD
   json selector.

   In case of unixfs retrieval, the selector must point at a single root node, and
   match the entire graph under that node.

   In case of CAR retrieval, the selector must have one common "sub-root" node.

   Examples:

   - Retrieve a file by CID
     $ lotus client retrieve Qm... my-file.txt

   - Retrieve a file by CID from f0123
     $ lotus client retrieve --provider f0123 Qm... my-file.txt

   - Retrieve a first file from a specified directory
     $ lotus client retrieve --data-selector /Links/0/Hash Qm... my-file.txt


OPTIONS:
   --car                                                   Export to a car file instead of a regular file (default: false)
   --data-selector value, --datamodel-path-selector value  IPLD datamodel text-path selector, or IPLD json selector
   --car-export-merkle-proof                               (requires --data-selector and --car) Export data-selector merkle proof (default: false)
   --from value                                            address to send transactions from
   --provider value, --miner value                         provider to use for retrieval, if not present it'll use local discovery
   --maxPrice value                                        maximum price the client is willing to consider (default: 0 FIL)
   --pieceCid value                                        require data to be retrieved from a specific Piece CID
   --allow-local                                           (default: false)
   --help, -h                                              show help
```

### lotus client cat
```
NAME:
   lotus client cat - Show data from network

USAGE:
   lotus client cat [command options] [dataCid]

CATEGORY:
   RETRIEVAL

OPTIONS:
   --ipld                           list IPLD datamodel links (default: false)
   --data-selector value            IPLD datamodel text-path selector, or IPLD json selector
   --from value                     address to send transactions from
   --provider value, --miner value  provider to use for retrieval, if not present it'll use local discovery
   --maxPrice value                 maximum price the client is willing to consider (default: 0 FIL)
   --pieceCid value                 require data to be retrieved from a specific Piece CID
   --allow-local                    (default: false)
   --help, -h                       show help
```

### lotus client ls
```
NAME:
   lotus client ls - List object links

USAGE:
   lotus client ls [command options] [dataCid]

CATEGORY:
   RETRIEVAL

OPTIONS:
   --ipld                           list IPLD datamodel links (default: false)
   --depth value                    list links recursively up to the specified depth (default: 1)
   --data-selector value            IPLD datamodel text-path selector, or IPLD json selector
   --from value                     address to send transactions from
   --provider value, --miner value  provider to use for retrieval, if not present it'll use local discovery
   --maxPrice value                 maximum price the client is willing to consider (default: 0 FIL)
   --pieceCid value                 require data to be retrieved from a specific Piece CID
   --allow-local                    (default: false)
   --help, -h                       show help
```

### lotus client cancel-retrieval
```
NAME:
   lotus client cancel-retrieval - Cancel a retrieval deal by deal ID; this also cancels the associated transfer

USAGE:
   lotus client cancel-retrieval [command options] [arguments...]

CATEGORY:
   RETRIEVAL

OPTIONS:
   --deal-id value  specify retrieval deal by deal ID (default: 0)
   --help, -h       show help
```

### lotus client list-retrievals
```
NAME:
   lotus client list-retrievals - List retrieval market deals

USAGE:
   lotus client list-retrievals [command options] [arguments...]

CATEGORY:
   RETRIEVAL

OPTIONS:
   --verbose, -v  print verbose deal details (default: false)
   --show-failed  show failed/failing deals (default: true)
   --completed    show completed retrievals (default: false)
   --watch        watch deal updates in real-time, rather than a one time list (default: false)
   --help, -h     show help
```

### lotus client deal
```
NAME:
   lotus client deal - Initialize storage deal with a miner

USAGE:
   lotus client deal [command options] [dataCid miner price duration]

CATEGORY:
   STORAGE

DESCRIPTION:
   Make a deal with a miner.
   dataCid comes from running 'lotus client import'.
   miner is the address of the miner you wish to make a deal with.
   price is measured in FIL/Epoch. Miners usually don't accept a bid
   lower than their advertised ask (which is in FIL/GiB/Epoch). You can check a miners listed price
   with 'lotus client query-ask <miner address>'.
   duration is how long the miner should store the data for, in blocks.
   The minimum value is 518400 (6 months).

OPTIONS:
   --manual-piece-cid value     manually specify piece commitment for data (dataCid must be to a car file)
   --manual-piece-size value    if manually specifying piece cid, used to specify size (dataCid must be to a car file) (default: 0)
   --manual-stateless-deal      instructs the node to send an offline deal without registering it with the deallist/fsm (default: false)
   --from value                 specify address to fund the deal with
   --start-epoch value          specify the epoch that the deal should start at (default: -1)
   --fast-retrieval             indicates that data should be available for fast retrieval (default: true)
   --verified-deal              indicate that the deal counts towards verified client total (default: true if client is verified, false otherwise)
   --provider-collateral value  specify the requested provider collateral the miner should put up
   --help, -h                   show help
```

### lotus client query-ask
```
NAME:
   lotus client query-ask - Find a miners ask

USAGE:
   lotus client query-ask [command options] [minerAddress]

CATEGORY:
   STORAGE

OPTIONS:
   --peerid value    specify peer ID of node to make query against
   --size value      data size in bytes (default: 0)
   --duration value  deal duration (default: 0)
   --help, -h        show help
```

### lotus client list-deals
```
NAME:
   lotus client list-deals - List storage market deals

USAGE:
   lotus client list-deals [command options] [arguments...]

CATEGORY:
   STORAGE

OPTIONS:
   --verbose, -v  print verbose deal details (default: false)
   --show-failed  show failed/failing deals (default: false)
   --watch        watch deal updates in real-time, rather than a one time list (default: false)
   --help, -h     show help
```

### lotus client get-deal
```
NAME:
   lotus client get-deal - Print detailed deal information

USAGE:
   lotus client get-deal [command options] [proposalCID]

CATEGORY:
   STORAGE

OPTIONS:
   --help, -h  show help
```

### lotus client list-asks
```
NAME:
   lotus client list-asks - List asks for top miners

USAGE:
   lotus client list-asks [command options] [arguments...]

CATEGORY:
   STORAGE

OPTIONS:
   --by-ping              sort by ping (default: false)
   --output-format value  Either 'text' or 'csv' (default: "text")
   --protocols            Output supported deal protocols (default: false)
   --help, -h             show help
```

### lotus client deal-stats
```
NAME:
   lotus client deal-stats - Print statistics about local storage deals

USAGE:
   lotus client deal-stats [command options] [arguments...]

CATEGORY:
   STORAGE

OPTIONS:
   --newer-than value  (default: 0s)
   --help, -h          show help
```

### lotus client inspect-deal
```
NAME:
   lotus client inspect-deal - Inspect detailed information about deal's lifecycle and the various stages it goes through

USAGE:
   lotus client inspect-deal [command options] [arguments...]

CATEGORY:
   STORAGE

OPTIONS:
   --deal-id value       (default: 0)
   --proposal-cid value  
   --help, -h            show help
```

### lotus client commP
```
NAME:
   lotus client commP - Calculate the piece-cid (commP) of a CAR file

USAGE:
   lotus client commP [command options] [inputFile]

CATEGORY:
   UTIL

OPTIONS:
   --help, -h  show help
```

### lotus client generate-car
```
NAME:
   lotus client generate-car - Generate a car file from input

USAGE:
   lotus client generate-car [command options] [inputPath outputPath]

CATEGORY:
   UTIL

OPTIONS:
   --help, -h  show help
```

### lotus client balances
```
NAME:
   lotus client balances - Print storage market client balances

USAGE:
   lotus client balances [command options] [arguments...]

CATEGORY:
   UTIL

OPTIONS:
   --client value  specify storage client address
   --help, -h      show help
```

### lotus client list-transfers
```
NAME:
   lotus client list-transfers - List ongoing data transfers for deals

USAGE:
   lotus client list-transfers [command options] [arguments...]

CATEGORY:
   UTIL

OPTIONS:
   --verbose, -v  print verbose transfer details (default: false)
   --completed    show completed data transfers (default: false)
   --watch        watch deal updates in real-time, rather than a one time list (default: false)
   --show-failed  show failed/cancelled transfers (default: false)
   --help, -h     show help
```

### lotus client restart-transfer
```
NAME:
   lotus client restart-transfer - Force restart a stalled data transfer

USAGE:
   lotus client restart-transfer [command options] [transferID]

CATEGORY:
   UTIL

OPTIONS:
   --peerid value  narrow to transfer with specific peer
   --initiator     specify only transfers where peer is/is not initiator (default: true)
   --help, -h      show help
```

### lotus client cancel-transfer
```
NAME:
   lotus client cancel-transfer - Force cancel a data transfer

USAGE:
   lotus client cancel-transfer [command options] [transferID]

CATEGORY:
   UTIL

OPTIONS:
   --peerid value          narrow to transfer with specific peer
   --initiator             specify only transfers where peer is/is not initiator (default: true)
   --cancel-timeout value  time to wait for cancel to be sent to storage provider (default: 5s)
   --help, -h              show help
```

## lotus msig
```
NAME:
   lotus msig - Interact with a multisig wallet

USAGE:
   lotus msig command [command options] [arguments...]

COMMANDS:
   create             Create a new multisig wallet
   inspect            Inspect a multisig wallet
   propose            Propose a multisig transaction
   propose-remove     Propose to remove a signer
   approve            Approve a multisig message
   cancel             Cancel a multisig message
   add-propose        Propose to add a signer
   add-approve        Approve a message to add a signer
   add-cancel         Cancel a message to add a signer
   swap-propose       Propose to swap signers
   swap-approve       Approve a message to swap signers
   swap-cancel        Cancel a message to swap signers
   lock-propose       Propose to lock up some balance
   lock-approve       Approve a message to lock up some balance
   lock-cancel        Cancel a message to lock up some balance
   vested             Gets the amount vested in an msig between two epochs
   propose-threshold  Propose setting a different signing threshold on the account
   help, h            Shows a list of commands or help for one command

OPTIONS:
   --confidence value  number of block confirmations to wait for (default: 5)
   --help, -h          show help
```

### lotus msig create
```
NAME:
   lotus msig create - Create a new multisig wallet

USAGE:
   lotus msig create [command options] [address1 address2 ...]

OPTIONS:
   --required value  number of required approvals (uses number of signers provided if omitted) (default: 0)
   --value value     initial funds to give to multisig (default: "0")
   --duration value  length of the period over which funds unlock (default: "0")
   --from value      account to send the create message from
   --help, -h        show help
```

### lotus msig inspect
```
NAME:
   lotus msig inspect - Inspect a multisig wallet

USAGE:
   lotus msig inspect [command options] [address]

OPTIONS:
   --vesting        Include vesting details (default: false)
   --decode-params  Decode parameters of transaction proposals (default: false)
   --help, -h       show help
```

### lotus msig propose
```
NAME:
   lotus msig propose - Propose a multisig transaction

USAGE:
   lotus msig propose [command options] [multisigAddress destinationAddress value <methodId methodParams> (optional)]

OPTIONS:
   --from value  account to send the propose message from
   --help, -h    show help
```

### lotus msig propose-remove
```
NAME:
   lotus msig propose-remove - Propose to remove a signer

USAGE:
   lotus msig propose-remove [command options] [multisigAddress signer]

OPTIONS:
   --decrease-threshold  whether the number of required signers should be decreased (default: false)
   --from value          account to send the propose message from
   --help, -h            show help
```

### lotus msig approve
```
NAME:
   lotus msig approve - Approve a multisig message

USAGE:
   lotus msig approve [command options] <multisigAddress messageId> [proposerAddress destination value [methodId methodParams]]

OPTIONS:
   --from value  account to send the approve message from
   --help, -h    show help
```

### lotus msig cancel
```
NAME:
   lotus msig cancel - Cancel a multisig message

USAGE:
   lotus msig cancel [command options] <multisigAddress messageId> [destination value [methodId methodParams]]

OPTIONS:
   --from value  account to send the cancel message from
   --help, -h    show help
```

### lotus msig add-propose
```
NAME:
   lotus msig add-propose - Propose to add a signer

USAGE:
   lotus msig add-propose [command options] [multisigAddress signer]

OPTIONS:
   --increase-threshold  whether the number of required signers should be increased (default: false)
   --from value          account to send the propose message from
   --help, -h            show help
```

### lotus msig add-approve
```
NAME:
   lotus msig add-approve - Approve a message to add a signer

USAGE:
   lotus msig add-approve [command options] [multisigAddress proposerAddress txId newAddress increaseThreshold]

OPTIONS:
   --from value  account to send the approve message from
   --help, -h    show help
```

### lotus msig add-cancel
```
NAME:
   lotus msig add-cancel - Cancel a message to add a signer

USAGE:
   lotus msig add-cancel [command options] [multisigAddress txId newAddress increaseThreshold]

OPTIONS:
   --from value  account to send the approve message from
   --help, -h    show help
```

### lotus msig swap-propose
```
NAME:
   lotus msig swap-propose - Propose to swap signers

USAGE:
   lotus msig swap-propose [command options] [multisigAddress oldAddress newAddress]

OPTIONS:
   --from value  account to send the approve message from
   --help, -h    show help
```

### lotus msig swap-approve
```
NAME:
   lotus msig swap-approve - Approve a message to swap signers

USAGE:
   lotus msig swap-approve [command options] [multisigAddress proposerAddress txId oldAddress newAddress]

OPTIONS:
   --from value  account to send the approve message from
   --help, -h    show help
```

### lotus msig swap-cancel
```
NAME:
   lotus msig swap-cancel - Cancel a message to swap signers

USAGE:
   lotus msig swap-cancel [command options] [multisigAddress txId oldAddress newAddress]

OPTIONS:
   --from value  account to send the approve message from
   --help, -h    show help
```

### lotus msig lock-propose
```
NAME:
   lotus msig lock-propose - Propose to lock up some balance

USAGE:
   lotus msig lock-propose [command options] [multisigAddress startEpoch unlockDuration amount]

OPTIONS:
   --from value  account to send the propose message from
   --help, -h    show help
```

### lotus msig lock-approve
```
NAME:
   lotus msig lock-approve - Approve a message to lock up some balance

USAGE:
   lotus msig lock-approve [command options] [multisigAddress proposerAddress txId startEpoch unlockDuration amount]

OPTIONS:
   --from value  account to send the approve message from
   --help, -h    show help
```

### lotus msig lock-cancel
```
NAME:
   lotus msig lock-cancel - Cancel a message to lock up some balance

USAGE:
   lotus msig lock-cancel [command options] [multisigAddress txId startEpoch unlockDuration amount]

OPTIONS:
   --from value  account to send the cancel message from
   --help, -h    show help
```

### lotus msig vested
```
NAME:
   lotus msig vested - Gets the amount vested in an msig between two epochs

USAGE:
   lotus msig vested [command options] [multisigAddress]

OPTIONS:
   --start-epoch value  start epoch to measure vesting from (default: 0)
   --end-epoch value    end epoch to stop measure vesting at (default: -1)
   --help, -h           show help
```

### lotus msig propose-threshold
```
NAME:
   lotus msig propose-threshold - Propose setting a different signing threshold on the account

USAGE:
   lotus msig propose-threshold [command options] <multisigAddress newM>

OPTIONS:
   --from value  account to send the proposal from
   --help, -h    show help
```

## lotus filplus
```
NAME:
   lotus filplus - Interact with the verified registry actor used by Filplus

USAGE:
   lotus filplus command [command options] [arguments...]

COMMANDS:
   grant-datacap                  give allowance to the specified verified client address
   list-notaries                  list all notaries
   list-clients                   list all verified clients
   check-client-datacap           check verified client remaining bytes
   check-notary-datacap           check a notary's remaining bytes
   sign-remove-data-cap-proposal  allows a notary to sign a Remove Data Cap Proposal
   list-allocations               List allocations made by client
   list-claims                    List claims made by provider
   remove-expired-allocations     remove expired allocations (if no allocations are specified all eligible allocations are removed)
   remove-expired-claims          remove expired claims (if no claims are specified all eligible claims are removed)
   help, h                        Shows a list of commands or help for one command

OPTIONS:
   --help, -h  show help
```

### lotus filplus grant-datacap
```
NAME:
   lotus filplus grant-datacap - give allowance to the specified verified client address

USAGE:
   lotus filplus grant-datacap [command options] [clientAddress datacap]

OPTIONS:
   --from value  specify your notary address to send the message from
   --help, -h    show help
```

### lotus filplus list-notaries
```
NAME:
   lotus filplus list-notaries - list all notaries

USAGE:
   lotus filplus list-notaries [command options] [arguments...]

OPTIONS:
   --help, -h  show help
```

### lotus filplus list-clients
```
NAME:
   lotus filplus list-clients - list all verified clients

USAGE:
   lotus filplus list-clients [command options] [arguments...]

OPTIONS:
   --help, -h  show help
```

### lotus filplus check-client-datacap
```
NAME:
   lotus filplus check-client-datacap - check verified client remaining bytes

USAGE:
   lotus filplus check-client-datacap [command options] clientAddress

OPTIONS:
   --help, -h  show help
```

### lotus filplus check-notary-datacap
```
NAME:
   lotus filplus check-notary-datacap - check a notary's remaining bytes

USAGE:
   lotus filplus check-notary-datacap [command options] notaryAddress

OPTIONS:
   --help, -h  show help
```

### lotus filplus sign-remove-data-cap-proposal
```
NAME:
   lotus filplus sign-remove-data-cap-proposal - allows a notary to sign a Remove Data Cap Proposal

USAGE:
   lotus filplus sign-remove-data-cap-proposal [command options] [verifierAddress clientAddress allowanceToRemove]

OPTIONS:
   --id value  specify the RemoveDataCapProposal ID (will look up on chain if unspecified) (default: 0)
   --help, -h  show help
```

### lotus filplus list-allocations
```
NAME:
   lotus filplus list-allocations - List allocations made by client

USAGE:
   lotus filplus list-allocations [command options] clientAddress

OPTIONS:
   --expired   list only expired allocations (default: false)
   --help, -h  show help
```

### lotus filplus list-claims
```
NAME:
   lotus filplus list-claims - List claims made by provider

USAGE:
   lotus filplus list-claims [command options] providerAddress

OPTIONS:
   --expired   list only expired claims (default: false)
   --help, -h  show help
```

### lotus filplus remove-expired-allocations
```
NAME:
   lotus filplus remove-expired-allocations - remove expired allocations (if no allocations are specified all eligible allocations are removed)

USAGE:
   lotus filplus remove-expired-allocations [command options] clientAddress Optional[...allocationId]

OPTIONS:
   --from value  optionally specify the account to send the message from
   --help, -h    show help
```

### lotus filplus remove-expired-claims
```
NAME:
   lotus filplus remove-expired-claims - remove expired claims (if no claims are specified all eligible claims are removed)

USAGE:
   lotus filplus remove-expired-claims [command options] providerAddress Optional[...claimId]

OPTIONS:
   --from value  optionally specify the account to send the message from
   --help, -h    show help
```

## lotus paych
```
NAME:
   lotus paych - Manage payment channels

USAGE:
   lotus paych command [command options] [arguments...]

COMMANDS:
   add-funds          Add funds to the payment channel between fromAddress and toAddress. Creates the payment channel if it doesn't already exist.
   list               List all locally registered payment channels
   voucher            Interact with payment channel vouchers
   settle             Settle a payment channel
   status             Show the status of an outbound payment channel
   status-by-from-to  Show the status of an active outbound payment channel by from/to addresses
   collect            Collect funds for a payment channel
   help, h            Shows a list of commands or help for one command

OPTIONS:
   --help, -h  show help
```

### lotus paych add-funds
```
NAME:
   lotus paych add-funds - Add funds to the payment channel between fromAddress and toAddress. Creates the payment channel if it doesn't already exist.

USAGE:
   lotus paych add-funds [command options] [fromAddress toAddress amount]

OPTIONS:
   --restart-retrievals  restart stalled retrieval deals on this payment channel (default: true)
   --reserve             mark funds as reserved (default: false)
   --help, -h            show help
```

### lotus paych list
```
NAME:
   lotus paych list - List all locally registered payment channels

USAGE:
   lotus paych list [command options] [arguments...]

OPTIONS:
   --help, -h  show help
```

### lotus paych voucher
```
NAME:
   lotus paych voucher - Interact with payment channel vouchers

USAGE:
   lotus paych voucher command [command options] [arguments...]

COMMANDS:
   create          Create a signed payment channel voucher
   check           Check validity of payment channel voucher
   add             Add payment channel voucher to local datastore
   list            List stored vouchers for a given payment channel
   best-spendable  Print vouchers with highest value that is currently spendable for each lane
   submit          Submit voucher to chain to update payment channel state
   help, h         Shows a list of commands or help for one command

OPTIONS:
   --help, -h  show help
```

#### lotus paych voucher create
```
NAME:
   lotus paych voucher create - Create a signed payment channel voucher

USAGE:
   lotus paych voucher create [command options] [channelAddress amount]

OPTIONS:
   --lane value  specify payment channel lane to use (default: 0)
   --help, -h    show help
```

#### lotus paych voucher check
```
NAME:
   lotus paych voucher check - Check validity of payment channel voucher

USAGE:
   lotus paych voucher check [command options] [channelAddress voucher]

OPTIONS:
   --help, -h  show help
```

#### lotus paych voucher add
```
NAME:
   lotus paych voucher add - Add payment channel voucher to local datastore

USAGE:
   lotus paych voucher add [command options] [channelAddress voucher]

OPTIONS:
   --help, -h  show help
```

#### lotus paych voucher list
```
NAME:
   lotus paych voucher list - List stored vouchers for a given payment channel

USAGE:
   lotus paych voucher list [command options] [channelAddress]

OPTIONS:
   --export    Print voucher as serialized string (default: false)
   --help, -h  show help
```

#### lotus paych voucher best-spendable
```
NAME:
   lotus paych voucher best-spendable - Print vouchers with highest value that is currently spendable for each lane

USAGE:
   lotus paych voucher best-spendable [command options] [channelAddress]

OPTIONS:
   --export    Print voucher as serialized string (default: false)
   --help, -h  show help
```

#### lotus paych voucher submit
```
NAME:
   lotus paych voucher submit - Submit voucher to chain to update payment channel state

USAGE:
   lotus paych voucher submit [command options] [channelAddress voucher]

OPTIONS:
   --help, -h  show help
```

### lotus paych settle
```
NAME:
   lotus paych settle - Settle a payment channel

USAGE:
   lotus paych settle [command options] [channelAddress]

OPTIONS:
   --help, -h  show help
```

### lotus paych status
```
NAME:
   lotus paych status - Show the status of an outbound payment channel

USAGE:
   lotus paych status [command options] [channelAddress]

OPTIONS:
   --help, -h  show help
```

### lotus paych status-by-from-to
```
NAME:
   lotus paych status-by-from-to - Show the status of an active outbound payment channel by from/to addresses

USAGE:
   lotus paych status-by-from-to [command options] [fromAddress toAddress]

OPTIONS:
   --help, -h  show help
```

### lotus paych collect
```
NAME:
   lotus paych collect - Collect funds for a payment channel

USAGE:
   lotus paych collect [command options] [channelAddress]

OPTIONS:
   --help, -h  show help
```

## lotus auth
```
NAME:
   lotus auth - Manage RPC permissions

USAGE:
   lotus auth command [command options] [arguments...]

COMMANDS:
   create-token  Create token
   api-info      Get token with API info required to connect to this node
   help, h       Shows a list of commands or help for one command

OPTIONS:
   --help, -h  show help
```

### lotus auth create-token
```
NAME:
   lotus auth create-token - Create token

USAGE:
   lotus auth create-token [command options] [arguments...]

OPTIONS:
   --perm value  permission to assign to the token, one of: read, write, sign, admin
   --help, -h    show help
```

### lotus auth api-info
```
NAME:
   lotus auth api-info - Get token with API info required to connect to this node

USAGE:
   lotus auth api-info [command options] [arguments...]

OPTIONS:
   --perm value  permission to assign to the token, one of: read, write, sign, admin
   --help, -h    show help
```

## lotus mpool
```
NAME:
   lotus mpool - Manage message pool

USAGE:
   lotus mpool command [command options] [arguments...]

COMMANDS:
   pending   Get pending messages
   sub       Subscribe to mpool changes
   stat      print mempool stats
   replace   replace a message in the mempool
   find      find a message in the mempool
   config    get or set current mpool configuration
   gas-perf  Check gas performance of messages in mempool
   manage    
   help, h   Shows a list of commands or help for one command

OPTIONS:
   --help, -h  show help
```

### lotus mpool pending
```
NAME:
   lotus mpool pending - Get pending messages

USAGE:
   lotus mpool pending [command options] [arguments...]

OPTIONS:
   --local       print pending messages for addresses in local wallet only (default: false)
   --cids        only print cids of messages in output (default: false)
   --to value    return messages to a given address
   --from value  return messages from a given address
   --help, -h    show help
```

### lotus mpool sub
```
NAME:
   lotus mpool sub - Subscribe to mpool changes

USAGE:
   lotus mpool sub [command options] [arguments...]

OPTIONS:
   --help, -h  show help
```

### lotus mpool stat
```
NAME:
   lotus mpool stat - print mempool stats

USAGE:
   lotus mpool stat [command options] [arguments...]

OPTIONS:
   --local                   print stats for addresses in local wallet only (default: false)
   --basefee-lookback value  number of blocks to look back for minimum basefee (default: 60)
   --help, -h                show help
```

### lotus mpool replace
```
NAME:
   lotus mpool replace - replace a message in the mempool

USAGE:
   lotus mpool replace [command options] <from> <nonce> | <message-cid>

OPTIONS:
   --gas-feecap value   gas feecap for new message (burn and pay to miner, attoFIL/GasUnit)
   --gas-premium value  gas price for new message (pay to miner, attoFIL/GasUnit)
   --gas-limit value    gas limit for new message (GasUnit) (default: 0)
   --auto               automatically reprice the specified message (default: false)
   --fee-limit max-fee  Spend up to X FIL for this message in units of FIL. Previously when flag was max-fee units were in attoFIL. Applicable for auto mode
   --help, -h           show help
```

### lotus mpool find
```
NAME:
   lotus mpool find - find a message in the mempool

USAGE:
   lotus mpool find [command options] [arguments...]

OPTIONS:
   --from value    search for messages with given 'from' address
   --to value      search for messages with given 'to' address
   --method value  search for messages with given method (default: 0)
   --help, -h      show help
```

### lotus mpool config
```
NAME:
   lotus mpool config - get or set current mpool configuration

USAGE:
   lotus mpool config [command options] [new-config]

OPTIONS:
   --help, -h  show help
```

### lotus mpool gas-perf
```
NAME:
   lotus mpool gas-perf - Check gas performance of messages in mempool

USAGE:
   lotus mpool gas-perf [command options] [arguments...]

OPTIONS:
   --all       print gas performance for all mempool messages (default only prints for local) (default: false)
   --help, -h  show help
```

### lotus mpool manage
```
NAME:
   lotus mpool manage

USAGE:
   lotus mpool manage [command options] [arguments...]

OPTIONS:
   --help, -h  show help
```

## lotus state
```
NAME:
   lotus state - Interact with and query filecoin chain state

USAGE:
   lotus state command [command options] [arguments...]

COMMANDS:
   power                       Query network or miner power
   sectors                     Query the sector set of a miner
   active-sectors              Query the active sector set of a miner
   list-actors                 list all actors in the network
   list-miners                 list all miners in the network
   circulating-supply          Get the exact current circulating supply of Filecoin
   sector, sector-info         Get miner sector info
   get-actor                   Print actor information
   lookup                      Find corresponding ID address
   replay                      Replay a particular message
   sector-size                 Look up miners sector size
   read-state                  View a json representation of an actors state
   list-messages               list messages on chain matching given criteria
   compute-state               Perform state computations
   call                        Invoke a method on an actor locally
   get-deal                    View on-chain deal info
   wait-msg, wait-message      Wait for a message to appear on chain
   search-msg, search-message  Search to see whether a message has appeared on chain
   miner-info                  Retrieve miner information
   market                      Inspect the storage market actor
   exec-trace                  Get the execution trace of a given message
   network-version             Returns the network version
   miner-proving-deadline      Retrieve information about a given miner's proving deadline
   actor-cids                  Returns the built-in actor bundle manifest ID & system actor cids
   help, h                     Shows a list of commands or help for one command

OPTIONS:
   --tipset value  specify tipset to call method on (pass comma separated array of cids)
   --help, -h      show help
```

### lotus state power
```
NAME:
   lotus state power - Query network or miner power

USAGE:
   lotus state power [command options] [<minerAddress> (optional)]

OPTIONS:
   --help, -h  show help
```

### lotus state sectors
```
NAME:
   lotus state sectors - Query the sector set of a miner

USAGE:
   lotus state sectors [command options] [minerAddress]

OPTIONS:
   --help, -h  show help
```

### lotus state active-sectors
```
NAME:
   lotus state active-sectors - Query the active sector set of a miner

USAGE:
   lotus state active-sectors [command options] [minerAddress]

OPTIONS:
   --help, -h  show help
```

### lotus state list-actors
```
NAME:
   lotus state list-actors - list all actors in the network

USAGE:
   lotus state list-actors [command options] [arguments...]

OPTIONS:
   --help, -h  show help
```

### lotus state list-miners
```
NAME:
   lotus state list-miners - list all miners in the network

USAGE:
   lotus state list-miners [command options] [arguments...]

OPTIONS:
   --sort-by value  criteria to sort miners by (none, num-deals)
   --help, -h       show help
```

### lotus state circulating-supply
```
NAME:
   lotus state circulating-supply - Get the exact current circulating supply of Filecoin

USAGE:
   lotus state circulating-supply [command options] [arguments...]

OPTIONS:
   --vm-supply  calculates the approximation of the circulating supply used internally by the VM (instead of the exact amount) (default: false)
   --help, -h   show help
```

#### lotus state sector, sector-info
```
```

### lotus state get-actor
```
NAME:
   lotus state get-actor - Print actor information

USAGE:
   lotus state get-actor [command options] [actorAddress]

OPTIONS:
   --help, -h  show help
```

### lotus state lookup
```
NAME:
   lotus state lookup - Find corresponding ID address

USAGE:
   lotus state lookup [command options] [address]

OPTIONS:
   --reverse, -r  Perform reverse lookup (default: false)
   --help, -h     show help
```

### lotus state replay
```
NAME:
   lotus state replay - Replay a particular message

USAGE:
   lotus state replay [command options] <messageCid>

OPTIONS:
   --show-trace    print out full execution trace for given message (default: false)
   --detailed-gas  print out detailed gas costs for given message (default: false)
   --help, -h      show help
```

### lotus state sector-size
```
NAME:
   lotus state sector-size - Look up miners sector size

USAGE:
   lotus state sector-size [command options] [minerAddress]

OPTIONS:
   --help, -h  show help
```

### lotus state read-state
```
NAME:
   lotus state read-state - View a json representation of an actors state

USAGE:
   lotus state read-state [command options] [actorAddress]

OPTIONS:
   --help, -h  show help
```

### lotus state list-messages
```
NAME:
   lotus state list-messages - list messages on chain matching given criteria

USAGE:
   lotus state list-messages [command options] [arguments...]

OPTIONS:
   --to value        return messages to a given address
   --from value      return messages from a given address
   --toheight value  don't look before given block height (default: 0)
   --cids            print message CIDs instead of messages (default: false)
   --help, -h        show help
```

### lotus state compute-state
```
NAME:
   lotus state compute-state - Perform state computations

USAGE:
   lotus state compute-state [command options] [arguments...]

OPTIONS:
   --vm-height value             set the height that the vm will see (default: 0)
   --apply-mpool-messages        apply messages from the mempool to the computed state (default: false)
   --show-trace                  print out full execution trace for given tipset (default: false)
   --html                        generate html report (default: false)
   --json                        generate json output (default: false)
   --compute-state-output value  a json file containing pre-existing compute-state output, to generate html reports without rerunning state changes
   --no-timing                   don't show timing information in html traces (default: false)
   --help, -h                    show help
```

### lotus state call
```
NAME:
   lotus state call - Invoke a method on an actor locally

USAGE:
   lotus state call [command options] [toAddress methodId params (optional)]

OPTIONS:
   --from value      (default: "f00")
   --value value     specify value field for invocation (default: "0")
   --ret value       specify how to parse output (raw, decoded, base64, hex) (default: "decoded")
   --encoding value  specify params encoding to parse (base64, hex) (default: "base64")
   --help, -h        show help
```

### lotus state get-deal
```
NAME:
   lotus state get-deal - View on-chain deal info

USAGE:
   lotus state get-deal [command options] [dealId]

OPTIONS:
   --help, -h  show help
```

#### lotus state wait-msg, wait-message
```
```

#### lotus state search-msg, search-message
```
```

### lotus state miner-info
```
NAME:
   lotus state miner-info - Retrieve miner information

USAGE:
   lotus state miner-info [command options] [minerAddress]

OPTIONS:
   --help, -h  show help
```

### lotus state market
```
NAME:
   lotus state market - Inspect the storage market actor

USAGE:
   lotus state market command [command options] [arguments...]

COMMANDS:
   balance  Get the market balance (locked and escrowed) for a given account
   help, h  Shows a list of commands or help for one command

OPTIONS:
   --help, -h  show help
```

#### lotus state market balance
```
NAME:
   lotus state market balance - Get the market balance (locked and escrowed) for a given account

USAGE:
   lotus state market balance [command options] [address]

OPTIONS:
   --help, -h  show help
```

### lotus state exec-trace
```
NAME:
   lotus state exec-trace - Get the execution trace of a given message

USAGE:
   lotus state exec-trace [command options] <messageCid>

OPTIONS:
   --help, -h  show help
```

### lotus state network-version
```
NAME:
   lotus state network-version - Returns the network version

USAGE:
   lotus state network-version [command options] [arguments...]

OPTIONS:
   --help, -h  show help
```

### lotus state miner-proving-deadline
```
NAME:
   lotus state miner-proving-deadline - Retrieve information about a given miner's proving deadline

USAGE:
   lotus state miner-proving-deadline [command options] [minerAddress]

OPTIONS:
   --help, -h  show help
```

### lotus state actor-cids
```
NAME:
   lotus state actor-cids - Returns the built-in actor bundle manifest ID & system actor cids

USAGE:
   lotus state actor-cids [command options] [arguments...]

OPTIONS:
   --network-version value  specify network version (default: 0)
   --help, -h               show help
```

## lotus chain
```
NAME:
   lotus chain - Interact with filecoin blockchain

USAGE:
   lotus chain command [command options] [arguments...]

COMMANDS:
   head                              Print chain head
   get-block, getblock               Get a block and print its details
   read-obj                          Read the raw bytes of an object
   delete-obj                        Delete an object from the chain blockstore
   stat-obj                          Collect size and ipld link counts for objs
   getmessage, get-message, get-msg  Get and print a message by its cid
   sethead, set-head                 manually set the local nodes head tipset (Caution: normally only used for recovery)
   list, love                        View a segment of the chain
   get                               Get chain DAG node by path
   bisect                            bisect chain for an event
   export                            export chain to a car file
   export-range                      export chain to a car file
   slash-consensus                   Report consensus fault
   gas-price                         Estimate gas prices
   inspect-usage                     Inspect block space usage of a given tipset
   decode                            decode various types
   encode                            encode various types
   disputer                          interact with the window post disputer
   prune                             splitstore gc
   help, h                           Shows a list of commands or help for one command

OPTIONS:
   --help, -h  show help
```

### lotus chain head
```
NAME:
   lotus chain head - Print chain head

USAGE:
   lotus chain head [command options] [arguments...]

OPTIONS:
   --help, -h  show help
```

#### lotus chain get-block, getblock
```
```

### lotus chain read-obj
```
NAME:
   lotus chain read-obj - Read the raw bytes of an object

USAGE:
   lotus chain read-obj [command options] [objectCid]

OPTIONS:
   --help, -h  show help
```

### lotus chain delete-obj
```
NAME:
   lotus chain delete-obj - Delete an object from the chain blockstore

USAGE:
   lotus chain delete-obj [command options] [objectCid]

DESCRIPTION:
   WARNING: Removing wrong objects from the chain blockstore may lead to sync issues

OPTIONS:
   --really-do-it  (default: false)
   --help, -h      show help
```

### lotus chain stat-obj
```
NAME:
   lotus chain stat-obj - Collect size and ipld link counts for objs

USAGE:
   lotus chain stat-obj [command options] [cid]

DESCRIPTION:
   Collect object size and ipld link count for an object.

      When a base is provided it will be walked first, and all links visisted
      will be ignored when the passed in object is walked.


OPTIONS:
   --base value  ignore links found in this obj
   --help, -h    show help
```

##### lotus chain getmessage, get-message, get-msg
```
```

#### lotus chain sethead, set-head
```
```

#### lotus chain list, love
```
```

### lotus chain get
```
NAME:
   lotus chain get - Get chain DAG node by path

USAGE:
   lotus chain get [command options] [path]

DESCRIPTION:
   Get ipld node under a specified path:

      lotus chain get /ipfs/[cid]/some/path

      Path prefixes:
      - /ipfs/[cid], /ipld/[cid] - traverse IPLD path
      - /pstate - traverse from head.ParentStateRoot

      Note:
      You can use special path elements to traverse through some data structures:
      - /ipfs/[cid]/@H:elem - get 'elem' from hamt
      - /ipfs/[cid]/@Hi:123 - get varint elem 123 from hamt
      - /ipfs/[cid]/@Hu:123 - get uvarint elem 123 from hamt
      - /ipfs/[cid]/@Ha:t01 - get element under Addr(t01).Bytes
      - /ipfs/[cid]/@A:10   - get 10th amt element
      - .../@Ha:t01/@state  - get pretty map-based actor state

      List of --as-type types:
      - raw
      - block
      - message
      - smessage, signedmessage
      - actor
      - amt
      - hamt-epoch
      - hamt-address
      - cronevent
      - account-state


OPTIONS:
   --as-type value  specify type to interpret output as
   --verbose        (default: false)
   --tipset value   specify tipset for /pstate (pass comma separated array of cids)
   --help, -h       show help
```

### lotus chain bisect
```
NAME:
   lotus chain bisect - bisect chain for an event

USAGE:
   lotus chain bisect [command options] [minHeight maxHeight path shellCommand <shellCommandArgs (if any)>]

DESCRIPTION:
   Bisect the chain state tree:

      lotus chain bisect [min height] [max height] '1/2/3/state/path' 'shell command' 'args'

      Returns the first tipset in which condition is true
                     v
      [start] FFFFFFFTTT [end]

      Example: find height at which deal ID 100 000 appeared
       - lotus chain bisect 1 32000 '@Ha:t03/1' jq -e '.[2] > 100000'

      For special path elements see 'chain get' help


OPTIONS:
   --help, -h  show help
```

### lotus chain export
```
NAME:
   lotus chain export - export chain to a car file

USAGE:
   lotus chain export [command options] [outputPath]

OPTIONS:
   --tipset value             specify tipset to start the export from (default: "@head")
   --recent-stateroots value  specify the number of recent state roots to include in the export (default: 0)
   --skip-old-msgs            (default: false)
   --help, -h                 show help
```

### lotus chain export-range
```
NAME:
   lotus chain export-range - export chain to a car file

USAGE:
   lotus chain export-range [command options] [arguments...]

OPTIONS:
   --head value          specify tipset to start the export from (higher epoch) (default: "@head")
   --tail value          specify tipset to end the export at (lower epoch) (default: "@tail")
   --messages            specify if messages should be include (default: false)
   --receipts            specify if receipts should be include (default: false)
   --stateroots          specify if stateroots should be include (default: false)
   --workers value       specify the number of workers (default: 1)
   --write-buffer value  specify write buffer size (default: 1048576)
   --help, -h            show help
```

### lotus chain slash-consensus
```
NAME:
   lotus chain slash-consensus - Report consensus fault

USAGE:
   lotus chain slash-consensus [command options] [blockCid1 blockCid2]

OPTIONS:
   --from value   optionally specify the account to report consensus from
   --extra value  Extra block cid
   --help, -h     show help
```

### lotus chain gas-price
```
NAME:
   lotus chain gas-price - Estimate gas prices

USAGE:
   lotus chain gas-price [command options] [arguments...]

OPTIONS:
   --help, -h  show help
```

### lotus chain inspect-usage
```
NAME:
   lotus chain inspect-usage - Inspect block space usage of a given tipset

USAGE:
   lotus chain inspect-usage [command options] [arguments...]

OPTIONS:
   --tipset value       specify tipset to view block space usage of (default: "@head")
   --length value       length of chain to inspect block space usage for (default: 1)
   --num-results value  number of results to print per category (default: 10)
   --help, -h           show help
```

### lotus chain decode
```
NAME:
   lotus chain decode - decode various types

USAGE:
   lotus chain decode command [command options] [arguments...]

COMMANDS:
   params   Decode message params
   help, h  Shows a list of commands or help for one command

OPTIONS:
   --help, -h  show help
```

#### lotus chain decode params
```
NAME:
   lotus chain decode params - Decode message params

USAGE:
   lotus chain decode params [command options] [toAddr method params]

OPTIONS:
   --tipset value    
   --encoding value  specify input encoding to parse (default: "base64")
   --help, -h        show help
```

### lotus chain encode
```
NAME:
   lotus chain encode - encode various types

USAGE:
   lotus chain encode command [command options] [arguments...]

COMMANDS:
   params   Encodes the given JSON params
   help, h  Shows a list of commands or help for one command

OPTIONS:
   --help, -h  show help
```

#### lotus chain encode params
```
NAME:
   lotus chain encode params - Encodes the given JSON params

USAGE:
   lotus chain encode params [command options] [dest method params]

OPTIONS:
   --tipset value    
   --encoding value  specify input encoding to parse (default: "base64")
   --to-code         interpret dest as code CID instead of as address (default: false)
   --help, -h        show help
```

### lotus chain disputer
```
NAME:
   lotus chain disputer - interact with the window post disputer

USAGE:
   lotus chain disputer command [command options] [arguments...]

COMMANDS:
   start    Start the window post disputer
   dispute  Send a specific DisputeWindowedPoSt message
   help, h  Shows a list of commands or help for one command

OPTIONS:
   --max-fee value  Spend up to X FIL per DisputeWindowedPoSt message
   --from value     optionally specify the account to send messages from
   --help, -h       show help
```

#### lotus chain disputer start
```
NAME:
   lotus chain disputer start - Start the window post disputer

USAGE:
   lotus chain disputer start [command options] [minerAddress]

OPTIONS:
   --start-epoch value  only start disputing PoSts after this epoch  (default: 0)
   --help, -h           show help
```

#### lotus chain disputer dispute
```
NAME:
   lotus chain disputer dispute - Send a specific DisputeWindowedPoSt message

USAGE:
   lotus chain disputer dispute [command options] [minerAddress index postIndex]

OPTIONS:
   --help, -h  show help
```

### lotus chain prune
```
NAME:
   lotus chain prune - splitstore gc

USAGE:
   lotus chain prune command [command options] [arguments...]

COMMANDS:
   compact-cold  force splitstore compaction on cold store state and run gc
   hot           run online (badger vlog) garbage collection on hotstore
   hot-moving    run moving gc on hotstore
   help, h       Shows a list of commands or help for one command

OPTIONS:
   --help, -h  show help
```

#### lotus chain prune compact-cold
```
NAME:
   lotus chain prune compact-cold - force splitstore compaction on cold store state and run gc

USAGE:
   lotus chain prune compact-cold [command options] [arguments...]

OPTIONS:
   --online-gc        use online gc for garbage collecting the coldstore (default: false)
   --moving-gc        use moving gc for garbage collecting the coldstore (default: false)
   --retention value  specify state retention policy (default: -1)
   --help, -h         show help
```

#### lotus chain prune hot
```
NAME:
   lotus chain prune hot - run online (badger vlog) garbage collection on hotstore

USAGE:
   lotus chain prune hot [command options] [arguments...]

OPTIONS:
   --threshold value  Threshold of vlog garbage for gc (default: 0.01)
   --periodic         Run periodic gc over multiple vlogs. Otherwise run gc once (default: false)
   --help, -h         show help
```

#### lotus chain prune hot-moving
```
NAME:
   lotus chain prune hot-moving - run moving gc on hotstore

USAGE:
   lotus chain prune hot-moving [command options] [arguments...]

OPTIONS:
   --help, -h  show help
```

## lotus log
```
NAME:
   lotus log - Manage logging

USAGE:
   lotus log command [command options] [arguments...]

COMMANDS:
   list       List log systems
   set-level  Set log level
   alerts     Get alert states
   help, h    Shows a list of commands or help for one command

OPTIONS:
   --help, -h  show help
```

### lotus log list
```
NAME:
   lotus log list - List log systems

USAGE:
   lotus log list [command options] [arguments...]

OPTIONS:
   --help, -h  show help
```

### lotus log set-level
```
NAME:
   lotus log set-level - Set log level

USAGE:
   lotus log set-level [command options] [level]

DESCRIPTION:
   Set the log level for logging systems:

      The system flag can be specified multiple times.

      eg) log set-level --system chain --system chainxchg debug

      Available Levels:
      debug
      info
      warn
      error

      Environment Variables:
      GOLOG_LOG_LEVEL - Default log level for all log systems
      GOLOG_LOG_FMT   - Change output log format (json, nocolor)
      GOLOG_FILE      - Write logs to file
      GOLOG_OUTPUT    - Specify whether to output to file, stderr, stdout or a combination, i.e. file+stderr


OPTIONS:
   --system value [ --system value ]  limit to log system
   --help, -h                         show help
```

### lotus log alerts
```
NAME:
   lotus log alerts - Get alert states

USAGE:
   lotus log alerts [command options] [arguments...]

OPTIONS:
   --all       get all (active and inactive) alerts (default: false)
   --help, -h  show help
```

## lotus wait-api
```
NAME:
   lotus wait-api - Wait for lotus api to come online

USAGE:
   lotus wait-api [command options] [arguments...]

CATEGORY:
   DEVELOPER

OPTIONS:
   --timeout value  duration to wait till fail (default: 30s)
   --help, -h       show help
```

## lotus fetch-params
```
NAME:
   lotus fetch-params - Fetch proving parameters

USAGE:
   lotus fetch-params [command options] [sectorSize]

CATEGORY:
   DEVELOPER

OPTIONS:
   --help, -h  show help
```

## lotus evm
```
NAME:
   lotus evm - Commands related to the Filecoin EVM runtime

USAGE:
   lotus evm command [command options] [arguments...]

COMMANDS:
   deploy            Deploy an EVM smart contract and return its address
   invoke            Invoke an EVM smart contract using the specified CALLDATA
   stat              Print eth/filecoin addrs and code cid
   call              Simulate an eth contract call
   contract-address  Generate contract address from smart contract code
   bytecode          Write the bytecode of a smart contract to a file
   help, h           Shows a list of commands or help for one command

OPTIONS:
   --help, -h  show help
```

### lotus evm deploy
```
NAME:
   lotus evm deploy - Deploy an EVM smart contract and return its address

USAGE:
   lotus evm deploy [command options] contract

OPTIONS:
   --from value  optionally specify the account to use for sending the creation message
   --hex         use when input contract is in hex (default: false)
   --help, -h    show help
```

### lotus evm invoke
```
NAME:
   lotus evm invoke - Invoke an EVM smart contract using the specified CALLDATA

USAGE:
   lotus evm invoke [command options] address calldata

OPTIONS:
   --from value   optionally specify the account to use for sending the exec message
   --value value  optionally specify the value to be sent with the invokation message (default: 0)
   --help, -h     show help
```

### lotus evm stat
```
NAME:
   lotus evm stat - Print eth/filecoin addrs and code cid

USAGE:
   lotus evm stat [command options] address

OPTIONS:
   --help, -h  show help
```

### lotus evm call
```
NAME:
   lotus evm call - Simulate an eth contract call

USAGE:
   lotus evm call [command options] [from] [to] [params]

OPTIONS:
   --help, -h  show help
```

### lotus evm contract-address
```
NAME:
   lotus evm contract-address - Generate contract address from smart contract code

USAGE:
   lotus evm contract-address [command options] [senderEthAddr] [salt] [contractHexPath]

OPTIONS:
   --help, -h  show help
```

### lotus evm bytecode
```
NAME:
   lotus evm bytecode - Write the bytecode of a smart contract to a file

USAGE:
   lotus evm bytecode [command options] [contract-address] [file-name]

OPTIONS:
   --bin       write the bytecode as raw binary and don't hex-encode (default: false)
   --help, -h  show help
```

## lotus net
```
NAME:
   lotus net - Manage P2P Network

USAGE:
   lotus net command [command options] [arguments...]

COMMANDS:
   peers                Print peers
   ping                 Ping peers
   connect              Connect to a peer
   disconnect           Disconnect from a peer
   listen               List listen addresses
   id                   Get node identity
   find-peer, findpeer  Find the addresses of a given peerID
   scores               Print peers' pubsub scores
   reachability         Print information about reachability from the internet
   bandwidth            Print bandwidth usage information
   block                Manage network connection gating rules
   stat                 Report resource usage for a scope
   limit                Get or set resource limits for a scope
   protect              Add one or more peer IDs to the list of protected peer connections
   unprotect            Remove one or more peer IDs from the list of protected peer connections.
   list-protected       List the peer IDs with protected connection.
   help, h              Shows a list of commands or help for one command

OPTIONS:
   --help, -h  show help
```

### lotus net peers
```
NAME:
   lotus net peers - Print peers

USAGE:
   lotus net peers [command options] [arguments...]

OPTIONS:
   --agent, -a     Print agent name (default: false)
   --extended, -x  Print extended peer information in json (default: false)
   --help, -h      show help
```

### lotus net ping
```
NAME:
   lotus net ping - Ping peers

USAGE:
   lotus net ping [command options] [peerMultiaddr]

OPTIONS:
   --count value, -c value     specify the number of times it should ping (default: 10)
   --interval value, -i value  minimum time between pings (default: 1s)
   --help, -h                  show help
```

### lotus net connect
```
NAME:
   lotus net connect - Connect to a peer

USAGE:
   lotus net connect [command options] [peerMultiaddr|minerActorAddress]

OPTIONS:
   --help, -h  show help
```

### lotus net disconnect
```
NAME:
   lotus net disconnect - Disconnect from a peer

USAGE:
   lotus net disconnect [command options] [peerID]

OPTIONS:
   --help, -h  show help
```

### lotus net listen
```
NAME:
   lotus net listen - List listen addresses

USAGE:
   lotus net listen [command options] [arguments...]

OPTIONS:
   --help, -h  show help
```

### lotus net id
```
NAME:
   lotus net id - Get node identity

USAGE:
   lotus net id [command options] [arguments...]

OPTIONS:
   --help, -h  show help
```

#### lotus net find-peer, findpeer
```
```

### lotus net scores
```
NAME:
   lotus net scores - Print peers' pubsub scores

USAGE:
   lotus net scores [command options] [arguments...]

OPTIONS:
   --extended, -x  print extended peer scores in json (default: false)
   --help, -h      show help
```

### lotus net reachability
```
NAME:
   lotus net reachability - Print information about reachability from the internet

USAGE:
   lotus net reachability [command options] [arguments...]

OPTIONS:
   --help, -h  show help
```

### lotus net bandwidth
```
NAME:
   lotus net bandwidth - Print bandwidth usage information

USAGE:
   lotus net bandwidth [command options] [arguments...]

OPTIONS:
   --by-peer      list bandwidth usage by peer (default: false)
   --by-protocol  list bandwidth usage by protocol (default: false)
   --help, -h     show help
```

### lotus net block
```
NAME:
   lotus net block - Manage network connection gating rules

USAGE:
   lotus net block command [command options] [arguments...]

COMMANDS:
   add      Add connection gating rules
   remove   Remove connection gating rules
   list     list connection gating rules
   help, h  Shows a list of commands or help for one command

OPTIONS:
   --help, -h  show help
```

#### lotus net block add
```
NAME:
   lotus net block add - Add connection gating rules

USAGE:
   lotus net block add command [command options] [arguments...]

COMMANDS:
   peer     Block a peer
   ip       Block an IP address
   subnet   Block an IP subnet
   help, h  Shows a list of commands or help for one command

OPTIONS:
   --help, -h  show help
```

##### lotus net block add peer
```
NAME:
   lotus net block add peer - Block a peer

USAGE:
   lotus net block add peer [command options] <Peer> ...

OPTIONS:
   --help, -h  show help
```

##### lotus net block add ip
```
NAME:
   lotus net block add ip - Block an IP address

USAGE:
   lotus net block add ip [command options] <IP> ...

OPTIONS:
   --help, -h  show help
```

##### lotus net block add subnet
```
NAME:
   lotus net block add subnet - Block an IP subnet

USAGE:
   lotus net block add subnet [command options] <CIDR> ...

OPTIONS:
   --help, -h  show help
```

#### lotus net block remove
```
NAME:
   lotus net block remove - Remove connection gating rules

USAGE:
   lotus net block remove command [command options] [arguments...]

COMMANDS:
   peer     Unblock a peer
   ip       Unblock an IP address
   subnet   Unblock an IP subnet
   help, h  Shows a list of commands or help for one command

OPTIONS:
   --help, -h  show help
```

##### lotus net block remove peer
```
NAME:
   lotus net block remove peer - Unblock a peer

USAGE:
   lotus net block remove peer [command options] <Peer> ...

OPTIONS:
   --help, -h  show help
```

##### lotus net block remove ip
```
NAME:
   lotus net block remove ip - Unblock an IP address

USAGE:
   lotus net block remove ip [command options] <IP> ...

OPTIONS:
   --help, -h  show help
```

##### lotus net block remove subnet
```
NAME:
   lotus net block remove subnet - Unblock an IP subnet

USAGE:
   lotus net block remove subnet [command options] <CIDR> ...

OPTIONS:
   --help, -h  show help
```

#### lotus net block list
```
NAME:
   lotus net block list - list connection gating rules

USAGE:
   lotus net block list [command options] [arguments...]

OPTIONS:
   --help, -h  show help
```

### lotus net stat
```
NAME:
   lotus net stat - Report resource usage for a scope

USAGE:
   lotus net stat [command options] scope

DESCRIPTION:
   Report resource usage for a scope.

     The scope can be one of the following:
     - system        -- reports the system aggregate resource usage.
     - transient     -- reports the transient resource usage.
     - svc:<service> -- reports the resource usage of a specific service.
     - proto:<proto> -- reports the resource usage of a specific protocol.
     - peer:<peer>   -- reports the resource usage of a specific peer.
     - all           -- reports the resource usage for all currently active scopes.


OPTIONS:
   --json      (default: false)
   --help, -h  show help
```

### lotus net limit
```
NAME:
   lotus net limit - Get or set resource limits for a scope

USAGE:
   lotus net limit [command options] scope [limit]

DESCRIPTION:
   Get or set resource limits for a scope.

     The scope can be one of the following:
     - system        -- reports the system aggregate resource usage.
     - transient     -- reports the transient resource usage.
     - svc:<service> -- reports the resource usage of a specific service.
     - proto:<proto> -- reports the resource usage of a specific protocol.
     - peer:<peer>   -- reports the resource usage of a specific peer.

    The limit is json-formatted, with the same structure as the limits file.


OPTIONS:
   --set       set the limit for a scope (default: false)
   --help, -h  show help
```

### lotus net protect
```
NAME:
   lotus net protect - Add one or more peer IDs to the list of protected peer connections

USAGE:
   lotus net protect [command options] <peer-id> [<peer-id>...]

OPTIONS:
   --help, -h  show help
```

### lotus net unprotect
```
NAME:
   lotus net unprotect - Remove one or more peer IDs from the list of protected peer connections.

USAGE:
   lotus net unprotect [command options] <peer-id> [<peer-id>...]

OPTIONS:
   --help, -h  show help
```

### lotus net list-protected
```
NAME:
   lotus net list-protected - List the peer IDs with protected connection.

USAGE:
   lotus net list-protected [command options] [arguments...]

OPTIONS:
   --help, -h  show help
```

## lotus sync
```
NAME:
   lotus sync - Inspect or interact with the chain syncer

USAGE:
   lotus sync command [command options] [arguments...]

COMMANDS:
   status      check sync status
   wait        Wait for sync to be complete
   mark-bad    Mark the given block as bad, will prevent syncing to a chain that contains it
   unmark-bad  Unmark the given block as bad, makes it possible to sync to a chain containing it
   check-bad   check if the given block was marked bad, and for what reason
   checkpoint  mark a certain tipset as checkpointed; the node will never fork away from this tipset
   help, h     Shows a list of commands or help for one command

OPTIONS:
   --help, -h  show help
```

### lotus sync status
```
NAME:
   lotus sync status - check sync status

USAGE:
   lotus sync status [command options] [arguments...]

OPTIONS:
   --help, -h  show help
```

### lotus sync wait
```
NAME:
   lotus sync wait - Wait for sync to be complete

USAGE:
   lotus sync wait [command options] [arguments...]

OPTIONS:
   --watch     don't exit after node is synced (default: false)
   --help, -h  show help
```

### lotus sync mark-bad
```
NAME:
   lotus sync mark-bad - Mark the given block as bad, will prevent syncing to a chain that contains it

USAGE:
   lotus sync mark-bad [command options] [blockCid]

OPTIONS:
   --help, -h  show help
```

### lotus sync unmark-bad
```
NAME:
   lotus sync unmark-bad - Unmark the given block as bad, makes it possible to sync to a chain containing it

USAGE:
   lotus sync unmark-bad [command options] [blockCid]

OPTIONS:
   --all       drop the entire bad block cache (default: false)
   --help, -h  show help
```

### lotus sync check-bad
```
NAME:
   lotus sync check-bad - check if the given block was marked bad, and for what reason

USAGE:
   lotus sync check-bad [command options] [blockCid]

OPTIONS:
   --help, -h  show help
```

### lotus sync checkpoint
```
NAME:
   lotus sync checkpoint - mark a certain tipset as checkpointed; the node will never fork away from this tipset

USAGE:
   lotus sync checkpoint [command options] [tipsetKey]

OPTIONS:
   --epoch value  checkpoint the tipset at the given epoch (default: 0)
   --help, -h     show help
```

## lotus status
```
NAME:
   lotus status - Check node status

USAGE:
   lotus status [command options] [arguments...]

CATEGORY:
   STATUS

OPTIONS:
   --chain     include chain health status (default: false)
   --help, -h  show help
```
