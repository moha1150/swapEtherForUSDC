A Node.js script that demonstrates how to swap ether for USDC tokens using the Uniswap smart contracts and the ethers.js library to connect to the Ethereum blockchain with Infura.

The script starts by connecting to the Ethereum blockchain using the ethers.js library and a provided Infura API key. It then loads the Uniswap Factory and Exchange contracts, and calls the getEthToTokenInputPrice function on the Exchange contract to retrieve the current exchange rate for ether to USDC tokens.

The script then calculates the amount of USDC tokens that can be purchased with 1 ether, and the minimum amount of ether required to purchase those tokens. It then calls the ethToTokenSwapInput function on the Exchange contract to execute the trade and waits for the transaction to be mined.

Finally, the script logs a message indicating that the trade was successful.
