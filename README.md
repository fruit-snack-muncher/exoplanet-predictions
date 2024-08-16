This is a data science project focused on using NASA database data regarding all observed, possible, and disproved
exoplanets. This database is available through CalTech as well. The comments within the notebook justify the decisions
I made, especially in preprocessing or hypertuning the models. 

When it comes to choosing data, there are two main response sets---the data from the Exoplanet Archive, and the one
From the Kepelr missions. The Kepler missions, not surprisngly, are basically a subset of the Exoplanet Archive. The 
EA (as I'll be referring to it) has a much more comprehensive set of data. Considering that our data set deals with 
exoplanets, which can be incredibly difficult to detect, we have a small data set of ~10,000 samples only. Furthermore,
many of the samples rely on incomplete data. Instead of imputing data, I chose to remove any samples with incomplete
data. Even then, the data set remained above 5,000 samples. Even after all this preprocessing our data was substantial 
enough to split the dataframe into test and train sets, and the complexity of our data justified using computationally
expensive models like a Random Forest Classifer.

After that, I split the data set into two distinct dataframes. The first contained only FALSE POSITIVE or CONFIRMED 
results---i.e. exoplanets that definitely do or do not exist. The second contained only CANDIDATE results---i.e. exo-
planets whose existence have not been proven nor disproven. I did a standard test-train split on the first dataframe,
and I trained and tested my Random Forest model using that dataframe. Then, I predicted the results for the second data-
frame, effectively offering my predictions on whether or not those CANDIDATE planets were exoplanets or not.

Once my Random Forest model was completed, I created a small piece of code using lightkurve's handy algorithms. That 
program displays a multi-quarter light curve for any exoplanet based on its Kepler ID. I tested the code on several of
the CANDIDATE exoplanets, and the some of the data suggests stars were the light dips significantly, briefly, and perio-
dically---three characteristics common to a transit.
