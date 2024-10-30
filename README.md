# SICK-Inspector-Ethernet-IP-guide
Guide to connecting SICK inspector camera with Ethernet/IP and Control Expert

**Guide to Sick Camera and Ethernet/IP**

**Download SOPAS Engineering Tool**
![image](https://github.com/user-attachments/assets/489cfd53-a249-418d-8da5-151a760301a1)

Ensure the camera is in **EDIT**, select InspectorPI50 from the top, and choose **interfaces and I/O settings** from the dropdown menu. This window will appear.
![image](https://github.com/user-attachments/assets/6e351903-0b0d-4837-aea2-2ca4b6eda90f)


Ensure that Ethernet is checked, and Ethernet/IP is selected.  /
Ensure the camera is in **EDIT**, and choose **Replace reference image**./
![image](https://github.com/user-attachments/assets/d2f8d941-9a9e-4017-b2de-0ef0c52946a7)


This window will appear. Select an **object locator** and draw a box around the area to be detected./
![image](https://github.com/user-attachments/assets/19b4e460-a586-4bbe-8a8a-c00faa965230)


Then place the object to be detected by the camera within the **Object locator** area, and green lines should appear around the object.  /
When you're done, select the **RUN** button and click **save to flash**. You have now taught the camera what object it should monitor. /

**Ethernet/IP in Control Expert**

Open Control Expert Classic  /
Select the **Tools** menu at the top, and choose **DTM Browser**  /
Right-click on the PLC. Select **Device menu**, **Additional Functions**, and **Add EDS to library**./
![image](https://github.com/user-attachments/assets/c74acafa-1864-440a-b865-2229945272dc)

Click **Next** on the window that appears./

![image](https://github.com/user-attachments/assets/6b163a2d-e2bc-4a86-bf2d-bc635a73c9a8)

Find the EDS file for the SICK camera, select it, and click **Next, Next**, and **Finish**./
Now you **MUST** restart control expert. Otherwise you will not be able to find your newly added .EDS file.

Right-click on the PLC in the DTM browser again, and select **Add...**/
![image](https://github.com/user-attachments/assets/67abe69b-6bdf-44cd-9fb6-8f10242c43c6)


Under Protocol, choose **Ethernet/IP**. Find the SICK camera in the list. It should be named something like **Inspector**. /
(Remember, you can click on the **Device** tab to display the list alphabetically.)
![image](https://github.com/user-attachments/assets/0a5d2e8a-aeb2-4320-bd94-030de3306ab9)


Once you've added it, double-click on the newly created device in the DTM browser. You’ll see this window./
![image](https://github.com/user-attachments/assets/ecf8cd9a-8b07-4b3b-b7de-1a06caf7307f)


Click **Add connection** and add **Input Only Result 1** and **Listen Only Result 1**. The window should now look like this:  /
Click **Apply** and close the window. /
![image](https://github.com/user-attachments/assets/10ded5a0-1e8a-44b6-8354-ee22c444127b)


Double-click on the PLC in the DTM browser, select the camera under **Device List**, go to the Address tab at the top, and set the address of your camera. /
(Remember, you can see the IP address of the camera in SOPAS Engineering Tool). /
In my case, the camera’s IP address is 192.168.1.160, so my window looks like this: /
![image](https://github.com/user-attachments/assets/2ef8dd31-fac5-4008-83cd-d6a5e76b2718)


**Congratulations!** The camera is now connected via Ethernet/IP to the Schneider PLC./

If you want to view the bits from the camera change within the PLC, do the following:  /
Right-click on **Animation tables** in the project browser, and select **New Animation Table**. Choose OK. /
The screen should now look like this: /
![image](https://github.com/user-attachments/assets/d13e4744-8954-45a6-9a57-bf598983c3b7)

Double-click on the black field under **Name** and click the button that appears. /
![image](https://github.com/user-attachments/assets/4c61dba1-2ca6-499a-9181-fdc791fb9a32)

Select the camera, and click **OK**. /
![image](https://github.com/user-attachments/assets/bcd82d9b-4dea-4bec-af27-0719f9371ad0)


Select **PLC** at the top, then **Set address**. /
Ensure the PLC address is correct (My PLC address is: 192.168.1.40), and Media is set to **TCPIP**. /
![image](https://github.com/user-attachments/assets/6af18fc2-0495-4d2f-8f03-79099f417e00)


Now select **PLC** again at the top, and **Connect**. Download your project to the PLC. /
![image](https://github.com/user-attachments/assets/d8c17450-2908-45be-8288-556ef6142b5f)


If you receive the error message **Project not built**, disconnect from the PLC, and click **Rebuild**. /
![image](https://github.com/user-attachments/assets/a6d87376-1c51-4db7-9604-78a22989236f)


When you are properly connected to the PLC, open your **Animation table** and view bits from the camera. /
If **Freshness** is 1, it means there is a good connection between the PLC and the camera. /
The first Input (InspectorPI50_Revision_I8KQOO.Inputs.Free1[0]) shows whether the **Object locator** you set up in SOPAS Engineering can see an object.
![image](https://github.com/user-attachments/assets/f0f2b9aa-44aa-4f7a-9e7f-868de679d3a6)
