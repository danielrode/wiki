# Concurrency / parallel processing

```R
library(parallel)
jobs = list(1, 2, 33, 11, 19)
worker = function(x) {
  return(x + 99)
}
products = parallel::mclapply(
  jobs, worker, mc.cores = parallel::detectCores()
)
```

# Find which package a function/variable came from

    ?func_or_var_name  # (in interactive prompt)

# Debugging scripts that need command line arguments

    args <- commandArgs(trailingOnly = TRUE)
    if (interactive()) {args = c("path.txt")}  # TODO for debugging

OR

    commandArgs = function(...) c("./path1", "./", "123", "456", "789")
    source("path")

# Anonymous function in pipeline

    "some text" |> (function(x) { paste(x, "more text")})()

# Get user input

In interactive session use `readline()` and in scripts use `readLines("stdin", n = 1)`.

