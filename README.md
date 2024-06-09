# Contract SmartContract
This project demonstrates a basic smart contract written in Solidity, a programming language for the Ethereum blockchain. this code provides a basic example of a secure value storage and withdrawal system on a blockchain using a smart contract. It also showcases different error handling mechanisms available in Solidity.
# Description
This project explores a fundamental smart contract on the Ethereum blockchain. It allows secure storage and withdrawal of a single value, like an asset amount. The owner controls updates, ensuring a minimum value to prevent issues. Withdrawals are managed by the owner, and the contract securely transfers funds. It also demonstrates three common error handling methods in Solidity for robustness. While a basic example, this project provides a foundation for understanding secure transactions and error handling on the blockchain.
## Getting Started
### Executing program
To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.
Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension. Copy and paste the following code into the file:
javascript
pragma solidity ^0.8.18;

contract SmartContract {
    address public owner;
    uint256 public value;

    constructor() {
        owner = msg.sender;
        value = 0;
    }

    function setValue(uint256 _newValue) public {
        require(msg.sender == owner, "Only the owner can set the value");
        require(_newValue > 0, "New value must be greater than zero");
        value = _newValue;
    }

    function withdraw() public {
        require(value > 0, "Value must be greater than zero");
        uint256 amount = value;
        value = 0;
        payable(msg.sender).transfer(amount);
    }

    function assertExample(uint256 x) public pure returns (uint256) {
        assert(x != 0); // Ensure input is not zero
        return 100 / x;
    }

    function revertExample(uint256 x) public pure returns (uint256) {
        if (x == 0) {
            revert("Input cannot be zero");
        }
        return 100 / x;
    }

    function requireExample(uint256 x) public pure returns (uint256) {
        require(x != 0, "Input cannot be zero");
        return 100 / x;
    }
}

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.18" (or another compatible version), and then click on the "Compile contract mytoken.sol" button.
Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "contract mytoken" contract from the dropdown menu, and then click on the "Deploy" button.
## Authors
Ved prakash
## License
This project is licensed under the MIT License - see the LICENSE.md file for details
