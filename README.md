# Self-confidence: Is there significant evidence that women and men express themself differently regarding assurance ?

Previous researchers have analyzed the influence of gender on self-confidence, and results show men tend to have higher self-confidence than women: this phenomenon has been dubbed the “Confidence Gap”. Studies showed that women usually underestimate their abilities, often experiencing “Imposter Syndrome”, where a person thinks they do not deserve their position and expect to be discovered for their incompetence at any time. We aim to determine whether this “Confidence Gap” is observable through verbal expression of the speakers in the Quotebank database. Following this, we will look at whether profession could influence confidence, at least based on speakers’ verbal expressions. We are thus interested in comparing the self-confidence of women that are at US Congress and those that are not. Focus on a single gender should allow us to solely observe any profession-related variations. If relevant, an confidence analysis on a variety of professions (all genders comprised) could be interesting.

For this project, we will analyse the provided data and ultimately try to answer to the following interrogations: 

Is there a difference in the expression of confidence between men and women?
What are the most used phrases or expressions by confident vs less confident speakers?
Does profession involving rhetoric influence results as well?

In addition to the quotation-centric Quotebank data, we will use the additional information on speakers and the QID label descriptions provided by the ADA teaching staff.

N.B : The article on which we are going to extract these confidence-relating phrases and on which we will base the comparison will be provided on the team’s GitHub.

To perform this analysis, we already pre-processed the data (ref. Notebook provided on the GitHub) in order to extract only the relevant information, namely speaker name, qID, quotation, gender, … 

The next step will consist of analyzing the quotes for each speaker and assigning a score for each quote, which will help establish an overall confidence score for each speaker. To do this, we will look to use machine learning methods, namely natural-language processing (NLP). The initial process would be to, first, establish a “confidence coefficient” for key words or phrases such as “I believe”, “I am sure”, “I promise”, and more. Using this library and with the help of open-source machine learning APIs such as TensorFlow, we will then be able to tokenize the words of each quotation, evaluate each word’s “confidence” and determine an overall confidence value for each quotation. Following this preliminary score calculation, NLP is also capable of analysing the syntactic structure of the quotes, when provided with an initial set of rules to abide by,  and we could thus weight the overall score of a given quote as a function of its syntax. For example, imperative sentences could be weighted with more significance than declarative sentences. This syntactic analysis should also include punctuation as a key criterion. Indeed, quotes containing ellipses or exclamation marks can also be considered signs of varying confidence between speakers.

After this text analysis, as mentioned previously, we will associate a value to each quotation according to our reference article. Those values will further be used to compute a confidence score for each speaker.
In order to calculate the score that is more meaningful instead of just taking all their quote values and averaging them, one possibility could be to perform a non-parametric bootstrap. We will compute several scores using multiple subsets of quotations per speaker, and then average these scores to produce our final confidence score per speaker.

Once we computed a meaning score per speaker, our idea was to generalize the score to every quote without confident-referring words of the same speaker, supposing that even if there is no specific word relating to confidence, the speaker might be equally confident.

Considering the speaker for whom it was impossible to compute a score e.g. because no words were recognized by our algorithm, we will perform a comparison with already scored quotes based on confidence-related vocabulary. The idea would be to constitute a list of keywords that contribute to high confidence scores, extracted from quotes enounced by highly confident speakers. We will then use this library to parse the quotes of non-scored speakers and determine their respective confidence.


To make sure we properly quantify the uncertainties, we will follow the statistical significance of our score by performing constant analysis of the deviation, and will provide confidence intervals for every score computed. Several tests will also be performed to assess if the means are comparable (Students’ t-tests). Additionally to p-values, we will also compute the effect size (Cohen’s d).


Given that we are 5 weeks away from the deadline of M3, we will first spend the two first weeks focusing on generating the ‘score’. This will include implementation of NLP-relative methods (tokenisation, syntax analysis, …) as well as a correct bootstrapping. Then, we will find a way of comparing non-scored speakers with scored ones, in order to have a fully scored set of speakers. In parallel, we will also generate every confidence interval associated with the newly produced data. 
Once every score is available, we will spend one week using these scores to assess the questions of interest listed above, this will involve several tests, and eventually additional secondary studies which could provide supplementary explanations for our results.
The last two weeks, we will be focusing on optimizing and cleaning the code, making sure that the code is well enough documented, creating great, powerful and meaningful visualisations of the results as well as writing our data story.

## Questions to ask the TAs

Statistics:
We know that we have to make sure that propensity score should be balanced overall : it shoudln't be a problem for the principal analysis ie men vs. women. However, is it meaningful in this case where the "treatment" is being a man or a woman, as there are no observed covariated linked to it?

Bootstrapping:
Are there conditions necessary for using bootstrap resampling? 
Indeed, we have seen instances of debates on how accurate bootstrapping is when considering small samples. We have not yet looked at the entire data set but it would not be surprising to have to deal with a very small sample.

