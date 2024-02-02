# Content/部署合约

好的！目前我们的钱包有一定余额了，我们可以尝试着使用这些 MNT 来进行一些简单的操作，例如：部署一个智能合约到 Mantle 链上。

通常，关于合约部署有这样几个基本步骤：

- 编写简单的智能合约
    
    > 为了方便演示，我们在这里提供了一份简单的HelloWorld合约。
    > 
- 使用Remix VM本地测试合约
- 本地部署
    1. 编译合约
        
        ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/40ad2819-285a-4795-a80f-f6a1f2a4d3bf/23387a2a-5ddd-4f57-9933-6f262be81381/Untitled.png)
        
    2. 使用Remix VM部署合约，这里我们选择 Remix VM(Shanghai)
        
        ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/40ad2819-285a-4795-a80f-f6a1f2a4d3bf/0afae291-62f1-49cb-b008-692d26ed5575/Untitled.png)
        
    3. 测试 ***get*** 函数
        
        ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/40ad2819-285a-4795-a80f-f6a1f2a4d3bf/1b848f6d-64e6-4ad5-a543-32452bb9f54c/Untitled.png)
        
    4. 测试 ***set*** 函数
        
        ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/40ad2819-285a-4795-a80f-f6a1f2a4d3bf/16ae9396-e9e7-4f2e-ba39-1ef10bcccfee/Untitled.png)
        
        ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/40ad2819-285a-4795-a80f-f6a1f2a4d3bf/a1e68d5f-bc60-4873-bc62-b2fb514dcce0/Untitled.png)
        
- 在Mantle链上部署合约
- 链上部署
    1. 编译合约
        
        ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/40ad2819-285a-4795-a80f-f6a1f2a4d3bf/23387a2a-5ddd-4f57-9933-6f262be81381/Untitled.png)
        
    2. 使用 Injected Provider - MetaMask 部署合约，首先我们需要确认将账户连接到我们的网站
        
        ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/40ad2819-285a-4795-a80f-f6a1f2a4d3bf/7747267d-4f45-413a-9ddd-adf1de5559ec/Untitled.png)
        
    3. 点击部署合约，并确认合约部署交易
        
        ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/40ad2819-285a-4795-a80f-f6a1f2a4d3bf/65c5592d-4537-463f-83ea-f14e54b2614d/Untitled.png)
        
- 验证合约的成功部署
- 区块链浏览器验证

# Example/示例代码
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.17;

contract HelloWorld {
    string public greeting;

    constructor() {
        greeting = "Hello, HackQuest!";
    }

    function getGreeting() public view returns (string memory) {
        return greeting;
    }

    function setGreeting(string memory _newGreeting) public {
        greeting = _newGreeting;
    }
}
```