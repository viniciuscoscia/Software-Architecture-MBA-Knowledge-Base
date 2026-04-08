# Docker — Comandos Essenciais

## Commands

`docker image ls | grep hello-world`
Lists locally stored **images** (templates) that contain "hello-world" in their repository name. Images are what you download/build before running containers.

`docker run hello-world`
Creates and starts a new **container** from the hello-world image. If the image doesn't exist locally, Docker pulls it first. The container runs, executes its default command, then exits.

`docker container ls -a | grep nginx`
Lists all **containers** (running instances) with "nginx" in their name, including stopped ones. The `-a` flag shows ALL containers; without it, only running containers appear.

`docker run node:20-slim --version`
Runs a container from node:20-slim image and executes a **custom command** (`--version`) instead of the image's default command. Container starts, prints Node version, then exits.

`docker run node:20-slim ls .`
Runs a container and executes the `ls .` command inside it, listing files in the container's working directory. Shows what files exist in the image's default location.

`docker run -it node:20-slim bash`
**Interactive mode**: `-i` keeps STDIN open, `-t` allocates a pseudo-TTY (terminal). Together they let you interact with the container's shell (bash) in real-time. Essential for debugging or exploring containers.

`docker run -d nginx:1.19.10-alpine`
**Detached mode**: `-d` runs container in background, freeing your terminal. Returns container ID. Used for services that should run continuously (like web servers).

`docker stop $(docker ps -q)`
Stops all running containers. `docker ps -q` outputs only container IDs (quiet mode), which are passed to `docker stop`. Useful for cleanup.

`docker container prune --filter "until=200h"`
Removes stopped containers older than 200 hours. `prune` cleans up resources; `--filter` targets specific containers. Frees disk space without removing recent containers.

`docker rmi nginx:1.19.10-alpine -f`
Force removes (`-f`) the nginx image even if containers are using it. `rmi` = remove image. Dangerous: can break running containers. Use carefully.

`docker image prune`
Removes **dangling images** (untagged, no container references). Safe cleanup for build artifacts and orphaned layers. Add `-a` to remove all unused images.

`docker run -it -d --rm --name nginx3 -p 8000:80 nginx:1.19.10-alpine`
Combines multiple flags: `-d` (detached), `-it` (interactive TTY for exec later), `--rm` (auto-delete when stopped), `--name` (custom name), `-p 8000:80` (maps host port 8000 to container port 80). Access via localhost:8000.

`docker exec -it nginx3 sh`
Executes a command (`sh` shell) in a **running** container (nginx3). Unlike `docker run`, this doesn't create a new container — it enters an existing one. Use for debugging live containers.

`docker logs nginx3`
Shows stdout/stderr output from the container. Essential for debugging. Add `-f` to follow logs in real-time.

`docker inspect nginx3`
Returns detailed JSON with container config, network settings, mounts, and state. Use with `| grep` or `--format` to extract specific info.

`docker volume ls`
Lists Docker volumes (persistent storage separate from containers). Volumes survive container deletion, used for databases and stateful apps.

`docker network ls`
Lists networks. Containers on the same custom network can communicate using container names as hostnames.
