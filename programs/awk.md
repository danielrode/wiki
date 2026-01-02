# Delete/remove empty lines

    awk 'NF'

# Strip leading/trailing spaces/tabs

    awk '{gsub(/^[ \t]+|[ \t]+$/, "", $0); print}'

# Show everything after the last '/'

    awk -F/ '{print $NF}'

Example: '/home/bill/hill' --> 'hill'

# Remove duplicate lines without sorting lines first

    awk '!x[$0]++'

# Print 3rd column

    awk '{print $3}'
