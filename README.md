# simpleAuction
A very simple auction simulator using a smart contract.

solidity versions = >=0.7.0 <0.9.0

First we create the contract named SimpleAuction.
Then we set the parameters of the auction such as beneficiary and auctionendtime, then we declare the highestbidder and the highestbid.
    address payable public beneficiary;
    uint public auctionEndTime;
    address public highestBidder;
    uint public highestBid;
After that we make a  public mapping  called pendingReturns with an address and a uint
    mapping(address => uint) public pendingReturns;
Then we declare a variable called ended that will tell us when the auction ends started of course in false.
After this we set 2 events: HighestBidIncrease with the address of the bidder and the amount to be raised. 
                            AuctoinEnded with the address of the winner and the amount.
After this we create a constructor that will have a biddingtime and a benefitiary
The constructor will set the benefitiary to the new benefitiary created and will make the endTime the moment the contract starts plus the bidding time.

After this we have 3 functions:
Bid: checks if the autions has ended, then checks that the amount you want to bid is higher than the highest bid and then it calls the HighestBidIncrease event.
withdraw: Allows you to get back your funds if you weren´t the highest bidder and want your coins back.
autionEnd:Checks if the auction has ended, makes the bool variable ended true, calls the event AuctionEnded and transfers the highest bid to the beneficiary.
