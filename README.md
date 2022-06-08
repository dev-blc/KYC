**********Instructions for Testing out the KYC Smart Contract on Remix IDE(Online)**********

-------Pre-requisites------- 

I.Have Remix IDE open on your browser (https://remix.ethereum.org)
II.Create a new workspace and rename the exisisting solidity file to “KYC.sol”.
III.Now copy the code content on the KYC.sol file in the Phase 2 folder to “KYC.sol”file in the Remix IDE. Assure that you have copied all the content from the file in a correct manner.

-------Compilation-------

I.In Remix IDE, click on the Solidity Icon button which expands to a menu pane named Solidity compiler.
II.Set the compiler version to local latest version or any version that is specified in the code 
III.Enable auto compile to see a green tick mark near the solidity icon on the left. If there is a red error icon, double check the code with the KYC.sol file that was provided for any copy errors.

-------Deployment-------

I. After successfully compiling the Smart Contract, navigate to the Deploy & Run Transaction pane below the compiler pane.
II.Keep the Environment, Account, Gas Limit & Value as same as the default values. 
III.Ensure that the Contract name appears as the same in the Contract box.
IV.Click Deploy & see the contract deployment details on the console bottom of the screen. 
V.You can see transaction hash, participants, gas consumed & input data in the console.

-------Run Transactions(Functions)-------

I.Scroll down in the Deploy & Run transaction pane to see Deployed Contracts dropdown option.
II.You can see the name of the Smart Contract followed by the address at which it has been deployed.
III.In the dropdown section, you can see the various functions available along with a text box to enter the parameters to be passed.

-------Smart Contract Flow(s)-------

* After deployment of the Smart Contract, the admin uses the addBank() function to add some banks to the Blockchain network.
* Now, change the account to any of the bankAddresses that you added and initiate a KYC request using addRequest() function.
* After the verification of the customer, add the customer data to the customer list.
* Change the account to a different bankAddresses you added and engage in voting process by calling either upVote() or downVote() function for a customer.
* Use different accounts(bankAddresses) which you added to cast the votes.
* You can call viewCustomer() at any point to view the votes, KYC status & other data.
* Check the changes in KYC status of a customer by changing the up votes and down votes count.
* Other Banks can also append, modify or change the data of any customer if they encounter any new data using modifyCustomer() function. This function removes all existing votes and removes the request from request list using the removeRequest() function. This enables the banks to vote again according to the new data added. 
* The removeRequest()  function can also be called separately by any of the banks(account/bankAddress) added by the admin. 
* viewBankDetails() can be called to observe bank details such as complaintsReported, KYC_Count & its voting right at any point of time.
* You can raise or report a complaint against a bank using reportBank() function. This function can be called by all the banks(account/bankAddress) added by the admin. The voting rights of the bank is changed if the number of complaints exceed 1/3rd of the number of banks. 
* You can also view the number of complaints raised against a bank using getComplaints() function.
* The Admin can change the voting rights of a bank and also remove a bank from the network at any point of time using votingRights() and removeBank() functions respectively. 

-------Transactions/Functions-------

Setup/Create Data (Setter Functions)

I.addBank() - Function to add a new bank. 
=> Call this function with the account from which you deployed the Smart 	Contract as that is the admin address.
=> Add minimum 6 Banks to test Voting and penalizing functionalities.
=> Use the addresses provided in Remix IDE in the Account list for the 	bankAddress parameter. You can add as many addresses you want 	using the + icon.
=> Use the below data  as a reference for the parameters to be passed
    		• bName - ICICI 
		• bankAddress - *(Use an address other than the owner address 				from the accounts provided to you by Remix IDE. 					Remember the address corresponding to the bank for easy 			use. Do not use the same address to a different bank)
		• bRegNumber - ICICI0001
=> Add 5 more banks by changing the mentioned parameters.

II.addRequest() - Function to add a KYC request to Request list.
=> Add a single KYC request for a single customer.
=> Call this function with the account from any of the bank address that 	you added.
=> Use the below data as a reference for the parameters to be passed
	• cName - Balaganapathy
	• cData - “PAN: ABCDE1234F, AADHAAR: 0123 4567 8900, PH.No: 			9876543210”
=> Add requests of all the customers that you want to add to Customer list.

III.addCustomer() - Function to add a new customer.
=> Add customers for whom you have raised the KYC request.
=> Call this function with the account from any of the bank address that 	you added. 
=> Use the below data as a reference for the parameters to be passed
		• cName - Balaganapathy
		• cData - “PAN: ABCDE1234F, AADHAAR: 0123 4567 8900, PH.No: 			9876543210”
=> Use the above cData format as a reference. Add few more customers 	with different bankAddress(Accounts).

Retrive Data(Getter Functions)

IV.viewBankDetails() - Function to view Bank Details.
=> Pass only valid Bank Addresses that you used.
=> Returns Bank Name, Address, Registration Number, Complaints 	reported, KYC Count, Voting Status. 
=> Use the below data  as a reference for the parameters to be passed
    		• bankAddress - *(Valid Bank Address from the accounts provided 			by the Remix IDE)
=> Use the below data  as a reference for the data to be returned 
		• bName - ICICI 
		• bankAddress - *(Valid Bank Address passed as a parameter)
		• bRegNumber - ICICI0001
		• complaintsReported - 2
		• KYC_Count - 5
		• isAllowedToVote - true

V.viewCustomer() - Function to view Customer Details.
=> Pass only valid Customer Name that you used.
=> Returns Name, Data submitted for KYC, Address of the bank in which 	the account is opened, KYC status, Up Votes, Down Votes. 
=> Use the below data  as a reference for the parameters to be passed
    		• cName - Balaganapathy
=> Use the below data  as a reference for the data to be returned 
		• cName - Balaganapathy
		• data - “PAN: ABCDE1234F, AADHAAR: 0123 4567 8900, PH.No: 			9876543210”
		• bank - *(Valid Address of the Bank which added the customer)
		• KYC - true
		• upVotes - 5
		• downVotes - 1

VI.getComplaints() - Function to get number of complaints registered against 				a Bank
=> Pass only valid Bank Addresses that you used.
=> Returns number of complaints against the bank.
=> Use the below data  as a reference for the parameters to be passed
    		• bankAddress - *(Valid Bank Address from the accounts provided 			by the Remix IDE)
=> Use the below data  as a reference for the data to be returned 
		• complaintsReported - 2

Voting Functions

VII.upVote() - Function to Up Vote a Customer
=> Pass only valid Customer Names that you used.
=> Call this function with the account from any of the bank address that 	you added.
=> A Bank can only cast a single Vote for a customer.
=> Banks with Voting Rights can only Vote.
=> Use the below data  as a reference for the parameters to be passed
		• cName - Balaganapathy
=> This function changes your has voted to true for the specific customer.
=> The KYC status of the Customer is reassured or checked again in 	accordance to the addition of the current vote.

VIII.downVote() - Function to DownVote a Customer
=> Pass only valid Customer Names that you used.
=> Call this function with the account from any of the bank address that 	you added.
=> A Bank can only cast a single Vote for a customer.
=> Banks with Voting Rights can only Vote.
=> Use the below data  as a reference for the parameters to be passed
		• cName - Balaganapathy
=> This function changes your has voted to true for the specific customer.
=> The KYC status of the Customer is reassured or checked again in 	accordance to the addition of the current vote.

Edit/Remove Data

IX.removeBank() - Function to Remove a Bank
=> Call this function with the account from which you deployed the Smart 	Contract as that is the admin address.
=> Pass only valid Bank Addresses that you used.
=> Use the below data  as a reference for the parameters to be passed
    		• bankAddress - *(Valid Bank Address from the accounts provided 			by the Remix IDE)

X.removeRequest() - Function to remove a KYC request from Request list
=> Call this function with the account from any of the bank address that 	you added.
=> Pass only valid Customer Name that you used to raise a Request.
=> Use the below data  as a reference for the parameters to be passed
		•cName - Balaganapathy

XI.votingRights() - Function to modify the Voting Rights of a Bank
=> Call this function with the account from which you deployed the Smart 	Contract as that is the admin address.
=> Pass only valid Bank Addresses that you used.
=> Use the below data  as a reference for the parameters to be passed
    		• bankAddress - *(Valid Bank Address from the accounts provided 			by the Remix IDE)
		• changedVotingStatus - false
=> This will change the Voting abilities of the bank.

XII.modfiyCustomer() - Function to change or correct Customer Details.
=> Call this function with the account from any of the bank address that 	you added. 
=> Pass only valid Customer Name that you have already added to the 	customer list.
=> Use the below data as a reference for the parameters to be passed
		• cName - Balaganapathy
		• cData - “PAN: ABCDE1234F, AADHAAR: 0123 4567 8900, PH.No: 			9876543210, DL: TN3568ABC1254”
=> This function will reset the values of up votes & down votes to zero.
      => This function also removes the old request from the request list.

XIII.reportBank() - Function to raise a Complaint against a Bank
=> Call this function with the account from any of the bank address that 	you added. 
=> Pass only valid Bank Addresses that you used.
=> Use the below data  as a reference for the parameters to be passed
    		• bankAddress - *(Valid Bank Address from the accounts provided 			by the Remix IDE)
=> This function will change the voting status of the bank if the number of 	complaints is above 1/3 rd of the total number of banks.