## Binary Classification Performance
- In order to determine the performance of a binary classification algorithm, a confusion table is used
#### Confusion Table
- A confusion table for a binary classification algorithm has the following form:
![[Pasted image 20241018104453.png]]
#### Attributes
- Based on the amounts of true positives and negatives and false ones, a number of attributes can be defined: 
	- Accuracy: $\frac{TP + TN}{TP + TN + FP + FN}$
	- Precision: $\frac{TP}{TP + FP}$
	- Sensitivity: $\frac{TP}{TP + FN}$
	- Specificity: $\frac{TN}{FP + TN}$
- Depending on the type of problem at hand, certain attributes are more relevant than others