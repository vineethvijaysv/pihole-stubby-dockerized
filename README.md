# pihole-stubby-dockerized

#### An easy way to run Pihole in your local network with stubby as the upstream DNS provider. Stubby itself uses DNS over TLS which ensures that DNS queries leaving your home network will be encrypted.

![Network Diagram](/pihole-stubby-dockerized.png)

#### To run the application,just clone the repositary, change the admin password for pihole in the docker-compose.yml file and run docker-compose
```
git clone pihole-stubby-dockerized pihole-dockerapp
cd pihole-dockerapp
docker-compose up -d
```

#### Default stubby.yml is configured to use 4 DNSoTLS Providers (2 Cloudfare IP's and 2 Quad9 IP's) in a roundrobin manner. To change this or any other behavior, refer DNSPrivacy's stubby documentation: https://dnsprivacy.org/wiki/display/DP/Configuring+Stubby

#### To reconfigure the pihole container, refer: https://hub.docker.com/r/pihole/pihole/

#### Wireshark/tcpdump of a sample query
######pihole --(clearText DNS request)--> Stubby --(encrypted request)--> CloudFare DNS --(encrypted response)--> Stubby --(cleartext Response)--> pihole
![Sample DNS Request](/wireshark-screenshot.png)
