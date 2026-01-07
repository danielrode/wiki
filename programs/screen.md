# Start a program running inside session

    screen PROGRAM

# List sessions

    screen -ls

# Force attach to existing session (even if it is already attached elsewhere)

This will detach other location, but session will be unharmed.

    screen -dr SESH_NAME
