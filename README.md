# Welcome to Developers Live : Hackathon

## Table of Contents
- [Goal](#goal)
- [Prerequisites](#prerequisites)
- [Configuring and validating your first destination with Destination SDK](#configuring-and-validating-your-first-destination-with-destination-sdk)

## Goal
### `Configure a new destination using Adobe Experience Platform Destination SDK and validate the configuration`

## Prerequisites:

1. Install [Postman](https://www.postman.com/downloads/) if you don't have it already
2. Go to Github [Postman APIs Collection](https://github.com/developerhackathon2021/developerhackathon2021/blob/main/Hackathon.postman_collection.json), press `Copy Raw Content` button (attach screenshot) and save it locally (in any text editor) as json
   ![Postman Collection Import](pictures/copyRawContentCollection.png?raw=true)
3. Go to Github [Postman Environment Variables](https://github.com/developerhackathon2021/developerhackathon2021/blob/main/Hackathon%202021%20Env%20Variables.postman_environment.json), press `Copy Raw Content` button and save it locally (in any text editor) as json
4. Import in Postman APIs Collection (saved at step 2 above)
   ![Postman Collection Import](pictures/postmanCollection1.png?raw=true)
   ![Postman Collection Drag & Drop](pictures/postmanCollection2.png?raw=true)
   ![Postman Collection Overview](pictures/postmanCollection4.png?raw=true)  

5. Import Environment Variables (saved at step 3 above)  
   ![Postman Environment Variables Import](pictures/postmanEnvVars2.png?raw=true)
   ![Postman Environment Variables Drag & Drop](pictures/postmanEnvVars3.png?raw=true)
   ![Postman Environment Variables Finish Import](pictures/postmanEnvVars555.png?raw=true)
   
6. Set `Hackathon 2021 Env Variables` as Environment Variable
   ![Postman Environment Variables Finish Choose_EnvVars](pictures/postmanReplaceEnvVars333.png?raw=true)

7. Replace `BEARER_TOKEN` environment variable values (`INITIAL VALUE` and `CURRENT VALUE`) with the string value shared in the chat.  
   ![Postman Environment Variables Replace](pictures/postmanReplaceEnvVars111.png?raw=true)
   
8. Repeat the same step as above (step 7) for `API_KEY` environment variable then Save.
   ![Postman Environment Variables Save](pictures/postmanReplaceEnvVars2.png?raw=true)

### Congratulations: your Postman setup is ready!

9. Next, we need to configure a webhook using https://webhook.site to simulate a destination endpoint.
   Once you clicked the [webhook url](https://webhook.site) above, please leave the browser tab open.  
   ![Postman Environment Variables Finish Import](pictures/webHookGenerator1.png?raw=true)  
   
### Now, your setup is complete! Let's go ahead and create your first Destination using Adobe Experience Platform Destination SDK! 

## Configuring and validating your first destination with Destination SDK
1. Go to Postman and open `[Step1] Create destination server` call.   
   Replace these fields from the `Body`:   
   * `name` -> your custom value   
   * `urlBasedDestination.url.value` -> copied from the webhook site you previously opened in browser (at 9th step from Preconditions).  
   ![Postman Environment Variables Finish Import](pictures/webHookGenerator2.png?raw=true)
2. Your setup from step above should look like this
   ![Create a Destination Server](pictures/hackStep1.png?raw=true)
3. Run this `POST` API call.  
   From the successful response (201, Created) body copy the `instanceId` value, since we will use it in the next step.
4. To check your destination server was correctly created, open `[Step2] Get destination server` API call.  
   Replace placeholder dummy value from the url with the `instanceId` value copied in the previous step(3).
   ![Get a Destination Server](pictures/hackStep2.png?raw=true)
5. Execute this `GET` API call.       
   Your output response should be similar to this one:
   ![Get a Destination Server Response](pictures/hackStep22.png?raw=true)  
6. Open `[Step3] Create destination` call.     
   In the Body call you need to replace : 
   * `name` -> your custom value  
   * `description` -> your custom value   
   * `destinationDelivery.destinationServerId` -> instanceId from the 3rd step.  
   ![Create a Destination](pictures/hackStep3.png?raw=true)
7. Run this call.  
   Your output response should be similar to this:
   ![Create a Destination Response](pictures/hackStep33.png?raw=true)  
   Save the instanceId from the response body, since we will use it in the next step.  
8. Open `[Step4] Get destination` call.   
   Replace placeholder from the url with instanceId from 7th step.
   ![Get Destination](pictures/hackStep4.png?raw=true)
9. Run this call.  
   Your output response should be similar to this:  
   ![Get Destination Response](pictures/hackStep44.png?raw=true)  
  
### Congratulations: your Destination has been created! Let's configure it through the UI!  
  
10. Go to your browser(Chrome preferably) and open [Adobe Experience Platform UI](https://experience.adobe.com).   
    Login using credentials shared in the chat.
11. Go to `Destinations` tab
   ![Click Destinations](pictures/hackStep6.png?raw=true)  
12. Go to Catalog tab
   ![Click Catalog](pictures/hackStep7.png?raw=true)  
13. Find your destination inside Mobile Engagement container (it should be something like: `<YOUR_NICKNAME>-test-destination`) and click on `Set up` button
   ![Set up Destination](pictures/hackStep8.png?raw=true)  
14. Set a dummy value in `Bearer token` input field and click `Connect to destination` button
   ![Set Authentication](pictures/hackStep9.png?raw=true)  
15. Set a `Name`(<YOUR_NICKNAME>-test-destination-instance) and `Description`(<YOUR_NICKNAME>-test-destination-instance-description) in `Destination details` and click `Next` button
    ![Set Name and Description](pictures/hackStep10.png?raw=true)  
16. Do not select any of Marketing Actions, just press `Create` button
    ![Set Data Governance](pictures/hackStep11_0.png?raw=true)
17. Select `Hackathon segment 1` and press `Next` button
    ![Set Segment](pictures/hackStep12_0.png?raw=true)
18. Click `Add new mapping`. For `Source Field` let's choose from Identity Namespace `Hackathon namespace 1`. For `Target Field` let's choose `emailMarketingIds` and click `Next` button
    ![Add new Mapping](pictures/hackStep13_0.png?raw=true)
    ![Set Source](pictures/hackStep13_1.png?raw=true)
    ![Set Target](pictures/hackStep13_2.png?raw=true)
    ![Click Next](pictures/hackStep13_3.png?raw=true)  
19. Click `Finish` button
    ![Click Finish](pictures/hackStep14_0.png?raw=true)  
20. From the url, get destination instance id (Ex: https://...destination/browse/`8b4deb36-e2d0-40a5-8742-2b42444fff72`/...)
    ![Get Destination Instance Id](pictures/hackStep15_0.png?raw=true)  
21. Go back to Postman and open `[Step5] Test destination`, replace placeholder from the url with the destination_instance_id you got in previous step and execute it;
    ![Test Destination Instance Id](pictures/hackStep16_0.png?raw=true)
    ![Test Destination Instance Id Response](pictures/hackStep16_1.png?raw=true)
22. Check exported profiles from webhook tab
    ![Check Webhook](pictures/hackStep17_0.png?raw=true)
    

# Thanks for joining this journey!