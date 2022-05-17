---
id: overview
title: Overview of building DApps
---

Cartesi's vision is that creating a DApp should not be too different from the general development of desktop, web, and mobile applications. To that end, Cartesi provides a Blockchain OS for building decentralized logic, giving developers full flexibility to use the tools and libraries of their preference.

From a developer's point of view, a Cartesi DApp is [composed of two main parts](../cartesi-rollups/dapp-architecture):
- **Front-end**: the user facing interface, which will often provide a UI (e.g., a web application) but may also be a command line interface (e.g., a hardhat task using ethers, or a command line using python).
- **Back-end**: the verifiable logic that will run inside the Cartesi Rollups infrastructure; this will store and update the application state given user input, and will produce outputs in the form of [vouchers](../cartesi-rollups/components#vouchers) (transactions that can be carried out on layer-1) and [notices](../cartesi-rollups/components#notices) (informational)

The suggested development process for Cartesi DApps involves a [series of stages](../cartesi-rollups/dapp-life-cycle), from the design of the application up to its final deployment. Although some of those stages involve blockchain or Cartesi-specific procedures, the intention is that developers should be able to code normally using their usual mainstream development environment for 90+% of the work, and to make that possible Cartesi provides some tools and infrastructure.

In particular, during development the Cartesi Rollups infrastructure can be executed locally in two modes, as described below.

## Production Mode

In **Production Mode**, the DApp's back-end logic is packaged to run inside a [Cartesi Machine emulator](../machine/overview), as will be the case when the application is deployed. This means that any code written in compiled languages such as C++ or Rust must be _cross-compiled_ to the Cartesi Machine's RISC-V architecture. In this mode, the computation performed by the back-end is reproducible and hence verifiable, enabling a truly trustless and decentralized execution.

## Host Mode

In **Host Mode**, the back-end logic is executed natively on localhost, just as any regular application. This is made possible because the Cartesi Rollups Host Environment provides the very same APIs as the regular mode, mimicking the behavior of the actual layer-1 and layer-2 components. This allows the developer to test and debug the back-end logic using familiar tools, such as an IDE or a debugger.

:::note
When running in host mode, localhost ports 5003 and 5004 will be used by default for the communication between the Cartesi Rollups framework and the DApp's back-end.
:::