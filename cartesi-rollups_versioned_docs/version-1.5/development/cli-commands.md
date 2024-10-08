---
id: cli-commands
title: CLI commands
---


The Cartesi CLI provides essential tools for developing, deploying, and interacting with Cartesi applications. This page offers a quick reference to available commands and usage.

## Basic Usage
To use any command, run:

```bash
cartesi [COMMAND]
```

For detailed help on a specific command, use:

```bash
cartesi help [COMMAND]
```

## Core Commands

| Command | Description |
|---------|-------------|
| `create` | Create a new application |
| `build` | Build the application |
| `run` | Run the application node |
| `send` | Send input to the application |
| `deploy` | Deploy application to a live network |
| `address-book` | Prints addresses of deployed smart contracts |
| `clean` | Clean build artifacts of the application |
| `doctor` | Verify the minimal system requirements |
| `hash` | Print the image hash generated by the build command |
| `shell` | Start a shell in the Cartesi machine of the application |


---
### `create`

Create a new Cartesi application from a template.

#### Usage:
```bash
cartesi create NAME --template <template-name> [--branch <value>]
```

#### Flags:

- `--template=<option>`: (required) Template name to use (options: `cpp`, `cpp-low-level`, `go`, `javascript`, `lua`, `python`, `ruby`, `rust`, `typescript`).
- `--branch=<value>`: [cartesi/application-templates](https://github.com/cartesi/application-templates) repository branch name to use.

---


### `build`
Compiles your application to RISC-V and builds a Cartesi machine snapshot.

#### Usage:
```bash
cartesi build [--from-image <value>] [--target <value>]
```

#### Flags:
- `--from-image=<value>`: Skip Docker build and start from this image.
- `--target=<value>`: Target of Docker multi-stage build.

---

### `run`
Run a local Cartesi node for the application.

#### Usage:
```bash
cartesi run [--block-time <value>] [--epoch-length <value>] [--no-backend] [-v] [--listen-port <value>]
```

#### Flags:

- `--block-time=<value>`: Interval between blocks in seconds (default: 5).
-  `--epoch-length=<value>`: length of an epoch in blocks (default: 720).
- `--no-backend`: Run a node without the application code.
- `-v`, `--verbose`: Run node with detailed container logs.
- `--listen-port=<value>`: Port to listen for incoming connections (default: 8080).

---

### `send`
Send generic, Ether, ERC20, ERC721 and dApp address inputs to the application in interactive mode.

#### Usage:
```bash
cartesi send
```

#### Sub-commands:

- `send dapp-address`: Send dApp address input.
- `send erc20`: Send ERC-20 deposit.
- `send erc721`: Send ERC-721 deposit.
- `send ether`: Send ether deposit.
- `send generic`: Send generic input.
---


### `deploy`

Deploy the application to a live network.


#### Usage:
```bash
cartesi deploy --webapp <value> [--hosting self-hosted|third-party]
```

#### Flags:
- `--webapp=<value>`: (required) Address of deploy webapp.
- `--hosting=<option>`: Hosting type (options: self-hosted, third-party).

---


### `address-book`
Prints addresses of the deployed ollups smart contracts.

#### Usage:
```bash
cartesi address-book [--json]
```

#### Flags:
- `--json`: Format output as JSON

---

### `shell`

Starts the Cartesi Machine in interactive mode, providing a shell interface.

#### Usage:
```bash
cartesi shell [IMAGE] [--run-as-root]
```

#### Flags:

```bash
--run-as-root: Run as root user
```
---

