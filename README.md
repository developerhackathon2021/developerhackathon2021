# Welcome to Developers Live : Hackathon

## Purpose
### `Create a custom destination using destination-sdk and activate it using some generated profiles`

## Table of Contents
- [Purpose](#purpose)
- [Prerequisites](#prerequisites)
- [Hackathon Steps](#hackathon-steps)

## Prerequisites:

1. Install [Postman](https://www.postman.com/downloads/) if you don't have it already
2. Download [Postman collection](https://github.com/developerhackathon2021/developerhackathon2021/blob/main/Hackathon.postman_collection.json)
3. Download [Postman Environment Variables](https://github.com/developerhackathon2021/developerhackathon2021/blob/main/Hackathon%202021%20Env%20Variables.postman_environment.json)
4. Import Postman Collection
   ![Postman Collection Import](pictures/postmanCollection1.png?raw=true)
   ![Postman Collection Drag & Drop](pictures/postmanCollection2.png?raw=true)
   ![Postman Collection Finish Import](pictures/postmanCollection3.png?raw=true)
   ![Postman Collection Overview](pictures/postmanCollection4.png?raw=true)  

5. Import Environment Variables  
   ![Postman Environment Variables](pictures/postmanEnvVars1.png?raw=true)
   ![Postman Environment Variables Import](pictures/postmanEnvVars2.png?raw=true)
   ![Postman Environment Variables Drag & Drop](pictures/postmanEnvVars3.png?raw=true)
   ![Postman Environment Variables Finish Import](pictures/postmanEnvVars4.png?raw=true)
   ![Postman Environment Variables Finish Import](pictures/postmanEnvVars5.png?raw=true)

6. Replace Environment Variables values from Postman with the ones from the chat, save and select them  
   ![Postman Environment Variables Replace](pictures/postmanReplaceEnvVars.png?raw=true)
   ![Postman Environment Variables Save](pictures/postmanReplaceEnvVars2.png?raw=true)
   ![Postman Environment Variables Finish Choose_EnvVars](pictures/postmanReplaceEnvVars3.png?raw=true)

7. Get a webhook from: https://webhook.site (it should be something like: https://webhook.site/351e6452-9187-49f3-9588-d2cf47be2666) and leave that tab opened.
   ![Postman Environment Variables Finish Import](pictures/webhookGenerator.png?raw=true)    

## Hackathon Steps
1. Go to Postman and open `[Step1] Create destination server` call, replace in the body: name and urlBasedDestination.url.value(obtained in `7th` step from `Preconditions`) and execute it
   ![Create a Destination Server](pictures/hackStep1.png?raw=true)
   ![Create a Destination Server Response](pictures/hackStep11.png?raw=true)  
2. Open `[Step2] Get destination server` call, replace placeholder from the url and execute it
   ![Get a Destination Server](pictures/hackStep2.png?raw=true)
   ![Get a Destination Server Response](pictures/hackStep22.png?raw=true)  
3. Open `[Step3] Create destination` call, replace in the body: name, description and destinationDelivery.destinationServerId and execute it
   ![Create a Destination](pictures/hackStep3.png?raw=true)
   ![Create a Destination Response](pictures/hackStep33.png?raw=true)  
4. Open `[Step4] Get destination` call, replace  placeholder from the url and execute it
   ![Get Destination](pictures/hackStep4.png?raw=true)
   ![Get Destination Response](pictures/hackStep44.png?raw=true)  
5. Go to your browser(Chrome preferably) and open Adobe Experience Platform UI https://experience.adobe.com and login using credentials from the chat
6. Go to `Destinations` tab
   ![Click Destinations](pictures/hackStep6.png?raw=true)  
7. Go to Catalog tab
   ![Click Catalog](pictures/hackStep7.png?raw=true)  
8. Find your destination inside Mobile Engagement container (it should be something like: `<YOUR_NICKNAME>-test-destination`) and click on `Set up` button
   ![Set up Destination](pictures/hackStep8.png?raw=true)  
9. Set a dummy value in `Bearer token` input field and click `Connect to destination` button
   ![Set Authentication](pictures/hackStep9.png?raw=true)  
10. Set a `Name`(<YOUR_NICKNAME>-test-destination-instance) and `Description`(<YOUR_NICKNAME>-test-destination-instance-description) in `Destination details` and click `Next` button
    ![Set Name and Description](pictures/hackStep10.png?raw=true)  
11. Do not select any of Marketing Actions, just press `Create` button
    ![Set Data Governance](pictures/hackStep11_0.png?raw=true)
12. Select `Hackathon segment 1` and press `Next` button
    ![Set Segment](pictures/hackStep12_0.png?raw=true)
13. Click `Add new mapping`. For `Source Field` let's choose from Identity Namespace `Hackathon namespace 1`. For `Target Field` let's choose `emailMarketingIds` and click `Next` button
    ![Add new Mapping](pictures/hackStep13_0.png?raw=true)
    ![Set Source](pictures/hackStep13_1.png?raw=true)
    ![Set Target](pictures/hackStep13_2.png?raw=true)
    ![Click Next](pictures/hackStep13_3.png?raw=true)  
14. Click `Finish` button
    ![Click Finish](pictures/hackStep14_0.png?raw=true)  
15. From the url, get destination instance id (Ex: https://...destination/browse/`8b4deb36-e2d0-40a5-8742-2b42444fff72`/...)
    ![Get Destination Instance Id](pictures/hackStep15_0.png?raw=true)  
16. Go back to Postman and open `[Step5] Test destination`, replace placeholder from the url with the destination_instance_id you got in previous step and execute it;
    ![Test Destination Instance Id](pictures/hackStep16_0.png?raw=true)
    ![Test Destination Instance Id Response](pictures/hackStep16_1.png?raw=true)  
    

# Thanks for joining this journey!