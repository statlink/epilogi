\name{pcor.equiv}
\alias{pcor.equiv}

\title{
Equivalence test using partial correlation
}

\description{
Equivalence test using partial correlation.
}

\usage{
pcor.equiv(res, y, x, alpha = 0.05)
}

\arguments{
\item{res}{
A vector with the residuals of the linear model.
}
\item{y}{
A vector with a selected predictor.
}
\item{x}{
A matrix with other predictors.
}
\item{alpha}{
The significance level to check for predictors from x that are equivalent to y.
}
}

\value{
A vector with 0s and 1s. 0s indicate that the predictors are not equivalent, while 1s indicate the equivalent predictors.
}

\author{
Michail Tsagris.

R implementation and documentation: Michail Tsagris \email{mtsagris@uoc.gr}.
}

\seealso{
\code{ \link{epilogi}
}
}

\examples{
#simulate a dataset with continuous data
set.seed(1234)
n <- 500
x <- matrix( rnorm(n * 50, 0, 30), ncol = 50 )

#define a simulated class variable
y <- 2 * x[, 1] - 1.5 * x[, 2] + x[, 3] + rnorm(n, 0, 15)

# define some simulated equivalences
x[, 4] <- x[, 1] + rnorm(n, 0, 1)
x[, 5] <- x[, 2] + rnorm(n, 0, 1)


b <- epilogi(y, x, tol = 0.05)
sel <- b$result[2, 1]
## standardise the y and x first
y <- (y - mean(y)) / Rfast::Var(y, std = TRUE)
x <- Rfast::standardise(x)

res <- resid( lm(y ~ x[, sel] ) )
sela <- b$result[2:3, 1]
pcor.equiv(res, x[, sela[2]], x[, -sela] )
## bear in mind that this gives the third variable after removing the first two,
## so this is essentially the 5th variable in the "x" matrix.
}


