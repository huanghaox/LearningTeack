# Content/Module

[DEX-1.output.mp4](../video/DEX-1.output.mp4)

1. 点击Try it Out进入HackQuest IDE。
2. 部署***MockTokenA***合约和***MockTokenB***合约
3. 传入参数***MockTokenA***合约地址以及***MockTokenB***地址并部署***LiquidityPool*** 合约
4. 查询***tokenA***和***tokenB***

# Example/示例代码

```jsx
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts@4.9.3/token/ERC20/ERC20.sol";

contract LiquidityPool is ERC20 {
    address public tokenA;
    address public tokenB;

    uint256 public reserveA;
    uint256 public reserveB;
    uint256 public totalLiquidity;

    constructor(address _tokenA, address _tokenB) ERC20("HackQuest", "HQ") {
        tokenA = _tokenA;
        tokenB = _tokenB;
    }
}

contract MockTokenA is ERC20 {
    constructor() ERC20("TokenA", "HQA") {
        _mint(msg.sender, 10 * 10**18);
    }
}

contract MockTokenB is ERC20 {
    constructor() ERC20("TokenB", "HQB") {
        _mint(msg.sender, 10 * 10**18);
    }
}
```