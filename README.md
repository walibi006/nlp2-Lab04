This lab is mainly about data and model analysis. There is very little code. Make sure you send back a proper report with your code, guideline, annotated sheets, and theoretical answers.
Introduction (1 point)

Your company wants to sell a moderation API tackling toxic content on Twitter. They ask you to come up with a model which detect toxic tweets. You remember your NLP classes, and start looking for existing models or datasets, and find a collection of academic Twitter dataset on HuggingFace hub. Especially, the hate and offensive datasets seem close to what you are looking for.

    (1 point) Pick one of the datasets between hate and offensive, and justify your choice. Remember that it is for a commercial application (there is a good and a bad answer).

Evaluating the dataset (5 points)

Before using the data to train a model, you have the right reflex and start with a data analysis.

    (1 point) Describe the dataset. Look at the splits, proportion of classes, and see what you can figure out by just looking at the text.
    (3 points) Use BERTopic to extract the topics within the data, and the main topics within each class. Please, think about fixing the random seed.
        A good model for sentence similarity is all-MiniLM-L6-v2, as it is fast, light, and pretty accurate. You can use another one, but make sure to document your choice.
        This might help.
    (1 point) What do you think about the results? How do you think it could impact a model trained on these data?
    Bonus By default, BERTopic extracts single keywords. Play with the model to extract bigrams or more. See if you can go deeper in your analysis.

Evaluate a model (8 points)

You were thinking about fine-tuning a RoBERTa model on the dataset, but RoBERTa has been train on 2019 data, which do not include any tweet. Moreover, pretraining a model from scratch can be costly. Fortunately, a reliable entity pretrained RoBERTa on recent tweets and even fine-tuned it on both datasets here and here.

    (2 points) Evaluate their model on the test split of the dataset you picked, using precision, recall, and F1-score.
    (2 points) Look for prediction failures. Extract the top 5 misclassified tweets (highest score in wrong class) for each class and discuss what could be wrong with the model.

To see how the model would fare on production data, you have 10K English tweets and replies available on the tweets.json file (taken from internet archive). Note that the language was filtered using the Twitter API, so there might still be tweets in more than just English. The JSON fields were trimmed to minimum and the text was already preprocessed to mask user handles and URLs, like the tweets in your dataset.

    (2 points) Extract the top 10 tweets your model is most confident about in the target class (offensive or hateful), the top 10 in the neutral class, and the top 10 your model is most uncertain about. Do you believe the model is doing a great job?
    Bonus Use SHAP on the provided tweets, or manually written texts, to see if you can find topics on which the model is biased.
    (2 points) What are the advantages of using a pre-trained transformer vs naive Bayes?
        Think about training, and usage in production.
    Bonus Train a naive Bayes model on the data, and compare its results with this model.

Annotate data (7 points)

Regardless of the model's performances, you decide to annotate your own collection of tweets.

    (1 point) Extract about 100 tweets containing at least 20% of your target class (offensive/hateful), from the 10K tweets provided. You can use the pretrained model to help you find tweets in the target class.
    (3 points) Altogether, write down an annotation guildeline (which should be at least 2/3 of a page long).
        What does the target class look like?
        Any examples you could provide for ambiguous cases?
        Keep "Can't tell / not annotable" class. Make sure you document what this class mean in your guideline.
    (1 point) Every person in your group is going to annotate these tweets separately. So if you are 3, annotate them 3 times.
        Typically, create a Google sheet or an excel document, one tab per person, in each tab one column for the text, and annother on the class.
    (2 point) Evaluate your inter-annotaor agreement using Fleiss Kappa.
        statsmodel provide an easy to use implementation.
        What does the score mean? Are you doing a good job annotating the data and, if not, why?
    Bonus Iterate on your annotation guideline with what you learned. Please send both version in your report.
    Bonus Evaluate the model your data. Use a majority vote for labels (remove majority "can't tell") and compute the precision, recall, and F1-score.

Please provide the annotation sheets, the guideline, and the inter-annotator agreement in your report.
Evaluation

This lab is mainly about data and model analysis. There is very little code. Make sure you send back a proper report with your code, guideline, annotated sheets, and theoretical answers.

The assignment will be evaluated on the following criteria.

    A report answering the questions above, describing your technical choices, and analysing your results.
    The quality of your code (modularity, efficiency, comments, coding standards).

For coding standards, please respect the following guidelines

    Use docstring format to describe your functions and their arguments
    Use typing
    Have clear and verbatim variable names (not x, x1, x2, xx, another_x, ...)
    Make your results reproducible (force random seeds values)
    Don't hesitate commenting in details part of the code you consider complex or hard to read

Provide a README.md file with

    A short description of the project
    A description of the file/module architecture

This part has to be sent back to marc.von-wyl at epita dot fr before Thursday 22nd of June 2023 at 10pm.