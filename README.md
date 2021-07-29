# Introduction to ICy
Project ICy (Internet Computer Yield) was developed by Duke Undergraduate Researchers through [Duke CS+] (https://www.cs.duke.edu/undergrad/summer_research) summer programming. 

ICy is a Decentralized Lending Protocol for the Internet Computer. Similar to Aave, ICy is intended for users to be able to lend, borrow, and earn interest on crypto assets without any intermediary involvement. ICy uses 7 canisters (Database, Product, Reserves, Treasury, Price Oracle, User A, User B, User Assets), and currently, it can be deployed locally and User A and User B can interact. Moreover, an arbitrary user can create an account in the database and keep track of their token and cycle amounts. Users will receive receipts for transactions in terms of ATokens and ACycles that will earn interest. The reserve canister is used to isolate assets and calculate liquidity, and the price oracle canister feeds for the exchange rate of the assets. 

## Canisters
There are 7 canisters used: Database, Product, Reserves, Treasury, Price Oracle, User A, User B, and User Assets. 
### Treasury
The Treasury canister can mint ICP and Cycle tokens to then transfer to the User Canister. The treasury keeps track of its balance.

### Reserve 
The Reserve canister keeps track of available tokens for borrowing as well as the amount locked up for collateral. Essentially, it serves the role of a bank.
### Product
Keeps track of all the aTokens outstanding. This canister interacts with the Reserve Canister by organizing User deposits and collateral to determine liquidity of specific token.
### User
Through the User Canister, a user can check their balance (similar to a digital wallet). A user can deposit ICP and Cycle tokens to the Product Canister to earn interest and in return be given back aTokens. A user can also redeem a deposit and borrow from the Product Canister if the User Canister has deposited enough tokens as a collateral.
### User Assets
The User Assets canister is meant solely for the front-end code that implement in the Motoko created functions. Project ICy is using HTML and Javascript.
### Price Oracle
This canister fetches the current ICP to cycles exchange rate in real time (which in the NNS is updated every ten minutes).

## Researchers 
<br/>
Lead Professor: Luyao Zhang
<br/>
Co-Lead Professors: Kartik Nayak, Fan Zhang, Yulin Liu
<br/>
Graduate Mentor: Derrick Adam
<br/>
Undergraduate Researchers: Dylan Paul and Malika Rawal
<br/>
Research Support: Tianyu Wu, William Zhao, Elliot Ha, Saad Lahrichi, Ray Zhu
<br/>

## Deploying ICy
Before going through the steps below, please go through [Dfinity's QuickStart] (https://sdk.dfinity.org/docs/quickstart/local-quickstart.html).

Once you have the latest version of dfx installed, you should begin your local environment by enacting the following commands:
In one terminal, navigate to the project directory and run
```
dfx start
```
In another terminal, navigate to the project directory and run
```
npm install
dfx deploy
```
Now you'll want to find the canister ID for the User1_assets canister, which can be achieved by doing as follows:
```
dfx canister id user1_assets
```
You should receive a long string of characters. For example: rno2w-sqaaa-aaaaa-aaacq-cai is a real canister ID.

Now, navigate to a web browser of your choice, and go to the following localhost url:
```
http://127.0.0.1:8000/?canisterId=[YOUR CANISTER ID]
```
For example,
```
http://127.0.0.1:8000/?canisterId=rno2w-sqaaa-aaaaa-aaacq-cai
```
That should then bring you to the following view:
![image](https://user-images.githubusercontent.com/59941308/127052935-fb28baf0-5ef0-4669-bdf8-6fe6cbaab537.png)
You are now accessing ICy's decentralized lending protocol!
