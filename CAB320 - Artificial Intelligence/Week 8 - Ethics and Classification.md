## 1 Trusting AI
![[Pasted image 20250502201326.png]]
## 2 Fairness
![[Pasted image 20250502202041.png]]
![[Pasted image 20250502202417.png]]

## 3 Classification Evaluation
### 3.1 Why Mastering Performance Evaluation
- To estimate the actual performance of a classifier as well as possible
- Expectation on performance
- Quantify magnitude or number of errors
- Depending on the application, knowing the types of errors may also be important
- Good to know when errors are committed (e.g. depending on the class but also depending on the instance)

### 3.2 Binary Classification (2 Classes)

![[Pasted image 20250502164327.png|400]]
**Accuracy**
![[Pasted image 20250502164849.png|300]]
**Accuracy** is the sum of diagonal elements of the confusion matrix (successful classification), divided by the sum of all elements of the matrix (i.e. total number of samples tested).
**Pros**: This gives us one number to summerise the results, easy to interpret.
**Cons**: Does not distinguish between types of errors (FP or FN). Sensitive to class imbalance

#### 3.2.1 Precision and Recall (Ignores TN)
![[Pasted image 20250502181619.png|300]]
 Gives more detail on type of errors, especially relevant if classes are not treated the same. Better with imbalanced classes.

Maximum precision can be reached when we choose all results as negative, meaning no false positives
#### 3.2.2 Sensitivity and Specificity
 
 ![[Pasted image 20250502192230.png|700]]

### 3.3 F1 Score

#### 3.3.1 Definition

The **F1 score** combines precision and recall into a single metric:

$$
F_1 = \frac{2PR}{P + R}
$$

Where:
- $$P = \text{Precision} = \frac{TP}{TP + FP}$$
- $$R = \text{Recall (Sensitivity)} = \frac{TP}{TP + FN}$$

Alternative equivalent forms:

$$
F_1 = \frac{2 \cdot TP}{2 \cdot TP + FP + FN}
$$

$$
F_1 = 2 \cdot \frac{\text{sensitivity} \cdot \text{precision}}{\text{sensitivity} + \text{precision}}
$$



#### 3.3.2 Notes

- **F1 ignores True Negatives (TN)**.
- The value of F1 depends on how the **positive class** is defined.
  - In imbalanced datasets, this can dramatically affect its interpretation.
  - A **favourable F1** is more likely if the **positive class has more samples** than the negative class.



#### 3.3.3 When to Use

- When precision and recall are **equally important**.
- When **True Negatives (TN)** are not critical to your application.

Example domains:
- Medical diagnostics
- Spam detection
- Fault detection


#### 3.3.4 Limitations

- Misleading for **highly imbalanced datasets**.
- Inadequate if **True Negatives are important** to the evaluation.

### 3.4 Matthews Correlation Coefficient (MCC)
MCC is a metric that is not biased by the choice of positive class
![[Pasted image 20250502193427.png|500]]
Since this is a correlation score, it goes from +1 to -1:
0 - no correlation
-1 - ani-correlation, gets the opposite results (mirror)
1 - perfect match

### 3.5 Normalised Confusion Matrix
![[Pasted image 20250502193858.png|300]]
Shows %'s instead of numbers. Helps compensate for possible class imbalance (but this also means it is no longer visible).
This allows us to compare different classes that might have different samples
Normalise by row (actual/true classes)
Each value in the matrix has to be between 0 and 1

### 3.6 Receiver Operating Characteristic (ROC) Curve
This one is specificity vs 1-specificity
![[Pasted image 20250502194140.png|300]]
perfect is when both of them are 1. Aim to get both as close as you can.

The area under the curve (AUC) is a good way to measure the performance of a classifier

### 3.7 Precision Recall Curve (other variant of ROC)
Want to maximise the area under the curve
![[Pasted image 20250502194721.png|400]]
AUC: area under the curve
mAP: mean average precision

### 3.8 Multi-Class Confusion Matrix
![[Pasted image 20250502195805.png|400]]
![[Pasted image 20250502195824.png|400]]
#### 3.8.1 Multi-Class Accuracy
![[Pasted image 20250502195842.png|600]]

#### 3.8.2 Multi-Class Precision and Recall
![[Pasted image 20250502200054.png|600]]
![[Pasted image 20250502200121.png|600]]
##### 3.8.2.1 Pros and Cons of Macro-Average vs Micro-Average
![[Pasted image 20250502200312.png|600]]
##### 3.8.2.2 Macro-averaging *(treats all classes equally)*
**Pros:**
- Good when all classes are equally important
- Handles imbalanced datasets

**Cons:**
- Performance may look worse due to low performance in a small class
- May not see poor performance in minority class when the number of classes is large

##### 3.8.2.3 Micro-averaging

**Pros:**
- Accounts for the total number of misclassifications (similar to accuracy)

**Cons:**
- Can overemphasize the performance of a majority class (highly represented in the dataset)
- Might not see poor performance of minority class


![[Pasted image 20250502200802.png]]

## 4 Other Important Factors Beyond Accuracy
![[Pasted image 20250502201229.png]]