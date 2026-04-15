
https://docs.voidlinux.org/config/services/index.html
http://smarden.org/runit/runscripts.html

# Setting up a new service

    sudo cp -a ~/code/tem/void-runit-sv-service/ /etc/sv/SERVICE_NAME
		sudo chown -R root:root /etc/sv/SERVICE_NAME
    sudo chmod 755 /etc/sv/SERVICE_NAME
    sudo chmod 755 /etc/sv/SERVICE_NAME/run
    sudo chmod 755 /etc/sv/SERVICE_NAME/log
    sudo chmod 755 /etc/sv/SERVICE_NAME/log/run

Fill out that template, then enable service:

    ln -s /etc/sv/SERVICE_NAME /var/service/

# Start and enable a service

    sudo vsv enable SERVICE
    sudo vsv start SERVICE

# Add restart delay

Use a ./finish file (in the same dir as the `./run` file). `./finish` is run
upon abonormal termination, so `sleep 30` (or whatever time) can be added in
that file to add a 30 second delay before runit tries to restart the service.
