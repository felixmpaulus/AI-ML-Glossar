
# Dynamic Adaption of Maintenance Packages within the Product Use Phase using Machine Learning Methods regarding Operating Data
Fabian Reinecke, Sebastian Sochaki, Stefan Bracke

- approach with rule learning & decision tree learning methods to determine candidates for specific failure modes on the basis of recorded field data
- C4.5 is used for decision tree learning
- RIPPER is used for rule learning
- classification models are built using both learning methods (separately)
- for each failure mode in the training data, the data is separated in to two sets. One set includes all data that leads to a specific failure mode FM (the class) and the other includes all remaining data (which consequently does not lead to the specific failure mode)
- each failure mode is represented by its own classification model 
- the dataset is based on warranty claims data and product fleet data, whereas the warranty claims data is a subset of the fleet data
- the dataset contains 4000 vehicles and was generated synthetically
- each generated vehicle contains 7 features (variables/attributes) which describe the vehicle usage up to the hypothetical readout time
- 193 datsets of those 4000 where manually assigned with hypothetical failure modes (FM1, FM2, FM3)
- the model then learned rules that describe the load profile where failure occurs

- Question? How do the calculated rules differ from the manually declared rules for the training data? Why are they not the same?


# Prediction of Failure Candidates of Technical Products in the Field Based on a Multivariate Usage Profile Using Machine Learning Algorithms Regarding Operating Data
Sebastian Sochacki, Fabian Reinecke, and Stefan Bracke

- predict the probability for each specific product in a fleet to be affected by one or more failure modes over their lifetime
- the specific usage by the end consumer is described by several usage variables
- synthetic dataset is used
- model is supervised machine learning technique of Gradient Tree Boosting
- Classification or Regression Tree (CART)


# Predictive maintenance enabled by machine learning: Use cases and challenges in the automotive industry
Andreas Theissler, Judith Perez-Velazquez, Marcel Kettelgerdes, Gordon Elger

### Abstract Conclusions
(a) publicly available data would lead to a boost in research activities
(b) the majority of papers rely on supervised methods requiring labelled data
(c) combining multiple data sources can improve accuracies
(d) the use of deep learning methods will further increase but requires efficient and interpretable methods and the availability of large amounts of (labelled) data


