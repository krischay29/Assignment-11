# Assignment-11
tukey_multiple <- function(x) {
  outliers <- array(TRUE,dim=dim(x))
  for (j in 1:ncol(x)) {
    outliers[,j] <- outliers[,j] & tukey.outlier(x[,j])
  }
  outlier.vec <- vector(length=nrow(x))
  for (i in 1:nrow(x)) {
    outlier.vec[i] <- all(outliers[i,])
  } 
  return(outlier.vec) 
}

The tukey_multiple R function is used to locate outliers in a matrix x using Tukey's approach. Here's an explanation of how it works:
Function definition: The function tukey_multiple takes one input, x, which is assumed to be a matrix.
The initialization code creates an array called outliers with all elements set to TRUE and the same dimensions as matrix x. This array will include logical values that indicate whether each element in x is an outlier or not.
Outlier Detection Loop:
It loops through each column of the input matrix x.
The function tukey.outlier is called for each column j, passing the column vector x[,j]. This function, presumably, uses Tukey's approach to discover outliers in the data.
It then applies an element-wise logical AND operation (&) to the current values in outliers[,j] and the output of tukey.outlier(x[,j]). This updates the outliers matrix with the found outliers in each column.
Outlier Vector Construction:
After recognizing outliers in each column, the program creates a vector named outlier.vec with a length equal to the number of rows in x.
It iterates through each row of the outlier’s matrix.
For each row i, it determines if all components in that row are TRUE, indicating that all columns in that row have been flagged as outliers.
It allocates the result to the appropriate element in outlier.vec.
Return: 
Finally, the function returns the outlier.vec, which contains logical values indicating whether each row of the input matrix x contains outliers.
Finally, the function returns the outlier.vec, which contains logical values indicating whether each row of the input matrix x contains outliers.
To summarize, this function applies Tukey's outlier identification approach to each column of the input matrix x, then aggregates the results to identify rows with outliers. It's an effective tool for detecting and highlighting probable outliers in multivariate data.
