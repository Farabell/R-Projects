#Functions

Poll.Graph <- function(x)
{
  Name <- c("Jeb", "Donald","Ted","Marco","Carly","Hillary","Bernie")
  ABC <- c(4,62,51,21,2,14,15)
  NBC <- c(12,75,43,19,1,21,19)

  newPolls = data.frame(NBC,ABC)
  mean_results = apply(newPolls,1,mean)
  median_results = apply(newPolls, 1, median)
  min_results = apply(newPolls,1,min)
  max_results = apply(newPolls, 1, min)
	
  Polls = cbind(Name,newPolls, mean_results,median_results,min_results,max_results)

  m= melt(Polls, id.vars='Name')
	
  p <- ggplot(m, aes(variable, value)) + geom_bar( stat = "identity", position ="dodge", aes(fill = Name)) 

  return(p)
}
