## Decision Trees

### compute_entropy(y):
This function calculates the entropy of a set of binary labels (0s and 1s).
It takes as input a numpy array y that indicates whether each example at a node is edible (1) or poisonous (0).
The entropy is computed using the formula: (-p_1 * log2(p_1)) - ((1 - p_1) * log2(1 - p_1)), where p_1 represents the proportion of positive labels in y.
The function returns the entropy value.

### split_dataset(X, node_indices, feature):
This function splits a dataset into left and right branches based on a specific feature.
It takes as input the data matrix X, a list of node_indices representing the active indices at a node, and the feature index to split on.
The function iterates through the node_indices and assigns samples to either the left or right branch based on the feature value.
It returns two lists: left_indices containing the indices with feature value == 1, and right_indices containing the indices with feature value == 0.

### compute_information_gain(X, y, node_indices, feature):
This function calculates the information gain of splitting a node on a given feature.
It takes as input the data matrix X, the target variable y, a list of node_indices, and the feature index to split on.
The function first splits the dataset into left and right branches using the split_dataset function.
It then computes the information gain by subtracting the weighted average of the entropies of the left and right branches from the entropy of the original node.
The function returns the computed information gain value.

### get_best_split(X, y, node_indices):
This function determines the best feature to split the data at a node, maximizing the information gain.
It takes as input the data matrix X, the target variable y, and a list of node_indices representing the active indices at a node.
The function computes the information gain for each feature using the compute_information_gain function and selects the feature with the highest information gain.
If all samples have the same label (0 or 1), or if all features have been exhausted, the function returns -1 (indicating no best feature).
Otherwise, it returns the index of the best feature.
