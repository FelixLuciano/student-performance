[Fábio Ayres, Dr.](http://lattes.cnpq.br/6229400946752974). Machine Learning. [Insper](https://github.com/Insper), 2024.

# Student Performance

This is the project of a regression model on a dataset of final grades of
elementary school students in relation to socio-environmental parameters.

## Dataset Information

This data approach student achievement in secondary education of two Portuguese
schools. The data attributes include student grades, demographic, social and
school related features) and it was collected by using school reports and
questionnaires. Two datasets are provided regarding the performance in two
distinct subjects: Mathematics (mat) and Portuguese language (por). In [Cortez
and Silva, 2008], the two datasets were modeled under binary/five-level
classification and regression tasks. Important note: the target attribute G3 has
a strong correlation with attributes G2 and G1. This occurs because G3 is the
final year grade (issued at the 3rd period), while G1 and G2 correspond to the
1st and 2nd period grades. It is more difficult to predict G3 without G2 and G1,
but such prediction is much more useful (see paper source for more details).

Cortez,Paulo. (2014). Student Performance. UCI Machine Learning Repository.
https://doi.org/10.24432/C5TG7T.

| column     | description                                                                                                                                      |
| :--------- | :----------------------------------------------------------------------------------------------------------------------------------------------- |
| school     | Student's school (binary: "GP" - Gabriel Pereira or "MS" - Mousinho da Silveira)                                                                 |
| sex        | Student's sex (binary: "F" - female or "M" - male)                                                                                               |
| age        | Student's age (numeric: from 15 to 22)                                                                                                           |
| address    | Student's home address type (binary: "U" - urban or "R" - rural)                                                                                 |
| famsize    | Family size (binary: "LE3" - less or equal to 3 or "GT3" - greater than 3)                                                                       |
| Pstatus    | Parent's cohabitation status (binary: "T" - living together or "A" - apart)                                                                      |
| Medu       | Mother's education (numeric: 0 - none, 1 - primary education (4th grade), 2 – 5th to 9th grade, 3 – secondary education or 4 – higher education) |
| Fedu       | Father's education (numeric: 0 - none, 1 - primary education (4th grade), 2 – 5th to 9th grade, 3 – secondary education or 4 – higher education) |
| Mjob       | Mother's job (nominal: "teacher", "health" care related, civil "services" (e.g. administrative or police), "at_home" or "other")                 |
| Fjob       | Father's job (nominal: "teacher", "health" care related, civil "services" (e.g. administrative or police), "at_home" or "other")                 |
| reason     | Reason to choose this school (nominal: close to "home", school "reputation", "course" preference or "other")                                     |
| guardian   | Student's guardian (nominal: "mother", "father" or "other")                                                                                      |
| traveltime | Home to school travel time (numeric: 1 - <15 min., 2 - 15 to 30 min., 3 - 30 min. to 1 hour, or 4 - >1 hour)                                     |
| studytime  | Weekly study time (numeric: 1 - <2 hours, 2 - 2 to 5 hours, 3 - 5 to 10 hours, or 4 - >10 hours)                                                 |
| failures   | Number of past class failures (numeric: n if 1<=n<3, else 4)                                                                                     |
| schoolsup  | Extra educational support (binary: yes or no)                                                                                                    |
| famsup     | Family educational support (binary: yes or no)                                                                                                   |
| paid       | Extra paid classes within the course subject (Math or Portuguese) (binary: yes or no)                                                            |
| activities | Extra-curricular activities (binary: yes or no)                                                                                                  |
| nursery    | Attended nursery school (binary: yes or no)                                                                                                      |
| higher     | Wants to take higher education (binary: yes or no)                                                                                               |
| internet   | Internet access at home (binary: yes or no)                                                                                                      |
| romantic   | With a romantic relationship (binary: yes or no)                                                                                                 |
| famrel     | Quality of family relationships (numeric: from 1 - very bad to 5 - excellent)                                                                    |
| freetime   | Free time after school (numeric: from 1 - very low to 5 - very high)                                                                             |
| goout      | Going out with friends (numeric: from 1 - very low to 5 - very high)                                                                             |
| Dalc       | Workday alcohol consumption (numeric: from 1 - very low to 5 - very high)                                                                        |
| Walc       | Weekend alcohol consumption (numeric: from 1 - very low to 5 - very high)                                                                        |
| health     | Current health status (numeric: from 1 - very bad to 5 - very good)                                                                              |
| absences   | Number of school absences (numeric: from 0 to 93)                                                                                                |
| grade      | Final grade on Mathematics (numeric: from 0 to 20, output target)                                                                                |

## Project description

The project has two parts: initial modeling, and model with data filtering.

### Phase 1

In the initial part, you must:

- Perform _feature engineering_ as needed
  - For example: encoding categorical variables with `OneHotEncoding`
  - Don't remove _outliers_ here: we'll do that in the next section
- Build three regression models:
  - A model using the
    [`DummyRegressor`](https://scikit-learn.org/stable/modules/generated/sklearn.dummy.DummyRegressor.html)
    regressor from scikit-learn that will serve as a "trivial regressor" for us.
  - A `Ridge` model.
  - Any other model of your choice. As the teacher is a saint, the first two are
    already implemented for you! Then all that remains is to choose the third
    one.
- Adjust model hyperparameters. The example code already shows how to adjust the
  initial models, you specify the test parameter grid for your third model.
- Compare model performances appropriately. Study the
  [material at scikit-learn](https://scikit-learn.org/stable/auto_examples/model_selection/plot_grid_search_stats.html)
  to learn how to perform a correlation-compensation t-test of model
  performances in a cross-validation scenario.
- Chosen the best model, train it on the training set and measure performance on
  the test set, to estimate the generalization performance of the model.
- Write your conclusions regarding what was learned correctly from the model,
  for example:
  - What are the consequences of the performance of the final model for
    estimating the final grades?
  - Which features are most important in determining the final grade estimate?
    Note that this question may or may not have an answer, depending on the
    capabilities of the regression models you choose.

### Phase 2

Now perform a filtering of the training data to remove abnormal values. For
example:

- Remove students who had a final grade of zero
- Remove students who are absent too much - define for yourself what "missing
  too much" is

Redo the phase 1 process for this filtered data.

### Rubric

The items to be evaluated in the project are:

1. `FEAT` – Do feature engineering properly;
2. `HYPER` – For each model, adjusted hyperparameters appropriately;
3. `MODEL` – Properly trained and compared models to select the best model;
4. `PERF` – Model performance analysis. NO SPECIFIC PERFORMANCE WILL BE
   REQUIRED, THIS IS NOT A PERFORMANCE COMPETITION;
5. `FILT` - Perform phase 2: adequate data filtering and repeating the
   experiment;

### Grading

- I – Insufficient: Did not deliver, or delivered bullshit;
- D – In development: One of `FEAT`, `MODEL`, `PERF` was missing;
- C – Minimum acceptable: Made `FEAT`, `MODEL`, `PERF`;
- B – Expected: Achieved grade C but also `HYPER`;
- A – Exceptional: Achieved grade B but also `FILT`.
