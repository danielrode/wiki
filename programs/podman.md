# Run X11 GUI program and see it on main host

	# Example
	podman run -it --rm -v "/tmp/.X11-unix:/tmp/.X11-unix:ro" -e DISPLAY alpine sh -c 'apk add xeyes && xeyes'

# List current capabilities granted to container

	podman exec <container_id> grep CapEff /proc/self/status
	capsh --decode=CODE

## Default capabilities as of Jan 2026

- cap_chown
- cap_dac_override
- cap_fowner
- cap_fsetid
- cap_kill
- cap_net_bind_service
- cap_setfcap
- cap_setgid
- cap_setpcap
- cap_setuid
- cap_sys_chroot

Capabilities descriptions:
https://docs.docker.com/engine/containers/run/#runtime-privilege-and-linux-capabilities
