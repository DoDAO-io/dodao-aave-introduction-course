## Header
This is the course header. This will be added on top of every page. Go to [DoDAO.io](https://www.dodao.io) to know more.

 ---
 
 ## Other Features of AAVE
 
 **Flash Loans**        
#### What are Flash Loans?
Flash loans are special transactions that allow you to borrow and repay assets, but unlike traditional DeFi borrowing, the money must be repaid within a single transaction. 
Flash loans do not require any collateral to function, and are instantaneous, hence the term “flash”. Flash loans are essentially like short-term loans that are codified by 
smart contracts. This means that the terms of the loan are written in code, which helps to prevent funds from being transferred out of one account to another unless certain conditions 
have been met. Flash loans are typically repaid in the same transaction, and they are only valid for as long as the liquidity remains in the pool. However, if a flash loan trade doesn't 
return the full amount of liquidity to the pool, the entire transaction will be reversed, which will also reverse all previous actions. This helps to ensure that funds are safe during the 
event of a flash loan.

#### Blockchain Transactions
A transaction is a way of transferring value or any other type of token using Blockchain. In order to transfer cryptocurrency, you must have a digital wallet. This wallet must have a public 
and private key. You can think of it like this: your wallet is your bank account, your public key is your account number, other users use this to send you assets. Your private key is your pin code, 
which allows you to access the assets in your wallet. Once you have connected your wallet, you can use various decentralized exchanges and decentralized finance platforms to complete transactions. 
On every transaction, a fee is added, which acts as an incentive to miners to keep the chain secure.
 
<<<<<<< Updated upstream
 #### Working of transactions
 `flashLoan`: Allows borrowers to access liquidity of *multiple reserves* in a single *flashLoan* transaction. The borrower also has an option to open a stable or variable rate debt position backed by supplied collateral or 
  credit delegation in this case.
 
 `flashLoanSimple`: Allows borrowers to access liquidity of *single reserve* for the transaction. In this case flash loan fee is not waived nor can the borrower open any debt position at the end of the transaction. 
  This method is gas efficient for those trying to take advantage of simple flash loans with a single reserve asset.
 
 
 #### Execution Flow
 Here is an example of an execution flow for developers,
 
 1. Your contract calls the Pool contract, requesting for a flash loan of a certain amount from reserve(s) using `flashLoanSimple()`` or `flashLoan()``.
 2. After some sanity checks, the pool transfers the requested amount from reserve(s) to your smart contract, then calls `executeOperation()`` on the receiver contract.    
 3. Your smart contract, now holding the flash loaned amount, executes any arbitrary operation in its code.
     * In case of a `flashloanSimple`, your code has finished. You just need to approve the pool the loaned amount + fee. 
     * If you are doing a `flashLoan`,  then depending on the interest rate mode and whether or not you want to open a debt position after the flash loan, you must either approve the 
       flash loan + fee to the pool or provide sufficient collateral or credit delegation should be available to open the debt position.
     * If the amount owed is not available to the pool due to lack of balance or insufficient approved amount, then all changes made in the transaction are reverted.
 4. All the above happens in one transaction block.

 #### Applications of flash loans

 **Arbitrage:** Users can earn a decent profit by trading assets at different platforms that offer different values. With flash loans, traders can launch an arbitrage without any existing assets. 
 Therefore, arbitrage trades using a flash loan become "cost-free" as long as the traders can afford the gas and flash loan fee to launch the transaction.

 **Swapping collateral:**  Crypto asset investors can use collateral swapping to change out their investments without having to repay the debt of the original investment. Collateral swapping lets an investor 
 replace their position with borrowed assets. Users can choose to pay back their CDP debt and take out all collateral, using part of it to repay flash loans and keeping the remaining 
 for themselves.

 **Self Liquidation:** Markets can be very volatile and can lead to liquidation of the sensitive positions. Liquidation can be quite expensive on certain platforms. There are many applications that make use 
 of flash loans and liquidate the position on user’s behalf saving the user hefty liquidation fees of the protocol.
=======
#### Working of Flash loans
`flashLoan`: Allows borrowers to access liquidity of *multiple reserves* in a single *flashLoan* transaction. The borrower also has an option to open a stable or variable rate debt position backed by supplied collateral or 
 credit delegation in this case.

`flashLoanSimple`: Allows borrowers to access liquidity of *single reserve* for the transaction. In this case flash loan fee is not waived nor can the borrower open any debt position at the end of the transaction. 
 This method is gas efficient for those trying to take advantage of simple flash loans with a single reserve asset.


#### Execution Flow
Here is an example of an execution flow for developers,

1. Your contract calls the Pool contract, requesting for a flash loan of a certain amount from reserve(s) using `flashLoanSimple()`` or `flashLoan()``.
2. After some sanity checks, the pool transfers the requested amount from reserve(s) to your smart contract, then calls `executeOperation()`` on the receiver contract.    
3. Your smart contract, now holding the flash loaned amount, executes any arbitrary operation in its code.
    * In case of a `flashloanSimple`, your code has finished. You just need to approve the pool the loaned amount + fee. 
    * If you are doing a `flashLoan`,  then depending on the interest rate mode and whether or not you want to open a debt position after the flash loan, you must either approve the 
      flash loan + fee to the pool or provide sufficient collateral or credit delegation should be available to open the debt position.
    * If the amount owed is not available to the pool due to lack of balance or insufficient approved amount, then all changes made in the transaction are reverted.
4. All the above happens in one transaction block.    #### Applications of flash loans       **Arbitrage:** Users can earn a decent profit by trading assets at different platforms that offer different values. With flash loans, traders can launch an arbitrage without any existing assets.     Therefore, arbitrage trades using a flash loan become "cost-free" as long as the traders can afford the gas and flash loan fee to launch the transaction.       **Swapping collateral:**  Crypto asset investors can use collateral swapping to change out their investments without having to repay the debt of the original investment. Collateral swapping lets an investor     replace their position with borrowed assets. Users can choose to pay back their CDP debt and take out all collateral, using part of it to repay flash loans and keeping the remaining     for themselves.       **Self Liquidation:** Markets can be very volatile and can lead to liquidation of the sensitive positions. Liquidation can be quite expensive on certain platforms. There are many applications that make use     of flash loans and liquidate the position on user’s behalf saving the user hefty liquidation fees of the protocol.
 
 **AAVE Portals**        
#### Layer 2 blockchains
In 2020, we had seen a lot of people using Ethereum, and transaction requests increased. However, Ethereum can only handle 30 transactions per second. This limitation caused gas prices to hike and transactions to become expensive.
On Ethereum mainnet, transactions can be slow and difficult, and the proof-of-work model can use a lot of energy. So we need an alternative that can improve these issues without compromising decentralization and security.
Layer 2 chains offer an alternative to the high transaction costs and slow speeds of Ethereum blockchain. The main reason Layer 2 blockchains exist is to increase the scalability of the blockchain. So the need for blockchain bridges arised.


#### What are Blockchain Bridges and Why do we use them? 
Bridges in crypto act as a connection between two different blockchains. This connection is important because, without a bridge, blockchains would be isolated from each other.
However, with a bridge between two blockchains it becomes possible to transfer assets and arbitrary data between them. Thus, blockchain bridges promote the interoperability in the crypto ecosystem and are necessary to make different blockchain networks compatible.
   
   * **Disadvantages of bridges:**
   Smart contract risks:
   This can happen in both trusted and trustless bridge contracts. Bugs in the smart contract can lead it to be hacked and cause loss.
   
   * **Systematic financial risks:**
   The majority of bridges use wrapped assets to mint canonical versions of original assets in the new chain. However, this exposes the bridge to systematic risk of the wrapped asset being exploited.
   
   * **Trust issues:**
   Bridges use third-party for the transfer of assets, this will require the users to put trust on the validator to not engage in activities detrimental to the users, like rag pulling.
   
   * **Nascent stage:**
   It is still unclear how bridges will work in various market conditions.



#### Aave portals and how it simplifies things
Now let us look at how Aave portals provide solutions to the problems posed by Bridges.

Portal's feature seamlessly allows assets to flow between Aave markets on different networks. Aave allows specific whitelist entities or specific bridges to burn aTokens (aTokens are nothing but AAVE’s token, which refers to 
a particular token as aDai refers to Dai) in the source network and instantly minting them on the destination network. The underlying assets are then transferred to the destination network in a deferred manner(postponed manner) 
by passing it to the pool after it has been moved through the bridge. The assets are transferred to the Aave pool on the destination chain after the burning and minting of aTokens.

Portals are authorized for only approved bridges by Aave Governance. The assets are moved under smart contracts, making the transactions highly secure. Transactions with this system are quick and easy. lt helps users overcome the 
difficulties of current bridging protocols, like liquidity fragmentation and non-optimal bridging experience. By reducing liquidity limitations of l2-l2 bridges, the portal will allow for a seamless experience for users, bettering 
the user experience. Many people will be attracted to the Aave portal because of its features, which will in turn increase the amount of capital in Aave markets. Portals act as gateways for alternate Ethereum chains (Evm L1), which 
are often connected to slow-moving centralized exchanges (CeFis). This can complicate onboarding new users, as it can be costly and difficult to reach alternatives. Portals reduce these difficulties by providing security and fast 
transactions, making alt Evm L1 chains attractive and easier to access.


#### How portals work
In order to bridge assets from one chain to another, the user first submits a bridge transaction to a verified bridging protocol (such as Connext). As soon as the transaction is mined, the user has access to the funds on the destination chain. 
Behind the scenes, the bridging protocol mints unbacked aTokens on the destination chain to the intermediate contract, and in turn withdraws and transfers the underlying asset to the user immediately. The bridge contract on L2 then supplies the 
underlying asset and fee to the Aave pool to back the previously minted unbacked aTokens. The "bridge" is used to store assets supplied by multiple users in a pool, and then to batch them together. The "hop" will use tokens to withdraw the assets 
from the pool, and then use its own bridging protocol to transfer the assets from the original to destination chain. The bridge contract in the destination chain will back the minted unbacked tokens, and reduce the fee for using Aave v3 portals. 
This is how portals enable seamless transactions between markets in different networks. Also, the bridges are approved, sand assets are transferred under smart contracts Hence the transactions are secure.

(Note: Only approved bridges use this portal feature, so there is no risk of withdrawing funds from Aave v3. Also, Aave portals are just a feature to transfer assets efficiently, but we need bridging protocols to transfer our assets. There are no 
other core protocols for directly using Aave portals from the user end.) 
>>>>>>> Stashed changes
 
 
