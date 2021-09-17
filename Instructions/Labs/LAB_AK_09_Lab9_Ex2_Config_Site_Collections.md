# Module 9 - Lab 9 - Exercise 2 - Configuring SharePoint Online Sites

In this exercise, Holly Dickson wants to begin exploring SharePoint Online site collections. A site collection is made up of one top-level site and all sites below it. For comparison purposes, Holly plans to create a site collection using the SharePoint Online admin center, followed by a second site collection using Windows PowerShell. She will then configure access permissions to the site collections, and then follow that up by verifying the access permissions work. 


## Task 1: Create a site using the SharePoint admin center

In this task, you will use the SharePoint admin center to create a site collection for Adatum's Marketing department. 

1. On **LON-CL1** you should still be logged in as the **Administrator** with a password of **Pa55w.rd**.

2. You should still have Microsoft Edge open from the previous exercise, along with tabs for the **Microsoft Office Home** page, the **Microsoft 365 admin center**, and the **SharePoint admin center**. If so, select the **SharePoint admin center** and proceed to the next step. 

	Otherwise, open Microsoft Edge, navigate to **https://portal.office.com/**, log in as **Holly@M365xZZZZZZ.onmicrosoft.com** (where ZZZZZZ is the tenant ID provided by your lab hosting provider) and a password of **Pa55w.rd**, and then in the **Microsoft Office Home** page, select **Admin** to open the Microsoft 365 admin center, select **Show all** in the left-hand navigation pane, and then under **Admin centers** select **Sharepoint**.


3. In the left-hand navigation page, expand **Sites** and select **Active sites**.

4. On the menu-bar above the list of sites, select **+ Create**.

5. On the **Create a site** window, select **Communication Site**.

6. In the **Communication Site** window, enter **Marketing** in the **Site name** field.

7. In the **Site owner** field, enter **Admin** and then select **MOD Administrator** from the list.

8. Leave the default values unchanged for the other settings and then select **Finish**. This will return you to the **Active sites** page.


 **Note:** It can sometimes take a few minutes for SharePoint Online to provision a new site. Eventually, the **Marketing** site will appear in the list of active sites. Do not proceed to the next step until the **Marketing** site appears in the list.


9. On the **Active sites** page, hover your mouse over the **URL** for the marketing site. Select the check box that appears to the left of the of the **Marketing** site's URL. 

10. Selecting the check box for the marketing site will trigger the **Sharing** menu to appear on the ribbon. However, it may take a few minutes for the **Sharing** menu to appear. You can speed this up by refreshing the page by selecting the **Refresh** icon to the left of the address bar, or by pressing the F5 key.

11. Select **Sharing** once the Sharing menu appears on the ribbon.

12. In the **Sharing** window, select **Anyone** and then select **Save**.

 **Note:** The site settings changes to allow external user sharing. This process is usually done within one minute. External user sharing is now enabled and you can use it for this marketing site.

13. Leave your Edge browser and all its tabs open and proceed to the next task.


## Task 2: Create a site collection using Windows PowerShell

Now that you have experience creating a site collection using the SharePoint admin center, you will use Windows PowerShell to create a site collection for Adatum's Accounting department. This will provide you with experience using both mechanisms to create sites. 

1. You should still be logged into **LON-CL1** and you should have the **SharePoint admin center** open from the prior task.

2. In the Search box in the bottom left corner of your taskbar, enter **powershell**. 

3. In the list of search results, right-click on **Windows PowerShell**, and in the menu that appears select **Run as administrator**.

4. If a **Do you want to allow this app to make changes to your device** dialog box appears, select **Yes**.

5. Maximize your PowerShell window. In **Windows PowerShell**, at the command prompt type the following command and then press Enter:

		Install-Module Microsoft.Online.SharePoint.PowerShell
	
6. If you are prompted to install the **NuGet provider**, enter **Y** to select **[Y] Yes**. 

7. If you are prompted to confirm whether you want to install the module from an untrusted repository (PSGallery), enter **A** to select **[A] Yes to All.** 

8. At the command prompt, type the following command and then press Enter (where ZZZZZZ is the unique tenant ID provided by your lab hosting provider): 

		Connect-SPOService –Url https://M365xZZZZZZ-admin.sharepoint.com –credential admin@M365xZZZZZZ.onmicrosoft.com

9. In the **Enter your credentials** dialog box, enter (or copy and paste in) the tenant admin password provided by your lab hosting provider and then Select **OK**.

10. At the command prompt, type the following command and then press Enter to add a new site titled **Accounting** (where ZZZZZZ is the tenant ID provided by your lab hosting provider): 

		New-SPOSite -Url https://M365xZZZZZZ.sharepoint.com/sites/Accounting -Owner Admin@M365xZZZZZZ.onmicrosoft.com -StorageQuota 500 -NoWait -Template PROJECTSITE#0 –Title “Accounting”

11. Minimize the **PowerShell** window.

12. In your Edge browser, the **Active sites** page should still be displayed from the prior task. If the new **Accounting** site does not appear in the list of sites, select the **Refresh** icon that appears to the left of the address bar. **Do not** proceed to the next step until you have verified that the new **Accounting** site appears in the Sites list.

13. Leave your Edge browser open along with the **Microsoft Office Home** tab, the **Microsoft 365 admin center** tab, and the **SharePoint admin center** tab, and then proceed to the next task.


## Task 3: Configure permissions on the sites

Now that you have added sites for Adatum's Marketing and Accounting departments, you will configure permissions for the Marketing site. Because you are still signed into Microsoft 365 as Holly Dickson, you must open an In-Private browser session in Edge and log into Microsoft 365 as the MOD Administrator so that you can assign Patti Fernandez as an admin to the Marketing site. 

Only a site's site admin can assign another user as an admin to the site. While you are signed into Edge as Holly Dickson, she is not an admin for the Marketing site. Therefore, you will have to open an InPrivate session so that you can log in as the MOD Administrator to make this assignment. 

You will then open a second InPrivate browsing session and log in as Patti Fernandez to verify that she is a site admin for the Marketing site. You will do this by accessing the Marketing site's **Site Collection Administrators** page, which is only accessible to site admins.  

1. On **LON-CL1**, right-click on the **Edge** icon on the taskbar, and in the menu that appears, select **New InPrivate window**.

2. In your **InPrivate Browsing** session, enter the following URL in the address bar: **https://portal.office.com**.

3. In the **Sign in** window, enter **admin@M365xZZZZZZ.onmicrosoft.com** (where ZZZZZZ is the tenant ID provided by your lab hosting provider), and then select **Next**.

4. In the **Enter password** window, enter (or copy and paste in) the tenant admin password provided by your lab hosting provider and then select **Sign in**.

5. On the **Stay signed in?** window, select **Don't show this again** and then select **Yes**. 

6. On the **Microsoft Office Home** page, select **Admin**.

7. On the **Microsoft 365 admin center** page, in the left-hand navigation pane, select **Show all**, and then under the **Admin centers** group, select **SharePoint**.

8. On the **SharePoint admin center** page, in the left-hand navigation pane, select **Sites**, and then select **Active Sites**.

9. On the **Active sites** page, note the **Marketing** and **Accounting** site collections appear in the list of active sites. Select the **Marketing** site.

10. At the time you created the **Marketing** site, the MOD Administrator was added as a site admin. You now want to add **Patti Fernandez** as a second site admin. 

	On the **Marketing** pane that appears on the right-side of the screen, select the **Permissions** tab.

11. In the **Permissions** tab, under the **Site admins** section, select **Manage**.

12. On the **Manage admins** page, in the **Add an admin** field, enter **Patti**. This will display a list of all active users whose first name starts with Patti. In the list of users that appears, select **Patti Fernandez** and then select **Save**. Patti and the MOD Administrator should now appear as admins for this site. 

13. Close the **Marketing** pane.

14. Close the **InPrivate** browsing session for the **MOD Administrator**. 

15. Perform the same steps as before to open a new **InPrivate** browsing session, this time for **Patti Fernandez**.

16. In your new **InPrivate** browsing session, enter the following URL in the address bar: **https://portal.office.com**

17. On the **Pick and account** dialog box, select **Use another account**.

18. In the **Sign in** window, enter **PattiF@M365xZZZZZZ.onmicrosoft.com** (where ZZZZZZ is the tenant ID provided by your lab hosting provider), and then select **Next**.

19. In the **Enter password** window, enter (or copy and paste in) the tenant admin password provided by your lab hosting provider and then select **Sign in**.

20. This opens the **Microsoft Office Home** tab in your InPrivate browsing session. Open a new tab in your browser and enter the following URL in the address bar: **https://M365xZZZZZZ.sharepoint.com/sites/Marketing** (where ZZZZZZ is the tenant ID provided by your lab hosting provider).

21. This opens the **Marketing** site collection. In the upper-right corner of the screen (to the left of Patti's picture), select the **gear (Settings)** icon (the wheel icon). In the **Settings** window that appears, select **Site permissions**.

22. On the **Site permissions** page, under the **Advanced permissions setings** group, select **Site collection administrators**.

23. Verify that **MOD Administrator** and **Patti Fernandez** appear in field. You have just verified that Patti is indeed a site administrator for the Marketing site, since she can access the Site Collection Administrators page (only site admins can access this page).

24. Close the **InPrivate** browsing session for **Patti Fernandez**. 

25. Leave your Edge browsing session open along with all its tabs. 

## Task 4: Verify access to the site collections

In this task, the MOD Administrator will assign access to the Marketing site to two users - Joni Sherman, who will request access, and Nestor Wilke, who the MOD Administrator felt should have access as well since Nestor is a company Director. While Nestor will not request access, the MOD Admin will share access to the site with him. You will again use InPrivate browsing sessions for the different users to access the Marketing site on LON-CL1.

1. On **LON-CL1**, right-click on the **Edge** icon on the taskbar, and in the menu that appears, select **New InPrivate window**.

2. In your **InPrivate Browsing** session, enter the following URL in the address bar: **https://portal.office.com**.

3. In the **Sign in** window, enter **JoniS@M365xZZZZZZ.onmicrosoft.com** (where ZZZZZZ is the tenant ID provided by your lab hosting provider), and then select **Next**.

4. In the **Enter password** window, enter (or copy and paste in) the tenant admin password provided by your lab hosting provider and then select **Sign in**.

5. On the **Stay signed in?** window, select **Don't show this again** and then select **Yes**. 

6. This opens the **Microsoft Office Home** tab in your Edge browser. Open a new tab in your browser and enter the following URL in the address bar: **https://M365xZZZZZZ.sharepoint.com/sites/Marketing** (where ZZZZZZ is the tenant ID provided by your lab hosting provider).

7. This displays an **Access required** page that indicates **You need permission to access this site.** A message field is prefilled with the following default message: **I'd like access, please**. 

	Since you can customize this message, Joni wants to enter a message that justifies why he needs permission to access this site. Replace the existing message with the following: **My name is Joni Sherman. I am a Technical Account Manager for Western Europe. I need access to this site so that I can stay abreast of the latest marketing plans for Adatum's Fabrication division.**

8. Select the **Request Access** button.

9. Close this InPrivate browsing session for **Joni Sherman**. 

10. Perform the same steps as before to open a new **InPrivate** browsing session, this time for the **MOD Administrator**.

11. In your new **InPrivate** browsing session, enter the following URL in the address bar: **https://portal.office.com**

12. In the **Sign in** window, enter **admin@M365xZZZZZZ.onmicrosoft.com** (where ZZZZZZ is the tenant ID provided by your lab hosting provider), and then select **Next**.

13. In the **Enter password** window, enter (or copy and paste in) the tenant admin password provided by your lab hosting provider and then select **Sign in**.

14. On the **Stay signed in?** window, select **Don't show this again** and then select **Yes**. 

15. This opens the **Microsoft Office Home** tab in your InPrivate browsing session. Open a new tab in your browser and enter the following URL in the address bar: **https://M365xZZZZZZ.sharepoint.com/sites/Marketing**.

16. This opens the **Marketing** site. In the upper-right corner of the screen (to the left of the circle with the **MA** initials), select the **gear (Settings)** icon (the wheel icon). In the **Settings** window that appears, select **Site contents**.

17. On the **Site contents** page, select **Access requests**.

18. On the **Access Requests** page, verify that Joni Sherman's request appears under the **Pending Requests** section. For Joni's request, select the **Approve** button.

19. On the current **Access Requests - Default** tab, select the back arrow on the address bar to return to the **Site Settings** page. Under the **Users and Permissions** group, select **Site permissions**.

20. On the **Site permissions** page, in the list of users who have access to this site, select **Marketing Visitors**.

21. In the **People and Groups - Marketing Visitors** page, verify that Joni Sherman's account appears in the list.  

22. You now want to invite Nestor Wilke to become a member of the Marketing Site. On the menu bar at the top of the page, select the drop-down arrow to the right of **New**, and then in the drop-down menu that appears, select **Add Users**.

23. On the **Share 'Marketing'** window, the **Invite People** tab is displayed by default. In the **Enter names or email addresses** field, enter **Nestor**. A list of users whose first name starts with Nestor will appear. Select **Nestor Wilke** and then select **Share**. 

	Nestor's name will now appear in the **People and Groups - Marketing Visitors** page along with Joni Sherman. 

24. Close this InPrivate browsing session for the **MOD Administrator**. 

25. You will now verify whether Joni Sherman can access the the Marketing site. Perform the same steps as before to open a new **InPrivate** browsing session.

26. In your new **InPrivate** browsing session, enter the following URL in the address bar: **https://portal.office.com**

27. In the **Sign in** window, enter **JoniS@M365xZZZZZZ.onmicrosoft.com** (where ZZZZZZ is the tenant ID provided by your lab hosting provider), and then select **Next**.

28. In the **Enter password** window, enter (or copy and paste in) the tenant admin password provided by your lab hosting provider and then select **Sign in**.

29. On the **Stay signed in?** window, select **Don't show this again** and then select **Yes**. 

30. This opens the **Microsoft Office Home** tab in your InPrivate browsing session. Open a new tab in your browser and enter the following URL in the address bar: **https://M365xZZZZZZ.sharepoint.com/sites/Marketing** (where ZZZZZZ is the tenant ID provided by your lab hosting provider).

31. This opens the **Marketing** site. You have just verified that Joni can access the site after requesting access to it and later being granted access by a site administrator.

32. Close this InPrivate browsing session for **Joni Sherman**. 

33. You will now verify whether Nestor Wilke can access the the Marketing site. Perform the same steps as before to open a new **InPrivate** browsing session.

34. In your new **InPrivate** browsing session, enter the following URL in the address bar: **https://portal.office.com**

35. In the **Sign in** window, enter **NestorW@M365xZZZZZZ.onmicrosoft.com** (where ZZZZZZ is the tenant ID provided by your lab hosting provider), and then select **Next**.

36. In the **Enter password** window, enter (or copy and paste in) the tenant admin password provided by your lab hosting provider and then select **Sign in**.

37. On the **Stay signed in?** window, select **Don't show this again** and then select **Yes**. 

38. This opens the **Microsoft Office Home** tab in your InPrivate browsing session. Open a new tab in your browser and enter the following URL in the address bar: **https://M365xZZZZZZ.sharepoint.com/sites/Marketing** (where ZZZZZZ is the tenant ID provided by your lab hosting provider).

39. This opens the **Marketing** site. You have just verified that Nestor can access the site after the site admin (the MOD Administrator) shared site membership with him.

40. Close this InPrivate browsing session for **Nestor Wilke**. 

41. Leave your Edge browsing session open along with all its tabs. 


**Results**: After completing this exercise, you should have created and configured SharePoint Online site collections.

# Proceed to Lab 9 - Exercise 3
