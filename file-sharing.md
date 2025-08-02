
# NCAT

NOTE: On some systems, the command is 'nc' rather than 'ncat'
NOTE: Make sure port is open on the receiver. I do not know if the sender needs to open ports.

On receiver machine

		ncat -l 8080 > FILE.EXT

On sender machine

		ncat IP.ADDRESS 8080 --send-only < FILE.EXT
		# OR on systems that do not have the '--send-only' flag
		cat FILE.EXT | ncat IP.ADDRESS 8080 > /dev/null

# SFTP

# Miniserve

"miniserve is a small, self-contained cross-platform CLI tool that allows you to serve file(s) via HTTP."

Miniserve allows users to upload files to the host machine. It also seems to support parallel and resumable downloads. Authentication can be enabled (by default it is off).

Usage:

		miniserve [-u] PATH

The '-u' flag enables the upload feature. PATH can be a file or directory.

https://github.com/svenstaro/miniserve
