# GoF-reproducibility


Replication instructions

Table 2 in main file: Run Table1seeded.m to reproduce Table 2 in the main document exactly. Takes approximately 15 minutes on a AMD Ryzen 7 5800H 8-core CPU.

Table 1 and 2 in Appendix C: Run hawkes_parallel_naive.m. To compare to different alternatives replace simulation parts (between 'START OF SIMULATION PART' and 'END OF SIMULATION PART', lines 14--26) by simulation parts from 

	hawkes_parallel.m (lines 5--17);
	PLHawkes_parallel.m (lines 5--36; set Tstationary = max(250,Tmax/250); Tmax2 = Tmax + Tstationary;
	shotnoise_parallel.m (lines 5--19), choose mu, alpha, beta in line 5; 
	selfcor_parallel.m (lines 5--18); 
	inhompoin_parallel.m lines(5--14). 
 
Set Tmax=50000 for Table 1. Change Tmax accordingly for Table 2.
For Table 1, alternatively one could set Tmax=50000 in Table1seeded.m

Table 3 and 4 in Appendix C: Run PLhawkes_parallel_naive.m. To compare to different alternatives replace simulation parts (between 'START OF SIMULATION PART' and 'END OF SIMULATION PART', lines 14--26) by simulation parts from 
	hawkes_parallel.m (lines 5--17);
	PLHawkes_parallel.m (lines 5--36; 
	shotnoise_parallel.m (lines 5--19), choose mu, alpha, beta in line 5; 
	selfcor_parallel.m (lines 5--18); 
	inhompoin_parallel.m lines(5--14). 
Set Tmax=50000 for Table 4. 

Table 5 in Appendix C: use RTC_parallel.m and RTC_parallel_PLH.m; To compare to different alternatives replace simulation parts (between 'START OF SIMULATION PART' and 'END OF SIMULATION PART', lines 14--26) by simulation parts from 

	hawkes_parallel.m (lines 5--17);
	PLHawkes_parallel.m (lines 5--36; set Tstationary = max(250,Tmax/250); Tmax2 = Tmax + Tstationary;
	shotnoise_parallel.m (lines 5--19), choose mu, alpha, beta in line 5; 
	selfcor_parallel.m (lines 5--18); 
	inhompoin_parallel.m lines(5--14). 

Figure 1 in main file: see end of hawkes_parallel_naive.m

Appendix D; temporal ETAS model: Use testingOgata.m; Import raw data Ogata1988dataRAW.xlsx; import 4th column as 'times' and 2nd column as 'magnitudes'. Further explanation is given in main text. Data is not yet preprocessed, and is preprocessed within the code. 

	Includes commands to generate Figure 1
 
Appendix D; a recursive point process model: Use testingSchoenberg.m; import third column as 'timesraw1', fourth column as 'counts', for the datasets California.xlsx and after that for the data set Florida.xlsx. timesraw1 then gives the onset of weeks in which there was at least one infection, while counts gives the number of infections in that week.

	Includes commands to generate Figure 2






To apply our methods to different models, the code of hakwes_parallel_naive.m can be adapted without much effort!

When the model is multivariate, our steps can be applied to each coordinate seperately; refer to Algorithm 1 in the main paper.

In hakwes_parallel_naive.m, alter the following: 

	 Replace simulation part by simulations for model you have in mind
	 write a function loglikelihood to calculate the negative log likelihood of the model you intend to use
	 write a function empiricaltransformation in which you calculate the compensated empirical process (N(t)-Lambda(t))/sqrt(t), using the compensator (time integrated conditional intensity) of the point process model you have in mind



	
