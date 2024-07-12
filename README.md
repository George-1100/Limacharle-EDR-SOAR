# Limacharle-EDR-SOAR
## Overview
In this project, I set up a Windows Server virtual machine equipped with the LimaCharlie agent to enhance endpoint detection capabilities. The primary objective was to create detection rule to detect the LaZagne password-cracking tool within the VM environment and tines used to send detections details to security team via email. Playbook craeated with using Liacharle API for isolate the machine

## What is Limacharle
real-time Endpoint Detection & Response (EDR) tool for desktops, servers, and cloud endpoints. 

## Environment Setup
  1. Created windows server virtual machine in virtual box

      ![image](https://github.com/George-1100/Limacharle-EDR-SOAR/assets/76154087/4bb4178e-e97b-4f6e-9c65-70fc8eaa7695)

  2. Setup limacharle EDR and create installed keys for windows 64bit machine

     ![image](https://github.com/George-1100/Limacharle-EDR-SOAR/assets/76154087/d1d8e6c0-2c0b-4363-a8bc-0e3e86d831f5)

  3. Installed the LimaCharlie agent on the Windows Server virtual machine to enable real-time detection and monitoring

     ![image](https://github.com/George-1100/Limacharle-EDR-SOAR/assets/76154087/af7e491e-c43f-4e6c-af82-13f08e82551a)

  4. Checked the services wherther Limacharle is running

     ![image](https://github.com/George-1100/Limacharle-EDR-SOAR/assets/76154087/a630e501-ed75-4791-922d-42786836925c)

  5. Checked Virual machine status in Limacharle

      ![image](https://github.com/George-1100/Limacharle-EDR-SOAR/assets/76154087/8ea0b4c5-3f24-42a1-b317-bafaf0971553)

  6. Checked Virtual machine artifacts in Limacharle (click Sensor list -> windows server)

     * Autoruns
    
       ![image](https://github.com/George-1100/Limacharle-EDR-SOAR/assets/76154087/46968894-c5e4-4bc4-b879-efdf4c29ae6d)

     * Console

       ![image](https://github.com/George-1100/Limacharle-EDR-SOAR/assets/76154087/58aea9bd-5b72-4640-bde2-28e20cee6cd3)

     * Drivers

       ![image](https://github.com/George-1100/Limacharle-EDR-SOAR/assets/76154087/4baa0fb7-1467-4021-8d47-45893db319f7)

     * File System

       ![image](https://github.com/George-1100/Limacharle-EDR-SOAR/assets/76154087/a089550f-4a1a-4eb0-9767-6ef9d40c739f)

     * Network

       ![image](https://github.com/George-1100/Limacharle-EDR-SOAR/assets/76154087/a5300458-3d3e-4d36-8ee0-f4bbbe2443b8)
   
   * Processes

     ![image](https://github.com/George-1100/Limacharle-EDR-SOAR/assets/76154087/33afcefc-41da-48e4-a691-46d07159bc96)

  * Services

    ![image](https://github.com/George-1100/Limacharle-EDR-SOAR/assets/76154087/f3d8086d-4dca-4990-9c74-bf35ba78b842)

 * Timeline

   ![image](https://github.com/George-1100/Limacharle-EDR-SOAR/assets/76154087/996e93c0-f96e-4a51-857b-925723844c0a)

 * Packages

   ![image](https://github.com/George-1100/Limacharle-EDR-SOAR/assets/76154087/35740b36-1c20-43d5-b141-c98956b02ddf)

* Analytics (View the number of events collected from this Sensor. Data is updated every ~15 minutes)

  ![image](https://github.com/George-1100/Limacharle-EDR-SOAR/assets/76154087/5f947a9d-ce69-4444-808e-bef6674e7178)

## Task Execution
  7. Deployed and ran the LaZagne password-cracking tool within the VM to simulate a potential security threat.
   
   ![image](https://github.com/George-1100/Limacharle-EDR-SOAR/assets/76154087/1c8124cf-4b88-49c0-9738-66da141584b0)
  
  8. Checked the Lazagne  processes details in timeline tab

   ![image](https://github.com/George-1100/Limacharle-EDR-SOAR/assets/76154087/e059dabf-a775-440c-aeb5-13adc21f4e6a)

## Detection Rule Creation (Automation -> D&R rules -> New rule)

  9. Developed a custom detection rule designed to identify the LaZagne tool based on its name and file hashes

      ![image](https://github.com/George-1100/Limacharle-EDR-SOAR/assets/76154087/973f182a-f732-4e88-ba09-fa8795c61780)

  10. rule working Checked (Copy and paste the test event section to check the rule working)

      ![image](https://github.com/George-1100/Limacharle-EDR-SOAR/assets/76154087/57c15ff5-aa8d-4d82-8aa7-8b235eca2c1b)

  11. Run the password craking tool to check whether detection rule is detecting

      ![image](https://github.com/George-1100/Limacharle-EDR-SOAR/assets/76154087/becd31f3-89ec-4e57-a30a-ebf92d71982c)

  ## Alert Integration
  12. Utilized the Tines webhook to automatically send detailed detection alerts to email, ensuring timely notification and response to the detected threat.

  ![image](https://github.com/George-1100/Limacharle-EDR-SOAR/assets/76154087/42d00286-b225-4824-98be-caf2f416feb6)

  13. Enter the webhook URL to the Output section. this will copy the detection details and send it to tines

      ![image](https://github.com/George-1100/Limacharle-EDR-SOAR/assets/76154087/548d0864-0ca2-4f8d-94ff-05017ffed0e5)

 14. Create story for webhook send detection setails to email (configure)

     [image](https://github.com/George-1100/Limacharle-EDR-SOAR/assets/76154087/ee8d9db4-8608-4927-ba0c-be7dac972de0)
 
15. Check the Automation working (hack tool ->detetion dule -> detection -> tines - > email)

      ![image](https://github.com/George-1100/Limacharle-EDR-SOAR/assets/76154087/91593746-7ce4-46cd-994f-0124e6df4ed7)

    ## Play book creation (SOAR)

16 . Created web page in tines and it has Yes/NO option for Isolate the machine

   ![image](https://github.com/George-1100/Limacharle-EDR-SOAR/assets/76154087/829fd527-2db6-4f0d-813b-8a3631d0e9a0)

   ![image](https://github.com/George-1100/Limacharle-EDR-SOAR/assets/76154087/6b39f765-d074-452a-a1ae-94f6e495f777)

   17.If user selection is No means no action tacken.
   18. If Yes, triggered action to sent a HTTP request for Isolate the machine (Created and conected with Limacharle creaticials in tines with using limacharle organization API)

   ![image](https://github.com/George-1100/Limacharle-EDR-SOAR/assets/76154087/0e11ac1d-8dac-45d0-bae4-17eb869ffd7a)

   ![image](https://github.com/George-1100/Limacharle-EDR-SOAR/assets/76154087/1a4b6e3e-59d6-4831-9cb5-71d7f2fa600d)

19. The machine has been automatically isolated fom the network

    ![image](https://github.com/user-attachments/assets/8335520d-f28b-4868-9f91-a5f7982897fb)




    


 


  



      


  

  

  





    










     
     


