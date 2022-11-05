## Header
This is the course header. This will be added on top of every page. Go to [DoDAO.io](https://www.dodao.io) to know more.

 ---
 
 ## Other Features of AAVE
 
 **Flash Loans**        
### **What are Flash Loans?**
Flash loans are special transactions that allow you to borrow and repay assets, but unlike traditional DeFi borrowing, the money must be repaid within a single transaction. 
Flash loans do not require any collateral to function, and are instantaneous, hence the term “flash”. Flash loans are essentially like short-term loans that are codified by 
smart contracts. This means that the terms of the loan are written in code, which helps to prevent funds from being transferred out of one account to another unless certain conditions 
have been met. Flash loans are typically repaid in the same transaction, and they are only valid for as long as the liquidity remains in the pool. However, if a flash loan trade doesn't 
return the full amount of liquidity to the pool, the entire transaction will be reversed, which will also reverse all previous actions. This helps to ensure that funds are safe during the 
event of a flash loan.

### **Blockchain Transactions**
A transaction is a way of transferring value or any other type of token using Blockchain. In order to transfer cryptocurrency, you must have a digital wallet. This wallet must have a public 
and private key. You can think of it like this: your wallet is your bank account, your public key is your account number, other users use this to send you assets. Your private key is your pin code, 
which allows you to access the assets in your wallet. Once you have connected your wallet, you can use various decentralized exchanges and decentralized finance platforms to complete transactions. 
On every transaction, a fee is added, which acts as an incentive to miners to keep the chain secure.
 
### **Working of Flash loans**
`flashLoan`: Allows borrowers to access liquidity of *multiple reserves* in a single *flashLoan* transaction. The borrower also has an option to open a stable or variable rate debt position backed by supplied collateral or 
 credit delegation in this case.

`flashLoanSimple`: Allows borrowers to access liquidity of *single reserve* for the transaction. In this case flash loan fee is not waived nor can the borrower open any debt position at the end of the transaction. 
 This method is gas efficient for those trying to take advantage of simple flash loans with a single reserve asset.


### **Execution Flow**
Here is an example of an execution flow for developers,

1. Your contract calls the Pool contract, requesting for a flash loan of a certain amount from reserve(s) using `flashLoanSimple()` or `flashLoan()`.
2. After some sanity checks, the pool transfers the requested amount from reserve(s) to your smart contract, then calls `executeOperation()` on the receiver contract.    
3. Your smart contract, now holding the flash loaned amount, executes any arbitrary operation in its code.
    * In case of a `flashloanSimple`, your code has finished. You just need to approve the pool the loaned amount + fee. 
    * If you are doing a `flashLoan`,  then depending on the interest rate mode and whether or not you want to open a debt position after the flash loan, you must either approve the 
      flash loan + fee to the pool or provide sufficient collateral or credit delegation should be available to open the debt position.
    * If the amount owed is not available to the pool due to lack of balance or insufficient approved amount, then all changes made in the transaction are reverted.
4. All the above happens in one transaction block.    #### Applications of flash loans       **Arbitrage:** Users can earn a decent profit by trading assets at different platforms that offer different values. With flash loans, traders can launch an arbitrage without any existing assets.     Therefore, arbitrage trades using a flash loan become "cost-free" as long as the traders can afford the gas and flash loan fee to launch the transaction.       **Swapping collateral:**  Crypto asset investors can use collateral swapping to change out their investments without having to repay the debt of the original investment. Collateral swapping lets an investor     replace their position with borrowed assets. Users can choose to pay back their CDP debt and take out all collateral, using part of it to repay flash loans and keeping the remaining     for themselves.       **Self Liquidation:** Markets can be very volatile and can lead to liquidation of the sensitive positions. Liquidation can be quite expensive on certain platforms. There are many applications that make use     of flash loans and liquidate the position on user’s behalf saving the user hefty liquidation fees of the protocol.
 
 **AAVE Portals**        
### **Layer 2 blockchains**
In 2020, we had seen a lot of people using Ethereum, and transaction requests increased. However, Ethereum can only handle 30 transactions per second. This limitation caused gas prices to hike and transactions to become expensive.
On Ethereum mainnet, transactions can be slow and difficult. So we need an alternative that can improve these issues without compromising decentralization and security.
Layer 2 chains offer an alternative to the high transaction costs and slow speeds of Ethereum blockchain. The main reason Layer 2 blockchains exist is to increase the scalability of the blockchain. 


### **What are Blockchain Bridges and Why do we use them?** 
Bridges in crypto act as a connection between two different blockchains. This connection is important because, without a bridge, blockchains would be isolated from each other.
However, with a bridge between two blockchains it becomes possible to transfer assets and arbitrary data between them. Thus, blockchain bridges promote the interoperability in the crypto ecosystem and are necessary to make different blockchain networks compatible.
   
   * **Disadvantages of bridges:**
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



### **AAVE portals and how it simplifies things**
Now let us look at how AAVE portals provide solutions to the problems posed by Bridges.

The Portal's feature on AAVE allows for tokenized assets to flow frictionlessly between markets on different networks. AAVE allows for certain whitelisted entities or specific bridges to 'burn' aTokens in the source network and instantly 
mint them on the destination network. The actual underlying assets are then transferred to the destination network at a later time by being passed to the pool after it has been moved through the bridge.. The assets are transferred to the AAVE 
pool on the destination chain after the burning and minting of aTokens.

Portals are only authorized for approved bridges by AAVE Governance, with transactions being completed through secure smart contracts. This system is quick and easy to use, helping users overcome the difficulties they may experience with current 
bridging protocols - like liquidity fragmentation and non-optimal bridging experience. By reducing liquidity limitations of l2-l2 bridges, the portal will allow for a more seamless experience for users, greatly improving the overall user experience.
Many people will be attracted to the AAVE portal because of its features, which will in turn increase the amount of capital in AAVE markets. Portals act as gateways for alternate Ethereum chains (Evm L1), which 
are often connected to slow-moving centralized exchanges (CeFis). This can complicate onboarding new users, as it can be costly and difficult to reach alternatives. Portals reduce these difficulties by providing security and fast 
transactions, making alt Evm L1 chains attractive and easier to access.


### **How portals work**
In order to bridge assets from one chain to another, the user first submits a bridge transaction to a verified bridging protocol (such as Connext). As soon as the transaction is mined, the user has access to the funds on the destination chain. 
Behind the scenes, the bridging protocol mints unbacked aTokens on the destination chain to the intermediate contract, and in turn withdraws and transfers the underlying asset to the user immediately. The bridge contract on L2 then supplies the 
underlying asset and fee to the AAVE pool to back the previously minted unbacked aTokens. The "bridge" is used to store assets supplied by multiple users in a pool, and then to batch them together. The "hop" will use tokens to withdraw the assets 
from the pool, and then use its own bridging protocol to transfer the assets from the original to destination chain. The bridge contract in the destination chain will back the minted unbacked tokens, and reduce the fee for using AAVE v3 portals. 
This is how portals enable seamless transactions between markets in different networks. Also, the bridges are approved, and assets are transferred under smart contracts Hence the transactions are secure.

(Note: Only approved bridges use this portal feature, so there is no risk of withdrawing funds from AAVE v3. Also, AAVE portals are just a feature to transfer assets efficiently, but we need bridging protocols to transfer our assets. There are no 
other core protocols for directly using AAVE portals from the user end.) 
 
 **AAVE GHO**        
### **Introduction AAVE GHO**

AAVE has introduced GHO, a decentralized multi-collateral, collateral-backed stablecoin that is fully backed. 
A proposal has been made by the AAVE DAO for the introduction of a native decentralized, collateral-backed stablecoin, GHO, which will be pegged to USD.
AAVE aims to provide users more variety and accessible to a wider user base, to make the AAVE stablecoin market more competitive and to generate more revenue for the DAO 
with the introduction of their own stablecoin, GHO. Before jumping into what GHO is, let us get a basic introduction of stablecoins

### **What is Stablecoin?**

Stable coins offer stability that is missing in crypto currencies while also maintaining the staple features of web3 - fast, secure and borderless. The stablecoins are quite popular to the audience that is not crypto-native. 
They help in furthering the technology by being attractive to a user base that is afraid of volatility or about getting started in the crypto world.


#### **Types of stablecoins:**

**Fiat-backed stablecoins -** These stablecoins are linked to the value of a fiat currency. The stablecoin issuer needs a centralized banking system in order to back the token with real Fiat money, such as USD.

**Commodity-backed stablecoins -** Similar to fiat-backed stablecoins, stablecoin issuers hold equivalent values of physical commodities. They are backed by commodities such as gold, silver, or oil. Even real estate can be used as collateral for this kind of stablecoin.

**Algorithmic stablecoin -** Algorithmic stablecoins have used an algorithm balancing the supply and demand of the stablecoin to preserve price stability rather than relying on fiat-backing or over-collateralized crypto-backing. On-chain collateral or conventional off-chain collateral are not used in this approach. 
                              Instead, the value of a second token serves as collateral for the stablecoin.


    **Collateral-backed stablecoins -** Since trustless systems and decentralization are the foundations of the crypto ecosystem, stablecoin protocols that are not controlled by a central entity had to be developed. These stablecoins are often generated using decentralized protocols to issue and redeem the tokens and are backed by other digital assets.

### **How GHO would work:**

Like with other stablecoins, GHO will be minted when the user satisfies the conditions put forth by the stablecoin minter. The minting process of GHO is different from that of USDC, where the user can mint one USDC with one dollar. GHO is minted by borrowing it in an overcollateralized fashion, though it does not work exactly like 
traditional borrowing in AAVE because the borrowed asset in this case (GHO) is minted on borrowing. The borrowing follows the same principle as borrowing in AAVE, the user will also continue to gain interest on the assets he has collateralized with, while being charged interest for his borrow position of GHO. When the user borrows, 
GHO is minted and when the borrow position is repaid, GHO is burnt. The interest rate for GHO will be initially determined by AAVE Dao, it will be a stable interest rate which can be adapted according to market conditions. With the introduction of GHO, the DAO will be able to manage GHO’s native interest rate through a governance process, 
which will be outlined in a future proposal. This means that GHO’s monetary policy will be controlled in a decentralized way by AAVE governance. The stable rate levied on GHO will provide certainty for the borrowers which is seen as synonymous with stablecoins. Like other assets listed on the AAVE protocol, an aToken and debt token for GHO will be 
deployed on the protocol and be registered on the Ethereum market once GHO is integrated to AAVE protocol.

### **Facilitators:**

With GHO, AAVE introduces the concept of facilitators. Facilitators are entities that can trustless mint and burn GHO tokens. The facilitators have to be approved by AAVE governance. Once approved, the facilitator will be able to apply different generation strategies for minting GHO. 
Each facilitator will also be given a “bucket” value. Bucket is a term made up by AAVE Dao to specify the upper limit of the amount of GHO a facilitator can generate.  Since the facilitators are able to mint GHO independently, it is important that they be regulated in this way to avoid 
misuse of the asset. The first facilitator will be the AAVE market on Ethereum. Governance will be able to determine and assign this facilitator a specific bucket capacity to bootstrap the GHO liquidity and the GHO market. 

### **Pros and cons of collateral backed and decentralized stablecoins like GHO:**

  #### **Pros:**

**Transparency and flexibility -** Transparent and fully decentralized and quick to turn into other crypto assets

**Trustless -** No external custodians, all assets are controlled by Ethereum accounts.

When it comes to GHO, 

**Risk management -** AAVE DAO incentivizes users for long-term success (for example, discount model) , the community has control over the stable rate of GHO after its release and the option to levy maximum and minimum caps on borrowing also helps to provide considerable risk management to GHO. 

**Flash crash prevention -**  AAVE protocol, throughout its past has had very conservative LTVs (Loan To Value ratio), an effective liquidation mechanism and a community of liquidators which helps them mitigate this risk more than any other platform. 

**Reduced collateral asset risk -** Assets allowed as collateral are determined by the DAO with considerable influence from Gauntlet who provides high quality risk management services to AAVE.


#### **Cons:**

**Collateral asset risk -** In most cases the collateral provided for the borrowing of stablecoins is a centralized cryptocoin (to reduce the risk of liquidation due to volatility), centralized entities have the ability to blacklist and freeze addresses from being able to use their currency.

**Flash crash conditions -** A sudden drop in the value of the collateralized asset could result in loss for the user who has borrowed stablecoin in an overcollateralized fashion. The sudden drop would result in a situation where liquidators are unable to buy your collateral to pay off the debt.

**Pool configuration and Risk management -** The users are to trust the DAO to have the appropriate pool configuration and risk management measures in place. Because all users are not experts who can understand the working of these pools and the implications of the risk management measures employed by the DAO.

**Smart contract risk -** The possibility of smart contract bugs and failures which could result in huge losses or assets being frozen forever always lingers in the case of blockchain development. 
 
 **Applications that can be built on top of AAVE**        
Let us take a look at some of the possible ideas for applications that can be build on top of AAVE's lending and borrowing.

### Other Application that can be done on top of Lending and Borrowing

**NFT lending and borrowing -** NFTs are gaining a lot of popularity among a non crypto native audience. Developers can and have already taken advantage of this scenario to bring them into the crypto ecosystem by creating applications that employ basic borrowing and lending with NFTs. When you buy NFTs the money 
 that you invested in it is locked, when it could be gaining interest in some investment, or it could be possible that the user needs liquidity. In these cases, the user can offer their NFT as collateral to borrow assets. Lending NFTs is also an option in case the borrower wants to overcollateralize and borrow the NFT, 
 sell it if there is a possibility of profit, buy it or pay back the loan and get back collateral in case the NFTs value does not appreciate, given the lender accepts the terms and conditions that would be needed for such a system. 

**Real world assets -** The combination of asset tokenization and DeFi lending and borrowing could result in some interesting applications where the user is able to loan assets against a tokenized form of the real estate, commodity or a possession they own. By fractionalizing the real world asset into multiple tokens, 
 the user can also decide what percent of it is to be used as collateral. Real world assets can also be borrowed, gaining the interest (example, rent) that the asset token can accrue and the paying interest for borrowing the real world asset token. 

**Under collateralized borrowing -** Overcollateralization is a great system but it acts as an obstacle that limits participation of the non crypto native user base from entering the DeFi ecosystem. We could come up with applications that verify a user’s credibility by running checks on linkedin, and other social profiles, 
 or generate credit score of a user using AI which could allow the user to take undercollateralized loans. 

**Liquidation strategies -** Applications that can allow the user to borrow from multiple pools in one borrow position can help with liquidity issues in the protocols while also providing the user with the lowest premium possible.  Other applications that come up with strategies that benefit both the protocol and user by 
 generating or safeguarding  liquidity for the protocol whilst also providing value for the user can be developed.
 
 **Applications that are built on top of AAVE**        

Let us look at some of the exciting and innovative applications that have developed on top of AAVE.

### Examples of Applications build on top of AAVE

 #### **Mean finance:**
 DCA stands for dollar cost average, it is an investing method adopted by users in order to minimize possible losses by investing a fixed amount of money in fixed periods of time, this way losses are compensated with the profits made from investing in another time. Mean finance brings two yield related project one building on 
 top of the other both using AAVE, first is a dollar-cost-averaging(DCA) product that deposits funds waiting to be swapped into investment token into AAVE to earn yield, second is a product that rather that DCA-ing the initial investment DCA’s earned yield into a selected asset.
 
 #### **Nomis:**
 The lack of undercollateralized in DeFi is something that keeps a lot of users from using it, it acts as an obstacle towards scaling DeFi to mainstream audience. This crypto protocol, based on a mathematical prediction model and AI that generates decentralized credit scores. They use AI trained in hierarchical analysis, since 
 there is a lack of past data of the crypto loan defaults for the development of predicting mathematical models based on statistical approaches. They offer users crypto loans on DeFi platforms with better terms (lower interest, less collateral) dependant on their generated credit score.
 
 #### **Hashspace:**
 A game that integrates AAVE’s yield generation and Lens protocols social graph into a socialFi like game. A DeFi product discovery game that makes it fun for players to learn and test out new DeFi products, solutions and protocols.
 
 #### **Polypus:**
 Polypus is a lending protocol using NFTs as collateral differentiating itself from the competition by offering better LTV and instant borrowing. The suppliers have to choose the LTV they are comfortable with. The protocol builds an offer book in the contract from the best to worst LTV for a given loan duration. When someone borrows, 
 they just take the best offers in the order. If a borrower doesn’t repay before the due date, their assets are sold in a dutch auction. The last part of our borrower-friendly experience is that borrowers enjoy a fixed interest rate. Suppliers only get interest if their offer was good enough to be automatically taken. Unmatched liquidity 
 providers will earn a yield on AAVE.
 
 
