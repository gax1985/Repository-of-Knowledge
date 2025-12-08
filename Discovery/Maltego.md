



### From Domain 1 - Discovery



![[Pasted image 20240908204026.png]]



![[Pasted image 20240908204037.png]]



![[Pasted image 20240908204051.png]]


![[Pasted image 20240908204104.png]]


![[Pasted image 20240908204116.png]]


![[Pasted image 20240908204135.png]]





[![](https://www.maltego.com/img/maltego-logo.svg)](https://www.maltego.com/)

![](https://www.maltego.com/img/icons/hamburger.svg)


# Beginners' Guide | Charting My First Maltego Graph

![](https://www.maltego.com/img/Social%20Profile%20Pic@4x.png)

##### Maltego Team

![](https://www.maltego.com/images/uploads/how_to_create_your_first_maltego_graph_0.png)

This post introduces Maltego graphs, Transforms, and Entities. It shows you how to create a new graph, populate the graph with Entities, run Transforms on those Entities to obtain new Entities and copy Entities from one graph to another.

If you have already played around with Maltego to create your first graph, read on about conducting a level 1 network footprint investigation in **[the next Beginners Guide article](https://www.maltego.com/blog/beginners-guide-to-maltego-mapping-a-basic-level-1-network-footprint-part-1/)**.

## Creating Our First Maltego Graph[](https://www.maltego.com/blog/beginners-guide-to-maltego-charting-my-first-maltego-graph/#creating-our-first-maltego-graph)

Let us create our first Maltego graph by clicking on the Maltego button in the top left corner and choosing **New** from the main menu. This creates a new graph for us to work on.

[![Footprint030](https://www.maltego.com/images/uploads/new-graph-1.png)](https://www.maltego.com/images/uploads/new-graph-1.png)

### Step 1: Creating Our First Entity in Maltego[](https://www.maltego.com/blog/beginners-guide-to-maltego-charting-my-first-maltego-graph/#step-1-creating-our-first-entity-in-maltego)

In this guide, we will use GNU organization as an example, which is identified by the domain **gnu[.]org**.

To add an Entity for this domain to the graph, we first search for the **Domain Entity** in the Entity Palette, which is on the left of the window, and drag a new Entity onto the graph.

[![Foorprint031](https://www.maltego.com/images/uploads/domain-entity-1.png)](https://www.maltego.com/images/uploads/domain-entity-1.png)

By default, Entities come with a default value. In our case, the **Domain Entity** has a default value of **maltego.com**. This can be changed by double clicking the Entity value (or pressing the F2 key with the Domain Entity selected) and changing the value to: **gnu[.]org**.

### Step 2: Running Maltego Transforms[](https://www.maltego.com/blog/beginners-guide-to-maltego-charting-my-first-maltego-graph/#step-2-running-maltego-transforms)

#### What Are Transforms?[](https://www.maltego.com/blog/beginners-guide-to-maltego-charting-my-first-maltego-graph/#what-are-transforms)

Transforms are functions which take an Entity as input and create new Entities as output. The output Entities are then linked to the input Entity. This is how a graph grows in Maltego. This could be compared to the way investigations are carried out: you start with some piece of information and you derive new pieces of information from it.

Each Transform accepts certain types of Entities as input. You can see the list of Transforms that can take an Entity as input by right-clicking anywhere on the graph with the Entity selected.

[![Footprint032](https://www.maltego.com/images/uploads/transform-menu-1.png)](https://www.maltego.com/images/uploads/transform-menu-1.png)

You can now choose what Transform to run by selecting that Transform in the context menu.

If you know which Transform you want to run, you can search for it using the search box in the Run Transform menu.

Note the + in the menu options: it indicates a Transform Set, where related Transforms are grouped together. Clicking on the Transform Set will show the Transforms in that set. To go back, select the back arrow as shown below, or simply right-click anywhere in the Transform menu.

[![Footprint009a](https://www.maltego.com/images/uploads/domain-owner-menu-2.png)](https://www.maltego.com/images/uploads/domain-owner-menu-2.png)

#### Run the To Email Address [From whois info] Transform to Find Email Addresses from A Domain[](https://www.maltego.com/blog/beginners-guide-to-maltego-charting-my-first-maltego-graph/#run-the-to-email-address-from-whois-info-transform-to-find-email-addresses-from-a-domain)

In this example, let us find the contact details for the owner of the domain **gnu.org**. Expand the “Domain owner detail” Transform set and select the **To Email address [From whois info]** Transform.

This Transform fetches the “whois” record for the **gnu.org** domain and extracts the administrative email addresses for the domain. Results from the Transform are added as child Entities to the Domain Entity.

[![Footprint011](https://www.maltego.com/images/uploads/to-email-result-1.png)](https://www.maltego.com/images/uploads/to-email-result-1.png)

We can also extract any phone numbers present in the whois data by running the **To Phone numbers [From whois info]** Transform.

[![Footprint012](https://www.maltego.com/images/uploads/to-phone-number-result-1.png)](https://www.maltego.com/images/uploads/to-phone-number-result-1.png)

#### Run the To DNS Name [Find common DNS names] Transform to Find DNS Hostnames Under A Domain[](https://www.maltego.com/blog/beginners-guide-to-maltego-charting-my-first-maltego-graph/#run-the-to-dns-name-find-common-dns-names-transform-to-find-dns-hostnames-under-a-domain)

To find some of the DNS hostnames that exist under gnu.org, run the Transform **To DNS Name [Find common DNS names]** on the **gnu.org** Domain Entity. You can search for this Transform by typing _“_DNS_”_ in the search box:

[![Footprint013](https://www.maltego.com/images/uploads/dns-transform-1.png)](https://www.maltego.com/images/uploads/dns-transform-1.png)

The Transform **To DNS Name [Find common DNS names]** will try to discover various common DNS names in a domain. The common DNS names are tested by prefixing domains with the following names: mail, mx, ns, ftp, webmail, web, gateway, secure, intranet, extranet, smtp, pop, ns1, mx1, email, admin, dmz, blog, dns, forum, ntp, pub, route, sql, ssh, webaccess, xml, imap, and more.

[![Footprint034](https://www.maltego.com/images/uploads/dns-results-1.png)](https://www.maltego.com/images/uploads/dns-results-1.png)

Our graph now contains the administrative contact details and some hostnames under the gnu.org domain.

#### Run the To IP Address Transform to Look Up IP Addresses of Hostnames[](https://www.maltego.com/blog/beginners-guide-to-maltego-charting-my-first-maltego-graph/#run-the-to-ip-address-transform-to-look-up-ip-addresses-of-hostnames)

Next, we can look up the IP addresses of these hostnames. This can be done by selecting all DNS Name Entities and running the Transform, **To IP address [DNS]**. Multiple Entities can be selected by dragging the mouse selection over them – click and drag the mouse to select Entities under the selection box:

[![Footprint035](https://www.maltego.com/images/uploads/multiple-select-1.png)](https://www.maltego.com/images/uploads/multiple-select-1.png)

This Transform returns us the IP address of these DNS names by querying the DNS.

[![Footprint036](https://www.maltego.com/images/uploads/ip-results-1.png)](https://www.maltego.com/images/uploads/ip-results-1.png)

## Remember to Save Your Maltego Graphs[](https://www.maltego.com/blog/beginners-guide-to-maltego-charting-my-first-maltego-graph/#remember-to-save-your-maltego-graphs)

Note: Get into the habit of regularly saving your graph as your investigation progresses. You can do this by selecting **Save As** in the main menu.

[![Footprint037](https://www.maltego.com/images/uploads/save-1.png)](https://www.maltego.com/images/uploads/save-1.png)

Since investigations tend to uncover and contain sensitive data, Maltego offers the option to encrypt saved Maltego graphs. You can choose to encrypt your graphs by selecting the **Encrypt** option and providing a password for encryption.

[![Footprint022](https://www.maltego.com/images/uploads/encrypt-1.png)](https://www.maltego.com/images/uploads/encrypt-1.png)

That’s it! The saved graph can be re-opened by entering your password.

## Dive into Level 1 Network Footprint with Maltego[](https://www.maltego.com/blog/beginners-guide-to-maltego-charting-my-first-maltego-graph/#dive-into-level-1-network-footprint-with-maltego)

In this blog, we’ve illustrated how to create a graph in Maltego, how data is represented as Entities and how to derive more Entities onto the graph by running Transforms.

For a deeper look into some of the Transforms in Maltego, see our next blog post **[Beginner’s Guide to Maltego: Mapping a Basic (Level 1) footprint—Part 1](https://www.maltego.com/blog/beginners-guide-to-maltego-mapping-a-basic-level-1-network-footprint-part-1/)**.

[CONTINUE READING: LEVEL 1 NETWORK FOOTPRINT IN MALTEGO](https://www.maltego.com/blog/beginners-guide-to-maltego-mapping-a-basic-level-1-network-footprint-part-1/)

  
  

Follow us on [Twitter](https://twitter.com/maltegohq) and [Linkedin](https://www.linkedin.com/company/maltego) or [subscribe to our email newsletter](https://www.maltego.com/newsletter-signup/) to make sure you don’t miss out on any updates.

## Related Articles

[Getting Started with Maltego](https://www.maltego.com/categories/getting-started-with-maltego/)

[

### Beginner's Guide | Mapping a Basic (Level 1) Network Footprint – Part 2

](https://www.maltego.com/blog/beginners-guide-to-maltego-mapping-a-basic-level-1-network-footprint-part-2/)[![](https://www.maltego.com/img/icons/share.svg)](https://www.maltego.com/blog/beginners-guide-to-maltego-mapping-a-basic-level-1-network-footprint-part-2/)

![thumbnail Image](https://www.maltego.com/images/uploads/mapping-level-1-network-footprint-with-maltego.png)

[Getting Started with Maltego](https://www.maltego.com/categories/getting-started-with-maltego/)

[

### Beginner's Guide | Mapping a Basic (Level 1) Network Footprint – Part 1

](https://www.maltego.com/blog/beginners-guide-to-maltego-mapping-a-basic-level-1-network-footprint-part-1/)[![](https://www.maltego.com/img/icons/share.svg)](https://www.maltego.com/blog/beginners-guide-to-maltego-mapping-a-basic-level-1-network-footprint-part-1/)

![thumbnail Image](https://www.maltego.com/images/uploads/mapping-level-1-network-footprint-with-maltego.png)

[Getting Started with Maltego](https://www.maltego.com/categories/getting-started-with-maltego/)

[

### Beginners' Guide | Setting up Maltego Community Edition (CE)

](https://www.maltego.com/blog/beginners-guide-to-maltego-setting-up-maltego-community-edition-ce/)[![](https://www.maltego.com/img/icons/share.svg)](https://www.maltego.com/blog/beginners-guide-to-maltego-setting-up-maltego-community-edition-ce/)

![thumbnail Image](https://www.maltego.com/images/uploads/setting_maltego_community_edition-ce-.png)

[Data in Maltego](https://www.maltego.com/categories/data-in-maltego/) [Maltego Tips & Tricks](https://www.maltego.com/categories/maltego-tips-tricks/) [Getting Started with Maltego](https://www.maltego.com/categories/getting-started-with-maltego/)

[

### Integrating Wireless Data into Your OSINT Investigations

](https://www.maltego.com/blog/integrating-wireless-data-into-your-osint-investigations/)[![](https://www.maltego.com/img/icons/share.svg)](https://www.maltego.com/blog/integrating-wireless-data-into-your-osint-investigations/)

![thumbnail Image](https://www.maltego.com/images/uploads/integrating_wireless_data_0.png)

[Getting Started with Maltego](https://www.maltego.com/categories/getting-started-with-maltego/)

[

### Beginners' Guide | Examining your Digital Profile and Social Media Footprint

](https://www.maltego.com/blog/beginners-guide-examining-your-digital-profile/)[![](https://www.maltego.com/img/icons/share.svg)](https://www.maltego.com/blog/beginners-guide-examining-your-digital-profile/)

![thumbnail Image](https://www.maltego.com/images/uploads/examining_your_digital_profile_and_social_media_footprint.png)

![](https://www.maltego.com/img/icons/caret-circle-left.svg)

![](https://www.maltego.com/img/icons/caret-circle-right.svg)
----------------------------------------------------------------------------------------------------------


Table of Contents

[Explore Our Membership](https://www.stationx.net/vip-membership?cta_src=blog&cta_p=sticky-sidebar)

- [What Is Maltego?](https://www.stationx.net/how-to-use-maltego/#what-is-maltego)
- [Starting Up](https://www.stationx.net/how-to-use-maltego/#starting-up)
- [Interface](https://www.stationx.net/how-to-use-maltego/#interface)
- [Starting an Investigation](https://www.stationx.net/how-to-use-maltego/#starting-an-investigation)
- [Working With Transforms](https://www.stationx.net/how-to-use-maltego/#working-with-transforms)
- [Best Practices](https://www.stationx.net/how-to-use-maltego/#best-practices)
- [Conclusion](https://www.stationx.net/how-to-use-maltego/#conclusion)
- [Frequently Asked Questions](https://www.stationx.net/how-to-use-maltego/#frequently-asked-questions)

Level Up in Cyber Security:Join Our Membership Today!

[Learn More](https://www.stationx.net/vip-membership?cta_src=blog&cta_p=sticky-sidebar)

[![StationX blue logo](https://www.stationx.net/wp-content/uploads/2022/02/StationX-blue-logo.svg)](https://www.stationx.net/)

# How to Use Maltego: A Beginner’s Guide to OSINT Analysis

May 11, 2024 / By  [Richard Dezso](https://www.stationx.net/author/richard-dezso/ "Richard Dezso")

![How to Use Maltego Featured Image](https://www.stationx.net/wp-content/uploads/2023/08/How-to-Use-Maltego-Featured-Image.png)



[](https://www.linkedin.com/shareArticle?title=How%20to%20Use%20Maltego%3A%20A%20Beginner%E2%80%99s%20Guide%20to%20OSINT%20Analysis&url=https%3A%2F%2Fwww.stationx.net%2Fhow-to-use-maltego%2F&mini=true)[](https://x.com/intent/post?text=How%20to%20Use%20Maltego%3A%20A%20Beginner%E2%80%99s%20Guide%20to%20OSINT%20Analysis&url=https%3A%2F%2Fwww.stationx.net%2Fhow-to-use-maltego%2F)[](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.stationx.net%2Fhow-to-use-maltego%2F)

You can use Maltego to gather, analyze, and visualize publicly available information, uncovering relationships and patterns between entities like domains, IP addresses, social media profiles, and more.

In this article, we'll show you how to use Maltego, a vital tool for cyber security professionals, particularly penetration testers. We'll begin by explaining what Maltego is and guiding you through the process of starting it up. Next, we'll explore the main interface, breaking down key sections to make them easy to understand.

After that, we'll provide an overview of utilizing Maltego's Transforms, a central feature that enables you to uncover hidden relationships within data sets. Finally, we'll discuss the best practices when using Maltego, ensuring you can utilize this powerful tool effectively and responsibly.

If you’re ready to dive into the world of Maltego, let’s begin.

## What Is Maltego?

[Maltego is a tool](https://www.maltego.com/) that leverages open-source intelligence (OSINT) developed by Paterva. Maltego comes in different versions, including a community edition that can be used for free with some limitations, as well as commercial versions that offer more features and capabilities.

Maltego is a vital tool in the arsenal of a penetration tester. As a graphical link analysis tool, it lets you visualize connections within complex data sets, displaying interconnected links. By analyzing information from various sources such as public websites, email addresses, social media, and cryptocurrency transactions, Maltego aids in uncovering hidden relationships and patterns.

This is particularly useful in penetration testing, where understanding the target's digital footprint and connections can be crucial. Working up to 80% faster with Maltego than traditional methods allows for efficient reconnaissance.

## Starting Up

We will now show you how to get Maltego up and running. For our demo moving forward, we will be using Kali. Maltego can also be installed on Windows, macOS, and other Linux distributions.

Before you can run Maltego, you need to run the installer, which can be found in the Applications menu under “Information Gathering.”

[![Maltego in Kali](https://www.stationx.net/wp-content/uploads/2023/09/image-53.png)](https://www.stationx.net/wp-content/uploads/2023/08/Maltego-in-Kali.png)

You will be taken to a terminal window if you want to install Maltego. Select “Y” to continue.

[![Maltego Installation](https://www.stationx.net/wp-content/uploads/2023/09/image-27.png)](https://www.stationx.net/wp-content/uploads/2023/08/Maltego-Installation.png)

You can also install Maltego from the terminal with the following command:

`sudo apt install -y maltego`

[![Install Maltego from Terminal](https://www.stationx.net/wp-content/uploads/2023/09/image-39.png)](https://www.stationx.net/wp-content/uploads/2023/08/Install-Maltego-from-Terminal.png)

Now, you can start Maltego by entering `maltego` in the terminal or running it from the application menu.

Once Maltego opens, you will be shown a window asking you to select a product. We are using the “Maltego CE (Free)” version for our demo. Select “Run” to continue.

[![Maltego Product Selection](https://www.stationx.net/wp-content/uploads/2023/09/image-40.png)](https://www.stationx.net/wp-content/uploads/2023/08/Maltego-Product-Selection.png)

Next, you’ll need to configure Maltego. The first step is to accept the license agreement and click “Next.”

The next step is to log in so you can use Maltego. If you do not already have an account, [register one here](https://www.maltego.com/ce-registration/?utm_source=maltego-suite&utm_medium=software).

[![Configure Maltego](https://www.stationx.net/wp-content/uploads/2023/09/image-52.png)](https://www.stationx.net/wp-content/uploads/2023/08/Configure-Maltego.png)

After logging in, you'll be able to see your details, like your name and email address, as well as the duration of your API key. Click “Next” to continue with the download of the Transforms.

[![Maltego Login Result](https://www.stationx.net/wp-content/uploads/2023/09/image-30.png)](https://www.stationx.net/wp-content/uploads/2023/08/Maltego-Login-Result.png)

The Transforms will be downloaded, and you must click “Next” to install them in Maltego.

[![Maltego Install Transforms](https://www.stationx.net/wp-content/uploads/2023/09/image-43.png)](https://www.stationx.net/wp-content/uploads/2023/08/Maltego-Install-Transforms.png)

The next screen will ask if you want to send error reports to Paterva, and then click “Next” to continue.

The final window will ask what external browser you want to open links to. Make your choice and then click “Finish” to complete the configuration. Maltego will now be ready to be used.

## Interface

This section will show you the main Maltego graphical user interface, and we will highlight three areas within the interface.

[![Maltego Main Interface](https://www.stationx.net/wp-content/uploads/2023/09/image-31.png)](https://www.stationx.net/wp-content/uploads/2023/08/Maltego-Main-Interface.png)

1. **Application Menu**

In the Application menu, you'll find the application button. This grants access to the following functions:

- New Graph
- Open Graph
- Save
- Save All
- Save As

Maltego can open and save graphs using the .mtgl extension. While these are some of the core features, there are also other advanced functions.

1. **Start Page**

The start page showcases the latest updates for products, Transform, and the Transform Hub. Any alerts affecting Maltego's functionality and security can also be found here.

1. **Transform Hub**

The Transform Hub catalogs all the Transforms offered by Maltego, third-party providers, or available through an API/dataset. You can either purchase these items or install them for free.

Transforms in Maltego are specialized pieces of code that process information in a very particular way. They take an Entity (a defined piece of data like an email address, IP address, or name) as input and then search for related information, returning more Entities as output.

Let's walk through installing Transforms in Maltego's Community Edition. First, navigate to the Transform Hub within the software.

Since we're using the Community Edition, you'll want to filter the available Transforms by selecting “Maltego Community” from the “Plans” menu. This will show you only the Transforms compatible with our version, making choosing and installing the ones you need easier.

You’ll also want to display Transforms that are “NOT INSTALLED.”

[![Maltego Transform Hub](https://www.stationx.net/wp-content/uploads/2023/09/image-34.png)](https://www.stationx.net/wp-content/uploads/2023/08/Maltego-Transform-Hub.png)

Now that we have the Transforms that will work for us let’s choose one to install. At the time of writing, there are 50 Transforms available to you in the Community Edition—everything from infrastructure and network information to searching social media sites.

Let’s install the Censys Transform, designed to map IP addresses to the target domain and vice versa, quickly identify server misconfigurations, and efficiently scan attack surfaces for vulnerabilities

[![Maltego Censys Transform](https://www.stationx.net/wp-content/uploads/2023/09/image-32.png)](https://www.stationx.net/wp-content/uploads/2023/08/Maltego-Censys-Transform.png)

This Transform is limited to twenty-five Transform runs per month on the Community Edition of Maltego.

Several Transforms will require you to have an API key from the provider, and Censys is one of them.

To work with the Censys Transform, you will need an account and an API key. You can sign up for an account at the [Censys registration page](https://accounts.censys.io/register).

[![Maltego Censys Information](https://www.stationx.net/wp-content/uploads/2023/09/image-38.png)](https://www.stationx.net/wp-content/uploads/2023/08/Maltego-Censys-Information.png)

To install, hover over the Censys Transform and click  “INSTALL.” It will ask you if you are sure you want to install it. Click “Yes” to continue.

[![Maltego Censys Install](https://www.stationx.net/wp-content/uploads/2023/09/image-35.png)](https://www.stationx.net/wp-content/uploads/2023/08/Maltego-Censys-Install.png)

Complete the three steps that follow to finish installing Censys inside Maltego.

Select “INSTALLED” from the Transform Hub to see the Censys Transform listed.

[![See Installed Transforms Maltego](https://www.stationx.net/wp-content/uploads/2023/09/image-47.png)](https://www.stationx.net/wp-content/uploads/2023/08/See-Installed-Transforms-Maltego.png)

## Starting an Investigation

The easiest way to start a new investigation is by using Machines in Maltego. These Machines are automated sequences of Transforms in Maltego that allow users to run multiple queries or operations with a single click.

We will demonstrate how to use a Machine in Maltego, specifically focusing on the “Company Stalker” Machine. This Machine aims to locate email addresses associated with a domain, map these to corresponding social media profiles, and finally, attempt to retrieve or analyze any related metadata.

To begin, click on the “Machines” tab at the top of the Maltego window.

[![Maltego Machines](https://www.stationx.net/wp-content/uploads/2023/09/image-29.png)](https://www.stationx.net/wp-content/uploads/2023/08/Maltego-Machines.png)

Next, select “Run Machine” to select the Machine you want to run.

[![Maltego Run Machines](https://www.stationx.net/wp-content/uploads/2023/09/image-28.png)](https://www.stationx.net/wp-content/uploads/2023/08/Maltego-Run-Machines.png)

Choose “Company Stalker” and click “Next.”

[![Maltego Start a Machines](https://www.stationx.net/wp-content/uploads/2023/09/image-33.png)](https://www.stationx.net/wp-content/uploads/2023/08/Maltego-Start-a-Machines.png)

Now enter a domain you want to use as the target. In our demo, we are using example.net and click “Finish.”

[![Maltego Enter Domain Name](https://www.stationx.net/wp-content/uploads/2023/09/image-48.png)](https://www.stationx.net/wp-content/uploads/2023/08/Maltego-Enter-Domain-Name.png)

Click through any popups you receive and wait for the machine to finish running. Once finished, you will be presented with any information that was returned.

[![Maltego Machine Results](https://www.stationx.net/wp-content/uploads/2023/09/image-41.png)](https://www.stationx.net/wp-content/uploads/2023/08/Maltego-Machine-Results.png)

For a more detailed investigation, you can also run one manually. If you want to start a new project in Maltego, the first step is to select “New”  in the Application menu.  

[![Maltego New Graph](https://www.stationx.net/wp-content/uploads/2023/09/image-37.png)](https://www.stationx.net/wp-content/uploads/2023/08/Maltego-New-Graph.png)

You will then be presented with different screens, such as the “Entity Palette,” “Graph,”  “Output,” and “Run View.”

[![Maltego Graph](https://www.stationx.net/wp-content/uploads/2023/09/image-46.png)](https://www.stationx.net/wp-content/uploads/2023/08/Maltego-Graph.png)

To begin your investigation, you will now want to add an “Entity” to the new graph. The easiest way to do this is using the “Entity Pallete” on the main interface's left side. You can either scroll through the list of entities or use the search function.

In Maltego, an Entity represents a single piece of data you want to investigate or analyze. It can be something as simple as an email address, a phone number, a domain name, or an IP address.

[![Maltego Entity Palette](https://www.stationx.net/wp-content/uploads/2023/09/image-51.png)](https://www.stationx.net/wp-content/uploads/2023/08/Maltego-Entity-Palette.png)

Let's add an Entity to the graph. In the “Personal” section, you can select the “Email Address” Entity or simply use the search bar to find “Email.” Once you locate the Entity, drag it onto the graph to add it.

[![Maltego Add Email Address](https://www.stationx.net/wp-content/uploads/2023/09/image-49.png)](https://www.stationx.net/wp-content/uploads/2023/08/Maltego-Add-Email-Address.png)

## Working With Transforms

Now, we will show you how to work with different Transforms. For this demo, we will be using a domain name to perform various analyzes.

Search for “Domain” in the Entity Palette and drag it to the Graph. We will use nmap.scanme.org for the demo, so change the domain name from maltego.com to nmap.scanme.org.

[![Maltego Add Domain](https://www.stationx.net/wp-content/uploads/2023/09/image-42.png)](https://www.stationx.net/wp-content/uploads/2023/08/Maltego-Add-Domain.png)

Let’s run our first Transform. Let’s run Censys to map an IP to the domain name. Right-click on the domain in the graph and select Censys. Then click the “Run All” button to run all the Censys Transforms simultaneously.

As a penetration tester, this information gathering technique during the information gathering phase can give insight into the organization's network structure and may reveal the relationships between different servers, such as mail servers and websites.

Read the steps involved in a penetration test in our article: [Penetration Testing Steps: A Comprehensive Assessment Guide](https://www.stationx.net/penetration-testing-steps/).

[![Maltego Run Censys Transform](https://www.stationx.net/wp-content/uploads/2023/09/image-44.png)](https://www.stationx.net/wp-content/uploads/2023/08/Maltego-Run-Censys-Transform.png)

The Transform will run and present you with the IP information in the graph.

[![Maltego After Transform](https://www.stationx.net/wp-content/uploads/2023/09/image-45.png)](https://www.stationx.net/wp-content/uploads/2023/08/Maltego-After-Transform.png)

Now let’s run another Transform. This time let’s run the “To Snapshots between Dates [Wayback Machine].” This can be extremely helpful when performing a penetration test as it could reveal important information such as past vulnerabilities, changes in security configurations, deprecated or hidden pages, and subdomains.

Right-click on the domain, and in the search bar, search for “wayback” then select “To Snapshots between Dates [Wayback Machine],” and finally click run.

[![Maltego Run To Snapshots](https://www.stationx.net/wp-content/uploads/2023/09/image-50.png)](https://www.stationx.net/wp-content/uploads/2023/08/Maltego-Run-To-Snapshots.png)

On the next screen, choose the begin and end dates for the search and click Run!

[![Maltego Enter Dates for To Snapshots](https://www.stationx.net/wp-content/uploads/2023/09/image-49.png)](https://www.stationx.net/wp-content/uploads/2023/08/Maltego-Enter-Dates-for-To-Snapshots.png)

Once the Transform completes, you will be shown the Wayback Machine data found. With this information, you could click on a specific date and open the URL for further information gathering and investigations.

[![Maltego To Snaphots Results](https://www.stationx.net/wp-content/uploads/2023/09/image-36.png)](https://www.stationx.net/wp-content/uploads/2023/08/Maltego-To-Snaphots-Results.png)

Maltego is an extremely powerful tool and can do so much more than what we’ve shown you here. Using Maltego, you could map out the digital footprint of a target organization, including identifying key employees, emails, social media profiles, or devices.

This information can be used with tools like the [Social Engineer Toolkit](https://www.stationx.net/social-engineer-toolkit/) for information gathering. It can be used to create:

**Phishing Campaigns:** Information gathered about email addresses and social connections could aid in crafting [targeted phishing emails](https://www.stationx.net/phishing-statistics/).

**Spear Phishing and Social Engineering Attacks:** Insights into the relationships between entities might inform more advanced spear-phishing or [social engineering attacks](https://www.stationx.net/social-engineering-example-2/).

## Best Practices

Let's talk about some Maltego usage best practices. Maltego is a very versatile tool that can do many things, and there are some things you can do to work more effectively and intelligently before and while using it. Our list of recommendations for working with Maltego is provided below.

- **Create a Strong Workflow:** Understand your goal before you start. Map out what you want to uncover and tailor your search accordingly.
- **Use Transforms Wisely:** Transforms are queries that fetch you different data types. Learn them well, and use only what's necessary. Too many unnecessary Transforms may clutter your results.
- **Secure Your Data:** Maltego can pull sensitive information. Make sure you handle it with care.
- **Stay Up to Date:** The digital world and tools like Maltego change rapidly. Regularly update to the latest version to keep up with new features and security enhancements.
- **Use Entities Properly:** Entities are the building blocks in Maltego. Use them correctly to represent the data you're working with.
- **Use Notes and Bookmarks:** You can attach notes to entities, connections and bookmark essential elements. This helps track why something is important or how you discovered it.
- **Export and Share with Care:** You can export your findings to share with others. But remember, this might include sensitive data, so only share it with those who need it.

## Conclusion

As you can see, Maltego is a powerful tool used in penetration testing and other investigations. It provides a graphical representation of your data and enables clear visualization of complex relationships and connections, and aids in the thinking process.

In this article, we began by explaining Maltego and guiding you through its installation process. Next, we demonstrated how to get Maltego up and running, and we introduced you to the main interface. Following that, we dove into initiating an investigation and working with Transforms. Finally, we outlined some best practices to follow when using Maltego.

We've just scratched the surface of what Maltego can do, but you should now understand how to use this tool effectively.

[![](https://www.stationx.net/wp-content/uploads/2023/08/Learn-Social-Engineering-From-Scratch.jpg)](https://courses.stationx.net/p/learn-social-engineering-from-scratch)

#### [Learn Social Engineering From Scratch](https://courses.stationx.net/p/learn-social-engineering-from-scratch)

4.8

★★★★★

![](https://www.stationx.net/wp-content/uploads/2022/12/logo-1.svg)

[![](https://www.stationx.net/wp-content/uploads/2022/12/Learn-Ethical-Hacking-From-Scratch-1.png)](https://courses.stationx.net/p/learn-ethical-hacking-from-scratch)

#### [Learn Ethical Hacking From Scratch](https://courses.stationx.net/p/learn-ethical-hacking-from-scratch)

4.9

★★★★★

![](https://www.stationx.net/wp-content/uploads/2022/12/logo-1.svg)

[![](https://www.stationx.net/wp-content/uploads/2023/08/The-Complete-Penetration-Testing-Bootcamp.jpg)](https://courses.stationx.net/p/the-complete-penetration-testing-bootcamp)

#### [](https://www.stationx.net/)[The Complete Penetration Testing Bootcamp](https://courses.stationx.net/p/the-complete-penetration-testing-bootcamp)

4.8

★★★★★

![](https://www.stationx.net/wp-content/uploads/2022/12/logo-1.svg)

## Frequently Asked Questions

**Is Maltego free?**

Maltego can be used for free with its Community Edition and includes some of the same functions as the Pro and Enterprise versions but has limitations such as only having up to 12 results per Transform and 10,000 Entities per graph and not having access to the commercial Transform Hub.

**Is it legal to use Maltego?**

**Why do hackers use Maltego?**

20

SHARES

[LinkedIn](https://www.linkedin.com/shareArticle?title=How%20to%20Use%20Maltego%3A%20A%20Beginner%E2%80%99s%20Guide%20to%20OSINT%20Analysis&url=https%3A%2F%2Fwww.stationx.net%2Fhow-to-use-maltego%2F&mini=true)[X](https://x.com/intent/post?text=How%20to%20Use%20Maltego%3A%20A%20Beginner%E2%80%99s%20Guide%20to%20OSINT%20Analysis&url=https%3A%2F%2Fwww.stationx.net%2Fhow-to-use-maltego%2F)[Facebook](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.stationx.net%2Fhow-to-use-maltego%2F)

#### Level Up in Cyber Security: Join **Our Membership** Today!

![vip cta image](https://www.stationx.net/wp-content/uploads/2022/10/vip_cta_image.png)

![vip cta details](https://www.stationx.net/wp-content/uploads/2022/10/vip_cta_details.png)

[MEMBERSHIP](https://www.stationx.net/join?cta_src=blog&cta_p=bottom-cta)

- ![Richard Dezso](https://www.stationx.net/wp-content/uploads/2023/05/Richard-Dezso.jpg)
    
    [Richard Dezso](https://www.stationx.net/author/richard-dezso/ "Richard Dezso")
    
    Richard is a cyber security enthusiast, eJPT, and ICCA who loves discovering new topics and never stops learning. In his home lab, he's always working on sharpening his offensive cyber security skills. He shares helpful advice through easy-to-understand blog posts that offer practical support for everyone. Additionally, Richard is dedicated to raising awareness for mental health. You can find Richard on [**LinkedIn**](https://www.linkedin.com/in/richarddezso/), or to see his other projects, visit his [**Linktree**](https://linktr.ee/richdezso).
    

## Related Articles

[![DVWA](https://www.stationx.net/wp-content/uploads/2024/06/DVWA.png)](https://www.stationx.net/dvwa-damn-vulnerable-web-application/)

### [The Best DVWA (Damn Vulnerable Web Application) 2024 Guide](https://www.stationx.net/dvwa-damn-vulnerable-web-application/)

[Read More »](https://www.stationx.net/dvwa-damn-vulnerable-web-application/)

[![nmap scripting engine featured image](https://www.stationx.net/wp-content/uploads/2023/06/nmap-scripting-engine-featured-image.png)](https://www.stationx.net/nmap-scripting-engine/)

### [How to Master the Power of the Nmap Scripting Engine](https://www.stationx.net/nmap-scripting-engine/)

[Read More »](https://www.stationx.net/nmap-scripting-engine/)

[![Complete OSEP Certification Guide](https://www.stationx.net/wp-content/uploads/2024/06/Complete-OSEP-Certification-Guide.png)](https://www.stationx.net/osep-certification/)

### [Complete OSEP Certification Guide (2024 Edition)](https://www.stationx.net/osep-certification/)

[Read More »](https://www.stationx.net/osep-certification/)

## Info

- [Affiliates](https://courses.stationx.net/p/affiliates)
- [Legal Notices](https://www.stationx.net/legal-notices/)
- [Privacy Policy](https://www.stationx.net/privacy-policy/)
- [Site Map](https://www.stationx.net/sitemap_index.xml)
- [Careers](https://www.stationx.net/careers/)
- [Contact](https://www.stationx.net/contact/)
- [Media](https://www.stationx.net/media-engagements/)

## Security Assessment

- [Penetration Testing](https://www.stationx.net/penetration-testing/)
- [Vulnerability Scanning](https://www.stationx.net/vulnerability-scanning/)
- [Build Reviews](https://www.stationx.net/build-review/)
- [Source Code Review](https://www.stationx.net/source-code-review/)
- [Social Engineering](https://www.stationx.net/social-engineering/)

## CONSULTING

- [Audit & Compliance](https://www.stationx.net/audit-compliance/)
- [Incident Response](https://www.stationx.net/incident-response/)
- [Security Architecture](https://www.stationx.net/security-architecture/)
- [Risk Assessment](https://www.stationx.net/risk-assessment/)
- [Security Training](https://www.stationx.net/security-training/)
- [Pro Bono Services](https://www.stationx.net/pro-bono-cybersecurity-services/)

![StationX footer logo](https://www.stationx.net/wp-content/uploads/2022/02/StationX-white-logo.svg)

Copyright © 2024 STATIONX LTD. ALL RIGHTS RESERVED.

[](https://www.linkedin.com/in/housenathan/)[](https://twitter.com/GotoNathan)

[](https://www.linkedin.com/company/stationx)[](https://www.youtube.com/c/+StationxNet)[](https://twitter.com/gotostationx/)[](https://www.instagram.com/goto.stationx/)[](https://www.tiktok.com/@gotostationx)[](https://www.facebook.com/pages/Station-X/1631192847101094)