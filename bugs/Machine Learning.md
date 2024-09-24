# Machine Learning
1. handle non-numeric data
   
   use [label encoder](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.LabelEncoder.html) or [one hot encoding](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.OneHotEncoder.html) for encoding categorical variables

2. logistic regression not converge

    The dataset given may be highly imbalanced and need to [under sample the majority class](https://imbalanced-learn.org/stable/references/generated/imblearn.under_sampling.RandomUnderSampler.html) to make the dataset balanced