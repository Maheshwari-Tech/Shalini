

1. Billing Module
	- To generate invoice and the charges.
	- To give the user option to download/preview the required documents based on the selection. (Revenue/cost etc)
	- Integration with different teams such as shipment team, booking team, taxation team etc
	- This system was already there with some existing functionalities in but in dot net. We migrated it to java - micro services, with some more new functionlities.
1. Taxation Module.
	- Existing system of taxation so small features on top of that.
	- On boarded 100 countries on our platform. So needed to integrate their taxation flow/logic in our system which was very complex.
	- So integrated with 3rd party tax computing engine - TR (Thomson Reuters).


Technical work for billing.
- In Billing initially I worked for code migration in java.
- Developed few features like - 
	- fetching offers and giving the updated changes in the price based on selected charges in billing page. 
	- Summary api for each bill (invoiced cost/revenue, unPosted, disbursement etc) and summary for listing page as well.
- In billing the very important part is to show the numbers and formatting of the user based on it's country or their selection of formatting. Wrote complete logic for amount formatting in billing module.
- Updated and optimised the existing codes and improved the performance of those api's upto 70%.
- Wrote few producers which were required by other teams.
- Wrote few consumers as well.
- Solved many bugs specially optimised the code.
- Added unit test cases for existing code and the new code that I wrote with line coverage of minimum 95%.



Used Kafka because - 
- To make things asynchronous
- To make things faster
- It is a method for fast communication between microServices.