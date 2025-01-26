## Bank Vault

The Vault is a smart contract that allows an admin to control and manage a token vault. The vault stores the tokens, tracks allocations to authorized addresses, and logs events for each transaction. It supports the following key functionalities:

- Token Deposits: Allows users with permissions to deposit tokens into the vault.
- Permission Management: The admin can grant or revoke permissions to other addresses to interact with the vault.
- Token Allocation: Allocates tokens to addresses, which can be claimed later by those addresses.
- Admin Management: The current admin can transfer control of the vault to a new admin.
- Withdrawals: Allows the admin to withdraw unallocated tokens from the vault.


#### Components
**Error Codes**
The following error codes are used in the module:

- E_NOT_ADMIN (1): Thrown if an operation is attempted by a non-admin.
- E_PERMISSION_DENIED (2): Thrown if a user without permission tries to interact with the vault.
- E_INSUFFICIENT_BALANCE (3): Thrown if the vault does not have enough tokens for a requested operation.
- E_NO_ALLOCATION (4): Thrown if an address has no allocation available to claim.
- E_ADDRESS_NOT_FOUND (5): Thrown if an address is not found where expected.

**Events**
The module emits the following events:

```shPermissionGrantedEvent: Emitted when permission is granted to an address.
PermissionRevokedEvent: Emitted when permission is revoked from an address.
AllocationMadeEvent: Emitted when tokens are allocated to an address.
AllocationClaimedEvent: Emitted when an address claims allocated tokens.
AllocationCanceledEvent: Emitted when an allocation is canceled.
AdminChangedEvent: Emitted when the admin of the vault is changed.
TokensDepositedEvent: Emitted when tokens are deposited into the vault.
TokensWithdrawnEvent: Emitted when tokens are withdrawn from the vault.
```
**Vault Struct**
The core struct of the module, Vault, contains the following fields:

- admin: The address of the admin who has control over the vault.
- vault_address: The address of the vault on the blockchain.
- permissions: A list of addresses authorized to deposit tokens into the vault.
- allocations: A table mapping addresses to token amounts that have been allocated.
- total_allocated: The total amount of tokens allocated to addresses.
- total_balance: The total amount of tokens currently in the vault.
- event handles: Various event handles to track changes to the vault (e.g., for permissions, allocations, deposits, withdrawals).
