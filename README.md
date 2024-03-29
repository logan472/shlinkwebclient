# Shlink On Railway

[![Deploy on Railway](https://railway.app/button.svg)](https://railway.app/template/kwu__Y?referralCode=IFlm92)

## What is this template?

Shlink is a self-hosted URL shortener that enables you to create, and track the usage of  "short" URLs that redirect to other, longer, URLs. Shlink also provides analytics on URL usage, such as visit counts and geographic location of the visitors.

This template spins up:
- [Shlink](https://shlink.io/documentation/api-docs/) the official shlink application. This handles short links and serves an authenticated API for management.
- [Shlink Web Client](https://shlink.io/documentation/shlink-web-client/) the official Shlink web client used for managing and monitoring your short links + HTTP basic-authentication via NGINX. 

*This template makes deploying Shlink extremely easy; **It can be setup in less than 5 minutes**.*

## Quick start guide 

1. Click the "Deploy on Railway" button above 
2. Follow the setup steps on Railway 
   1. Enter a username for the shlink web client.
   2. Enter a password for the shlink web client.
   3. Click "deploy!"
3. Monitor your services as the come up; wait until everyting is up with a green checkmark.
4. You're good to go!
   1. You can access the web client using your username and password.
   2. You can access shlink directly via the API using the API key generated by Railway.

### Optional: configuring your own domains

You'll probably want your shlink service to have a custom domain so the generated shortlinks are *shorter* than the links you're redirecting to. 

See [this guide on Railway for configuring a custom domain](https://docs.railway.app/guides/public-networking#custom-domains).

### Optional: configuring app sleeping

If you want your services to scale down when not in use, you can setup [app sleeping on Railway](https://docs.railway.app/reference/app-sleeping).

See [this guide on Railway for configuring app sleeping](https://docs.railway.app/guides/optimize-usage#enabling-app-sleeping).

## Project structure & services

This template is made up of three railway services: 

- [Shlink](https://shlink.io/documentation/): primary short link application
   - The primary short link application.
   - [Serves a REST API](https://shlink.io/documentation/api-docs/) that allows users to manage short links.
   - All your generated short links will be at this service's URL.
- [Shlink Web Client](https://shlink.io/documentation/shlink-web-client/): web app for managing Shlink
   - Web UI for handling your short URLs, creating new ones or monitoring visit stats.
   - The Web UI hooks into the Shlink service's API on template generation and requires no extra setup.
   - This template bolts on HTTP basic-authentication to the web client making it safe to expose to the internet. 
- PostgreSQL Database: primary database used by Shlink

## Additional resources

- [Shlink homepage](https://shlink.io/)
- [Shlink documentation](https://shlink.io/documentation/)
- [Shlink web client documentation](https://shlink.io/documentation/shlink-web-client/)

## Feedback

If you have feedback on this template, [please submit a GitHub issue](https://github.com/mykalmachon/shlink-on-railway) with as much detail as possible. 

### Known issues

- [Shlink cannot connect to the database via private networking](https://github.com/MykalMachon/shlink-on-railway/issues/1): this is due to the fact that shlink appears to not support IPV6 networking (which Railway uses for it's private networking features). If you can see a way around this, feel free to leave an explanation in the open issue or file a pull request.
