
# Generate one random number/integer in R

    sample(1:999999999, 1)

# Get bounding box of raster as sf object polygon in R

    spat_rast = terra::rast("PATH/TO/SPAT_RAST.tif")
    bbox_sf_poly = spat_rast |>
        sf::st_bbox(crs=terra::crs(spat_rast)) |>
        sf::st_as_sfc() |>
        sf::st_as_sf()

# `mkdir -p` in R

    dir.create("PATH", showWarnings=FALSE, recursive=TRUE, mode="0700")

# Get coordinate components (xmin, xmax, ymin, ymax) from SpatExtent object in R

    as.numeric(SPAT_EXT_OBJ[INDEX])

Where INDEX is 1, 2, 3, or 4.

# `mv` in R (move file in R)

    file.rename(SRC, DST)

# Define function in R that takes an undefined number of arguments

    fn = function(...) {
        args = list(...)
    }

# strf (format) `Sys.time()` in R

    format(Sys.time(), "%Y-%m-%d %H:%M:%S")

# Join a list of strings together in R

    joined_text = do.call(paste0, list_of_strs)

# Show recent login attempts on Linux

    last
    lastb

# Remove and garbage collect variable in R

    scrub = function(x) {
        rm(x)
        gc(verbose=FALSE, full=TRUE)
    }

    scrub(LARGE_VAR)

# Check if path is mountpoint in Python

    if Path("path/to/dir").is_mount():
        print("This is a mount point.")

# Convert SpatExtent to WKT in R

    library(terra)
    wkt = ext(chunk) |>
        terra::as.polygons() |>
        terra::geom(wkt=TRUE)

# Write text to file in R

    cat("TEXT", file="output.txt")

# Create empty file in R (`touch`)

    file.create("PATH")

# Show size of installed packages on Void Linux

    sudo xbps-query -p filename-size -s '' | sort -k2 -h

# `id -u` and `id -g` (get user and group ID) in Python

    os.getuid(); os.getgid()

# Knit R Markdown document in R

    rmarkdown::render('path/to/doc.rmd')

# Linux flush disk IO cache

    echo 3 | sudo tee /proc/sys/vm/drop_caches

# Show XBPS/VPM package install/update log on Void Linux

    xilog

# Location of XBPS/VPM Void Linux package cache

/var/cache/xbps

# Neovim dump current mappings

    :map
    :nmap
    :vmap
    :imap

# Show/cat/display/view XBPS/VPM logs on Void Linux systems running socklog

    svlogtail xbps

# Strip filename extension in R

Use regex via `sub()`.

# Write SpatExtent object to a shapefile in R

Jk, we are going to use geopackage (shapefile sucks).

    terra::writeVector(
        SPAT_EXTENT_OBJ |> terra::as.polygons(crs=SPAT_EXTENT_OBJ_EPSG),
        './DEST.gpkg'
    )

# Ask/prompt user for text input on command line in R

    response = readline("Enter something: ")

# Append to list in R

    my_list = list(1, 2)
    my_list = c(my_list, 3)

OR

    my_list = list(a=1, b=2)
    my_list = c(my_list, list(c=3))

# Iterate over 2nd through last items in a list in R

    for (i in seq_len(my_list[-1])) {
        my_list[i]
    }

# Make terra plot each raster layer on a new PDF page in R

    library(terra)

    r = terra::rast("TIF_PATH")
    pdf("DEST_PDF_PATH.pdf", onefile=TRUE)

    for (i in seq_len(nlyr(r))) {
        plot(r[[i]], main=names(r)[i])
    }

    dev.off()

# Access environment variables in R

    Sys.getenv("ENV_VAR_NAME")

# Get number of CPU cores in R

    library(parallel)
    parallel::detectCores()

# Get path to current script file in R

    args = commandArgs(trailingOnly = FALSE)
    file_arg = "--file="
    script_path = sub(file_arg, "", args[grep(file_arg, args)])

# Get the SHA1 hash of a variable in R

    library(digest)
    digest::digest(x)  # Where x can be pretty much any object

# Get current working directory in R

    getwd()

# Filter a list in R

    Filter(FN, LIST)

# `sub()` vs `gsub()` in R

`sub()`	Replaces only the first match.
`gsub()` Replace all matches (global).

# Grep string in R (find pattern)

    grp = function(regex, string) {
        match_indexes = gregexpr(regex, string)
        return(regmatches(string, match_indexes))
    }

# Slice/index/strip N characters from string in R

Strip first 2 and last 4 characters from each string:

    strings = c("Apple123", "Banana456", "Cherry789")
    # NOTE: strings must be a vector, not a list. If you start with a list,
    # pass it to `unlist()` first.
    result = substring(strings, 2 + 1, nchar(strings) - 4)

# Get (slice/index) last N elements from list (vector) R

    VECT[(length(VECT)-N+1):length(VECT)]

# Sort list alphabetically in R

    sort(VECTOR)

OR

    sort(unlist(LIST))

# Run system command (subprocess) in R

Use `system2` function.

# Continue loop in R

Use `next` keyword.

# Determine if command run via R `system2()` function exited with error

    rc = system2(c("ls", "/non/exist/path"))
    if (rc != 0) {
        cat("FAIL!")
    }

# Read text file in as string in R

    fp = "FILE/PATH"
    file_str = readChar(fp, file.info(fp)$size)

# Write text string to file in R

    cat(STRING, file="FILE/PATH")

# Equivalent of Linux command `realpath` in R (for getting absolute path)

`normalizePath` function.

# Return TRUE if all vector items are TRUE in R (same as Python's all())

    all(c(thing, thing, ...))

# Sum disk usage for list of individual files

    fd ... | tr '\n' '\0' | du -ch --files0-from=-

# `rm -fr` in R

    unlink("dir", recursive=T)

# Line item count/frequency/histogram
# (show count for number of times each unique line occurs)

    | sort  | uniq -c

# Git clone latest commit contents only, plus repo commit history

	git clone --filter=tree:0 URL

# Git clone latest commit only

	git clone --depth=1 URL

