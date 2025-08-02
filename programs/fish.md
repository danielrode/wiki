# Run block of code over each line from stdin

    cmd1 | while read l
        cmd2 $l
        cmd3
        cmd4 $l
    end
