
# Bind (forward) remote port to local port

    ssh -NL LOCAL_PORT:localhost:REMOTE_PORT REMOTE_USER@REMOTE_IP

# Bind (forward) local port to remote port

    ssh -NR REMOTE_PORT:localhost:LOCAL_PORT REMOTE_USER@REMOTE_IP
