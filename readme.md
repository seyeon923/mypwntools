## Container Run Command in WSL

```
docker run -it -v /tmp/.X11-unix:/tmp/.X11-unix \
            -v /mnt/wslg:/mnt/wslg \
            -e DISPLAY \
            -e WAYLAND_DISPLAY \
            -e XDG_RUNTIME_DIR \
            -e PULSE_SERVER \
            -u root \
            --privileged \
            --rm seyeon923/ubuntu2204-pwn
```
