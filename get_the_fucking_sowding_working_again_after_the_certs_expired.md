#### how we got the site working again after the certs expired.

# Set up cron job for letsencrypt:

## 0. confirm precusers exist
rc-service crond status

## 1. Create a cronjob file

doas printf '#!/bin/sh\ncertbot renew --quiet --deploy-hook "rc-service nginx reload"\n' > /etc/periodic/daily/certbot-renew

## 2. Make It Executable & Verify

doas chmod +x /etc/periodic/daily/certbot-renew

cat /etc/periodic/daily/certbot-renew

## 3. Test and run the setup
doas certbot renew --dry-run

doas run-parts /etc/periodic/daily

---

# Sowding Anyways!
get_the_fucking_sowding_working_again_after_the_certs_expired.md