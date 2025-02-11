
## Principle of Least Privilege

### Overview
Ensuring your smart contract functions are secure is essential. By default, it’s best to restrict access to public functions to avoid unauthorized interactions that could lead to exploits. Only grant access to specific roles, contracts, or addresses that genuinely require it. Before making any function accessible to everyone, take a moment to assess its necessity and the potential security risks.

### Code Example

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/proxy/Clones.sol";

contract Factory {
    function createClone(
        address _implementation,
        bytes calldata _extraData
    ) external returns (address gauge) {
        address clonedContract = Clones.cloneDeterministic(_implementation, keccak256(abi.encode(_extraData)));

        Clone(clonedContract).init(_extraData);

        return clonedContract;
    }
}

interface Clone {
    function init(bytes calldata _extraData) external;
}
```

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "./Factory.sol";  // Import the Factory contract

contract CloneCaller {
    Factory factory;  // Instance of the Factory contract
    address public admin;  // Admin address

    modifier onlyAdmin() {
        require(msg.sender == admin, "Caller is not the admin");
        _;
    }

    constructor(address _factoryAddress, address _admin) {
        factory = Factory(_factoryAddress);  // Set the Factory contract address
        admin = _admin;  // Set the admin address
    }

    function createNewClone(address _implementation, bytes calldata _extraData) external onlyAdmin returns (address) {
        // Call the createClone function from the Factory contract
        address newClone = factory.createClone(_implementation, _extraData);
        return newClone;
    }
}
```

This example highlights a potential vulnerability. While `CloneCaller.createNewClone()` is access-controlled, there’s a risk from front runners who could directly call `Factory.createClone()`, potentially blocking `createNewClone()` and causing a denial of service. Therefore, `Factory.createClone()` should be restricted only for `CloneCaller`.

### Best Practices

#### 1. Implement Role-Based Access Control (RBAC)
RBAC is a great way to ensure that only those with the proper authority can access sensitive functions. Assign roles carefully, always asking: "Does this role truly need this level of access?"

#### 2. Default to Restricting Access
By default, it’s safest to lock down functions until there’s a compelling reason to expose them. If you must make a function public, thoroughly evaluate the potential security implications.

#### 3. Define Roles Clearly
Establish clear roles like `ADMIN`, `OPERATOR`, and `USER`, ensuring each role has only the permissions it actually needs. Broad permissions can quickly introduce security risks, so avoid giving too much access by default.

#### 4. Regularly Review and Adjust Permissions
Access control should be seen as an ongoing process, not a one-time setup. Regularly revisit your function permissions and make adjustments as needed. If a role no longer requires access to a function, revoke it immediately.
