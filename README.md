# media-stack

**[WIP]**

Repository for multiple docker-compose files for media stack composed of : Radarr, Sonarr, Deluge, Jackett, Jellyfin.
Possible changes : Prowlarr instead of Jackett and Plex instead of Jellyfin.

This stack is supossed to come with different flavors, with vpn and traefik.

- [base](docker-compose_base.yml) : Completed, uses ports, no vpn and no reverse proxy
- [base + vpn](docker-compose_base-vpn.yml) : Not completed, uses ports, vpn and no reverse proxy
- [traefik](docker-compose_traefik.yml) : Not completed, uses reverse proxy and no vpn
- [traefik + vpn](docker-compose_traefik-vpn.yml) : Not completed, uses reverse proxy and vpn

## File structure on the host:

```
data
├── media
│   ├── films
│   └── tv
└── torrents

```

## Deluge configuration

- Plugins : Label
- Download to : /data/torrents
- Do not check **any** *move completed to* checkbox, radarr and sonnar are in charge of moving the finished files.

## Radarr / Sonarr configuration

- Rename Movies : Yes
- Delete empty folders : Yes
- Unmonitor Deleted Movies : Yes
- Root Folders : /data/media/{films/tv}
- Connect Jackett
- Connect Deluge

## Jellyfin configuration

- Create media librairies and mont them on **/data/media/{films/tv}**
