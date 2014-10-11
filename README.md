# UpFlare

A simple CLI executable to lookup and update CloudFlare's DNS Records. DIY Dynamic DNS.

## Usage

The followings are required:

- CloudFlare API Key
- CloudFlare Email
- CloudFlare Zone

For lookups, it will query CloudFlare's API method `rec_load_all` and find matching records. While for updates, it will get the external IP from `https://icanhazip.com`.

```bash
# Lookup a domain's rec_id
$ ./upflare --api-key API_KEY --email EMAIL --zone ZONE --lookup --subdomain SUBDOMAIN.ZONE

# Update a record
$ ./upflare --api-key API_KEY --email EMAIL --zone ZONE --lookup --subdomain SUBDOMAIN.ZONE --rec-id REC_ID
```

To keep updating records, schedule this script. Scheduling for every 5 minutes on an Ubuntu machine might look like below.

```
$ crontab -e
*/5 * * * * /home/ubuntu/bin/upflare --api-key API_KEY --email EMAIL --zone ZONE --lookup --subdomain SUBDOMAIN.ZONE --rec-id REC_ID
```
