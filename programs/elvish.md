
# Ask user for input and write it to file, line-by-line

    while true { read-line } | to-lines > file

# Run command and continue if it fails (inverse set -e)

    try {
        command1
    } catch e {
        echo $e
    }
    command2

# Run a command on each line

    echo "line1
    line2
    line3" | each {|i| cmd $i}

# Args as array

    var args = [
        --interactive --tty
        --publish 25565:25565
        --name mc-craftmine
        --volume mc-craftmine-data:/data
        --env EULA=TRUE
        --env VERSION=25w14craftmine
        # --env MODE=creative
        ghcr.io/itzg/minecraft-server
    ]
    podman run $@args

# Run command with custom env var

    { tmp E:ENV_VAR_NAME = ENV_VAR_VAL; CMD CMD_ARGS... }
    # OR
    env ENV_VAR_NAME=ENV_VAR_VAL CMD CMD_ARGS...

# Basic if condition with using `or`

    if (or (CONDITION1) (CONDITION2)) {
        DO SOMETHING
    }
