# Escrow-8
Escrow.sol
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract Escrow {
    address public payer;
    address public payee;

    constructor(address _payee) {
        payer = msg.sender;
        payee = _payee;
    }

    function deposit() public payable {}

    function release() public {
        require(msg.sender == payer, "Not payer");
        payable(payee).transfer(address(this).balance);
    }
}
