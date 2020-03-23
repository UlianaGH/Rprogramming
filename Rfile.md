makeCacheMatrix <- function(x = matrix()) {
m <- NULL
## Define function to set the value of the matrix and inverse from the cache
set <- function(y) 
{x <<- y    
m <<- NULL }
        
## Define function to get the value of the matrix
get <- function() x
## Define function to set the inverse. 
setInverse <- function(inverse) m <<- inverse
## Define function to get the inverse
getInverse <- function() m
    
## Return a list with the above four functions
list(set = set, get = get,
setInverse = setInverse,
getInverse = getInverse)}

cacheSolve <- function(x) {
m <- x$getInverse() # This fetches the cached value for the inverse
if(!is.null(m)) { # If the cache was not empty, we can just return it
message("getting cached data")
return(m)
}
## Getting the value of matrix. Calculate cache and then return the inverse
data <- x$get()  
m <- solve(data) 
x$setInverse(m)  
m }
