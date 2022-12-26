const ethers = require('ethers');

async function swapEtherForUSDC() {
  // Replace with your own Infura API key
  const apiKey = 'YOUR_INFURA_API_KEY';
  const provider = new ethers.providers.InfuraProvider('mainnet', apiKey);

  // Replace with your own Ethereum private key
  const privateKey = 'YOUR_PRIVATE_KEY';
  const wallet = new ethers.Wallet(privateKey, provider);

  // Load the Uniswap Factory contract
  const factoryAddress = '0x5C69bEe701ef814a2B6a3EDD4B1652CB9cc5aA6f';
  const factoryContract = new ethers.Contract(factoryAddress, uniswapFactory.abi, wallet);

  // Load the Uniswap Exchange contract for USDC
  const usdcAddress = '0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48';
  const usdcExchangeAddress = await factoryContract.getExchange(usdcAddress);
  const usdcExchangeContract = new ethers.Contract(usdcExchangeAddress, uniswapExchange.abi, wallet);

  // Call the Uniswap "getEthToTokenInputPrice" function to get the amount of USDC tokens that can be purchased with 1 ether
  const exchangeRate = await usdcExchangeContract.getEthToTokenInputPrice();

  // Calculate the amount of USDC tokens that can be purchased with 1 ether, and round down to the nearest whole token
  const usdcAmount = exchangeRate.div(ethers.utils.parseUnits('1', 'ether')).floor();

  // Calculate the minimum amount of ether required to purchase the USDC tokens
  const minEtherAmount = exchangeRate.mul(usdcAmount);

  // Call the Uniswap "ethToTokenSwapInput" function to execute the swap
  const tx = await usdcExchangeContract.ethToTokenSwapInput(usdcAmount, minEtherAmount);

  // Wait for the transaction to be mined
  await tx.wait();

  console.log(`Successfully swapped ${minEtherAmount} ether for ${usdcAmount} USDC tokens`);
}

swapEtherForUSDC();
