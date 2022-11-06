# media-stack

**[WIP]**

Repository for multiple docker-compose files for media stack composed of : Radarr, Sonarr, Prowlarr, Deluge, Jellyfin, Plex.
Possible changes : Plex instead of Jellyfin. Integration of Overseerr.

This stack is supossed to come with different flavors, with vpn and traefik.

- [base](docker-compose_base.yml) : Completed, uses ports, no vpn and no reverse proxy
- [base + vpn](docker-compose-base-vpn.yml) : Not completed, uses ports, vpn and no reverse proxy
- [traefik](docker-compose-traefik.yml) : Completed, uses reverse proxy and no vpn
- [traefik + vpn](docker-compose-traefik-vpn.yml) : Not completed, uses reverse proxy and vpn

## File structure on the host:

```
data
├── media
│   ├── films
│   └── tv
└── torrents

```

The user need to have write and read permission on the data directory and sub directories.

## Deluge configuration

- Plugins : Label
- Download to : /data/torrents
- Do not check **any** *move completed to* checkbox, radarr and sonnar are in charge of moving the finished files.

## Radarr / Sonarr configuration

To connect the indexors and download client, the url must :

- Be in http
- Use either the subdomain, the ip address or the container name of the service

Parameters :

- Rename Movies : Yes
- Delete empty folders : Yes
- Unmonitor Deleted Movies : Yes
- Root Folders : /data/media/{films/tv}
- Connect Jackett
- Connect Deluge


## Jellyfin configuration

- Create media librairies and mont them on **/data/media/{films/tv}**
