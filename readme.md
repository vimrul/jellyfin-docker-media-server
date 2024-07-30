Replace the /path/to/ placeholders with the actual paths to your media locations on your host machine. Here’s a brief explanation of the volumes used:

/path/to/config:/config: Stores Jellyfin configuration files.
/path/to/cache:/cache: Stores cache files for Jellyfin.
/path/to/media1:/media/movies: The first media location, typically for movies.
/path/to/media2:/media/tv: The second media location, typically for TV shows.
/path/to/media3:/media/music: The third media location, typically for music.
/path/to/media4:/media/photos: The fourth media location, typically for photos.
/path/to/media5:/media/audiobooks: The fifth media location, typically for audiobooks.
Make sure to adjust the PUID, PGID, and TZ environment variables to match your system’s user ID, group ID, and timezone, respectively.

#Finding PUID:
id -u

#Finding PGID:
id -g

