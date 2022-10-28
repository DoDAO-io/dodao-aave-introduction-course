## Header
This is the course header. This will be added on top of every page. Go to [DoDAO.io](https://www.dodao.io) to know more.

 ---
 
 ## How to Lend and Borrow in AAVE
 
 
---

##### Which of the following is required for lending in Aave?  

- [ ]  Users need to complete the KYC process
- [x]  Users need to have a cryptocurrency wallet
- [ ]  Users need to be above 25 years
- [ ]  The assets should be lent more than 100 dollars
  
Hint: Wallet
         
Explanation: Aave is a popular cryptocurrency lending platform that requires users to have only one cryptocurrency wallet to start lending. There are no age restrictions or KYC requirements in order to start lending on Aave.

Sub Topics: connect-aave
 

---

##### Which of the following is/are correct about lending in Aave?  

- [x]  Users must have some native tokens to pay gas fees
- [ ]  Users can use any token to pay the gas fees for lending
- [x]  Users can add aTokens to their wallet to track their balances
- [ ]  Users can lend only up to a maximum value of 10000 dollars
  
Hint: noHint
         
Explanation: In order to pay gas fees, users need to have some native tokens. For example, if you want to lend in the Ethereum network, 
you need to own some ether to pay the gas fees for the transaction. By adding aTokens to their wallet, users can track their balances.


Sub Topics: lending-Aave
 

---

##### The procedure for lending is different for different networks  

- [ ]  True
- [x]  False
  
Hint: All networks have same procedure
         
Explanation: While the procedure for lending is the same for all networks, the market for different networks can vary. Therefore, the above statement is false.

Sub Topics: lending-Aave
 

---

##### Which of the following is correct about interest rates in borrowing?  

- [ ]  Users can only borrow assets at a stable interest rate
- [ ]  Users can only borrow assets at a variable interest rate
- [x]  Users can borrow assets at both stable and variable rate
  
Hint: noHint
         
Explanation: Loans can be borrowed in both stable and variable interest rates so that users can choose what is best for them and their current financial situation. 
Interest rates can also be changed by the user at any time if their needs should happen to change in the future.


Sub Topics: borrowing-Aave
 

---

##### What is the repayment period for the loan?  

- [x]  There is no time limit for repayment
- [ ]  Borrowed loans must be repaid before 70 days of borrowing
- [ ]  The repayment time for a loan depends on the amount borrowed
- [ ]  Users need to repay the loans when their health factor reaches 10
  
Hint: Norepayment
         
Explanation: In Aave, there is no set repayment period or deadline for borrowers. Instead, users must make sure to have a good health factor to prevent liquidation of collateral.

Sub Topics: borrowing-Aave
 

---

##### Which of the following order is correct for borrowing loans in Aave?

A- Confirm the transaction using the connected wallet
B- To borrow, click the "Borrow" button. A new window will pop up. Fill in the required fields and click "Borrow."
C- Do not close the window until the transaction is complete
D- Connect the wallet and lock the collateral for borrowing
E- After the transaction has been finalized. We can add the tokens to our wallet
  

- [ ]  A=>B=>C=>D=>E
- [ ]  B=>E=>A=>C=>D
- [x]  D=>B=>A=>C=>E
- [ ]  E=>D=>C=>B=>A
  
Hint: Starts with connecting the wallet
         
Explanation: The first thing you need to do is connect your wallet and lock your collateral. Then, click the borrow button and fill in the required details. After that, confirm 
the transaction using your wallet. Once the transaction is complete, the tokens will be added to your wallet.


Sub Topics: borrowing-Aave
 

---

##### Which of the following factor(s) is/are considered more significant while borrowing?  

- [x]  Interest rates for borrowing
- [ ]  Utilization ratio
- [x]  Health factor
- [x]  Liquidation threshold of the collateral
  
Hint: Interest rate and health factor
         
Explanation: Health factor should be considered while borrowing users need to make sure that they have a good health factor. Users also need to check the interest rates and liquidation ratio of collateral to ensure the safety of collateral.

Sub Topics: borrowing-Aave
 

---

##### How the maximum borrowing limit is determined while borrowing assets?  

- [ ]  It is determined randomly using the SHA-256 algorithm
- [x]  It is determined based on the loan-to-value (LTV) of the collateral
- [ ]  It is determined based on the lending rate of the asset
- [ ]  None of these
  
Hint: Loan-to-Value
         
Explanation: The maximum loan amount you're able to take out is based on the Loan-to-Value (LTV) ratio of the collateral you're putting up.

Sub Topics: borrowing-Aave
 

---

##### What assets can be used as collateral?  

- [ ]  All assets can be used as collateral
- [x]  Assets that are marked with a tick in the "can be collateral" column can be used as collateral
- [ ]  Stablecoins like USDC, DAI, etc. can be used as collateral
- [ ]  Only ether can be used as collateral
  
Hint: can be collateral
         
Explanation: Assets that are marked with a tick in the "can be collateral" column can be used as collateral. Other assets cannot be used as collateral. Additionally, users can choose whether or not to use a particular asset as collateral.

Sub Topics: lending-Aave
 

---

##### How much ATokens will be minted after lending 1000 USDC in Aave?  

- [ ]  2000 aUSDC
- [ ]  3000 aUSDC
- [x]  1000 aUSDC
- [ ]  500 aUSDC
  
Hint: 1:1 ratio
         
Explanation: ATokens are minted when corresponding assets are lent, in a 1:1 ratio. So, for example, 1000aUSDC will be minted for 1000 USDC that is lent. Atokens can be stored and transferred like other ERC20 tokens.

Sub Topics: working-ATokens
 

---

##### Which of the following EIP's are implemented by ATokens in Aave?  

- [x]  EIP-20/ERC-20
- [ ]  EIP-162
- [ ]  EIP-137
- [x]  EIP-2612
  
Hint: EIP-20 and EIP-2612
         
Explanation: The ATokens include EIP-20/ERC20 token methods with a few modifications, as well as EIP-2612.

Sub Topics: working-ATokens
 

---

##### Is it possible to transfer ATokens from one wallet to another wallet?  

- [x]  Yes, ATokens can be transferred from one wallet to another wallet
- [ ]  No, It can't be transferred
- [ ]  can't be determined
  
Hint: ERC-20 tokens
         
Explanation: The ATokens include the standard EIP-20/ERC20 token methods. This means that ATokens can be transferred in the same way as other tokens.

Sub Topics: working-ATokens
 

---

##### When does accrual of interest on lent assets end?  

- [ ]  It will be stopped when the asset is used as collateral
- [ ]  It will be stopped when Health factor is zero
- [x]  It will be stopped when the assets are withrawn
- [ ]  None of these
  
Hint: withdraw
         
Explanation: Accrual of interest only stops when assets are withdrawn. Even if an asset is lent as collateral, accrual of interest will not stop.


Sub Topics: working-ATokens
 

---

##### What happens when a user withdraws or redeems their assets in Aave?  

- [x]  ATokens are burnt and assets are supplied in 1:1 ratio of burnt ATokens
- [ ]  Liquidation call will occur
- [x]  The function `redeem` will be executed
- [ ]  Aave will transfer the assets to the user's connected bank account
  
Hint: noHint
         
Explanation: ATokens are destroyed or "burned" when they are redeemed, similar to how new coins are minted. The function `redeem` executes this operation whenever a user withdraws assets. 
This function will burn the ATokens and supply the assets at a 1:1 ratio of burnt ATokens to the user whenever they withdraw.


Sub Topics: working-ATokens
 

---

##### Consider a case, Jack is a lender who wants to lend 1000 USDC in return for interest. He chooses Aave as his lending platform and deposits 1000 USDC. 
In return, he gets 1000 aUSDC and adds the atokens to his wallet. Luna was Jack's friend, and she asked him for 200 USDC. However, Jack had already lent out all his USDC, 
so he sent her 200 aUSDC instead. Luna kept the aUSDC as is, and after a few days, she connected her wallet to Aave.

Which of the following option(s) is/are correct for the above case?
  

- [ ]  The accrual of interest will be stopped for the sent ATokens
- [x]  The accrual of interest will not be stopped. It will accrued for both jack and Luna
- [ ]  Jack's remaining aUSDC will accrue interest but Luna's 200 aUSDC will accrue interest only when she connect her wallet to the Aave's app
- [ ]  Jack can use his 800aUSDC as collateral but Luna cannot use her 200aUSDC as a collateral
  
Hint: noHint
         
Explanation: ATokens are transferable tokens that earn interest. Even though Jack owned ATokens through his wallet, any wallet can accrue interest from them. 
Therefore, 200 aUSDC will earn interest for Luna even though she didn't connect her wallet to Aave. the ATokens of Luna can be used as a collateral if it is indicated.


Sub Topics: working-ATokens
 

---

##### Which of the following factor(s) is/are correct?  

- [x]  Borrowing implements tokenisation in order to represent the borrow position
- [ ]  users can take out a loan against an asset, which must have a minimum value of 35 ETH in order to serve as collateral
- [x]  Loan borrowed are overcollaterlized
- [x]  The debt tokens are minted in 1:1 ratio to the corresponding borrowed asset
  
Hint: tokenisation
         
Explanation: Borrowing in Aave implements the concept of tokenisation, which is similar to lending. The loans that are borrowed are overcollateralised in order to 
reduce the effect of volatility of the assets and to maintain the security of the assets.


Sub Topics: borrowing-technical
 

---

##### Debt tokens can be transferred and stored like ATokens.  

- [ ]  True
- [x]  False
  
Hint: noHint
         
Explanation: Debt tokens implement most of the functionalities in ERC-20 with the exeception of transfer functions like "transfer" and "allowance".
This means that debt tokens cannot be transferred like ATokens.


Sub Topics: borrowing-technical
 

---

##### What is the variable interest rate when Utilization rate is less than optimal Utilization rate?  

- [ ]  R<sub>o </sub> + U/R<sub>t </sub> * R<sub>slope1</sub>
- [x]  R<sub>o </sub> + U/U<sub>optimal </sub> * R<sub>slope1</sub>
- [ ]  R<sub>o </sub>+ [(U-U<sub>optimal</sub>)/(1-U<sub>optimal</sub>)]*R<sub>slope2</sub>
- [ ]  0.02% for all assets
  
Hint: Variable rate
         
Explanation: R<sub>t</sub> = R<sub>o </sub> + U/U<sub>optimal </sub> * R<sub>slope1</sub>. Where R<sub>o </sub> is the base variable borrow rate and R<sub>slope1</sub> is a constant.

Sub Topics: borrowing-technical
 

---

##### When the stable interest rate rebalances?  

- [ ]  When variable interest rate exceeds 5%
- [x]  when stable interest rate is less than variable rate
- [ ]  Ratio<sub>st</sub> > O<sub>ratio</sub>
- [ ]  U>U<sub>optimal</sub>
  
Hint: stable to total debt ratio
         
Explanation: The interest rate rebalances when Ratio<sub>st</sub> > O<sub>ratio</sub>. 
where, Ratio<sub>st</sub> is the stable debt to total debt ratio.
O<sub>ratio</sub> is the optimal stable debt to total debt ratio.      


Sub Topics: borrowing-technical
 

---

##### What is the stable interest rate if Utilization rate is greater than optimal Utilization rate?  

- [x]  Base<sub>s </sub> + R<sub>slope1 </sub>+ R<sub>slope2</sub>*[(U-U<sub>optimal</sub>)/E<sub>util</sub>]
- [ ]  variable interest rate * 20
- [ ]  Base<sub>s </sub> + R<sub>slope1 * </sub>(U/U<sub>optimal</sub>)
- [ ]  10%
  
Hint: Stable rate
         
Explanation: The stable rate when Utilization rate is less than optimal Utilization rate is  R<sub>s </sub> = Base<sub>s </sub> + R<sub>slope1 </sub>+ R<sub>slope2</sub>*[(U-U<sub>optimal</sub>)/E<sub>util</sub>].
where R<sub>s </sub> is the stable interest rate and Base<sub>s </sub> is the base stable interest rate
R<sub>slope1 </sub> and R<sub>slope2</sub> are constants
U is the utilization rate Similarly U<sub>optimal</sub> is the optimal utilization rate
E<sub>util</sub> is a value equals to (10^27 - U<sub>optimal</sub>)


Sub Topics: borrowing-technical
 
