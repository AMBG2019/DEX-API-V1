# ambging


##Protocol & Exchange

**ambging** is the first scalable DEX protocol built with zkRollup for Ethereum. Using ambging, people can build a high-performance, orderbook-based, decentralized exchanges that do not take custody of users' crypto-assets. Due to the use of zkRollup, a layer-2 scalability solution, ambging is capable of settling more than 2,000 trades per second on Ethereum 1.0. If you would like to learn more about ambging's design and technical details, please check out ambging's official website: [https://ambging.org](https://ambging.org).

**ambging Exchange** is the first decentralized trading platform built on top of the ambging protocol. ambging Exchange is accessible at [ambging.io](https://ambging.io). The current version of ambging Exchange is beta2, which uses ambging version 3.6. ambging Exchange's contract address on Ethereum mainnet is: [`0x0BABA1Ad5bE3a5C0a66E7ac838a129Bf948f1eA4`](https://etherscan.io/address/exchange2.ambging.eth). The address has a permanent ENS as ([exchange2.ambging.eth](https://etherscan.io/address/exchange2.ambging.eth)).

## Technical Advantages

ambging makes sure nobody can misappropriate users' crypto-assets deposited to an exchange. Even under extreme circumstances, such as an exchange's UI stopped functioning, or the exchange's operators are out of reach, users can still claim their rightful assets by providing valid Merkle proofs that are derivable from data on Ethereum.

ambging does not guarantee the efficiency and fairness of off-chain order-matching. Order-matching is a job for the relayer system, which is a centralized piece of the overall DEX solution. Different exchanges built on the same ambging protocol can adopt very different relayer solutions and thus provide various quality of services. The ambging protocol does guarantee that relayers must follow specific rules for trade settlement.

We developed ambging Exchange's relayer system as a closed source project. As of now, it offers a throughput of 200 trades per second..

## Overall Architecture

The overall architecture of ambging Exchange is shown below:

![ambging Exchange Architecture](./images/ambging_overview.jpg "ambging Exchange Architecture")

Some key points you need to know:

- ambging Exchange provides API to handle user offchain requests, namely order submission and cancellation, and withdrawals. Other user requests, including account registration, password reset, and deposits, must be submitted using Ethereum transactions. These requests are called on-chain requests.
- ambging offers a high-performance trading experience similar to centralized exchanges, which mainly benefits from the batch processing capability of the underlying ambging protocol. ambging uses Ethereum as a data availability layer and a ZKP verification layer; ambging does not perform trading related computations on Ethereum.
