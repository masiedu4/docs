---
id: http-api
title: Overview
resources:
  - url: https://github.com/cartesi/machine-emulator
    title: Off-chain implementation of the Cartesi Machine
  - url: https://github.com/cartesi/rollups-node
    title: Reference implementation of the Rollups Node
  - url: https://github.com/cartesi/rollups-contracts/tree/v1.4.0/onchain/rollups/contracts
    title: Smart Contracts for Cartesi Rollups
---

In the Cartesi architecture, the frontend and backend components of a dApp communicate through the Cartesi Rollups framework using HTTP and GraphQL APIs. 

These APIs are designed to abstract away the low-level details of Cartesi Rollups, allowing developers to focus on building their applications.

## Backend APIs

The dApp's backend runs inside the Cartesi Machine as a standard Linux application and interacts with the Cartesi Rollups framework by retrieving requests as inputs and producing corresponding outputs via HTTP endpoints.

There are two main types of requests the backend can handle:


- **Advance requests** change the dApp's state based on the input data and generate verifiable notices, vouchers, and non-verifiable reports. 

- **Inspect requests** allow reading the dApp's state without modifying it. For inspect requests, the backend sends the request directly to the Cartesi Node via an HTTP API call and receives a non-verifiable report in response.


![img](../../../static/img/v1.3/backend.jpg)



## Frontend APIs

The dApp's frontend interacts with the Cartesi Rollups framework to submit user requests and retrieve the corresponding outputs produced by the backend. Some key interactions include:

* Send inputs: The frontend sends input data to the backend through base layer smart contracts like the InputBox, using JSON-RPC transactions. Upon receiving the inputs, the backend processes them and generates outputs such as notices, vouchers, and reports.

* Query outputs: The frontend can submit queries to a Cartesi node to retrieve the notices, vouchers, and reports, as specified by the Cartesi Rollups GraphQL schema.

* Validate outputs: The frontend can submit JSON-RPC blockchain transactions to request the validation and execution of specific verifiable outputs, such as notices or vouchers, by the relevant smart contracts on the base layer.


* Inspect state: The frontend can make HTTP calls to the Cartesi node to retrieve arbitrary dApp-specific application state.

![img](../../../static/img/v1.3/frontend.jpg)
