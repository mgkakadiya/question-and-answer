```
docker system prune
docker ps

docker container exec [OPTIONS] CONTAINER COMMAND [ARG...]
docker exec -it postgres_db bash

docker logs -f postgres_db
docker images
docker rmi be28e3e5b0e0
docker compose up --build
docker compose up -d 
```


# Fixing "Permission Denied" for Docker Daemon

If you encounter the error:

```
permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Get "http://%2Fvar%2Frun%2Fdocker.sock/v1.47/containers/json": dial unix /var/run/docker.sock: connect: permission denied
```

It means your user does not have the necessary permissions to access the Docker daemon. Here’s how to resolve it:

---

## Solution: Add Your User to the Docker Group

1. **Check the Current Groups for Your User**:
   ```bash
   groups
   ```
   If you don't see `docker` in the list, you need to add your user to the Docker group.

2. **Add Your User to the Docker Group**:
   ```bash
   sudo usermod -aG docker $USER
   ```

3. **Log Out and Log Back In**:
   Changes to group memberships only take effect after logging out and back in. Alternatively, use the `newgrp` command:
   ```bash
   newgrp docker
   ```

4. **Verify Access**:
   Run the following command to check if the issue is resolved:
   ```bash
   docker ps
   ```

---

## Temporary Solution: Use `sudo`

If you don’t want to modify group memberships or need a quick fix, prefix your Docker commands with `sudo`:
```bash
sudo docker ps
```

---

## Troubleshooting Steps

If the issue persists after adding your user to the Docker group:

1. **Check if the Docker Daemon is Running**:
   ```bash
   sudo systemctl status docker
   ```
   If it’s not running, start it:
   ```bash
   sudo systemctl start docker
   ```

2. **Check Docker Group**:
   Ensure the Docker group exists:
   ```bash
   grep docker /etc/group
   ```

3. **Reboot the System**:
   In some cases, a full system reboot might be required:
   ```bash
   sudo reboot
   ```

---

Let me know if you need further assistance!
