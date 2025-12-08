
https://nscconline.brightspace.com/d2l/le/content/332228/viewContent/5260436/View

Select from the menu : 


1. Social Engineering Attack 

then 

1. Web Attack 

Then

2. Site Cloner



set:webattack > IP address ? 

set:webattack > Enter URL to clone? 

set:webattack > credential harvester attack

set:webattack > Site Cloner




**Social Engineering Lab**

Have 2 VMs running. One being Kali and the other being any other OS capable of using a browser.

On the Kali machine, perform the following:

sudo apt update && sudo apt install set

sudo setoolkit

You should see the following:

![](file:///tmp/lu45857609zz.tmp/lu4585760a1v_tmp_10e217ae.png)

Now select the desired mode of operation:

set> 1 # For "Social-Engineering Attacks"

set> 2 # For "Website Attack Vectors"

set:webattack> 3 # For "Credential Harvester Attack"

set:webattack> 2 # For "Site Cloner"

Allow for the default IP to be used, this should be the IP of your Kali VM.

For the URL to be cloned, choose:

set:webattack> Enter the url to clone: https://app.simplelogin.io/auth/login

On your other VM, open a browser and navigate to the IP of your Kali VM. It should display the app.simplelogin.io login page. Enter some credentials (not your actual one) and then note the logged information on your Kali VM.

You should see something like the following.

![](file:///tmp/lu45857609zz.tmp/lu4585760a1v_tmp_f7938225.png)
