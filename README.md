# Waqas-IOTA-Smart-contract
Data integrity solution for integrity assurance of fog based e health care architecture
/ SPDX-License-Identifier: GPL-3.0

pragma solidity >=0.7.0 <0.9.0;
// WAQAS AHMED-SMART CONTRACT for ensuring Data integrity in fog computing & verifying the same

contract Integrity {

    mapping (bytes => bytes32) hashes;

    function store(string memory data,string memory account) public {

          hashes[abi.encodePacked(account,data)]=keccak256(abi.encodePacked(data));
    
    }
    function verify(string memory data,string memory account) public view returns (bool){
        if(keccak256(abi.encodePacked(data))==hashes[abi.encodePacked(account,data)]){
            return true;
        }else{
            return false;
        }

    }
}
