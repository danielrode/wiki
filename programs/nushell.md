# Get output of command

    (command)

# Get command line argments

    def main [cmdline_arg1: cmdline_arg1_type] {
      script_cmd1
      script_cmd2 $cmdline_arg1
    }

# Convert column from table into newline separated plain text output

    ls | get name | to text

# Get table from inside other table

    | get TABLE_NAME

# Trim off first and last line from text input

    | lines | skip 1 | drop 1 | to text

# Explore/pan/view/page csv (and other tables)

    open file.csv | explore -i -p  # ESC to exit

# Save/set output to variable

    let var = (command)

# Compare (find differences) between two columns

    open table.csv | each {|row| if $row.col1 != $row.col2 { $row } }

# Join/concatinate two input/command streams

    (CMD1 ARGS) + (char newline) + (CMD2 ARGS) 

# Split string into array of words

    | split row ' '

# Get random sample of rows from table (data)

    open table.csv | sel col1 col2 | shuffle | first SAMPLE_SIZE

# Remove color highlighting

    Use `ansi strip`.

# Exclude/ignore empty/null/nan values in array/table column

    | filter { not ($in | is-empty) }

# Exception/error handling

    try {
        FAIL
    } catch {|err|
        # Handle exception
        echo $err.msg
        RECOVER
        # Raise exception
        echo $err.raw
        exit 1
    }

# Loop/iterate over list of files with specific extension

    for i in (glob *.ext) { echo $i }

# Remove empty lines

    | lines -s

# Case/Switch Statement

    Use `match` statement.

# Search command history

    Ctrl+r

# Print filetype of first 3 Python files of a directory

    file ...(glob working/*.py | first 3)

# Print filetype of 3 random Python file of a directory

    file ...(glob working/*.py | shuffle | first 3)

# Pipe/redirect both stdin and stdout

    cmd e+o>| cmd2

# Expand alias/abbriviation

    Ctrl+Space (custom shortcut)

# Convert list to table column

    $list | wrap col_name

# Combine two columns/tables into single table

    $table1 | merge $table2
