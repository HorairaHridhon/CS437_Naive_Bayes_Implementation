# Naïve Bayes Classifier: Zoo Dataset

This project is an implementation of a Bernoulli Naïve Bayes Classifier applied to a dataset of animals with their features. The goal is to classify animals into one of seven categories (e.g., mammal, bird, reptile) based on their binary and categorical features.

---

## Dataset
The dataset used for this project is `zoo.csv`, which contains information about various animals and their features. The last column, `class_type`, represents the animal category, numbered from 1 to 7. An additional file, `class.csv`, provides the mapping of these numbers to animal categories.

### Sample Rows from `zoo.csv`
```
animal_name  hair  feathers  eggs  milk  airborne  aquatic  predator  toothed  backbone  breathes  venomous  fins  legs  tail  domestic  catsize  class_type
   aardvark     1         0     0     1         0        0         1        1         1         1         0     0     4     0         0        1           1
   antelope     1         0     0     1         0        0         0        1         1         1         0     0     4     1         0        1           1
       bass     0         0     1     0         0        1         1        1         1         0         0     1     0     1         0        0           4
       bear     1         0     0     1         0        0         1        1         1         1         0     0     4     0         0        1           1
       boar     1         0     0     1         0        0         1        1         1         1         0     0     4     1         0        1           1
```

### Mapping from `class.csv`

Below is the mapping of class numbers to animal categories, along with the number of species in each category and examples of animals belonging to that category.

| Class Number | Class Type   | Number of Species | Example Animal Names                        |
|--------------|--------------|-------------------|---------------------------------------------|
| 1            | Mammal       | 41                | aardvark, antelope, bear, boar, buffalo, ...|
| 2            | Bird         | 20                | chicken, crow, dove, duck, flamingo, ...    |
| 3            | Reptile      | 5                 | pitviper, seasnake, slowworm, tortoise, ... | 
| 4            | Fish         | 13                | bass, carp, catfish, chub, dogfish, ...     |
| 5            | Amphibian    | 4                 | frog, frog, newt, toad                      |
| 6            | Bug          | 8                 | flea, gnat, honeybee, moth, ...             | 
| 7            | Invertebrate | 10                | clam, crab, lobster, octopus, ...           | 

---

## Methodology
1. **Data Preparation**:
    - The dataset is split randomly into a training set (70% of data) and a test set (30% of data).
    - Only the binary features and `legs` column are used for classification. The `name` and `class_type` columns are excluded from feature calculations.

2. **Model Implementation**:
    - Conditional probabilities are calculated based on the training set.
    - Laplace smoothing with an alpha value of 0.0001 is applied to avoid zero probabilities.
    - The classifier calculates posterior probabilities for each class and assigns the most probable class to each test instance.

3. **Evaluation**:
    - The test set is used to evaluate the classifier's performance, and the output is compared to the true `class_type`.
    - Accuracy is calculated, and predictions are marked as either `CORRECT` or `wrong`.

---

## Output Format
The classifier outputs results in CSV format, showing:
- Features of the animal.
- Predicted class.
- Probability of the predicted class.
- Whether the prediction was correct (`CORRECT` or `wrong`).

### Sample Output
```
animal_name  hair  feathers  eggs  milk  airborne  aquatic  predator  toothed  backbone  breathes  venomous  fins  legs  tail  domestic  catsize  class_type  predicted  probability correct?
    buffalo     1         0     0     1         0        0         0        1         1         1         0     0     4     1         0        1           1          1     1.000000  CORRECT
       carp     0         0     1     0         0        1         0        1         1         0         0     1     0     1         1        0           4          4     0.999955  CORRECT
    catfish     0         0     1     0         0        1         1        1         1         0         0     1     0     1         0        0           4          4     1.000000  CORRECT
    cheetah     1         0     0     1         0        0         1        1         1         1         0     0     4     1         0        1           1          1     1.000000  CORRECT
       crab     0         0     1     0         0        1         1        0         0         0         0     0     4     0         0        0           7          7     1.000000  CORRECT
```

---

## Files in the Repository
- `naive_bayes_implementation.ipynb`: Jupyter Notebook with the implementation.
- `zoo.csv`: Main dataset containing animal features.
- `class.csv`: Mapping of `class_type` to animal categories.
- `output.csv`: Example of the expected output format.

---

## Requirements
The project requires Python and the following libraries:
- pandas
- math

To install the dependencies, run:
```
pip install pandas
```

---

## Observations
- The choice of alpha for Laplace smoothing affects accuracy. An alpha value of 0.0001 was used.
- The classifier achieves an accuracy of over 83% consistently, as per the project requirements.

---

## License
This project is licensed under the MIT License.

---

## Acknowledgments
- Dataset Source: [Kaggle - Zoo Animal Classification](https://www.kaggle.com/datasets/uciml/zoo-animal-classification)
- Instructions provided by the course professor.
