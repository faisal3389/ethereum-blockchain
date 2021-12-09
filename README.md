To sync Ethereum nodes run
`./geth --syncmode "light" --datadir /Volumes/Blr Samsung SSD Space/Downloads/geth-darwin-amd64-1.10.13-7a0c19f8/nodes`


steps: 
1. compile contract with solidity plugin compiler
2. `truffle deploy --reset`
3. `truffle console`
4. inside console `HelloWorld.deployed().then(function(instance) {return instance});`
4. inside console `HelloWorld.deployed().then(function(instance) {return instance.getHelloMessage()});`




----
in case of error:
RE: Error: HelloWorld has not been deployed to detected network (network/artifact mismatch)

The class video is a bit incomplete. 
After creating the HelloWorld.sol file, you can compile it (by pressing F5 in VS Code). Make sure that you see: "Compilation completed successfully!", don't worry yet about the "SPDX warnings".
What is missing in the video is that you have to edit the migrations/1_initial_migration.js file. This file specifies the contracts to be deployed. You need to add your smart contract:

const HelloWorld = artifacts.require("HelloWorld");

and then make sure it is deployed by calling deployer.deploy, for example:

module.exports = function (deployer) {
deployer.deploy(Migrations);
deployer.deploy(HelloWorld);
};

After that run truffle deploy --reset again - and the HelloWorld will actually deploy. 