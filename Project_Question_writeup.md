## GOAL
Create a model to determine a potential correlation between an actor hosting an episode of SNL prior to their movie's opening, and the subsequent financial success of the movie.

-- "financial success" = the traditional calculation is the domestic revenue is 2x the budget (inaccurate but calibration could be future improvement)
-- "hosting prior to opening" = hosting SNL 30 days or fewer prior to the release date of a movie.

## USE CASE 
A manager or publicist (to say nothing of the movie studio) has to give their client (star) as much positive public exposure in the hope of increasing awareness of a movie and selling more tickets. A model like this (extensible to other appearance opportunities like the Today Show or Late Night with Stephen Colbert) could help determine what media gigs they should book for a movie press junket.


## DATA SOURCES
Primary source = IMDB/OMDb (what we used in class) 
	- Complete list of SNL episodes (the episode title contains the Host/Musical Guest)  
	- Actor's bio  
Secondary source = wikipedia for actor biographical information (age, place of birth, marital status, etc)  
Potential source if needed = comScore (fka Rentrack) for movie cost/profit (if needed). Although comScore is usually not free.  


## POTENTIAL VARIABLES (STILL IN DEVELOPMENT)
	host gender
	host age (at time of movie's premiere)
	? number of times hosting SNL
	number of movies host (at time of premiere)
	
	
## POTENTIAL FUTURE IMPROVEMENTS (OUTSIDE SCOPE)
	- impact to box office net (average of prior movies versus movie after appearance)
	- crawl episode transcripts to see if the movie is mentioned in the opening monologue
	- SNL cast members in the host episode (ie does Will Farrell correlate with a positive/negative correlation)?
	- demographics of movie ticket purchases.
	- tv actors promoting new series/season, or musicians promoting new albums.



## LINKS FOR RESOURCES (STILL IN DEVELOPMENT)
(http://www.boxofficeflops.com/articles/when-does-a-movie-break-even-at-the-box-office/)
(https://en.wikipedia.org/wiki/Hollywood_accounting)
(https://en.wikipedia.org/wiki/Film_budgeting)
(http://www.marklitwak.com/glossary-of-industry-terms.html)









