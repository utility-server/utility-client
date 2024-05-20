# utility-client

1. First, download the .deb package from GitHub using wget:
$ wget https://github.com/utility-server/utility-client/raw/main/UtilityClient-Debin-amc64-3.02.deb

2. Then, install the downloaded package using dpkg:
$ sudo dpkg -i UtilityClient-Debin-amc64-3.02.deb

If there are any dependencies missing, you may need to install them manually using apt-get install -f:
$ sudo apt-get install -f

$ utility-client

Commands:
./common-client -setConfig
./common-client -loadClient=<"CLIENT ID"/LIST>
./common-client -printConfiguration
./common-client -warmupCache [./path/to/URLlist FILE (optional)]
./common-client -purgeAllCache
./common-client -purgeURLCache <URI> OR <Image URL> OR <./path/to/URLlist FILE>
./common-client -downloadLogReport <date>
./common-client -reloadMyConf
./common-client -updateTTL=<TTL>
./common-client -getStats=<month>
./common-client -fetchLiveLogs
./common-client -whitelistIPs <Space separated IPV4 and IPV6>
