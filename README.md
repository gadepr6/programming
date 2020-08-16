# programming


setwd('C:/Users/gadepr6/Documents/Coursera-R')

## set the input x as a matrix
## changed "mean" to "avg"
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

## changed "mean" to "avg" 
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
