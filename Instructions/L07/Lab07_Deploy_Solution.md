---
lab:
    title: 'Lab 7 - Deploy Solution'
    module: 'Module 7 - Unattended Flows'
---

# Unattended Flows

## Scenario

In this lab, you will deploy the solution to run unattended flows in a 
new test environment.

## High-level lab Objectives

-   Configure VM for unattended execution

-   Configure a machine group

-   Create and configure an Azure Key Vault

-   Use Key Vault in automations

-   Configure and use environment variables

-   Transport the solution from dev to test

# Exercise \#1: Configure VM

In this exercise, you will configure the Virtual Machine.

## Task \#1: Configure VM

1.  Go to your Azure portal <https://portal.azure.com/>, go to Virtual machines and and open the **Funding** virtual machine.

> <img src="../L07/media/image1.png" style="width:4.5in;"
> alt="select the vm described" />

2.  Click the **Connect** button.

> <img src="../L07/media/image2.png" style="width:5.15905in;height:1.42677in"
> alt="connect button" />

3.  Select **Download RDP File**. Select **Keep** to download the file and launch the remote desktop connection file.

4.  Select **Use a different account** if needed, enter **Funding** for Username,
    enter the password you created in lab00, and click **OK**.

> <img src="../L07/media/image4.png" style="width:3.39625in"
> alt="Sing in to VM" /> 

5. If prompted, click **Yes** to connect anyway and complete the setup.

6.  On the VM, open the **Microsoft Store** app and go to **Library**.

> <img src="../L07/media/image4b.png" style="width:2.40817in"
> alt="Select My Library from the three dots menu" />

7. Locate **Power Automate** in the list and select **Open**. 

8. **Wait** while any updates are installed. 

9.  Launch **Power Automate** provide your Power Platform admin login credentials and **Sign in** to Power Automate Desktop. 

10. Go to **Settings** and under **Machine settings** select **Open machine settings**. 

11. Select the **Install app** button. 

12. On the installer, check the box to agree to the terms of use then select the **Install** button. 

17. Select **Launch app**. 

13. On the **Machine settings** section, select the **Machine environment** dropdown and select your **Test
    environment**. 

14. Click **Change**. 

> <img src="../L07/media/image6.png" style="width:4.40817in;height:1.98166in"
> alt="select as described" />

15. Select the **Machine group** tab. 

16. Click **+ New machine group**.

17. Enter **Funding** for Machine group name and click **Create**. 

18. Click on the **Funding** machine group you created. 

19. Click **Add machine**. 

20. Click **Add machine** again. 

21. Click **Got it**.

22. You should now see the **Joined machine group** with one machine.

> <img src="../L07/media/image7.png" style="width:5.59998in;height:2.76529in"
> alt="review the results of the prior steps" />

23. Go to your **Local** computer and copy the **Labs** folder located
    in your C:\\ drive.

> <img src="../L07/media/image8.png" style="width:4in;height:0.74in"
> alt="image of file explorer" />

24. Go back to the **Remote desktop** and open file explorer.

25. Browse to C:\\ and paste the **Labs** folder you copied. This folder
    must be in the same location on both computers.

> <img src="../L07/media/image9.png" style="width:4in;height:1.83in"
> alt="image of file explorer" />

26. Browse to **C:\Labs\Resources\Funding manager app** and launch the **Woodgrove Bank Funding Manager.exe** app. If prompted, download .NET and install. Then try to launch Woodgrove Bank Funding Manager.exe again.

<img src="../L07/media/image10.png" alt="Screenshot showing the Woodgrove Bank Funding Manager.exe file" />

27. The app should install and launch. Close the application.

28. Launch Microsoft Edge.

29. Click **Settings** and select **Extensions**.

> <img src="../L07/media/image11.png" style="width:3.50508in;height:3.30129in"
> alt="menu in Microsoft Edge" />

30. Click Open Microsoft Edge Add-ons website.

> <img src="../L07/media/image12.png" style="width:3.35143in;height:3.07289in"
> alt="select as described" />

31. Search for Power Automate extensions and click to open **Microsoft
    Power Automate**.

> <img src="../L07/media/image13.png" style="width:5.67248in;height:1.65993in"
> alt="select as described" />

32. Click **Get** or turn it on if already installed.


# Exercise \#2: Key Vault

In this exercise, you will create a Key Vault.

## Task \#1: Create Key Vault

1.  In your **Local** machine, go to your Azure portal.

2.  Click **Subscriptions**.

> <img src="../L07/media/image14.png" style="width:5.67163in;height:1.18583in"
> alt="select as described" />

3.  Open the subscription.

4. Select **Resource providers**.

4.  Search for **Microsoft.PowerPlatform** and select it.

5.  Click **Register**.

> <img src="../L07/media/image15.png" style="width:5.56346in;height:1.23692in"
> alt="select as described" />

6.  Click **Home**.

7.  Click **+ Create a resource**.

8.  Search for **key vault** and select **Key Vault**.

> <img src="../L07/media/image16.png"
> alt="select as described" />

9.  Click **Create**.

10. Select **Funding** for Resource group, type **FundingFL** (Replace FL
    with your initials) for Key vault name and select **Review +
    create**.

> <img src="../L07/media/image17.png" style="width:5.10334in;height:4.00471in"
> alt="review the results of the prior steps" />

11. Review the values and select **Create**.

12. **Wait** for the deployment to complete.

13. Select **Go to resource**.

> <img src="../L07/media/image18.png" style="width:5.71619in;height:2.12403in"
> alt="select as described" />

14. Select **Access controm (IAM)**.

15. Click **+ Add** and select **Add role assignment**.

> <img src="../L07/media/image18a.png" style="width:5.71619in;height:2.12403in"
> alt="Add role assignment" />

16. Select **Key Vault Administrator** and then **Members** tab.

> <img src="../L07/media/image18b.png" style="width:5.71619in"
> alt="Members tab" />

17. Click **+ select members**

18. Select your username and then click **Select**.

19. Click **Review + assign**

20. Click **Review + assign** again.

21. Click **+ Add** and select **Add role assignment** again.

22. Select **Key Vault Secret User** and then **Members** tab.

23. Click **+ select members**.

24. Search for dataverse and select **Dataverse**.

> <img src="../L07/media/image22.png" style="width:5.17868in"
> alt="Dataverse"/>

25. Click **Select**.

26. Click **Review + assign**.

27. Click **Review + assign** again.

28. Select **Secrets** and then **+ Generate/Import**.

> <img src="../L07/media/image19.png" style="width:5.52461in;height:2.85556in"
> alt="select as described" />

29. Enter **FundingPassword** for Name, enter **pass@word1** for Value,
    and select **Create**.

> <img src="../L07/media/image20.png" style="width:5.27637in;height:2.66863in"
> alt="select and complete as described" />



# Exercise \#3: Environment Variables

In this exercise, will create environment variables and use them in the
flows.

## Task \#1: Create environment variables

1.  In your Local machine, navigate to <https://make.powerapps.com/> and
    make sure you are in your Dev environment.

2.  Select Solutions and open the **Construction Funding** solution.

3.  Click **+ New** and select **More \| Environment variable**.

> <img src="../L07/media/image30.png" style="width:5.72361in;height:2.94313in"
> alt="select as described" />

4.  Enter **Funding Run Mode** for Display name, select **Text** for
    Data type, enter **Unattended** for Default value, go to the
    **Current value** section, and click **+ New value**.

> <img src="../L07/media/image31.png" style="width:2.46452in;height:5.25708in"
> alt="select as described" />

5.  Enter **Attended** and click **Save**.

6.  Select environment variables and click to open variable you just
    created.

> <img src="../L07/media/image32.png" style="width:5.54655in;height:2.03848in"
> alt="select as described" />

7.  Click on the **…** button of the **Current value** and select
    **Remove from this solution**. We are removing the value from the
    solution, so it won’t move to test/production.

> <img src="../L07/media/image33.png" style="width:3.04496in;height:2.52732in"
> alt="select as described" />

8.  Close the edit pane.

9.  Click **+ New** and select **More \| Environment variable** again.

10. Enter **Funding Password** for Display name, select **Secret** for
    Data type, enter **secretid** for Default value, select **Azure Key
    Vault** for Secret Store, and click **+ New Azure Key Vault secret
    reference**.

> <img src="../L07/media/image34.png" style="width:2.16142in;height:3.82184in"
> alt="select as described" />

11. DO NOT navigate away from this page. Start a new browser window or
    tab and navigate to your **Azure** portal.

12. Click to open the **FundingFL** Key Vault you created. Remember the
    name of the Key Vault (FL will be your initials)

13. Copy the **Subscription ID**.

> <img src="../L07/media/image35.png" style="width:6.07932in;height:1.51333in"
> alt="select as described" />

14. Go back to the environment variable and paste it in the **Azure
    subscription Id** field.

> <img src="../L07/media/image36.png" style="width:2.76248in;height:3.01628in"
> alt="paste as described" />

15. Enter **Funding** for Resource group name, **FundingFL (FL will be
    your initials)** for Azure Key Vault name, and **FundingPassword** for
    Secret name. These values must match what you
    used or you will see an error at the top of the panel.

> <img src="../L07/media/image37.png" style="width:2.74909in;height:4.36789in"
> alt="select as described and review results of the prior steps" />

16. Click **Save** again.

17. Select **Environment variables** and open the **Funding Password**
    variable you just created.

18. Click on the **…** button of the current value and select **Remove
    from this solution**.

> <img src="../L07/media/image38.png" style="width:3.46832in;height:2.12473in"
> alt="select as described" />

19. Close **Edit** pane.

20. Select **Cloud flows**, select the **CF Manage Inspection Process**
    flow, and click **Edit**.

21. Expand the **Run a flow built with Power Automate for desktop**
    step.

22. Click on the **Run Mode** dropdown and select **Custom Value**.

> <img src="../L07/media/image39.png" style="width:5.14783in;height:2.7123in"
> alt="select as described" />

23. Select the **Funding Run Mode** environment variable from the
    dynamic content pane. This will allow us to determine if the desktop
    flow runs attended or unattended in each environment the solution is
    imported into.

24. Click **Save** and wait for the flow to be saved.

25. Click on the back button.

26. Select **Cloud flows**, select the **CF Manage Woodgrove Funding
    Process** flow, and click **Edit**.

27. Expand the **Run a flow built with Power Automate for desktop**
    step.

28. Click on the **Run Mode** dropdown and select **Enter custom value**.

> <img src="../L07/media/image40.png" style="width:4.95877in;height:2.55824in"
> alt="select as described" />

29. Select the **Funding Run Mode** environment variable from the
    dynamic content pane.

30. Click the **+ Insert a new step** after the trigger and select **Add
    an action**.

31. Select the **Perform an unbound action** action from the **Microsoft Dataverse** connector.

> <img src="../L07/media/image41.png" style="width:4.73702in;height:2.53891in"
> alt="select as described" />

32. Select **RetrieveEnvironmentVariableSecretValue** for Action name,
    enter **rc_FundingPassword** for EnvironmentVariableName, click on
    the **…** Menu button, and select **Settings**.

> <img src="../L07/media/image42.png" style="width:5.16566in;height:1.56956in"
> alt="select as described" />

33. Turn on **Secure Outputs** and click **Done**. This ensures the
    value is not visible when someone views the run details after
    execution.

> <img src="../L07/media/image43.png" style="width:4.51597in;height:2.93498in"
> alt="select as described" />

34. Expand the **Run a flow built with Power Automate for desktop** step
    again.

35. Remove the current Password value and select
    **RetrieveEnvironmentVariableSecretValueResponse** from the dynamic
    content pane.

> <img src="../L07/media/image44.png" style="width:5.06403in;height:3.03463in"
> alt="select as described" />

36. Click on the **…** Menu button and select **Settings**.

37. Turn on **Secure Inputs** and click **Done**.

38. Click **Save** and wait for the flow to be saved.

# Exercise \#4: Export Solution

In this exercise, will export the Builder Risk Service and the
Construction Funding solutions.

## Task \#1: Export solution

1.  In your Local machine, navigate to <https://make.powerapps.com/> and
    make sure you are in your Dev environment.

2.  Select Solutions, select the **Builder Risk Service** solution and
    click **Export solution**.

> <img src="../L07/media/image45.png" style="width:5.64801in;height:2.49031in"
> alt="select as described" />

3.  Click **Publish** and wait for the publishing to complete.

4.  Click **Next**.

5.  Select **Managed** and click **Export**.

> <img src="../L07/media/image46.png" style="width:2.67828in;height:3.59729in"
> alt="select as described" />

6.  Wait for the export to complete and click **Download**.

7.  Select the **Construction Funding** solution and click **Export
    solution**.

8.  Click **Publish** and wait for the publishing to complete.

9.  Click **Next**.

10. Select **Managed** and click **Export**.

11. Wait for the solution to be exported.

12. Click **Download**.

13. Click to open the **Construction Funding** solution.

> <img src="../L07/media/image47.png" style="width:5.34335in;height:2.82772in"
> alt="select as described" />

14. Select Cloud flows, select the **Process Construction Funding
    Request** flow and click **Turn Off**. We are doing this simply so
    we can use the same shared email for testing, in a real solution you
    would use separate mailboxes for dev/test/production.

> <img src="../L07/media/image48.png" style="width:6.12099in;height:2.26987in"
> alt="select as described" />

# Exercise \#5: Import Solution

In this exercise, will import the Builder Risk Service and Construction
Funding solutions and test the flows.

## Task \#1: Import solution

1.  Select your **Test** environment.

2.  Select **Solution** and click **Import solution**.

3.  Click **Browse**.

4.  Select the **BuilderRiskService_1\_0_0\_1_managed.zip** solution you
    exported and click **Open**.

5.  Click **Next**.

6.  Click **Import** and wait for the import to complete.

7.  Click **Import solution** again.

8.  Click **Browse**.

9.  Select the **ConstructionFunding_1\_0_0\_1_managed.zip** solution
    you exported and click **Open**.

10. Click **Next**.

11. Click **Next** again.

12. Click on the drop down for the **Builder Risk Service** connection
    and select **+ New connection**.

> <img src="../L07/media/image49.png" style="width:5.07772in;height:3.64737in"
> alt="select as described" />

13. DO NOT navigate away from this page. Start a new browser window or
    tab and navigate to
    <https://adatumbuilderrisktest.azurewebsites.net/>

14. Click on the **API Key** link.

15. Copy the **API Key**.

> <img src="../L07/media/image50.png" style="width:4in;height:2.36in"
> alt="select as described" />

16. Go back to the Builder Risk Service connection, paste the API Key
    you copied and click **Create**.

17. Close the connections browser tab or window.

18. Click **Refresh**.

> <img src="../L07/media/image51.png" style="width:3.69745in;height:1.84352in"
> alt="select as described" />

19. Click on the **Office 365** connection dropdown and select **+ New
    connection**.

20. Click **Create**.

21. Select your credentials.

22. Close the connections browser tab or window.

23. Click **Refresh**.

24. Click on the **Desktop flows** connection dropdown and select **+
    New connection**.

25. Enter **Funding** for Domain and username, enter the password you created in lab00, and click **Create**.

> <img src="../L07/media/image52.png" style="width:4in;height:3.2in"
> alt="select as described" />

26. Close the connections browser tab or window.

27. Click **Refresh**.

28. Click on the **Dataverse** connection dropdown and select **+ New
    connection**.

29. Click **Create**.

30. Select your credentials.

31. Close the connections browser tab or window.

32. Click **Refresh**.

33. Click Next.

> <img src="../L07/media/image53.png" style="width:4.24517in;height:2.47826in"
> alt="select as described" />

34. DO NOT navigate away from this page. Start a new browser window or
    tab and navigate to your Azure portal.

35. Click to open the Key Vault.

> <img src="../L07/media/image54.png" style="width:5.96955in;height:1.75005in"
> alt="select as described" />

36. Copy the **Subscription ID**. For this lab you will use the same
    subscription you used for the Dev. Usually, you would create a
    different subscription for Dev, Test, and Production.

> <img src="../L07/media/image55.png" style="width:6.03344in;height:1.72108in"
> alt="select as described" />

37. Paste the text below in the Funding Password field.
    Replace **[SubscriptionID]** with subscription id you copied and
    replace **[FL]** with your initials.

> /subscriptions/**\[SubscriptionID\]**/resourceGroups/Funding/providers/Microsoft.KeyVault/vaults/Funding[FL]/secrets/FundingPassword

38. Click **Import** and wait for the import to complete.

> <img src="../L07/media/image56.png" style="width:4.7211in;height:2.86757in"
> alt="select as described" />

39. Import should succeed. Note: If it takes more than five minutes to
    import, check History to see if it failed. If you didn’t have the
    correct Key Vault information this can occur.

> <img src="../L07/media/image57.png" style="width:5.18967in;height:1.57983in"
> alt="select as described" />

40. **Publish all customizations** and wait for the publishing to complete.

41. Click to open the **Construction Funding** solution.

42. Select Cloud flows and open the **Create Test Data** flow.

> <img src="../L07/media/image58.png" style="width:5.58397in;height:2.55693in"
> alt="select as described" />

43. Click **Run**.

44. Click **Run flow**.

45. Click **Done**.

46. Wait for the run to complete.

47. Select the **Process Construction Funding Request** cloud flow and turn it on if it not already turned on.

## Task \#2: Test

1.  Go to your remote desktop and **Sign out**. Make sure you choose
    sign out and not disconnect as unattended flows won’t run when you
    are signed in.

> <img src="../L07/media/image59.png" style="width:6.02215in;height:2.50923in"
> alt="select as described" />

2.  Go to the resources folder of the lab and open the Test folder.

3.  You will attach the **Attachment AI Test** file when you send the
    email.

> <img src="../L07/media/image60.png" style="width:5.52944in;height:1.00782in"
> alt="select the file for testing" />

4.  Send an email to <Funding@yourdomain.onmicrosoft.com> make sure the
    subject of the email is **MC3747** and you attach the **Attachment
    AI Test.pdf** file.

5.  Navigate to <https://make.powerapps.com/> and make sure you have the
    **Test** environment selected.

6.  Select **Solutions** and click to open the **Construction Funding**
    solution.

7.  Select **Cloud flows** and open the **Process Construction Funding
    Request** flow.

8.  Review the **28-day run history**.

9.  You should see a flow run with a Status of **Running**. Select the timestamp 
    to open the flow run details.

10. Wait for the flow run to complete.

11. The flow run should succeed, and you should get an email back with the Subject line
    **Draw approved**.

> <img src="../L07/media/image61.png" style="width:5.96545in;height:4.0184in"
> alt="review the results of the prior steps" />
