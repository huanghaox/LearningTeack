# Content/烧毁调用者稳定币

刚刚我们提到，为了完成稳定币的偿还，我们还需要将用户稳定币给烧毁，这样才完成了稳定币⇒抵押物的交换。

现在让我们来完成这最后一个步骤吧！

**Syntax**

function call

- 提示
    
    ```solidity
    _burn(msg.sender, amount);
    ```
    
