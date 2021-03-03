[地址](https://www.zhihu.com/column/p/28266204)
## 单位
一个语句中的数字可以带有 wei、finney、szabo 或者 ether 的后缀，可以在以太币的子单位之间进行转换，其中没有后缀的以太币会被假定为以 wei 为单位。例如：
2 ether == 2000 finney 

## 特殊变量和函数（Special Variables and Functions）

有一些特殊的变量和函数总是存在于全局命名空间中，主要用于提供关于区块链的信息。

### 区块和交易属性（Block and Transaction Properties）
1. block.blockhash(uint blockNumber) returns (bytes32):指定区块的哈希值，仅适用于最近且不包括当前的256个区块
2. block.coinbase (address) : 当前区块的矿工地址（将挖出）

3. block.difficulty (uint) : 当前区块的难度

4. block.gaslimit (uint) : 当前区块的 gaslimit

5. block.number (uint) : 当前区块号

6. block.timestamp (uint) : 当前区块时间戳，从unix纪元开始以秒为单位计数

7. msg.data (bytes) : 完整的 calldata

8. sg.gas (uint) : 剩余的 gas

9. msg.sender (address) : 当前调用的message的发送者 （当前的调用）

10. msg.sig (bytes4): calldata 的前四个字节（即函数标识符）

11. msg.value (uint) : message发送的wei数量（以太币）

12. now (uint) : 当前区块时间戳 （block.timestamp 的别名）

13. tx.gasprice (uint) : 交易的gas price

14. tx.origin (address) : 交易的发送者 (full call chain)

>注：msg 的所有成员的值（包括 msg.sender 和 msg.value）可以针对每个外部函数调用进行更改。 这包括对库函数的调用。

>注：如果要使用 msg.sender 在库函数中实现访问限制，则必须手动提供 msg.sender 的值作为参数。

>注：由于可扩展性的原因，区块哈希值不适用于所有区块。你只能访问最近256个区块的散列值，所有其他区块的哈希值将为零。

## 视频
[ Sending Ether to a smart contract](https://www.youtube.com/watch?v=4k_ak3SFczc)

## web3.eth.Contract
[methods.myMethod.send](https://web3js.readthedocs.io/en/v1.2.11/web3-eth-contract.html#methods-mymethod-send)

Will send a transaction to the smart contract and execute its method. Note this can alter the smart contract state.

```javascript
// using the callback
myContract.methods.myMethod(123).send({from: '0xde0B295669a9FD93d5F28D9Ec85E40f4cb697BAe'}, function(error, transactionHash){
    ...
});
```


## methods.myMethod.call
Will call a “constant” method and execute its smart contract method in the EVM without sending any transaction. Note calling cannot alter the smart contract state.
[文档](https://web3js.readthedocs.io/en/v1.2.11/web3-eth-contract.html?highlight=send#methods-mymethod-call)





