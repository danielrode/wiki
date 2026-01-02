
# Dump file from snapshot

    restic dump SNAPSHOT_ID FILE_PATH > file_name.ext

# Restore a path

    restic restore --target ~/working --include PATH_TO_RESTORE latest


# Compare two most recent snapshots

    restic snapshots --compact | awk '{print $1}' | tail -4 | head -2 | tr '\n' ' '


# Get snapshot size

    restic forget SNAPSHOT_ID --prune --dry-run

# Dry run

To get an idea of how much space will by the next backup (for instance, if some new software is installed and you wonder if it has installed some files which may blow up the size of your next backup). There is a `ncdu` command to see how effective your restic exclude list will be. To find this command, see the restic exclude file (under ~/code/cfg).
