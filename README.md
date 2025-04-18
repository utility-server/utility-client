## Utility Client

**Utility Client** is a versatile tool designed to streamline the management of your Utility Server's configuration. It empowers you to download logs, monitor stats, and fetch live logs effortlessly.

## Introduction

This guide provides a comprehensive overview of using Utility Client. It covers configuration, managing multiple clients, cache management, whitelisting IPs, viewing stats, downloading logs, and fetching live logs.

## Setting Up Utility Client on Linux

**Here's how to download and configure Utility Client on Ubuntu:**

1. **Download Utility Client:**

   ```bash
   $ wget https://github.com/utility-server/utility-client/raw/main/UtilityClient-Debin-amd64-3.02.deb
   ```

2. **Install Utility Client:**

   ```bash
   $ sudo dpkg -i UtilityClient-Debin-amd64-3.02.deb
   ```

## Configuring Utility Client

**Use the `-setConfig` command to configure Utility Client. Here's how to execute it:**

```bash
$ utility-client -setConfig
```

**Prompts:**

Upon running the command, you'll be prompted to provide the following information:

* Registered Domain (e.g., [www.yourbusiness.com](https://www.yourbusiness.com))
* ClientID (Your Client ID)
* End Point (As shared)
* Access Key (Access Key as shared)
* Client Secret (Client Secret as shared)
* SitemapURL (e.g., [https://www.mydomain.com/sitemap.xml](https://www.mydomain.com/sitemap.xml))
* ConcurrentThread (Number of Concurrent Threads)

The client will securely store this information for future use.

## Setting Up with Multiple Configurations

Utility Client can be configured for multiple clients, modules, or services, each with its own set of configurations.

**Configuring Multiple Clients:**

Follow the steps mentioned in "Configuring Utility Client" for each client. Each configuration will generate a separate file named `common-client-[CLIENT ID].conf`. The last configured client will be preloaded and activated by default.

**Reviewing Loaded Configuration:**

Use the following command to review the loaded configuration:

```bash
$ utility-client -printConfig
```

This command displays the activated client configuration stored locally.

**Listing and Loading Clients:**

If you have multiple configurations, use these commands to list and load them:

```bash
# List all configurations
$ utility-client -loadClient=<LIST>

# Load a specific configuration
$ utility-client -loadClient="<CLIENT ID>"
```

Ensure to enclose the CLIENT ID in double quotes for proper loading.

## Reloading Server Cache Configuration

The server maintains cache of TTL (Time to Live) and whitelisted IP addresses. Use the following command to reload the server cache whenever these configurations change:

```bash
$ utility-client -reloadMyConf
```

## Cache Management

**Utility Server maintains a cache of rendered pages for optimized performance. Here's how to manage the cache:**

* **Purging Full Cache:**

  ```bash
  $ utility-client -purgeAllCache
  ```

  **Warning:** Purging the entire cache is not recommended for production deployments. Perform cache warmup afterwards for smooth operation.

* **Purging URL-Specific Cache:**

  ```bash
  # Purge cache for a single URL
  $ utility-client -purgeURLCache <URI>

  # Purge cache for multiple URLs from a file
  $ utility-client -purgeURLCache ./path/to/URLlist_FILE
  ```

  Replace `<URI>` with the part of the URL after the domain name (starting with a forward slash "/").

* **Updating Time To Live (TTL):**

  ```bash
  $ utility-client -updateTTL=<TTL>
  ```

  Replace `<TTL>` with an integer between 1 and 100 (days) to define the duration for which cached pages are maintained.

* **Cache Warmup:**

  ```bash
  # Warmup cache from Sitemap.xml
  $ utility-client -warmupCache

  # Warmup cache from a URL list file
  $ utility-client -warmupCache ./path/to/URLlist_FILE
  ```

  Ensure proper whitelisting at your firewall end for smooth warmup.

## Whitelisting IPs

Utility Server listens only from whitelisted IPs for security. Here's how to whitelist IPs:

```bash
$ utility-client -whitelistIPs <Space separated IPV4 and IPV6>
```

Whitelist static IP addresses of the machines running TTSCC and your web server. Separate IPs with a space.

## Viewing Stats

Use the following command to view stats like credit quota, number of renders, requests served from cache, and more:

```bash
$ utility-client -getStats=<MONTH>
```

Replace `<MONTH>` with the desired month (e.g., `January`).

## User Account Management

**Activating an Account:**

```bash
$ utility-client -activateAccount
```

Follow the prompts to activate an account using the registered email ID.

**Logging In and Out:**

```bash
# Log in
$ utility-client -login

# Log out
$ utility-client -logout
```

**Requesting Password Reset:**

```bash
$ utility-client -resetPassword
```

Follow the prompts to request a password reset via the registered email ID.

## Client Onboarding

**Initiating Client Onboarding:**

```bash
$ utility-client -onboardClient
```

Follow the prompts to initiate the onboarding process for a new client.

## Downloading and Monitoring Logs

**Downloading Log Reports:**

```bash
$ utility-client -downloadLogReport
```

**Fetching Live Logs:**

```bash
$ utility-client -fetchLiveLogs
```

## Updating and Managing Keys

**Pushing Access and Secret Keys:**

```bash
# Push a new access key
$ utility-client -pushAccessKey

# Push a new secret key
$ utility-client -pushSecretKey
```

**Rotating Access and Secret Keys:**

```bash
# Rotate the access key
$ utility-client -rotateAccessKey

# Rotate the secret key
$ utility-client -rotateSecretKey
```

## Validating Transactions

**Validating a Transaction:**

```bash
$ utility-client -validateTxn=<transaction>
```

Replace `<transaction>` with the specific transaction to validate.

## Viewing Available Plans

**Showing Available Plans:**

```bash
$ utility-client -showPlans
```

## Updating Utility Client

**Updating to the Latest Version:**

```bash
$ utility-client -update
```

## Session Management

**Terminating Active Sessions:**

```bash
$ utility-client -terminateSession
```

## Viewing User Information

**Displaying Logged-In User:**

```bash
$ utility-client -whoami
```

**Displaying Utility Client Version:**

```bash
$ utility-client -ver
```

## Help

**Showing Detailed Usage Information:**

```bash
$ utility-client -help
```
