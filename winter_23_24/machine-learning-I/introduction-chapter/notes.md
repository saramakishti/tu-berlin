## Introduction

**Pattern recognition - the act of taking in raw data and taking an action based on the 'category' of the pattern.**

Let's take the example of sorting fish on a conveyor belt: salmon vs sea bass.
There are certain differences between these two types of fish such as: length, lightness, width, number and shape of fins, position of mouth etc. Given that there are these differences between the population of sea bass and salmon, we view them as having different _models_ - which are typically mathematical in form.

_The goal and approach in patten recognition is to hypothesize the class of these models, process the sensed data to eliminate noise (not due to the models) and for any sensed pattern choose the model that corresponds best._

The system usually follows these steps:

1. The camera captures the image of the fish
2. The camera signals are _preprocessed_ to simplify subsequent operations without loosing important information.
3. Using a _segmentation_ operation in which the images of different fish are somehow isolated from one another and from the background.
4. The information from a single fish is sent to a _feature extractor_, whose purpose is to reduce the data by measuring different 'features' or 'properties'.
5. These features (or the values of these features) are then passed to a _classifier_ that evaluates the evidence presented and makes a final decision as to the species.

We can choose the _length_ of the fish to be an obvious classification feature: sea bass has a greater length than salmon. So we can classify by seeing whether or not the length _l_ of a fish exceeds some critical value _l_ *. To choose *l\* * we could obtain some *design* or *training sample\* of the different types of fish, make length measurements and inspect the results.

The data we gathered (presented in a histogram) shows the disappointing result that although the sea bass are longer on average, using length a single classification criteria can lead to errors - no matter how we choose _l_ \*.

So we introduce another feature: the average lightness of the fish scales. The resulting histogram is much more satisfactory and the classes are better separated.

We can assume that the consequences of our actions are equally costly: deciding the fish was a sea bass when in fact it was a salmon was just as undesirable as the converse. Such a symmetry in the _cost_ is often, but not invariably the case. Then the author brings up the case that customers wouldn't mind pieces of salmon in a can labeled 'sea bass' but would object to having pieces of sea bass in a can labeled 'salmon'. So in this case, we need to reduce our decision boundary _x_ \* to smaller values of lightness, reducing the number of sea bass that are classified as salmon.

*The more our customers object to getting sea bass with their salmon - the more costly this type of error - the lower we should set the decision threshold *x\* \*.

**Decision Theory:** Such considerations suggest that there is an overall single cost associated with our decision and our true task is to make a decision rule (set a decision boundary) so as to **minimize** such a cost.

To improve recognition, we must resort to the use of _more_ than one feature at a time.

We can use two features for classifying fish such as:

- x1 = the lightness
- x2 = the width

So we can construct a _feature vector x_ in a two-dimensional _feature space_ where: x = [x1, x2]

If we measure the feature vectors for our samples and construct the scattering diagram, we can follow this rule for separating the fish:

> Classify the fish as sea bass if its feature vector falls above the _decision boundary_ and as salmon otherwise.

We may include more features to separate our samples, but how do we know which of these features will work best?

- Some features might be redundant
- Some features may be too expensive or too expensive to measure

The central aim for designing a classifier is to suggest actions when presented with _novel_ patterns, fish not yet seen. This is the issue of _generalization_.

We need a clear decision boundary and even by increasing the training data, the decision boundary would still be very complicated.

We might be satisfied with the slightly poorer performance on the training samples if it means that our classifier will have better performance on novel patterns.

Central problems in statistical pattern recognition:

- How should we quantify and favor simpler classifiers?
- How would our system automatically determine that the simple curve is a better decision boundary than a complicated one or a straight line?
- Can we predict how well our system will generalize to new patterns?

Different decision tasks may require different features and yield boundaries quite different from those useful for our original categorization problem.

Our decisions are fundamentally task or cost specific and that creating a single _general purpose_ artificial pattern recognition device is a very difficult challenge.

Since classification is, at base, the task of recovering the model that generated the
patterns, different classification techniques are useful depending on the type of candidate models themselves.

> In statistical pattern recognition we focus on the statistical
> properties ofthe patterns (generally expressed in probability densities).

A central aspect in virtually every pattern recognition problem is that
of achieving such a "good" representation, one in which the structural relationships among the components is simply and naturally revealed, and one in which the true (unknown) model ofthe patterns can be expressed.

The extent to which we create or learn a proper representation and how we quantify near and far apart will determine the success ofour pattern classifier.

A central technique, when we have insufficient training data, is to incorporate knowledge of the problem domain. Indeed the less the training data the more important is such knowledge, for instance how the patterns themselves were produced. One method that takes this notion to its logical extreme is that of _analysis by synthesis_, where in the ideal case one has a model of how each pattern is generated.

**Pattern classification vs. hypothesis testing**

Hypothesis testing might be used to determine whether the fish on the conveyor belt belong to a single class (the null hypothesis) or from two classes (the alternative). In contrast, given some data, pattern classification seeks to find the most probable hypothesis from a set of hypotheses — "this fish is probably a salmon."

**Pattern classification vs. image processing**

In image processing, the input is an image and the output is an image. Image processing steps often include rotation, contrast enhancement, and other transformations which preserve all the original information. Feature extraction, such as finding the peaks and valleys of the intensity, lose information (but hopefully preserve everything relevant to the task at
hand.) As just described, feature extraction takes in a pattern and produces feature values.

> Because of the crucial role of a decision in pattern recognition information, it is fundamentally an information reduction process.

**Sub-problems of pattern classification**

1. Feature extraction: the task of feature extraction is much more problem and domain dependent than is classification proper, and thus requires knowledge of the domain.

2. Noise: any property of the sensed pattern due not to the true underlying model but instead to randomness in the world or the sensors.

3. Overfitting: while an overly complex model may allow perfect classification of the training samples, it is unlikely to give good classification of novel patterns — a situation known as overfitting.

4. Model Selection: how do we know when a hypothesized model differs significantly from the true model underlying our patterns, and thus a new model is needed?

5. Prior Knowledge: in some applications the knowledge ultimately derives from information about the production of the patterns, as we saw in analysis-by-synthesis. In others the knowledge may be about the form of the underlying categories, or specific attributes of the patterns, such as the fact that a face has two eyes, one nose, and so on.

6. Missing Features: since our two-feature recognizer never had a single-variable threshold value x∗ determined in anticipation of the possible absence of a feature, how shall it make the best decision using only the feature present?

7. Mereology: the problem of subsets and supersets - how do we recognize or group together the "proper" number of elements — neither too few nor too many?

8. Segmentation: in our fish example, we have tacitly assumed that the fish were isolated, separate on the conveyor belt. In practice, they would often be abutting or overlapping, and our system would have to determine where one fish ends and the next begins — the individual patterns have to be segmented. If we have already recognized the fish then it would be easier to segment them. But how can we segment the images before they have been categorized or categorize them before they have been segmented? It seems
   we need a way to know when we have switched from one model to another, or to know when we just have background or “no category.”

9. Context: use context — input-dependent information other than from the
   target pattern itself— to improve our recognizer.

10. Invariances: absolute position of fish in the belt, the orientation of fish (vertical or horizontal) etc aare irrevelant to the category of the fish. How do we determine whether an invariance is present? How do we efficiently incorporate such knowledge into our recognizer?

11. Evidence Pooling: We might imagine that we could do better if we had several component classifiers. If these categorizers agree on a particular pattern, there is no difficulty. But suppose they disagree. How should a "super" classifier pool the evidence from the component recognizers to achieve the best decision?

12. Costs & Risks: classification error - what percentage of new patterns are called the wrong category.

13. Computational Complexity: how an algorithm scales as a function of the
    number of feature dimensions, or the number ofpatterns or the number of categories. What is the tradeoff between computational ease and performance?

**Learning and Adaptation**

Learning refers to some form of algorithm for reducing the error on a set of training data. A range of _gradient descent_ algorithms that alter a classifier’s parameters in order to reduce an error measure now permeate
the field of statistical pattern recognition.

1. Supervised learning: provided is a category label or cost for each pattern in a training set, and we seek to reduce the sum of the costs for these patterns.
2. Unsupervised learning: the system forms clusters or "natural groupings" of the input patterns. "Natural" is always defined explicitly or implicitly in the clustering system itself, and given a particular set of patterns or cost function, different clustering algorithms lead to different clusters.
3. Reinforcement learning: The most typical way to train a classifier is to present an input, compute its tentative category label, and use the known target category label to improve the classifier. In _reinforcement learning or learning with a critic_, no desired category signal is given; critic
   instead, the only teaching feedback is that the tentative category is right or wrong. This is analogous to a critic who merely states that something is right or wrong, but does not say specifically how it is wrong.

These sub-problems are rarely addressed in isolation and they are invariably interrelated.

**Interesting reading materials: Bibliography in Introduction chapter**
