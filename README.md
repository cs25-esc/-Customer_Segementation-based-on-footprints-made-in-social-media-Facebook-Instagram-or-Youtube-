# Customer_Segmentation-based-on-footprints-made-in-social-media-Facebook-Instagram-or-Youtube


firstly i have imported the social media interactions data from kaggle.
containing some features like timestamp , personid , content id , engagements that they have made for each content , and some features that i felt unnessescary.

i just want to segement the persons by clustering them based on the similar content engagements.

in the event type column i have observed the engagements were 5 kinds VIEW LIKE BOOKMARK COMMENT CREATED FOLLOW.
initially i thought of assigning value 1 to each engagement but later i realised that :

but the views , likes , comments , follow and bookmark are different kinds of engagements i.e, follow >> viewing or liking
so i have decided to add some weights to the engagements -- view < like < comment < follow < bookmark

i have assigned weights like - {'VIEW' : 1 , 'LIKE' : 2 , 'COMMENT CREATED' : 3, 'FOLLOW' : 4 , 'BOOKMARK' : 5 }.

then i have grouped based on the [personid,conrentid] -- sum of events for each unique pair of personid and contentid.

now i have pivoted the content id as columns and person id as index and eventtype sum at mapping each unique pair of personid and contentid.

we now at 1895 rows × 2987 columns

i have used Kmeans clustering with 1 to 100 clusters without any dimensionality reduction to find the optimal number of clusters.
by elbow method i have observed less than 10 clusters is fine.

for 20 kmeans clusters - then i have used the pca to reduce the dimensions and i have iterated 100 to 1000 pca components and observed that 100 components giving the better results.

for 20 clusters - then i have again used pca to reduce the dimensions and iterated over 10 to 100 pca components and observed that 10 components are giving the better results.

for 20 clusters - then i have again used pca to reduce the dimensions and iterated over 1 to 15 pca components and observed that 2 components are giving the better results. with 3 clusters.

the finally finalised 3 clusters with 2 pca components.

ty
