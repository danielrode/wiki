
# Delete first line

    cat FILE | sed 1d

# Delete last line

    cat FILE | sed '$d'

# Print Nth line

    sed -n '5p'

# Delete a Nth line from a file

    # Delete the 5th line
    sed -e 5d FILE

    # Delete lines 5 through 10 and line 12
    sed -e '5,10d;12d' FILE
    # Same, but write to file
    sed -i -e '5,10d;12d' FILE

    # Replace 3rd line with text "hello"
    sed -i 3c\\hello
