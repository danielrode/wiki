# Concurrency / Parallel Processing
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
