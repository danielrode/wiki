
https://docs.voidlinux.org/config/services/index.html
http://smarden.org/runit/runscripts.html

# Setting up a new service

	sudo su
	mkdir /etc/sv/SERVICE_NAME
    cd /etc/sv/SERVICE_NAME

	printf "#!/bin/sh
	exec 2>&1
	exec SERVICE_EXE_FULL_PATH
	" > run

	chmod +x run
	mkdir log

	printf "#!/bin/sh
	exec vlogger -t SERVICE_NAME -p daemon
	" > log/run

	ln -s /etc/sv/SERVICE_NAME /var/service/

# Start and enable a service

	sudo vsv enable SERVICE
	sudo vsv start SERVICE

# Add restart delay

Use a ./finish file (in the same dir as the `./run` file). `./finish` is run
upon abonormal termination, so `sleep 30` (or whatever time) can be added in
that file to add a 30 second delay before runit tries to restart the service.
