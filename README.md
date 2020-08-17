setwd('C:/Users/gadepr6/Documents/Coursera-R')
## Example: Caching the Mean of a Vector
## In this example we introduce the <<- operator which can be used to assign a value to an object in an environment that is different from the current environment. Below are    two functions that are used to create a special object that stores a numeric vector and caches its mean.
## The first function, makeCacheMatrix creates a special "vector", which is really a list containing a function to
## 1.set the value of the vector
## 2.get the value of the vector
## 3.set the value of the mean
## 4.get the value of the mean

makeCacheMatrix <- function(x = matrix(sample(1:100,9),3,3)) {
  s <- NULL
  set <- function(y) {
    x <<- y
    s <<- NULL
  }
  get <- function() x
  setavg <- function(solve) s <<- avg
  getsolve <- function() s
  list(set = set, get = get,
       setsavg = setavg,
       getavg = getavg)
}

## The following function calculates the mean/average of the special "vector" created with the above function. However, it first checks to see if the mean has already been calculated. If so, it gets the mean from the cache and skips the computation. Otherwise, it calculates the mean of the data and sets the value of the mean in the cache via the setmean function.
cacheSolve <- function(x, ...) {
  s <- x$getavg()
  if(!is.null(s)) {
    message("getting inversed matrix")
    return(s)
  }
  data <- x$get()
  s <- avg(data, ...)
  x$setavg(s)
  s
}
