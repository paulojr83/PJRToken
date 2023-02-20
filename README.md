### First, you need to install Solidity and Ethereum.

*Install o Solidity: *
``npm install -g solc ``

*Install o Ethereum: *
``npm install -g ethereumjs-testrpc ``

#### *Create a new file called MyToken.sol with the following code:*
``
pragma solidity ^0.8.0;

contract MyToken { 

    // Defina as propriedades do seu token aqui 

    string public name; 
    string public symbol; 

    // Defina a quantidade de tokens que serão emitidos aqui 

    uint256 public totalSupply;

    // Crie uma variável para armazenar os detalhes dos proprietários do token aqui

    mapping (address => uint256) public balanceOf;

   // Crie uma função para transferir tokens de um endereço para outro aqui

   function transfer(address _to, uint256 _value) public { 

        require(balanceOf[msg.sender] >= _value); // Verifique se o remetente tem saldo suficiente para transferir tokens  

        balanceOf[msg.sender] -= _value; // Subtraia os tokens do remetente  

        balanceOf[_to] += _value; // Adicione os tokens ao destinatário  
   }  

   // Crie uma função para atribuir tokens ao proprietário inicial aqui  

   function assign(address _to, uint256 _value) public {    

        require(balanceOf[_to] == 0); // Verifique se o destinatário já possui algum saldo de token    

        balanceOf[_to] = _value; // Atribua os tokens ao destinatário    

        totalSupply += _value; // Aumente a quantidade total de tokens emitidos    
   }    
}  
``

*[solc](https://www.npmjs.com/package/solc?activeTab=readme)*
*Compile the contract using solc:*
``sol``
