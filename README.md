# server-containers
Docker Compose Files for some containers I like


## How to

To use each container `cd` into the directory in question and run `docker compose up -d`, you'll want to change any `YOU@EMAIL.COM`, `GENERATEYOUROWN` and `YOURDOMAIN.COM` to make each container work together.

### Example

```sh
# in the server-containers repo folder...

cd media
docker compose up -d
```

### Advice

I advise you start the containers and setup in this order:

1. <abbr title="Only needed if you have a dynamic WAN IP to update cloudflare">cloudflare-ddns*</abbr>
1. dns
1. traefik (You'll need to forward ports on your router for this to be accessible)
1. portainer
1. authentik (optional, see below)

without ddns your domain won't work, you'll want to change your DHCP on your network to use the local DNS server on the IP this docker node is running on too otherwise your local devices won't be able to use the domain, if your router has the option to change it's port for the web UI 

#### A note on authentik

> "authentik is an IdP (Identity Provider) and SSO (single sign on) that is built with security at the forefront of every piece of code, every feature, with an emphasis on flexibility and versatility."

It's mint, it really is... but it can be a pain to be seen by other containers i.e. networking and dns. it's in here and it works but I advise you to do your own reading on the matter and continue where I left off, you can setup an auth server with it to have sso and oauth login for your apps, I got it working... it wasn't what I hoped but I fully recognise that it's my lack of understanding of authentik, *good luck solider!*

- [Authentik Docs](https://docs.goauthentik.io/docs/)