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
```
 Class_Number  Number_Of_Animal_Species_In_Class Class_Type                                                                                                                                                                                                                                                                                                                        Animal_Names
            1                                 41     Mammal aardvark, antelope, bear, boar, buffalo, calf, cavy, cheetah, deer, dolphin, elephant, fruitbat, giraffe, girl, goat, gorilla, hamster, hare, leopard, lion, lynx, mink, mole, mongoose, opossum, oryx, platypus, polecat, pony, porpoise, puma, pussycat, raccoon, reindeer, seal, sealion, squirrel, vampire, vole, wallaby, wolf
            2                                 20       Bird                                                                                                                                                                                chicken, crow, dove, duck, flamingo, gull, hawk, kiwi, lark, ostrich, parakeet, penguin, pheasant, rhea, skimmer, skua, sparrow, swan, vulture, wren
            3                                  5    Reptile                                                                                                                                                                                                                                                                                     pitviper, seasnake, slowworm, tortoise, tuatara
            4                                 13       Fish                                                                                                                                                                                                                                 bass, carp, catfish, chub, dogfish, haddock, herring, pike, piranha, seahorse, sole, stingray, tuna
            5                                  4  Amphibian                                                                                                                                                                                                                                                                                                              frog, frog, newt, toad
```

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
This project follows the DbCL license for the dataset, as per [opendatacommons.org/licenses/dbcl/1-0](https://opendatacommons.org/licenses/dbcl/1-0).

---

## Acknowledgments
- Dataset Source: [Kaggle - Zoo Animal Classification](https://www.kaggle.com/datasets/uciml/zoo-animal-classification)
- Instructions provided by the course professor.
