# Redbelly-smart-contract-integration

Note: In order to start using the smart contract, users must set uptheir wallet. Must need a metamask or any wallet to deploy the contract

Step 1: Head to the [Remix](https://remix.ethereum.org/#lang=en&optimize=false&runs=200&evmVersion=null&version=soljson-v0.8.18+commit.87f61d96.js).

Step 2: : Go to Workspace from the left-panel menu and choose the Create New File icon.

![image](https://github.com/AgileRampler/Redbully-contract-integration/assets/43984000/90fdef9a-3439-400c-afea-d5d729e4440d)

Step 3: Create a new file under contracts folder with the name “redbelly.sol”

![image](https://github.com/AgileRampler/Redbully-contract-integration/assets/43984000/e4964a54-6108-4248-8b05-16f402544318)

**Note:** .**sol is the extension of Solidity files.**

Step 4: Writing the code

You can either paste your existing code in the main panel of the redbelly.sol file or upload your contract file in the Workspace.




**Use  the  code below
**

```bash
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.13;


// https://github.com/OpenZeppelin/openzeppelin-contracts/blob/v3.0.0/contracts/token/ERC20/IERC20.sol
interface IERC20 {
   function totalSupply() external view returns (uint);
   function balanceOf(address account) external view returns (uint);
   function transfer(address recipient, uint amount) external returns (bool);


   function allowance(address owner, address spender) external view returns (uint);


   function approve(address spender, uint amount) external returns (bool);


   function transferFrom(
       address sender,
       address recipient,
       uint amount
   ) external returns (bool);


   event Transfer(address indexed from, address indexed to, uint value);
   event Approval(address indexed owner, address indexed spender, uint value);
}


contract ERC20 is IERC20 {
   uint public totalSupply;
   mapping(address => uint) public balanceOf;
   mapping(address => mapping(address => uint)) public allowance;
   string public name = "Solidity by Example";
   string public symbol = "SOLBYEX";
   uint8 public decimals = 18;




   function transfer(address recipient, uint amount) external returns (bool) {
       balanceOf[msg.sender] -= amount;
       balanceOf[recipient] += amount;
       emit Transfer(msg.sender, recipient, amount);
       return true;
   }




   function approve(address spender, uint amount) external returns (bool) {
       allowance[msg.sender][spender] = amount;
       emit Approval(msg.sender, spender, amount);
       return true;
   }




   function transferFrom(
       address sender,
       address recipient,
       uint amount
   ) external returns (bool) {
       allowance[sender][msg.sender] -= amount;
       balanceOf[sender] -= amount;
       balanceOf[recipient] += amount;
       emit Transfer(sender, recipient, amount);
       return true;
   }




   function mint(uint amount) external {
       balanceOf[msg.sender] += amount;
       totalSupply += amount;
       emit Transfer(address(0), msg.sender, amount);
   }




   function burn(uint amount) external {
       balanceOf[msg.sender] -= amount;
       totalSupply -= amount;
       emit Transfer(msg.sender, address(0), amount);
   }
}
```



This is how your screen will appear after pasting either  code mentioned above: 
![image](https://github.com/AgileRampler/Redbelly-contract-integration/assets/43984000/79214738-fcc6-48cc-9ad8-f5dbbcaba193)


ep 5: Compilation

Go to the Solidity Compiler from the left-panel.

To compile a contract, either select the desired file from the File Explorer, or ensure that the desired file is the active one in the Editor if multiple files are open.

If there is an active file chosen in the file explorer, then the solidity compiler will look like this:

![image](https://github.com/AgileRampler/Redbelly-contract-integration/assets/43984000/471ce1e2-f94f-4dd6-a77a-67d2b5810ca4)


Click on Compile redbelly.sol to compile the contract file.

After successful compilation, this is what your screen will look like:

![image](https://github.com/AgileRampler/Redbully-contract-integration/assets/43984000/df56466d-8d11-4911-b554-dcb31d821f21)



Step 6: Deployment

Go to the Deploy & Run Transactions sidebar from the left-panel.

In order to use this module, it is necessary to have a compiled contract. Hence, if there is a contract name in the CONTRACT select box (the select box is under the VALUE input field), you can use this module.)


![image](https://github.com/AgileRampler/Redbully-contract-integration/assets/43984000/836654bd-d0b9-46db-a2eb-209e858f50a8)

Click on Deploy.
Confirm the transaction on Web3 extension.


Once the transaction is confirmed, the deployment details, contract address and transaction, will be visible in the terminal:


![image](https://github.com/AgileRampler/Redbully-contract-integration/assets/43984000/a5b1f4e0-9915-4896-a8ad-2d2db5006e7e)

you can check the trasaction hash in the debug button of terminal 


![image](https://github.com/AgileRampler/Redbully-contract-integration/assets/43984000/8a7ef2ec-47c8-4ff1-937c-021639da9922)


finally you can use  the transaction hash in redebelly scan to check the contract deployed
https://explorer.devnet.redbelly.network/overview





