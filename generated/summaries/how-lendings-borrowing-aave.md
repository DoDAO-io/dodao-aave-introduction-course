## Header
This is the course header. This will be added on top of every page. Go to [DoDAO.io](https://www.dodao.io) to know more.

 ---
 
 ## How to Lend and Borrow in AAVE
 
 **How to connect wallet to Aave**        
Aave is a decentralized finance platform that allows users to lend and borrow assets. In order to do so, users need to have a cryptocurrency wallet set up. 
Once the wallet is set up, they can then commence lending and borrowing on the Aave platform. Follow this link for Aave's Dapp: [Aave app](https://app.aave.com/).

Follow the following steps to connect the wallet to Aave

1. we need to click the "connect wallet" button and select your preferred wallet for lending and borrowing and connect it.
2. After connecting the wallet, we can select our preferred network for lending and borrowing assets.
3. We need to pay gas fees for lending and borrowing, similar to transactions so we need some native tokens to pay the gas fees.
 
 **How to lend in Aave**        
Follow the following steps to lend assets in  Aave

1. In order to supply tokens, please click on the 'Supply' button next to the token. After that, a new window will pop up with additional details.
2. Fill in the required transaction details in the fields provided and click on the 'Supply' button in that new window.
3. Now the connected wallet will pop up and ask you to confirm the transaction. Confirm the transaction and wait for it to finish.
4. Please keep this window open until the transaction is completed. After the transaction has been finalized, we can add the atokens to our wallet to track the balances.

This procedure is same for all networks. Tokens which are indicated by the tick mark in the "can be collateral" column can be used as a collateral.
 
 **How to borrow in Aave**        
Follow the following steps to borrow assets in  Aave

1. In order to borrow, you will need to put up some collateral first. After you have supplied the required collateral, you can click “borrow” in the borrowing column.
2. After clicking the borrowing button, a new window will appear with details about the borrowing process. We need to fill in the necessary information and hit the borrow button. 
   We can choose a stable or variable rate for our borrowing.
3. Keep an eye on the health factor to make sure it stays at a reasonable level.
4. Now the connected wallet will pop up and ask you to confirm the transaction. Confirm the transaction and wait for it to finish.
5. Please keep this window open until the transaction is completed. After the transaction has been finalized, we can add the tokens to our wallet.
 
 **How ATokens works in Lending**        
The ATokens are interest-bearing derivative tokens that are minted and burned upon Deposit and Redeem. ATokens are pegged to corresponding asset in the ratio 1:1. 
ATokens can be stored and transferred. ATokens are minted in a 1:1 ratio to the deposited amount using the `Deposit` function. If these minted tokens are added to the wallet, 
users will be able to track their balances from the wallet itself instead of having to open Aave's app. The ATokens can be transferred or traded in a similar 
way to normal tokens. When a user withdraws their assets, the `redeem` function is executed which will effectively "burn" the ATokens and provide the user with their assets in a 1:1 ratio.

The interest rate is based on the earn rate of the Aave. The accrual of interest never stops until the lent assets are withdrawn.
The ATokens include EIP-20/ERC20 token methods with a few modifications, as well as EIP-2612. 
 
 **How Borrowing works in Aave**        
Borrowing in Aave implements tokenisation concept similar to lending. When a user borrows assets, the `borrow` function is called and debt tokens are minted in a 1:1 ratio to the corresponding borrowed asset. 
Debt tokens implement most of the functionalities in ERC-20 with the exeception of transferring properties. Debt tokens are interest-accruing tokens that accrue interest according to the interest rate. 
There are two types of debt tokens: stable debt tokens and variable debt tokens. 

Debt tokens are minted according to the type of interest rate. The `repay` function is executed when a user repays a loan, which will burn the debt tokens in the 1:1 ratio to the corresponding repaid asset.
Users can change the interest rate from stable to variable or vice-versa at any time. 

### Calculation of interest rates

#### Important  Terms

1. U = Utilization rate   = B<sub>t </sub>/ L<sub>t </sub>. Where B<sub>t </sub>is the total assets borrowed and L<sub>t</sub> is the total liquidity. Each reserve have its own Utilization rate. 
2. U<sub>optimal </sub> = expected Utilization rate or targeted Utilization rate.
3. R<sub>o</sub> = Base Variable borrow rate. It is zero for B<sub>t</sub> =0.
4. R<sub>slope1</sub> = It is a constant called as interest rate slope below optimal
5. R<sub>slope2</sub> = It is a constant called as interest rate slope above optimal
6. O<sub>ratio</sub> = Optimal stable to total debt ratio
7. Base<sub>s</sub> = Base stable borrow rate


#### Variable rate calculation

The interest rate R<sub>t </sub> follows the model:

If U≤U<sub>optimal</sub>   

R<sub>t</sub> = R<sub>o </sub>+ U/U<sub>optimal </sub> * R<sub>slope1</sub>

If U>U<sub>optimal</sub>

R<sub>t</sub> = R<sub>o </sub>+ [(U-U<sub>optimal</sub>)/(1-U<sub>optimal</sub>)]*R<sub>slope2</sub>


### Stable Interest rate calculation

Base<sub>s</sub> = R<sub>slope1</sub> + offset<sub>base   </sub>;   E<sub>util</sub> = 10^27 - U<sub>optimal</sub>

Ratio<sub>st</sub> = debt<sub>stable</sub>/Total debt ;  where Total debt = debt<sub>stable</sub>+<sub> </sub>debt<sub>variable</sub>

This ratio is called as stable to debt ratio.

Interest rate R<sub>s</sub> is calculated as follows :

If U > U<sub>optimal</sub>

R<sub>s </sub>= Base<sub>s </sub> + R<sub>slope1 </sub>+ R<sub>slope2</sub>*[(U-U<sub>optimal</sub>)/E<sub>util</sub>]

Otherwise

R<sub>s </sub>= Base<sub>s </sub> + R<sub>slope1 * </sub>(U/U<sub>optimal</sub>)

The interest rate rebalances when Ratio<sub>st</sub>> O<sub>ratio</sub>

R<sub>s</sub>  =  R<sub>s</sub>  + offset<sub>excess</sub> * [(ratio-O<sub>ratio</sub> )/10^27-O<sub>ratio</sub>] 
 
 
