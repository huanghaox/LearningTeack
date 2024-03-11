# Content/记录借贷数额

在扣除了用户的抵押物后，我们就要进入到稳定币的发放了，在铸造稳定币前，我们还需要记录用户的借贷数额。

只需要在用户对应的借贷总额映射***loanAmount***中加上这笔即将要发放的稳定币即可。

**Syntax**

mapping

- 提示
    
    ```solidity
    loan[msg.sender] += reward;
    ```
    
