Get list of hosted zones on sandbox account.. These are primarily aladdin generated subdomains for namespaces

aws route53 list-hosted-zones -profile sandbox| grep -v CONFIG | awk '{ print $4 }' | sed 's/\.$//g' > hosts

Manually edit hosts to remove domains to keep, leaving all the dynamically generated test domains.


Loop through the list, removing the zones.

while read domain; do ./bin/aws-route53-wipe-hosted-zone $domain; done <host

In AWS R53, remove NS records for testing subdomains from kdev186.fstest.info.



