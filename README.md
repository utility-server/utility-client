Utility Client:

Utility Client is a versatile utility designed to assist you in managing your Utility Server’s configuration efficiently. It offers features such as downloading logs, monitoring stats, and fetching live logs seamlessly.

Introduction to Using Utility Client:

Configuring and utilizing Utility Client empowers you to streamline your Utility Cleint setup and access various functionalities effortlessly. Whether you're downloading logs, monitoring stats, or managing configurations, the Utility Client serves as your go-to tool for simplifying these tasks.

Setting Up Utility Client on Linux:

Follow these steps to download and configure Utility Client on Ubuntu System:
1.	Download Utility Client for Ubuntu using the command: 
$ wget https://github.com/utility-server/utility-client/raw/main/UtilityClient-Debin-amc64-3.02.deb

2.	Installing Utility Client:
$ sudo dpkg -i UtilityClient-Debin-amc64-3.02.deb

Configuring Utility Client:

To set up and configure Utility Client, use the -setConfig command. Here's how you can execute it:

Command:  -setConfig
Syntax: 
$ utility-client  -setConfig
Prompts: Upon running the command, you'll be prompted to provide the following information:
•	Registered Domain <www.yourbusiness.com>
•	ClientID <Your Client ID>
•	End Point (As shared)
•	Access Key <Acess Key as shared>
•	Client Secret <Client Secret as shared>
•	SitemapURL <https://www.mydomain.com/sitemap.xml>
•	ConcurrentThread <Number of Concurent Threads

Once all information is provided, the client will securely store it for future use.



Setting Up Utility Client  with Multiple Configurations:

Utility Client  is equipped with the capability to be configured for multiple clients, modules, or services, each with its own set of configurations. This flexibility allows you to seamlessly switch between configurations based on your requirements.

Configuring Multiple Clients:

To configure TTSCC for multiple clients, follow the steps outlined in "Configuring Utility Client ." Each configuration will generate a separate configuration file named common-client-[CLIENT ID].conf for each client. The last configured client will be preloaded and activated to process commands by default.

Reviewing Loaded Configuration:

It's essential to review the loaded configuration at times to ensure everything is set up correctly. To do so, use the following command:

Command: -printConfiguration
Syntax: 
$ utility-client -printConfiguration

This command is designed to print the activated client configuration saved locally on the client end, providing you with an overview of the current setup.

Listing and Loading Clients:

If you have configured multiple clients, modules, or services, you can list down all configurations and reload them as needed using the following commands:

Command: -loadClient=<"CLIENT ID"/LIST>

Syntax:

To list down all configurations:
$ utility-client -loadClient=<LIST>

To load the desired configuration:
$ utility-client -loadClient=<"CLIENT ID">

Ensure that the CLIENT ID is wrapped with double quotes to load the desired configuration correctly.

These commands enable you to manage and switch between multiple configurations effortlessly, ensuring smooth operation of TTSCC across various client setups.


Reloading Server Cache Configuration:

The server maintains cache of two major variables configurable from the TTSCC (Text-to-Speech Common Client): TTL (Time to Live) and Whitelisted IP Addresses. It is advisable to reload the server cache whenever changes are made to the TTL or whitelisted IP addresses.
Command: -reloadMyConf 
Syntax: 
$ utility-client -reloadMyConf

Executing this command triggers the server to reload the configuration settings specified in the TTSCC, ensuring that any updates to TTL or whitelisted IP addresses take effect promptly.


Purging Full Cache of Rendered Pages:

Utility Server maintains a cache of all rendered pages for a defined Time To Live (TTL), optimizing the use of render credits and ensuring swift delivery of repeated requests from Bots and Crawlers.

Purging the entire cache is not recommended for production deployments.

Command: -purgeAllCache 
Syntax: 
$ utility-client -purgeAllCache

Performing a full cache purge removes all cached pages, effectively clearing the cache. This action should be exercised with caution, particularly in production environments.
It is recommended to perform cache warmup after purging the full cache to ensure smooth operation and efficient caching for subsequent requests.


Purging URL-Specific Cache of Rendered Pages:

Utility Server maintains a cache of all rendered pages for a defined Time To Live (TTL), optimizing the use of render credits and ensuring swift delivery of repeated requests from Bots and Crawlers.

You can purge selective URL cache if there is a change that can't wait for the TTL to expire.

You have the option to remove cache for a single URL or to purge cache for multiple URLs by providing a text file containing a list of URLs (one URL per line).
Command: -purgeURLCache <URI> OR <./path/to/URLlist FILE> 
Syntax: 
To hit cache purge for a URL:
$ utility-client -purgeURLCache <URI>

To hit cache purge for a List of URLs:
$ utility-client -purgeURLCache <./path/to/URLlist FILE>

The <URI> represents a part of the URL after the domain name. Please do not provide the full URL. The URI always starts with a forward slash ("/").
For example:
•	URL: http://www.mybusiness.com/some/path
•	URI: /some/path
By utilizing this command, you can effectively purge specific URL caches, ensuring that updated content is promptly served to users and search engine crawlers.


Updating Time To Live (TTL) for Caching:

TTL (Time To Live) represents the duration for which the system maintains cached pages without fetching them from the origin server to render them again.

It is recommended to set a maximum TTL to safeguard your render credits and ensure fast responses to requests from Bots and Crawlers.

Command: -updateTTL=<TTL> 
Syntax: 
$ utility-client -updateTTL=<TTL>

The <TTL> parameter should be an integer number between 1 to 100, representing the duration in days for which the cached pages will be maintained.
By utilizing this command, you can adjust the TTL according to your requirements, balancing between efficient use of render credits and ensuring timely delivery of content to users and search engine crawlers.


Cache Warmup:

Cache warmup is an essential process that ensures the smooth handling of the very first request coming from Bots or Crawlers.

Command: -warmupCache [./path/to/URLlist FILE (optional)]

To warm up the cache, TTSCC utilizes two methods:

1. Cache Warmup from Sitemap.xml: This command reads the sitemap from the website URL provided during the configuration of TTSCC (e.g., https://www.mybusiness.com/sitemap.xml). 
Syntax: 
$ utility-client -warmupCache

2. Cache Warmup from a URL List: This command reads URLs from a file containing a list of URLs, with each line representing one URL. 
Syntax: 
$ utility-client -warmupCache ./path/to/URLlist-FILE

The -warmupCache command is a multi-threaded process capable of hitting multiple URLs simultaneously to accelerate the warmup process. However, this may require a good internet connection and a computer with moderate to high configuration.
To ensure that cache warmup is able to reach your server, please ensure proper whitelisting at your firewall end for either the IP of the system on which TTSCC is running or the HTTP Header “User-Agent: TTS-Common-Client/* for www.yourbusiness.com”


Whitelisting IPs:

Utility Server is configured to listen only from restricted resources to ensure security and maintain performance by serving authentic requests.

The initial IP whitelisting is performed during onboarding. For subsequent whitelisting, you can utilize TTSCC by using the following command:

Command: -whitelistIPs <Space separated IPV4 and IPV6> 
Syntax: 
$ utility-client -whitelistIPs <Space separated IPV4 and IPV6>

It is recommended to whitelist the static IP addresses of the computer or machine on which TTSCC is running. This ensures uninterrupted access to the Utility Server Server. IP whitelisting should be performed for both IPV4 and IPV6 addresses, including the IPs of the computer running TTSCC and your proxy or web server responsible for routing the traffic.

Note: IPs should be separated by a white space.


Viewing Stats:

To stay informed about crucial metrics such as your credit quota allocation, number of renders, requests served from cache, total hits, and credit consumed, you can easily fetch these details using the following command:

Command: -getStats=<month> 
Syntax: 
$ utility-client -getStats=<month>

Here, <month> refers to the specific month for which you want to retrieve the stats, formatted as YYYY-MM. Simply replace <month> with the desired month in this format when executing the command.


Downloading Logs or Log Report:

Logs or Log Reports offer a detailed breakdown of each incoming hit, providing essential information for analyzing request patterns and understanding system performance.

Command: -downloadLogReport <date> 
Syntax: 
$ utility-client -downloadLogReport <date>

In this command, <date> signifies the specific date for which you intend to retrieve the logs. Ensure to input the date in the format YYYY-MM-DD. By executing this command, you'll obtain a comprehensive log report for the specified date, facilitating thorough examination and analysis of system activities.

Fetching Live Logs:

The Utility Client  includes an exclusive feature designed to monitor live logs, providing real-time insights into incoming hits, system behaviour, and performance metrics.

Command: -fetchLiveLogs 
Syntax: 
$ utility-client -fetchLiveLogs

By executing this command, you can access live logs directly through the Utility Client interface. This feature enables you to stay updated on the latest activities, allowing for immediate observation and analysis of system performance and behaviour.

