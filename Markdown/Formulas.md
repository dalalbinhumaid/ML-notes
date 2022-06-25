# Formulas
Wed, 08 Jun 2022 at 02:48

## Text Analysis

#idf #search #tf-idf #recall #percision
#### Term Frequency
$$ tf(t,d) = count(t,d)$$
#### Inverse Document Frequency
$$ idf(t) = log_{10}{(\dfrac{N}{df(t)})} $$
> Where $df(t)$ is the number of documents that contain the term $t$

#### Term Frequency - Inverse Document Frequency

$$ tfidf(t,d) = tf(t,d) \times idf(t)$$

#### Document Relevance
$$ relevance(d) = \sum_{i=0}{tfidf(t_i, d)}$$
## Logistic Regression
#logit #link #function #odds-ratio
$$P(event) = \dfrac{outcome\,of\,interest}{all\,possible\,outcomes}$$
$$odds(event) = \dfrac{P}{1-P}$$
 $$odds\,ratio= \dfrac{odds(event_1)}{odds(event_2)}$$
#### Log odds - logit function
$$logit(p)=\ln(\dfrac{P}{1-P})=\ln(p)-\ln(1-p)$$

#### Sigmoid function - inverse logit function - antilog
$$logit^{-1}(\alpha)=\dfrac{e^\alpha}{1+e^\alpha}=\dfrac{1}{1+e^{-\alpha}}$$
#### Estimated probability through the logit link function
 $$\ln(\dfrac{P}{1-P}) = {\beta_0+\beta_1x_1}$$
 $$\hat{p}=\dfrac{e^{\beta_0+\beta_1x_1}}{1+e^{\beta_0+\beta_1x_1}}$$

> When we invert the logit expression we reach the odds-ratio expression used in interpreting the results [[Logistic Regression#Interpetation]]

 $$(\dfrac{P (y=1)}{1-P(y=1)}) = e^{\sum_{j=0}^k\beta_jx_j}$$
 > And per the properties of exponentials can be expressed as 

 $$(\dfrac{P (y=1)}{1-P(y=1)}) = \prod_{j=0}^k e^{\beta_jx_j}$$
  
#### Psuedo-$R^2$
 $$psuedo=R^2 = 1 - \dfrac{deviance}{null\,deviance}$$
1. deviance is your model's variance
2.  null deviance is calculated as $\dfrac{positive\,class}{total\,records}$
	- another way is by taking the $log(odds)$ of the positive class and projecting it back to a probability
## Decision Trees
#entropy #information #gain #classification

#### Base Entropy
$$ H_C = -\sum_{i=0}^k{P(C_i) \log_2P(C_i)}$$
1. The minimum value of entropy is 0 which means the node is 100% pure
2.  The maximum value of entropy is $\log_2 k\,\,\,;\,\,\,k = no.\,of \,classes$
#### Conditional Entropy
$$H_{C|X} = -\sum_{x\in X}P(x) \sum_{i=0}^kP(C_i|x)\log_2 P(Ci|x)$$
#### Information Gain
$$ InfoGain = H_C - H_{C|X}$$
#### Gini Index
$$ Gini_x = 1-\sum_{\forall x\in X}{P(x)^2} $$
## Naïve Bayes
#bayes #theorem #classification 

#### Poseriori probablity
$$P(C_k|X) = \dfrac{P(X|C_k)\times P(C_k)}{P(X)} \propto {P(X|C_k)\times P(C_k)} \quad ; \,\forall \,\, k \in k \,\, classes $$
1. $P(X|C_k)$ is the likelihood
2.  $P(X)$ is the prior probability for the predictor
3. $P(C_k)$ is the initial or prior probability of the class

$$P(X|C_k) = \prod_{i=0}^nP(x_i|C_k)$$
## Model Evaluation and Selection
#accuracy #recall #percision #tpr #fpr 
#### Accuracy - Recognetion Rate
$$ accuracy = \dfrac{TP+TN}{P+N}$$
#### Error Rate
$$error\,rate = 1-acccuracy =\dfrac{FP+FN}{P+N}$$
#### Recall - Sensitivity - TPR
$$reacll=\dfrac{TP}{P}=\dfrac{TP}{TP+FN}$$
#### Specificity - TNR
$$specificity=\dfrac{TN}{N}$$
#### Precision
$$percision = \dfrac{TP}{P\,'} = \dfrac{TP}{TP+FP}$$$$percision \propto \dfrac{1}{recall}$$
#### FPR
$$ fpr = 1 - specifity = \dfrac{FP}{FP+TN}$$
#### F-score - $F_1$ - Harmonic mean
$$F_1 = 2 \times \dfrac{percision \times recall}{percision +recall}$$

#### Fbeta - $F_\beta$
> Value of $\beta$ is chosen such that recall is considered $\beta$ times more important than precision.


$$F_{\beta} = (1+\beta^2)\times \dfrac{percision \times reacll}{(\beta^2 \times percision)+reacll}$$
