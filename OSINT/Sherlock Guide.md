Hello aspiring ethical hackers. In our previous blogpost, you learnt what is [OSINT](https://www.hackercoolmagazine.com/beginners-guide-to-osint/) and its importance in ethical [hacking](https://www.hackercoolmagazine.com/beginners-guide-to-hacking/), different types of OSINT etc. In this blogpost, you will learn about Sherlock, a OSINT tool.

Sherlock’s role in OSINT comes while gathering information from social media. It works by hunting for a particular username across various social networks. It does this by relying on social media site’s design feature to provide a URL with the username when a user registers an account on the social network.

Sherlock queries that URL and determines if the user has an account on that particular social network. It works by querying that URL and then uses that response to determine if there is a username. Sherlock can search for users on over 300 social networks that include Apple Developer, Arduino, Docker Hub, GitHub, GitLab, Facebook, Bitcoin Forum, CNET, Instagram, PlayStore, PyPi, Scribd, Telegram, TikTok, Tinder etc.

Let’s see how this tool works. For this I will be using Kali Linux which has Sherlock in its repository. You can install sherlock on Kali as shown below.

[![Sherlock 1](https://www.hackercoolmagazine.com/wp-content/uploads/2024/12/Sherlock_1.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/12/Sherlock_1.jpg)

The simplest way to query a username with sherlock is by just supplying a username.

[![Sherlock 2](https://www.hackercoolmagazine.com/wp-content/uploads/2024/12/Sherlock_2.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/12/Sherlock_2.jpg)

[![Sherlock 3](https://www.hackercoolmagazine.com/wp-content/uploads/2024/12/Sherlock_3.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/12/Sherlock_3.jpg)

[![Sherlock 4](https://www.hackercoolmagazine.com/wp-content/uploads/2024/12/Sherlock_4.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/12/Sherlock_4.jpg)

**Searching on a particular social media site**

Instead of searching for a username on all the social media accounts, you can search for a username’s presence even on a single site as shown below. For example let’s search for a username on site Twitch.

[![Sherlock 5](https://www.hackercoolmagazine.com/wp-content/uploads/2024/12/Sherlock_5.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/12/Sherlock_5.jpg)

**Searching for similar usernames**

Sometimes, a username can be slightly different to a person we are searching for. We can also search for similar usernames with this tool as shown below.

[![Sherlock 11](https://www.hackercoolmagazine.com/wp-content/uploads/2024/12/Sherlock_11.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/12/Sherlock_11.jpg)

Here, {?} will be replaced with – or hyphen or period (.).

**Searching for multiple usernames at once**

You can even search for multiple usernames with this tool as shown below. For example, let’s search for “hackercoolmagazine” and “hackercool” on Instagram.

[![Sherlock 6](https://www.hackercoolmagazine.com/wp-content/uploads/2024/12/Sherlock_6.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/12/Sherlock_6.jpg)

**Using a proxy while searching**

You can even route your query through a proxy to remain anonymous.

[![Sherlock 7](https://www.hackercoolmagazine.com/wp-content/uploads/2024/12/Sherlock_7.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/12/Sherlock_7.jpg)

**Dump the entire HTTP response**

We can even see the HTTP response of the site while searching using this option.

[![Sherlock 8](https://www.hackercoolmagazine.com/wp-content/uploads/2024/12/Sherlock_8.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/12/Sherlock_8.jpg)

[![Sherlock 9](https://www.hackercoolmagazine.com/wp-content/uploads/2024/12/Sherlock_9.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/12/Sherlock_9.jpg)

**Time to call**

By default, while querying for usernames, this tool waits for 60 seconds for response to the request it made. With this timeout option, this time can be changed as shown below. The value should be set in seconds.

[![Sherlock 12](https://www.hackercoolmagazine.com/wp-content/uploads/2024/12/Sherlock_12.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/12/Sherlock_12.jpg)

**Print all the output**

By default, Sherlock only prints out the social network where the username was found. Using the option, we can see all the social networks this tool queries for and also the reason why it was not found.

[![Sherlock 13](https://www.hackercoolmagazine.com/wp-content/uploads/2024/12/Sherlock_13.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/12/Sherlock_13.jpg)

[![Sherlock 14](https://www.hackercoolmagazine.com/wp-content/uploads/2024/12/Sherlock_14.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/12/Sherlock_14.jpg)

**Print only positives found**

This option prints out all the social networks on which the username is found.

[![Sherlock 15](https://www.hackercoolmagazine.com/wp-content/uploads/2024/11/Sherlock_15.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/11/Sherlock_15.jpg)

**Browse**

By setting this option, we can use Sherlock to view the job result page on browser.

[![Sherlock 16](https://www.hackercoolmagazine.com/wp-content/uploads/2024/12/Sherlock_16.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/12/Sherlock_16.jpg)

[![Sherlock 17](https://www.hackercoolmagazine.com/wp-content/uploads/2024/12/Sherlock_17.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/12/Sherlock_17.jpg)

**Search NSFW sites too**

By default, sherlock doesn’t query NSFW sites while searching for a username. When we set this option, it even queries NSFW sites for the particular username.

[![Sherlock 18](https://www.hackercoolmagazine.com/wp-content/uploads/2024/12/Sherlock_18.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/12/Sherlock_18.jpg)

**Writing the output to a file**

Like any other tool, we can use Sherlock too to save the output to a file of our choice using the “-o” option as shown below.

[![Sherlock 20](https://www.hackercoolmagazine.com/wp-content/uploads/2024/12/Sherlock_20.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/12/Sherlock_20.jpg)

[![Sherlock 21](https://www.hackercoolmagazine.com/wp-content/uploads/2024/12/Sherlock_21.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2024/12/Sherlock_21.jpg)

Follow Us