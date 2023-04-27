## ERC20Portal

Transfer ERC-20 tokens to a DApp and add an input to the DApp's input box to signal such operation.

### getInputBox

```solidity
function getInputBox() external view returns (contract IInputBox)
```

Get the input box used by this portal

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | contract IInputBox | the input box |

### depositERC20Tokens

```solidity
function depositERC20Tokens(contract IERC20 _token, address _dapp, uint256 _amount, bytes _execLayerData) external
```

Transfer ERC-20 tokens to a DApp and add an input to
        the DApp's input box to signal such operation.

_The caller must allow the portal to withdraw at least
     `_amount` tokens from their account beforehand._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _token | contract IERC20 | The ERC-20 token contract |
| _dapp | address | The address of the DApp |
| _amount | uint256 | The amount of tokens to be transferred |
| _execLayerData | bytes | Additional data to be interpreted by the execution layer |