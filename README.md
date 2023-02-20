<h1> First, you need to install Solidity and Ethereum. </h1>

<b>Install o Solidity:</b>

<code>npm install -g solc</code>

<b>Install o Ethereum:</b>

<code>npm install -g ethereumjs-testrpc</code>

<h3>Create a new file called MyToken.sol with the following code:</h3>

```
pragma solidity ^0.8.0;

contract MyToken { 

    // Set your token properties here
    string public name; 
    string public symbol; 

    // Set the amount of tokens to be issued here
    uint256 public totalSupply;

    // Create a variable to store the token owners details here
    mapping (address => uint256) public balanceOf;

   // Create a function to transfer tokens from one address to another here
   function transfer(address _to, uint256 _value) public { 

        require(balanceOf[msg.sender] >= _value); //Make sure the sender has enough balance to transfer tokens

        balanceOf[msg.sender] -= _value; //Subtract sender tokens  

        balanceOf[_to] += _value; //Add tokens to recipient  
   }  

   //Create a function to assign tokens to the initial owner here
   function assign(address _to, uint256 _value) public {    

        require(balanceOf[_to] == 0); //Check if the recipient already has any token balance  

        balanceOf[_to] = _value; //Assign the tokens to the recipient 

        totalSupply += _value; //Increase the total amount of issued tokens 
   }    
}  
```

*[solc](https://www.npmjs.com/package/solc?activeTab=readme)*
<h3>Compile the contract using solc:</h>
<code>sol</code>
