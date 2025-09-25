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
}

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