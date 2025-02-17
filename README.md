# 🔗 LittleLink-Server

This project is based on the great work from [littlelink](https://github.com/sethcottle/littlelink)
It takes the same simple approach to a link page and hosts it within a NodeJS server with React Server Side Rendering, containerized for you to use. Now, customizing `LittleLink` with `littlelink-server` is as easy as passing in some environment variables.  If you need help configuring this, please see [this video that explains everything](https://www.youtube.com/watch?v=42SqfI_AjXU).

# 🚀 Getting Started

## Supported Links
Check the [config](https://github.com/techno-tim/littlelink-server/blob/master/src/config.js) file for all supported buttons!
## Docker

This container image is published on both [GitHub Container Registry](https://github.com/techno-tim/littlelink-server/pkgs/container/littlelink-server) and [DockerHub](https://hub.docker.com/repository/docker/timothystewart6/littlelink-server) choose whichever one works for you.  They will both be updated during CI.

`docker-compose.yml`

```yml
---
version: '3'
services:
  little-link:
    image: ghcr.io/techno-tim/littlelink-server:latest
    # dockerhub is also supported timothystewart6/littlelink-server
    #image: timothystewart6/littlelink-server:latest
    container_name: littlelink-server
    environment:
      - META_TITLE=Techno Tim
      - META_DESCRIPTION=Techno Tim Link page
      - META_AUTHOR=Techno Tim
      - THEME=Dark
      - FAVICON_URL=https://pbs.twimg.com/profile_images/1286144221217316864/qIAsKOpB_200x200.jpg
      - AVATAR_URL=https://pbs.twimg.com/profile_images/1286144221217316864/qIAsKOpB_200x200.jpg
      - AVATAR_2X_URL=https://pbs.twimg.com/profile_images/1286144221217316864/qIAsKOpB_400x400.jpg
      - AVATAR_ALT=Techno Tim Profile Pic
      - NAME=TechnoTim
      - BIO=Hey! Just a place where you can connect with me!
      - FOOTER=Thanks for stopping by!
      - GITHUB=https://github.com/timothystewart6
      - TWITTER=https://twitter.com/TechnoTimLive
      - INSTAGRAM=https://www.instagram.com/techno.tim
      - YOUTUBE=https://www.youtube.com/channel/UCOk-gHyjcWZNj3Br4oxwh0A
      - TWITCH=https://www.twitch.tv/technotim/
      - DISCORD=https://discord.gg/DJKexrJ
      - TIKTOK=https://www.tiktok.com/@technotim
      - KIT=https://kit.co/TechnoTim
      - FACEBOOK=https://facebook.com
      - FACEBOOK_MESSENGER=https://facebook.com
      - LINKED_IN=https://linkedin.com
      - PRODUCT_HUNT=https://www.producthunt.com/
      - SNAPCHAT=https://www.snapchat.com/
      - SPOTIFY=https://www.spotify.com/
      - REDDIT=https://www.reddit.com/
      - MEDIUM=https://medium.com
      - PINTEREST=https://www.pinterest.com/
      - EMAIL=you@example.com
      - EMAIL_TEXT=Email Me!
      - EMAIL_ALT=you@example.com
      - EMAIL_ALT_TEXT=Email Us!
      - SOUND_CLOUD=https://souncloud.com
      - FIGMA=https://figma.com
      - TELEGRAM=https://telegram.org/
      - TUMBLR=https://www.tumblr.com/
      - STEAM=https://steamcommunity.com/
      - VIMEO=https://vimeo.com/
      - WORDPRESS=https://wordpress.com/
      - GOODREADS=https://www.goodreads.com/
      - SKOOB=https://www.skoob.com.br/
      - LETTERBOXD=https://letterboxd.com/
      - MASTODON=https://mastodon.social/
      - MICRO_BLOG=https://micro.blog/
      - WHATSAPP=https://www.whatsapp.com/
      - STRAVA=https://strava.com/
    ports:
      - 8080:3000
    restart: unless-stopped
    security_opt:
      - no-new-privileges:true
```

Docker command

```
docker run -d \
  --name=littlelink-server \
  -p 8080:3000 \
  -e META_TITLE='Techno Tim' \
  -e META_DESCRIPTION='Techno Tim Link page' \
  -e META_AUTHOR='Techno Tim' \
  -e THEME='Dark' \
  -e FAVICON_URL='https://pbs.twimg.com/profile_images/1286144221217316864/qIAsKOpB_200x200.jpg' \
  -e AVATAR_URL='https://pbs.twimg.com/profile_images/1286144221217316864/qIAsKOpB_200x200.jpg' \
  -e AVATAR_2X_URL='https://pbs.twimg.com/profile_images/1286144221217316864/qIAsKOpB_400x400.jpg' \
  -e AVATAR_ALT='Techno Tim Profile Pic' \
  -e NAME='TechnoTim' \
  -e BIO='Hey! Just a place where you can connect with me!' \
  -e GITHUB='https://github.com/timothystewart6' \
  -e TWITTER='https://twitter.com/TechnoTimLive' \
  -e INSTAGRAM='https://www.instagram.com/techno.tim' \
  -e YOUTUBE='https://www.youtube.com/channel/UCOk-gHyjcWZNj3Br4oxwh0A' \
  -e TWITCH='https://www.twitch.tv/technotim' \
  -e DISCORD='https://discord.gg/DJKexrJ' \
  -e TIKTOK='https://www.tiktok.com/@technotim' \
  -e KIT='https://kit.co/TechnoTim' \
  -e EMAIL='someone@example.com' \
  -e EMAIL_TEXT='Email me!' \
  -e FOOTER=Thanks for stopping by! \
  --restart unless-stopped \
  ghcr.io/techno-tim/littlelink-server:latest
```

## Kubernetes

[Unofficial helm chart provided by k8s-at-home](https://github.com/k8s-at-home/charts/tree/master/charts/stable/littlelink-server)

```
helm repo add k8s-at-home https://k8s-at-home.com/charts/
helm repo update
helm install littlelink-server \
  --set env.TZ="America/New York" \
  --set env.META_TITLE="TechnoTim"
    k8s-at-home/littlelink-server
```
Or use a values.yaml files

`helm install littlelink-server k8s-at-home/littlelink-server -f values.yaml`


# 👇 What is LittleLink? 

![LittleLink](https://cdn.cottle.cloud/littlelink/social-circle.png)

LittleLink is a lightweight DIY alternative to services like [Linktree](https://linktr.ee)
and [many.link](https://www.google.com). LittleLink was built using [Skeleton](http://getskeleton.com/), a dead simple, responsive boilerplate—we just stripped out some additional code you wouldn't need and added in branded styles for popular services. 😊

![Themes](https://cdn.cottle.cloud/littlelink/themes.png)

LittleLink has more than 20 company button styles you can use and we'll be throwing more in soon. You'll also find a light and dark theme ready to go. Not a fan of the colors? Update `skeleton-light.css` or `skeleton-dark.css` to the HEX values of your choosing. 

![Performance](https://cdn.cottle.cloud/littlelink/performance.png)

Using [Skeleton](http://getskeleton.com/) let us build something that loads quickly & doesn't have any of the unnecessary bloat you would get from using a large framework for a page that requires nothing more than simplicity. LittleLink scored a 99/100 in performance when tested with [Google Lighthouse](https://developers.google.com/web/tools/lighthouse).


