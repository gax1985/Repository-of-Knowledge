<small><span><span>April 28, 2017</span> updated by </span><a href="https://www.top-password.com/blog/reset-forgotten-windows-server-2016-password/#comments" rel="nofollow">Leave a reply »</a></small>

What to do if you forgot the administrator password in Windows Server 2016? As a IT administrator, you should have ever experienced trouble logging into a server with unknown password, so in this post we’ll show two simple ways to reset forgotten Windows Server 2016 administrator password. These methods work on other Windows versions as well.

![forgot-server-2016-password](https://www.top-password.com/blog/wp-content/uploads/2016/10/forgot-server-2016-password.png)

**Method 1: Reset Windows Server 2016 Password with Installation Disk**

If you have the original Windows installation disk, you can [reset forgotten Windows Server 2016 password](http://www.top-password.com/knowledge/reset-windows-server-2016-password.html) by following these steps:

1.  Boot the server from the Windows Server 2016 Installation DVD. When the Setup screen appears, press **SHIFT + F10** keys to open Command Prompt.
2.  At the Command Prompt, run the following commands:  
    `d:   cd Windows\System32   ren Utilman.exe Utilman.exe.original   copy cmd.exe Utilman.exe   shutdown -r -t 0`
    
    ![replace-utilman-with-cmd](https://www.top-password.com/blog/wp-content/uploads/2016/10/replace-utilman-with-cmd.png)
    
3.  The server should now reboot and present the logon screen. Press **Windows Key + U** or click the **Ease of Access** button, Command Prompt will pop up and type:  
    `net user Administrator P@ssword123`
    
    ![reset-windows-server-2016-password](https://www.top-password.com/blog/wp-content/uploads/2016/10/reset-windows-server-2016-password.png)This will set the password for the Administrator to be P@ssword123 (case sensitive).
    
4.  Close the Command Prompt and you should now be able to log back onto Windows Server 2016 using the password you have provided in the previous step. After logging in, browse to the directory C:\\Windows\\System32, delete Utilman.exe and rename Utilman.exe.original back to Utilman.exe.

**Method 2: Reset Windows Server 2016 Password with PCUnlocker**

[PCUnlocker](http://www.top-password.com/reset-windows-password.html) is easy to use bootable utility that can help you reset domain & local administrator password in Windows Server 2016. Here’s how:

1.  Boot your server from PCUnlocker Live CD (or USB drive). If you don’t have one, you need to create it from another working PC. Download the PCUnlocker ISO file and burn it to CD (or USB drive) using the [ISO2Disc](http://www.top-password.com/iso2disc.html) software.
    
    ![](https://www.top-password.com/images/iso2disc.png)
    
2.  When booting to the PCUnlocker program, you’ll see two options: **Reset Local Admin/User Password**, **Reset Active Directory Password**. The latter option is for domain controller only.
    
    ![pcunlocker](https://www.top-password.com/blog/wp-content/uploads/2016/10/pcunlocker.png)
    
3.  Select the Administrator account and click the **Reset Password** button. Depend on your account type (local account or domain account), the program will set the password to be empty or Password123.
    
    ![reset-server-2016-domain-password](https://www.top-password.com/blog/wp-content/uploads/2016/10/reset-server-2016-domain-password.png)
    
4.  After resetting the password, reboot the server and take out CD. You can then log into Windows Server 2016 administrator account successfully.

  

-   [Previous Post: How to Add Missing Disk Cleanup in Windows Server 2012](https://www.top-password.com/blog/add-missing-disk-cleanup-in-windows-server-2012/)
-   [Next Post: 5 Ways to Stop or Start SQL Server Service](https://www.top-password.com/blog/stop-or-start-sql-server-service/)