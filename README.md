# Welcome to Developers Live : Hackathon

## Prerequisites:

1. Install Postman from https://www.postman.com/downloads/
2. Download Postman collection from <calea proiect>
3. Download Postman Environment Variables from <calea proiect>
4. Import Postman Collection  (pic)
5. Import Environment Variables (pic)
6. Replace Environment Variables values from Postman with the ones from the chat
7. Get a webhook from: https://webhook.site (it should be something like: https://webhook.site/351e6452-9187-49f3-9588-d2cf47be2666)

## Hackathon Steps
1. Go to Postman and open `[Step1] Create destination server` call, replace in the body: name and urlBasedDestination.url.value(obtained in `7th` step from `Preconditions`) and execute it 
2. Open `[Step2] Get destination server` call, replace placeholder from the url and execute it
3. Open `[Step3] Create destination` call, replace in the body: name, description and destinationDelivery.destinationServerId and execute it
4. Open `[Step4] Get destination` call, replace  placeholder from the url and execute it
5. Go to your browser(Chrome preferably) and open Adobe Experience Platform UI https://experience.adobe.com and login using credentials from the chat
6. Go to `Destinations` tab
7. Go to Catalog tab
8. Find your destination inside Mobile Engagement container (it should be something like: `<YOUR_NICKNAME>-test-destination`) and click on `Set up` button
9. Set a dummy value in `Bearer token` input field and click `Connect to destination` button
10. Set a `Name`(<YOUR_NICKNAME>-test-destination-instance) and `Description`((<YOUR_NICKNAME>-test-destination-instance-description)) in `Destination details` and click `Next` button
11. Do not select any of Marketing Actions, just press `Create` button
12. Select your destination from the main grid (it should be called something like: `<YOUR_NICKNAME>-test-destination`) and click `Next` button
13. Select `Hackathon segment 1` and press `Next` button
14. Click `Add new mapping`. For `Source Field` let's choose from Identity Namespace `Hackathon namespace 1`. For `Target Field` let's choose `emailMarketingIds` and click `Next` button
15. Click `Finish` button
16. From the url, get destination instance id (Ex: https://...destination/browse/`8b4deb36-e2d0-40a5-8742-2b42444fff72`/...)
17. Go back to Postman and open `[Step5] Test destination`, replace placeholder from the url with the destination_instance_id you got in previous step and execute it;

