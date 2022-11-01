## Header
This is the course header. This will be added on top of every page. Go to [DoDAO.io](https://www.dodao.io) to know more.

 ---
 
 ## Other Features of AAVE
 
 **Flash Loans**        
#### What are Flash Loans?
* Flash loans are special transactions that allow you to borrow and repay assets, but unlike traditional DeFi borrowing, the money must be repaid within a single transaction. 
* Flash loans do not require any collateral to function, and are instantaneous, hence the term “flash”. 
* Flash loans are typically repaid in the same transaction, and they are only valid for as long as the liquidity remains in the pool. 
* However, if a flash loan trade doesn't return the full amount of liquidity to the pool, the entire transaction will be reversed, which will also reverse all previous actions.

#### Transactions
* A transaction is a way of transferring value or any other type of token using Blockchain. 
* In order to transfer cryptocurrency, you must have a digital wallet. This wallet must have a public and private key. 
* If your wallet is your bank account, your public key is your account number, other users use this to send you assets. 
* Similarly, your private key is your pin code, which allows you to access the assets in your wallet. 
* On every transaction, a fee is added, which acts as an incentive to miners to keep the chain secure.

#### Working of flash loans
##### **`flashLoan`** 
* Allows borrowers to access liquidity of *multiple reserves* in a single *flashLoan* transaction. 
* The borrower also has an option to open a stable or variable rate debt position backed by supplied collateral or 
 credit delegation in this case.

##### **`flashLoanSimple`** 
  * Allows borrowers to access liquidity of *single reserve* for the transaction. 
  * In this case flash loan fee is not waived nor can the borrower open any debt position at the end of the transaction. 
  * This method is gas efficient for those trying to take advantage of simple flash loans with a single reserve asset.

#### Execution Flow
1. Your contract calls the Pool contract, requesting for a flash loan of a certain amount from reserve(s) using `flashLoanSimple()`` or `flashLoan()``.

2. After some sanity checks, the pool transfers the requested amount from reserve(s) to your smart contract, then calls `executeOperation()`` on the receiver contract.

3. Your smart contract, now holding the flash loaned amount, executes any arbitrary operation in its code.
    * In case of a `flashloanSimple`, your code has finished. You just need to approve the pool the loaned amount + fee. 
    * If you are doing a `flashLoan`,  then depending on the interest rate mode and whether or not you want to open a debt position after the flash loan, you must either approve the 
      flash loan + fee to the pool or provide sufficient collateral or credit delegation should be available to open the debt position.
    * If the amount owed is not available to the pool due to lack of balance or insufficient approved amount, then all changes made in the transaction are reverted.

4. All the above happens in one transaction block.

 #### Applications of flash loans

 **Arbitrage:** 
 * Users can earn a decent profit by trading assets at different platforms that offer different values. 
 * With flash loans, traders can launch an arbitrage without any existing assets. 
 * Therefore, arbitrage trades using a flash loan become "cost-free" as long as the traders can afford the gas and flash loan fee to launch the transaction.

 **Swapping collateral:**
 * Crypto asset investors can use collateral swapping to change out their investments without having to repay the debt of the original investment. 
 * Collateral swapping lets an investor replace their position with borrowed assets. 
 * Users can choose to pay back their CDP debt and take out all collateral, using part of it to repay flash loans and keeping the remaining for themselves.

 **Self Liquidation:**
 * Markets can be very volatile and can lead to liquidation of the sensitive positionsand liquidation can be quite expensive on certain platforms.  
 * There are many applications that make use of flash loans and liquidate the position on user’s behalf saving the user hefty liquidation fees of the protocol.
 
 **AAVE Portals**        
#### Layer 2 blockchains 
* Ethereum can only handle 30 transactions per second. This limitation caused gas prices to hike and transactions to become expensive.
* On Ethereum mainnet, transactions can be slow and difficult.
* Layer 2 chains offer an alternative to the high transaction costs and slow speeds of Ethereum blockchain. The main reason Layer 2 blockchains exist is to increase the scalability of the blockchain.

#### What are Blockchain Bridges and Why do we use them? 
* Bridges in crypto act as a connection between two different blockchains. This connection is important because, without a bridge, blockchains would be isolated from each other.
* With a bridge between two blockchains it becomes possible to transfer assets and arbitrary data between them.
   
   **Disadvantages of bridges:**
   
   * **Smart contract risks:**
   This can happen in both trusted and trustless bridge contracts. Bugs in the smart contract can lead it to be hacked and cause loss.
   
   * **Systematic financial risks:**
   The majority of bridges use wrapped assets to mint canonical versions of original assets in the new chain. However, this exposes the bridge to systematic risk of the wrapped asset being exploited.
   
   * **Trust issues:**
   Bridges use third-party for the transfer of assets, this will require the users to put trust on the validator to not engage in activities detrimental to the users, like rag pulling.
   
   * **Nascent stage:**
   It is still unclear how bridges will work in various market conditions.

   * **Complexity:**
   Complexity is another big issue as the user needs to know the various steps needed to transfer the assets. These steps are often not standard and varies from one bridge to another which acts as cause for confusion
   for users.



#### Aave portals and how it simplifies things
* Portal's feature seamlessly allows assets to flow between Aave markets on different networks. 
* Aave allows specific whitelist entities or specific bridges to burn aTokens (aTokens are nothing but AAVE’s token, which refers to a particular token as aDai refers to Dai) 
  in the source network and instantly minting them on the destination network. 
* The underlying assets are then transferred to the destination network in a deferred manner(postponed manner) by passing it to the pool after it has been moved through the bridge. 
* The assets are transferred to the Aave pool on the destination chain after the burning and minting of aTokens.
* Portals are authorized for only approved bridges by Aave Governance. The assets are moved under smart contracts, making the transactions highly secure.
* Portal helps users overcome the difficulties of current bridging protocols, like liquidity fragmentation and non-optimal bridging experience. 
* By reducing liquidity limitations of l2-l2 bridges, the portal will allow for a seamless experience for users, bettering the user experience.
* Portals act as gateways for alternate Ethereum chains (Evm L1), which are often connected to slow-moving centralized exchanges (CeFis). This can complicate onboarding new users, as it can be costly and difficult to 
  reach alternatives. Portals reduce these difficulties by providing security and fast transactions, making alt Evm L1 chains attractive and easier to access.


#### How portals work
* In order to bridge assets from one chain to another, the user first submits a bridge transaction to a verified bridging protocol (such as Connext). 
* As soon as the transaction is mined, the user has access to the funds on the destination chain. 
* Behind the scenes, the bridging protocol mints unbacked aTokens on the destination chain to the intermediate contract, and in turn withdraws and transfers the underlying asset to the user immediately. 
* The bridge contract on L2 then supplies the underlying asset and fee to the Aave pool to back the previously minted unbacked aTokens. 
* The "bridge" is used to store assets supplied by multiple users in a pool, and then to batch them together. 
* The "hop" will use tokens to withdraw the assets from the pool, and then use its own bridging protocol to transfer the assets from the original to destination chain. 
* The bridge contract in the destination chain will back the minted unbacked tokens, and reduce the fee for using Aave v3 portals. 
* Note that, Aave portals are just a feature to transfer assets efficiently, but we need bridging protocols to transfer our assets, there are no other core protocols for directly using Aave portals from the user end.
 
 **AAVE GHO**        
### **Introduction AAVE GHO**

* Aave has introduced GHO, a decentralized multi-collateral, collateral-backed stablecoin pegged to the USD that is fully backed and it is proposed by the Aave DAO.
* Aave aims to provide users more variety and accessible to the a wider user base, to make the Aave stablecoin market more competitive and to generate more revenue for the DAO with the introduction of GHO.


### **What is Stablecoin?**

* Stable coins offer stability that is missing in crypto currencies while also maintaining the staple features of web3 - fast, secure and borderless. 
* The stablecoins are quite popular to the audience that is not crypto-native, helping to scale the technology up to a user base that is not used to it.


### **Types of stablecoins:**

**Fiat-backed stablecoins -** These stablecoins are linked to the value of a fiat currency. The stablecoin issuer needs a centralized banking system in order to back the token with real Fiat money, such as USD.

**Commodity-backed stablecoins -** Similar to fiat-backed stablecoins, stablecoin issuers hold equivalent values of physical commodities. They are backed by commodities such as gold, silver, or oil. Even real estate can be used as collateral for this kind of stablecoin.

**Algorithmic stablecoin -** Algorithmic stablecoins have used an algorithm balancing the supply and demand of the stablecoin to preserve price stability rather than relying on fiat-backing or over-collateralized crypto-backing.

**Collateral-backed stablecoins -** These stablecoins are often generated using decentralized protocols to issue and redeem the tokens and are backed by other digital assets provided as collateral.

### **How GHO would work:**

* GHO is minted by borrowing it in an overcollateralized fashion and burnt when the borrow position is repaid
* The borrowing follows the same principle as borrowing in Aave, the user will also continue to gain interest on the assets he used as collateral.
* The interest rate for GHO will be initially determined by Aave DAO, it will be a stable interest rate which can be adapted according to market conditions, providing certainty for the borrowers.  
* The DAO will be able to manage GHO’s native interest rate through a governance process. 
* Like other assets listed on the Aave protocol, an aToken and debt token for GHO will be deployed on the protocol and be registered on the Ethereum market once GHO is integrated to Aave protocol.

### **Facilitators:**

* Facilitators are entities approved by Aave governance that can trustless mint and burn GHO tokens.
* The facilitator will be able to apply their own generation strategies for minting GHO. 
* Each facilitator will be given a bucket value, signifying the upper limit of the amount of GHO a facilitator can generate.  
* The first facilitator will be the Aave market on Ethereum. Governance will be able to determine and assign this facilitator a specific bucket capacity to bootstrap the GHO liquidity and the GHO market. 

### **Pros and cons of collateral backed and decentralized stablecoins like GHO:**

#### **Cons:**

**Collateral asset risk -** Centralized entities have the ability to blacklist and freeze addresses from being able to use their currency.

**Flash crash conditions -** A sudden drop in the value of the collateralized asset would result in a situation where liquidators are unable to buy your collateral to pay off the debt.

**Pool configuration and Risk management -** The users are to trust the DAO to have the appropriate pool configuration and risk management measures in place.

**Smart contract risk -** The possibility of smart contract bugs and failures which could result in huge losses or assets.

#### **Pros:**

**Transparency and flexibility -** Transparent and fully decentralized and quick to turn into other crypto assets

**Trustless -** No external custodians, all assets are controlled by Ethereum accounts.

When it comes to GHO, 

**Risk management -** Aave DAO incentivizes users for long-term success (for example, discount model) , the community has control over the stable rate of GHO after its release and the option to levy maximum and minimum caps on borrowing also helps to provide considerable risk management to GHO. 

**Flash crash prevention -**  Aave protocol, throughout its past has had very conservative LTVs (Loan To Value ratio), an effective liquidation mechanism and a community of liquidators which helps them mitigate this risk more than any other platform. 

**Reduced collateral asset risk -** Assets allowed as collateral are determined by the DAO with considerable influence from Gauntlet who provides high quality risk management services to Aave.
 
 **Applications that can be built on top of AAVE**        
**NFT lending and borrowing -** 
* When you buy NFTs the money that you invested in it is locked, it is not possible to gain interest on it or generate liquidity without selling in case need arises.
* The user can offer their NFT as collateral to borrow assets or lend their NFT to generate liquidity, invest the loaned money somewhere else, and to gain interest on their lend position. 

**Real world assets -** 
* The user is able to loan assets against a tokenized form of the real estate, commodity or a possession they own. 
* By fractionalizing the real world asset into multiple tokens, the user can decide what percent of the asset is to be used as collateral. 

**Under collateralized borrowing -** 
* Overcollateralization acts as an obstacle that limits participation of general users in the DeFi ecosystem. 
* Applications that verify a user’s credibility by running checks on linkedin, and other social profiles, or generate credit score of a user using AI could be used to provide under-collateralized loans. 

**Liquidation strategies -** 
* Applications that can allow the user to borrow from multiple pools in one borrow position can help with liquidity issues in the protocols.
* This paves way for algorithms that allow users to get loans at the lowest premium possible.  
* Applications providing strategies that benefit both the protocol and user by generating or safeguarding liquidity for the protocol whilst also providing value for the user can be developed.
 
 **Applications that are built on top of AAVE**        

Let us look at some of the exciting and innovative applications that have developed on top of AAVE.

### Examples of Applications build on top of AAVE

 ####**Mean finance:**
 * DCA stands for Dollar Cost Average, it is an investing method adopted by users in order to minimize possible losses by investing a fixed amount of money in fixed periods of time. 
 * Mean finance brings two yield related project one building on top of the other both using AAVE, first is a dollar-cost-averaging(DCA) product that deposits funds waiting to be swapped into investment token into AAVE to earn yield.
 * Second is a product that rather that DCA-ing the initial investment DCA’s earned yield into a selected asset.
 
 ####**Nomis:**
 * Overcollateralized loans act as an obstacle towards DeFi's accessibility to mainstream audience. 
 * This crypto protocol, based on a mathematical prediction model, use AI trained in hierarchical analysis to generate decentralized credit scores. 
 * They offer users crypto loans on DeFi platforms with better terms (lower interest, less collateral) dependant on their generated credit score.
 
 ####**Hashspace:**
 * A game that integrates AAVE’s yield generation and Lens protocols social graph into a socialFi like game, helping users learn and discover more about the DeFi ecosystem in a fun way.
 
 ####**Polypus:**
 * Polypus is a lending protocol using NFTs as collateral offering good LTV and instant borrowing to the users. 
 * The protocol builds an offer book in the contract from the best to worst LTV for a given loan duration, When someone borrows, they just take the best offers in the order. 
 * If a borrower doesn’t repay before the due date, their assets are sold in a dutch auction.
 * Unmatched liquidity providers will still earn a yield on AAVE.
 
 
 
