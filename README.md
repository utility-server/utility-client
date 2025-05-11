## Utility Client Manual

**Utility Client** is a versatile command-line tool designed to manage Utility Server's operations, including configuration management, client onboarding, caching, logging, and system monitoring. It supports both standard CLI and an interactive shell mode.

## For more details, check out our [Knowledge Base](https://github.com/utility-server/utility-client/wiki).
---

## Table of Contents
1. [Installation](#installation)
2. [Execution Modes](#execution-modes)
3. [Configuration](#configuration)
4. [Client Management](#client-management)
5. [Cache Management](#cache-management)
6. [Log Management](#log-management)
7. [User & Security Operations](#user--security-operations)
8. [Statistics & Plans](#statistics--plans)
9. [Session Management](#session-management)
10. [Miscellaneous](#miscellaneous)
11. [Command Reference](#command-reference)

---

## Installation

### On Linux (Ubuntu/Debian-based)

```bash
$ wget https://github.com/utility-server/utility-client/raw/main/UtilityClient-Debin-amd64-latest.deb
$ sudo dpkg -i UtilityClient-Debin-amd64-latest.deb
```

---

## Execution Modes

Utility Client supports two modes:

### 1. **Standard CLI Mode**
Run commands prefixed with a dash (`-`) like:
```bash
$ utility-client -login
```

### 2. **Interactive Shell Mode**
Enter by typing:
```bash
$ utility-client
```
You will see a prompt like:
```bash
֎ [CLIENT_ID] MODULE %
```
Run commands **without the dash** in this mode:
```bash
֎ demoClient default % login
```

---

## Configuration

### Set Configuration
```bash
$ utility-client -setConfig
```
Prompts for:
- Registered Domain
- Client ID
- End Point
- Access Key
- Client Secret
- Sitemap URL
- Concurrent Threads

### View Configuration
```bash
$ utility-client -printConfig
```

### Reload Server Cache Configuration
```bash
$ utility-client -reloadMyConf
```

---

## Client Management (Only for Admins and Resellers)

### List Clients
```bash
$ utility-client -listClients
```
Lists all configured clients under the current session.

### Load Client Configuration
```bash
$ utility-client -loadClient=<LIST | CLIENT ID>
```
Loads configuration for a selected client.

### Onboard New Client
```bash
$ utility-client -onboardClient
```
Starts the interactive onboarding process for new clients.

### Assign New Plan to Client
```bash
$ utility-client -assignNewPlan
```
Assigns a billing or usage plan to a selected client.

---

## Cache Management

### Purge All Cache
```bash
$ utility-client -purgeAllCache
```
Removes all cached data for the active client.

### Purge Specific URL Cache
```bash
$ utility-client -purgeURLCache <URI | ./path/to/URLlist>
```
Purges cache for a specific URL or batch list.

### Update Cache TTL
```bash
$ utility-client -updateTTL=<TTL>
```
Sets TTL (time-to-live) for cached content. Value is in days.

### Warmup Cache
```bash
$ utility-client -warmupCache [./path/to/URLlist]
```
Prefetches resources to warm up the cache.

---

## Log Management

### Download Log Report
```bash
$ utility-client -downloadLogReport
```
Downloads compressed logs for review.

### Fetch Live Logs
```bash
$ utility-client -fetchLiveLogs
```
Streams live logs from Utility Server.

---

## User & Security Operations

### Activate Account
```bash
$ utility-client -activateAccount
```
Activates a user account using their registered email.

### Login
```bash
$ utility-client -login
```
Prompts user login with credential validation.

### Logout
```bash
$ utility-client -logout
```
Ends the current session.

### Reset Password
```bash
$ utility-client -resetPassword
```
Initiates password reset by sending email.

### Push Access Key / Secret Key
```bash
$ utility-client -pushAccessKey
$ utility-client -pushSecretKey
```
Pushes a new access or secret key for secured requests.

### Rotate Access Key / Secret Key
```bash
$ utility-client -rotateAccessKey
$ utility-client -rotateSecretKey
```
Replaces current keys with new ones.

### Whitelist IPs
```bash
$ utility-client -whitelistIPs <IPV4 IPV6 ...>
```
Adds IPs to the whitelist for client access.

---

## Statistics & Plans

### Fetch Statistics by Month
```bash
$ utility-client -getStats=<MONTH>
```
Returns usage reports for a given month.

### Show Available Plans
```bash
$ utility-client -showPlans
```
Lists all available plans and their limits.

---

## Session Management

### Validate Transaction
```bash
$ utility-client -validateTxn=<transaction>
```
Validates a transaction ID from logs or API.

### Who Am I (Current Logged-in User)
```bash
$ utility-client -whoami
```
Displays the current logged-in user identity.

### Terminate All Sessions
```bash
$ utility-client -terminateSession
```
Closes all active sessions under this user.

---

## Miscellaneous

### Help
```bash
$ utility-client -help
```
Prints help details.

### Version
```bash
$ utility-client -ver
```
Shows the Utility Client version installed.

### Update (Requires `sudo`)
```bash
$ sudo utility-client -update
```
Installs the latest version of Utility Client.

### History (Interactive Mode Only)
```bash
history
```
Shows previously executed commands.

### Clear History (Interactive Mode Only)
```bash
clearHistory
```
Clears command history.

### View Orders
```bash
$ utility-client -myOrders
```
Displays confirmed service or billing orders.

### Set Active Module
```bash
$ utility-client -setActiveModule
```
Sets the currently focused module in interactive session.

### Sitemap Operations
```bash
$ utility-client -sitemap <add|update|flush|get|delete>
```
Manages sitemap functions for client websites.

---

## Command Reference

| Command                    | Description                                      |
|----------------------------|--------------------------------------------------|
| -activateAccount           | Activate an account using email ID              |
| -assignNewPlan             | Assign a new plan to a client                   |
| -clearHistory              | Clear all historical commands (interactive)     |
| -downloadLogReport         | Download log reports                            |
| -fetchLiveLogs             | Fetch live system logs                          |
| -getStats=<MONTH>          | Retrieve monthly stats                          |
| -help                      | Show help info                                  |
| -history                   | Show past commands (interactive only)           |
| -listClients               | List all configured clients                     |
| -loadClient=<...>          | Load or switch to a specific client             |
| -login                     | Login to your account                           |
| -logout                    | Logout from current session                     |
| -myOrders                  | View your confirmed orders                      |
| -onboardClient             | Start onboarding a new client                   |
| -printConfig               | Display current config                          |
| -purgeAllCache             | Clear all cache data                            |
| -purgeURLCache             | Purge specific URLs from cache                  |
| -pushAccessKey             | Set a new access key                            |
| -pushSecretKey             | Set a new secret key                            |
| -reloadMyConf              | Reload cached configs                           |
| -resetPassword             | Trigger password reset                          |
| -rotateAccessKey           | Rotate access key                               |
| -rotateSecretKey           | Rotate secret key                               |
| -setActiveModule           | Set the active module                           |
| -setConfig                 | Configure Utility Client                        |
| -showPlans                 | List available plans                            |
| -sitemap                   | Manage sitemap (Add, Update, Flush, etc.)       |
| -terminateSession          | End all active sessions                         |
| -update                    | Update Utility Client (requires `sudo`)         |
| -updateTTL=<TTL>           | Set TTL for cached entries                      |
| -validateTxn=<txn>         | Validate a transaction ID                       |
| -ver                       | Display Utility Client version                  |
| -warmupCache               | Prefetch & warm cache                           |
| -whitelistIPs              | Whitelist IPs for access                        |
| -whoami                    | Show current logged-in user                     |

