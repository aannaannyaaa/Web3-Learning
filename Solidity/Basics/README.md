Solidity is a statically-typed, contract-oriented programming language designed for developing smart contracts on Ethereum Virtual Machine (EVM). It's influenced by C++, Python, and JavaScript, supporting inheritance, libraries, and complex user-defined types.


## Contract Structure

**Basic Contract Template:**

```jsx
text// SPDX-License-Identifier: MIT
pragma solidity ^0.8.19;

contract MyContract {
    // State soliditylang+2variables, functions, events, etc.
}
```

**Version Pragma :**

All Solidity files must start with a version pragma to specify the compiler version and prevent future breaking changes.


## State Variables

**Definition:**

State variables are permanently stored in contract storage on the Ethereum blockchain, similar to database records.

```jsx
contract SimpleStorage {
    uint256 public storedData;  // State variable
    string private name;        // Private state variable
}
```


## Data Types

**Unsigned Integers (uint):**

```jsx
uint256 public balance;     // 256-bit unsigned integer
uint8 public age;          // 8-bit unsigned integer
uint public count;         // Default uint256
```

**Structs - Custom Data Types:**

```jsx
struct Person {
    uint age;
    string name;
    address wallet;
}

Person public owner;
```

**Arrays:**

```jsx
// Fixed-size array
string[5] fixedArray;

// Dynamic array
uint[] public dynamicArray;

// Array of structs
Person[] public people;

// Adding to dynamic arrays
people.push(Person(25, "Alice", msg.sender));
```


## Functions

**Function Syntax and Types:**

```solidity
contract MyContract {
    uint256 private _number;

    // Public function (default visibility)
    function setNumber(uint256 _num) public {
        _number = _num;
    }

    // View function (reads state, doesn't modify)
    function getNumber() public view returns (uint256) {
        return _number;
    }

    // Pure function (no state access)
    function addNumbers(uint256 a, uint256 b) public pure returns (uint256) {
        return a + b;
    }

    // Private function (internal use only)
    function _helper() private view returns (uint256) {
        return _number * 2;
    }

    // Payable function (can receive Ether)
    function deposit() public payable {
        // Function can receive ETH
    }
}
```

**Function Visibility:**

- `public`: Accessible from anywhere
- `private`: Only within the current contract
- `internal`: Within current contract and derived contracts
- `external`: Only from outside the contract

**Function Types:**

- `view`: Reads blockchain state but doesn't modify it
- `pure`: No state access, purely computational
- `payable`: Can receive Ether payments[metana+2](https://metana.io/blog/solidity-functions-types-and-use-cases/)


## Memory vs Storage

**Reference Types Must Specify Location:**

```solidity
function processArray(uint[] memory _data) public {
    // _data is stored in memory (temporary)
}

function modifyState(uint[] storage _data) internal {
    // _data references storage (permanent)

```


## Built-in Functions

**Keccak256 Hash Function:**

```solidity
function generateHash(string memory _input) public pure returns (bytes32) {
    return keccak256(abi.encodePacked(_input));
}
```


## Events

**Event Declaration and Emission:**

```solidity
contract EventExample {
    event Transfer(address indexed from, address indexed to, uint256 value);
    
    function transfer(address _to, uint256 _amount) public {
        // Transfer logic here
        emit Transfer(msg.sender, _to, _amount);
    }
}
```

Events communicate blockchain occurrences to external applications and are cheaper than storing data in state variables.


## Ethereum Accounts and Addresses

Ethereum accounts are digital identities that can hold Ether (ETH) and interact with the blockchain. Each account has a unique address—a 42-character hexadecimal identifier starting with "0x" (e.g., `0x0cE446255506E92DF41614C46F1d6df9Cc969183`).

**Types of Accounts:**

- **Externally Owned Accounts (EOA):** Controlled by private keys, used by humans
- **Contract Accounts:** Controlled by smart contract code, no private keys


## Mappings

**Definition and Usage:**

Mappings are key-value data structures for efficient storage and lookup, similar to hash tables or dictionaries in other languages.

```solidity
// Syntax: mapping(keyType => valueType) visibility name;
mapping(address => uint) public accountBalance;
mapping(uint => string) userIdToName;
mapping(address => mapping(address => uint)) public allowances; // Nested mapping

contract Bank {
    mapping(address => uint) public balances;
    
    function deposit() public payable {
        balances[msg.sender] += msg.value;
    }
    
    function getBalance(address _user) public view returns (uint) {
        return balances[_user];
    }
}
```

**Key Features:**

- Fast O(1) lookups
- Cannot iterate over keys
- All possible keys exist with default zero values
- Only usable in storage, not memory


## Global Variables

**msg.sender :**

A global variable containing the address of the account that called the current function.

```solidity
function withdraw(uint _amount) public {
    require(balances[msg.sender] >= _amount, "Insufficient balance");
    balances[msg.sender] -= _amount;
    payable(msg.sender).transfer(_amount);
}
```

**Other Important Globals :**

- `msg.value`: Amount of wei sent with the transaction
- `block.timestamp`: Current block timestamp
- `block.number`: Current block number


## require Statements

**Purpose:**

`require` validates conditions and reverts the transaction if they fail, providing error messages.

```solidity
function transfer(address _to, uint _amount) public {
    require(_to != address(0), "Cannot transfer to zero address");
    require(balances[msg.sender] >= _amount, "Insufficient balance");
    
    balances[msg.sender] -= _amount;
    balances[_to] += _amount;
}
```


## Inheritance

**Basic Inheritance:**

Solidity supports single and multiple inheritance using the `is` keyword.

```solidity
// Base contract
contract Animal {
    string public name;
    
    function speak() public virtual returns (string memory) {
        return "Some sound";
    }
}

// Derived contract
contract Dog is Animal {
    function speak() public pure override returns (string memory) {
        return "Woof!";
    }
}

// Multiple inheritance
contract Mammal {
    bool public warmBlooded = true;
}

contract Pet is Animal, Mammal {
    address public owner;
    
    constructor(string memory _name, address _owner) {
        name = _name;
        owner = _owner;
    }
}
```

**Key Keywords:**

- `virtual`: Allows function to be overridden
- `override`: Required when overriding a function
- `super`: Calls parent contract's function


## Import Statements

**File Imports :**

```solidity
import "./MyContract.sol";
import {SpecificContract} from "./contracts/SpecificContract.sol";
import * as MyModule from "./MyModule.sol";
```


## Storage vs Memory

**Storage :** Permanent blockchain storage, expensive gas costs, persists between function calls.

**Memory :** Temporary storage during function execution, cheaper gas, cleared after function ends.

```solidity
contract DataLocation {
    uint[] public storageArray; // State variable in storage
    
    function addToArray(uint[] memory _tempArray) public {
        // _tempArray is in memory (temporary)
        storageArray = _tempArray; // Copy from memory to storage
    }
    
    function processArray() public view returns (uint[] memory) {
        uint[] memory tempArray = new uint[](3); // Memory allocation
        tempArray[0] = storageArray[0];
        return tempArray; // Returns memory array
    }
}
```

**Data Location Rules:**

- State variables are always in storage
- Function parameters are in memory by default
- Reference types must specify location (memory/storage/calldata)
- Value types (uint, bool, address) don't need location specification


## Interfaces

Interfaces define function signatures without implementation, enabling contracts to interact with unknown contracts.

```solidity
// Interface definition
interface IERC20 {
    function totalSupply() external view returns (uint256);
    function balanceOf(address account) external view returns (uint256);
    function transfer(address to, uint256 amount) external returns (bool);
}

// Using interface to interact with external contract
contract TokenInteractor {
    IERC20 public token;
    
    constructor(address _tokenAddress) {
        token = IERC20(_tokenAddress);
    }
    
    function getTokenBalance(address _user) public view returns (uint256) {
        return token.balanceOf(_user);
    }
}

// Implementing an interface
contract MyToken is IERC20 {
    mapping(address => uint256) private _balances;
    uint256 private _totalSupply;
    
    function totalSupply() public view override returns (uint256) {
        return _totalSupply;
    }
    
    function balanceOf(address account) public view override returns (uint256) {
        return _balances[account];
    }
    
    function transfer(address to, uint256 amount) public override returns (bool) {
        require(_balances[msg.sender] >= amount, "Insufficient balance");
        _balances[msg.sender] -= amount;
        _balances[to] += amount;
        return true;
    }
}
```

**Interface Rules:**

- Cannot have implemented functions
- Cannot inherit from other contracts
- All functions must be external
- Cannot declare constructor
- Cannot declare state variables


## Contract Immutability and Ownership

**Immutability :** Once a contract is deployed to Ethereum, it is immutable—it cannot be altered or upgraded. All logic and data structures are set forever at the moment of deployment.

**Ownable Contracts :** Many contracts follow an **Ownable** pattern, assigning an initial owner (usually the deployer) special permissions.

```solidity
import "@openzeppelin/contracts/access/Ownable.sol";

contract MyContract is Ownable {
    constructor() Ownable(msg.sender) {}
    
    function restrictedFunction() public onlyOwner {
        // Only owner can call this
    }
}
```

## Security Best Practices

**Essential Security Measures :**

- **Checks-Effects-Interactions Pattern:** Always check conditions, update state, then interact with external contracts.
- **Reentrancy Protection:** Use OpenZeppelin's **`ReentrancyGuard`** or **`nonReentrant`** modifier.
- **Access Control:** Implement proper role management with OpenZeppelin's **`AccessControl`**.
- **Input Validation:** Always validate function parameters with **`require`** statements.


## Gas Optimization

**Key Optimization Strategies :**

- **Use appropriate data types:** Choose smallest suitable type (e.g., **`uint8`** instead of **`uint256`** when possible).
- **Pack struct variables:** Arrange struct members to minimize storage slots.
- **Cache storage reads:** Store frequently accessed storage variables in memory.
- **Use events for logging:** Events are cheaper than storage for data that doesn't need on-chain queries.

## Time Variables & Units

Solidity provides special variables and units for working with time:

- **`block.timestamp`**: returns the current Unix timestamp (seconds since Jan 1, 1970).
- Units: **`seconds`**, **`minutes`**, **`hours`**, **`days`**, **`weeks`**, **`years`** (all convert to seconds).