# Traffic Police Consultants
## Executive Summary

### Problem Statement:
	
	Reddit has suffered an internal attack by a disgruntled ex-employee.  As a parting gift,
	the ex-employee left the company by replacing all subreddit fields with " ¯\_(ツ)_/¯ ".
	As dedicated Data Analysts, we will build a classification model that can sort certain subreddits
	into two hats.  Without the subreddit fields being assigned, the links do not work.  
		With a classification model, Reddit will be able to get started on re-assigning the
	fields of each post, at which point the subreddit links will populate and 
	be functional again.
		How successful our model is, of course, will determine whether or not it saves time.
	To measure the effectiveness of the different models we build, we will measure each model's
	accuracy (correct classifications made divided by all classifications made).
		Before building any models, though, we must: first, retrieve the data; second, clean
	and format the data; and third, vectorize the cleaned text columns (to allow them to be
	included as features in the models).  The subreddits we have selected are the Mario Party
	and the Super Smash Ultimate subreddits, two relatively young, active, and present (the
	two games were very recently released) subreddits.  We will be using two different methods
	of vectorization: CountVectorize and TF-IDF.
		After retrieving, cleaning, and vectorizing the data, we will remove certain columns,
	including the 'target' column, of course, from a 'features' list.  This list, as implied,
	will contain a list of the columns to be included in the model as a feature and
	therefore constitute our X's.  Our 'target' column, which contains a binary value of 0 
	or 1 (0 representing that the post came from the Super Smash Ultimate subreddit and 1 
	representing that the post came from the Mario Party subreddit), will be used as our y.
		Next, we will split the dataset into two: a training set, and a testing set.  By using
	sklearn's train_test_split, we can check the results of our model when run on 'unseen' data,
	giving ourselves a more realistic reading on the model's effectiveness.
		Finally, we will run our data through the modeling process.  We will use four different
	classification models: 1. Logistic Regression; 2. K Nearest Neighbors; 3. Random Forests;
	and 4. Extra Trees.  After running each model, we will also run the model through a gridsearch,
	testing different paramaters for each model to further evaluate how well a model could perform.
		Once all models have ran, we will evaluate their accuracy scorings, find the strongest
	performing model and declare it the model most worth pursuing further.
		While we continue to improve our model, though, our hope is that reddit would
	partner with us and use our model to help sort their subreddits.  After all, the reddit team
	knows their product best and would be able to help us most when trying to improve our model.
	
	
### Conclusions and Recommendations:

	What we found was that our best performing model was Logistic Regression.  We Gridsearched
	it and some of the parameters that resulted were: C = 1.0; penalty = Ridge; tolerance = 0.0001.
		We believe the subreddits may not have had as much overlap as we initially expected; i.e.,
	the subreddits were more different from each other and therefore were easier to classify.
	With this being the case, we decided to handicap the model, in a sense, by removing certain
	words from being vectorized (the words found in the subreddits' titles, like Mario, Party, Super,
	Smash, etc.).  We also removed the post authors from the features; we did not want our model to
	be even partially dependent on this post trait because these two subreddits are relatively young
	and therefore may have concentrated groups of authors, making them a giveaway in this case alone.
	Ideally, our model can work on subreddits that older/have more diverse pools of authors,
	so when building our model, we removed the column entirely from the features.
		After handicapping the model, though, the results were still strong, with our best model
	having a Train Set Accuracy Score of .999 and a Test Set Accuracy Score of .950.  We also had a
	strong performing Extra Trees model, and its number of trees turned out to be 10, implying that
	not many features were needed to build a strong model (at least with this particular dataset).
		Of course, we would love to see how our models work on different pairs of subreddits and
	compare results.  Does our model work well on the MARIOPARTY/SuperSmashUltimate subreddits,
	or does it also work well on other subreddit pairs?  We'd like to find out.
	
	We recommend that reddit use our model on the MARIOPARTY/SuperSmashUltimate subreddits!
	The model seems to work well, at least on this data set, and may work well on others.
		Although our model seems to be very strong, it cannot guarantee 100% accuracy, therefore
	we have a second suggestion: add a "Misplaced Post" button so that users may suggest a post
	as being in the wrong subreddit.  This way, even if a post is misclassified, it can be rectified.

	