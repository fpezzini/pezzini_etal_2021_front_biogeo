# Comparing models in Bayesian analysis 

I have followed Condamine et al. 2015.

The most suitable model can be selected by comparing the Bayes Factor (BF). 
The BF is equal to the ratio of the Marginal Likelihood Estimate (MLE) of two models (`BF=MLE1/MLE2`) or 
to the difference of MLEs in log space (`log(BF)=log(MLE1) – log(MLE2)`). 

Positive values of BF would favour MLE1, and different values have different strengths. 
Values above five indicates that one model is significantly favoured over the other (Kass and Raftery 1995, Condamine et al. 2015), 
values above 20 indicate strong support and values above 150 overwhelming support.

## How to calculate the Marginal Likelihood?

https://www.beast2.org/model-comparison/ 

I used the Nested Sampling algorithm (Skilling 2006) implemented in the NS package version 1.0.4 (Russel et al. 2019) for BEAST2 version 2.5.1 
with 60 particles and 10,000 chain length. The NS package also calculates **the standard deviation (SD)** of the estimated Marginal Likelihood, 
which **allows us to have confidence in the BF values calculated**.

A tutorial for this package can be found here: https://taming-the-beast.org/tutorials/NS-tutorial/

https://github.com/BEAST2-dev/nested-sampling/wiki/How-to-use-NS

https://www.beast2.org/2018/09/19/nested-sampling.html

https://www.beast2.org/2018/10/01/nested-sampling2.html

and a useful Q&A: https://groups.google.com/g/beast-users/c/gNjLduwHvo4

A useful troubleshooting link: https://groups.google.com/forum/#!topic/beast-users/62P2CZduZG0

# Checking for differences in rates of evolution in each partition

Software:: PartitionFinder2 version 2.1.1 (Lanfear et al. 2017) using PhyML version 3.0 (Guindon et al. 2010) and the greedy search algorithm (Lanfearet al. 2012).


# Determining best fitting model of sequence evolution for each of the three partitions

## ML analysis :: PartitionFinder2 version 2.1.1 (Lanfear et al.2017) 

Tutorial here: http://www.robertlanfear.com/partitionfinder/tutorial/

One of mine `partition_finder.cfg` files:

```## ALIGNMENT FILE ##
alignment = ITS_clipped_from_all_regions_final_Ceiba_clade_17102018_chap01_noKB2_final_08122018.fasta-out.phy; # a typical file name of a PhD student!

## BRANCHLENGTHS: linked | unlinked ##
branchlengths = unlinked;

## MODELS OF EVOLUTION: all | allx | mrbayes | beast | gamma | gammai | <list> ##
models =  all;
# MODEL SELECCTION: AIC | AICc | BIC #
model_selection = aicc;

## DATA BLOCKS: see manual for how to define ##
[data_blocks]

its1 = 1 - 336;
58s = 337 - 495;
its2 = 496 - 780; 

## SCHEMES, search: all | user | greedy | rcluster | rclusterf | kmeans ##
[schemes]
search = greedy;

```


## Bayesian analysis :: reversible jump model selection (RB) implemented in BEAST2 version 2.5.1 (Bouckaert et al. 2019)

Link ot the package: http://www.beast2.org/features/substitution-model-reversible-jump.html



