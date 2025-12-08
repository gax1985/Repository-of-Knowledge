


You have two files : 

1. Lure
2. Malicious .EXE file


The idea is to **combine the two files into one file** and the target will open the combined file.

As far as the person knows, the intended program will be executed, with the malicious binary executing in the background. 

It is bad for email, but it is most useful in **USB drops**. 

Phil used an .xls file (Microsoft Excel file) to do this. 


Phil mentioned that in the penetration test, Eric wrote a code that scrapes the information of interest, and sends it back to the **Command-and-Control Server (C2)**. 


The exploit is in the file, *not the USB*!


## Choose a Bait File


Choose a bait file that the target will open. We did **Macros** in the first year. 

We need to  : 

1. who they are ?
2. Who do they work for ?

To be successful , you need the **best idea of who your target will be** to maximize the chances they will open it. 

**OSINT** is the first step!

If the target is an Administrative Employee, the bait file could be :

1. PDF
2. Excel Sheet (proposed salaries sheet) 


Do NOT worry about the size! if they have file extensions showing, it would be .xls.exe. 

Ron : We will not necessarily do the USB drops in the office of the target. You can do this in the :

1. Parking Lot : If the USB is dropped in the parking lot and not picked up by the employees, the person who picks it up opens it and announces to the office "I have checked this USB drive, and it contains our organization's name". Them being a good person would do this. Think of the gender class of the lowest-paid employees, and how you can use that to make sure they are the ones they pick up the USB. 



## Create Malicious Binary


He used **Auto-Py-to-Exe**. MSFVenom would be detected, but then you would do extensive testing and EDR evasion. Test this on Windows 11, Windows 10 and any different configurations that our target will have. 

The name is not important. The target will not see the name. Although, simpler is better!



## Install *WinRAR*


It is a compression tool. It is easiest to use a Windows virtual machine. The target is **Windows** so it is easier to build everything on the same OS.


## Find the .ICO image


This is the image that Windows uses to pick the icon. The icon for each file type is different depending on each Windows version. The default icon for .exe file is the little window, and you do not want it to be that. It should appear exactly as a real Excel file. You can extract the .ico file from icons that are on Windows 10 and Windows 11. 


## Create the Archive


We have the two files. We are compressing the two files together. WinRAR will pop up!



## Name the Archive 


The archive name should have the same name as the bait file. Choose **"Create SFX archive*" , which is a self-extracting archive. Compression method is **normal**, and the **Dictionary Size** is **32 MB**. 


## Create your Archive


Open **Advanced SFX Options**. click on the **Setup** tab, and select **Run After Extraction**. In the **Run after Extraction** box, enter the malicious file's name first, then the Excel file. 


Unpack to Temporary Finder, and select **Hide All**. Then to the **Text and Icon, and choose the SFX icon from the particular icon file**. 


In the **Update** tab, select **Extract and Update Files**, and then select **Overwrite all Files**. 


## Finalize the Archive


Click on OK twice



>[!note]
>
>There is another way you can do this with the **.lnk** file. Ron will demonstrate it later! Ron would like us to think of this class as **One Redteam**. We have a client, and we are going to use most of the skills we learned in the program, as well as new skills we will gain on the way. Ron does not know if we went to a Red Team presentation, or if we have done it ourselves. OSINT, Social Engineering planning and techniques are the most important thing. We do NOT want to discover anything new while doing it. 




>[!Ron's Statement]
>
>We look at the **organizational chart for the client**. Who do we find typically in the **Support** or **Clerical Roles**? typically they are women. If you want a woman to pick up the USB, you would plant the USB next to the toilet in the women's bathroom (as well as the Men's bathroom). 
>
>## USBs 
>
>>We want them to be noticable and visible. What do we know about people's psychology to attract them to this USB? it should be noticed. For men, they are most likely to be attracted to something rugged, steel-made or other attributes. You want your test to be successful! 
>
>If we decide to do a **Parking Lot Drops**, we would need **Multiple days of Surveillance** to know where the target parks. The company puts pictures of their employees on their website. You simply have to park far away, and watch with binoculars, match names to faces, record the car's information, figure out if they park the car in the same spot every day, leave it by their parking space. Once you have the car identified, take their picture, wait until they are in the office, and go and drop off the USB next to the driver's car. 



>[!todo]
>
>Much of the work this week will be covering the OSINT aspect. We will review the profiles as a class, and fill in any details that anyone missed. 



If we are doing Lockheed Martin, we would focus on the **Supply Chain**. it is difficult to gain the cooperation of the supply chain partner. You could make the attack look like the Supply Chain Partner. You would have to be careful about that, and to gain the supply chain's legal approval. You focus your activity on the client who signed the contract with you, by the most senior authority in the organization who could. 


We are not in short! What if one random employee decides to take independent legal action due to them being picked out as the errant entity in the Penetration Test in question? This is why we do **NOT** pinpoint them. An agreement would be signed to protect us against that, where the contract would involve us telling them that this person in question is the errant entity, and they can go to their SOC and check the email blocking status of this person in question (Ron mentioned that we should not tell them who is it exactly, unless the legal agreement protects us personally). 