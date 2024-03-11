# Content/引文

在本节中，我们将实现稳定币（DAI借贷市场）合约的第一个功能：将**抵押品**存入合约。 

我们之前提到，要想换出**稳定币DAI**，就必须选择一个抵押物进行抵押，例如ETH，也可以是一些ERC20代币，例如DOGE等。

这种抵押类似于我们生活中的房产抵押，当你需要现金流时，你就可以在银行将房产进行抵押，换取贷款。对应到我们的借贷市场，ETH等抵押品就是房产，而DAI就是借贷市场为你提供的贷款。

你可能会有疑惑，为什么我们需要将ETH抵押，贷款出DAI？

这是因为DAI是一个稳定币，其价格与美元挂钩，因此对于那些需要稳定流通货币的人来说，DAI是一个更好的选择。

通过将ETH抵押换取DAI，用户可以在避免ETH价格波动的同时，获得稳定的货币流动性。

好了，说了这么多，让我们先来实现抵押品的存入吧！

# Example/ Code

```solidity
pragma solidity 0.8.17;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

contract SimpleStableCoin is ERC20 {
    IERC20 public collateralToken;
    mapping(address => uint256) public totalCollateral;
    mapping(address => uint256) public remainingCollateral;
    mapping(address => uint256) private loanAmount;
    uint256 public collateralRatio;
    uint256 public liquidationRatio;
    uint256 public price;

    constructor(
        address _collateralToken,
        uint256 _collateralRatio,
        uint256 _liquidationRatio
    ) ERC20("SimpleStableCoin", "SSC") {
        collateralToken = IERC20(_collateralToken);
        collateralRatio = _collateralRatio;
        liquidationRatio = _liquidationRatio;
    }

		function setPrice(uint256 _price) public {
        price = _price;
    }

}
```