# ML_HappyDevelopers
Retaining software engineers in today's ultra-competitive job market is vital to the success of today's technology companies. Using the Stack Overflow 2018 Developer Survey, what are the key predictors of job satisfaction? 

# Data Source
The data source for this exploration is the Stack Overflow 2018 survey results, hosted on <a href="https://www.kaggle.com/stackoverflow/stack-overflow-2018-developer-survey">Kaggle</a>

This dataset contains 129 columns and includes responses from roughly 100,000 developers located across the world.

# Target Variable
In the Stack Overflow 2018 survey, there's a column called <i>JobSatisfaction</i> which contains the following values:
<ul>
  <li>Extremely satisfied (12.6%)</li>
  <li>Moderately satisfied (26.3%)</li>
  <li>Slightly satisfied (10.1%)</li>
  <li>Neither satisfied nor dissatisfied (5.0%)</li>
  <li>Slightly dissatisfied (7.1%)</li>
  <li>Moderately dissatisfied (6.4%)</li>
  <li>Extremely dissatisfied (2.5%)</li>
  <li>NA (29.9%)</li>
</ul>

I wanted to explore which combination of job variables would have a positive correlation towards someone being extremely satisfied in their present role.

Because <i>JobSatisfaction</i> is going to be used in our target variable, I needed to drop survey responses where <i>JobSatisfaction</i> was NA. 

Initially, I included all non-NA records in my exploration, but I quickly found that there wasn't enough contrast between respondants who answered that they were extremely satisfied with their jobs vs those who were moderately or slightly satisfied. 

To create the largest possible contract, I kept only survey results in which the developer answered that they were extremely satisfied, moderately dissatisfied, or extremely dissatisified in my training and test sets.

# Key Challenges
Aside from the many NA responses for <i>JobSatisfaction</i> other challenges include:

<ol>
  <li>Most of the responses were categorical variables that would require one-hot encoding</li>
  <li>Most of the questions were optional, so there were many sparse or empty values to deal with</li>
  <li>Many of the categorical variables were further complicated by being multi-select. For example, a developer could select multiple languages that they work with any this would be represented as a semi-colon delimited value in the survey response. Example: JavaScript;Python;CSS</li>
  <li>After parsing multi-select categorical variables and one-hot encoding everything, we were left with over 900 features</li>
</ol>

# Feature Selection / Modeling / Results
The following video describes the process of feature selection, creating a random forest model, and the results of that model.

# Conclusion
Determining key indicators of developer job satisfaction from the StackOverflow 2018 survey results was very difficult, as I believe there were factors not asked as part of the survey that contributed to how respondants felt about their jobs. Because of this, the model could only make correct predictions 67% of the time, with an 82% recall, but only a 67% precision.

Based on the random forest model that was created, the following features appeared to be the most important:
<ol>
  <li>Whether or not the developers contribute to open-source projects</li>
  <li>Whether or not developers love the industry they're currently working in</li>
  <li>The ability to work from home or work remotely</li>
  <li>Developers new to their job (within the last year) appeared to be happiest</li>
</ol>

Surprisingly, salary did not appear to be a major contributing factor towards job satisfaction.
