
# Tee to STDOUT

    ... | tee /dev/tty | ...

Only works if attached to a terminal.

# Tee to STDERR

    ... | tee /dev/fd/2 | ...
