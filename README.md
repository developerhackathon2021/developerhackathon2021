# Welcome to Developers Live : Hackathon

## Table of Contents
- [Goal](#goal)
- [Prerequisites](#prerequisites)
- [Configure your first destination with Destination SDK](#configure-your-first-destination-with-destination-sdk)
- [Validate the newly created destination](#validate-the-newly-created-destination)

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

## Configure your first destination with Destination SDK

1. Go to Postman and open `[Step1] Create destination server` call.   
   Replace these fields from the `Body`:   
   * `name` -> your custom value   
   * `urlBasedDestination.url.value` -> copied from the webhook site you previously opened in browser (at 9th step from Preconditions).  
   ![Postman Environment Variables Finish Import](pictures/webHookGenerator2.png?raw=true)
2. Your setup from step above should look like this
   ![Create a Destination Server](pictures/hackStep1.png?raw=true)
3. Run this `POST` API call.  
   From the successful response (201, Created) `Body` copy the `instanceId` value, since we will use it in the next step.
4. To check your destination server was correctly created, open `[Step2] Get destination server` API call.  
   Replace placeholder dummy value from the url with the `instanceId` value copied in the previous step(3).
   ![Get a Destination Server](pictures/hackStep2.png?raw=true)
5. Execute this `GET` API call.       
   Your output response should be similar to this one:
   ![Get a Destination Server Response](pictures/hackStep22.png?raw=true)  
6. Open `[Step3] Create destination` `POST` API call.     
   In the `Body` you need to replace: 
   * `name` -> your custom value  
   * `description` -> your custom value   
   * `destinationDelivery.destinationServerId` -> the `instanceId` value copied at step 3.  
   ![Create a Destination](pictures/hackStep3.png?raw=true)
7. Run this `POST` API call.  
   From the successful response (201, Created) `Body` copy the `instanceId` value, since we will use it in the next step. 
   ![Create a Destination Response](pictures/hackStep33.png?raw=true)
8. To check your destination was correctly created, open `[Step4] Get destination` API call.   
   Replace placeholder dummy value from the url with the `instanceId` value copied in the previous step(7).
   ![Get Destination](pictures/hackStep4.png?raw=true)
9. Execute this `GET` API call.       
   Your output response should be similar to the one below - you've just created a destination that will show up in the mobile category from Adobe Experience Platform UI 
   ![Get Destination Response](pictures/hackStep44.png?raw=true)

## Validate the newly created destination

1. Go to your browser and open [Adobe Experience Platform UI](https://experience.adobe.com).   
    Login using credentials shared in the chat.
2. Go to `Destinations` tab
   ![Click Destinations](pictures/hackStep6.png?raw=true)  
3. Go to Catalog tab
   ![Click Catalog](pictures/hackStep7.png?raw=true)  
4. Find your destination inside Mobile Engagement category (it should have the name you created previously, something like: `<YOUR_CUSTOM_VALUE>-test-destination`).  
   Click on `Set up` button
   ![Set up Destination](pictures/hackStep8.png?raw=true)  
5. Next, for the demo purposes, you can add any dummy value in `Bearer token` input field and click `Connect to destination` button
   ![Set Authentication](pictures/hackStep9.png?raw=true)  
6. In the `Destination details` section fill in the following fields with custom values and then press `Next` button: 
   * `Name` -> <YOUR_CUSTOM_VALUE>-test-destination-instance
   * `Description` -> <YOUR_CUSTOM_VALUE>-test-destination-instance-description
    ![Set Name and Description](pictures/hackStep10.png?raw=true)  
7. In this demo we will skip this step (Marketing Actions), just click the `Next` button
    ![Set Data Governance](pictures/hackStep11_0.png?raw=true)
8. We need to select the audience/segment which we previously defined for this demo to include all profiles with birth year equals to 1901.  
   Choose `Hackathon segment 1` and press the `Next` button.  
    ![Set Segment](pictures/hackStep12_0.png?raw=true)
9. We reached the `Mapping` phase where you, as a partner, need to map customer data (identities, attributes) to your target destination.   
   Click the `Add new mapping` button and configure the `Source` and `Target` fields as follows:
   * Press the arrow button next to `Source field`  
   * `Select identity namespace` option as `Source field` and pick `Hackathon namespace 1` value. 
   * For `Target Field` let's choose `emailMarketingIds` and click `Next` button
    ![Add new Mapping](pictures/hackStep999_0.png?raw=true)
    ![Set Source](pictures/hackStep999_1.png?raw=true)
    ![Set Target](pictures/hackStep999_3.png?raw=true)
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