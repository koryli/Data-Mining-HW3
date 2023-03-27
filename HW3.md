# HW3

## Q1: What causes what?

1.  Because we don't know what causes what. We cannot tell whether more police lead to lower crime or higher crime leads to more police. What we can only say is that there may exist some correlation between police and crime. If we could do an experiment with random assignment pf cops in some place and see the crime rate of that place, we would know if there exists a causation.

2.  They found a natural experiment to isolate the effect and used terrorism alert systems. When there is a high alert, more cops would be placed in the streets, which is unrelated with crime. And the researchers collected the crime data and the related alert situation. In the table, days with the higher alert have lower crimes. The coefficient is statistically significant at the 5% level. And controlling for the METRO ridership reduces the impact of police on crime.

3.  They controlled for the ridership because during the high alert day, if less people are out, there will be fewer opportunities for crime, so the crime will be lower. This effect is not caused by the police. Therefore, we need to control. After controlling, we can capture the relationship of police on crime sorting out the impact of people going out.

4.  The model uses the interaction between distractions and high alert days and estimates whether the effect of high alert day on crime was the same in different districts. The results show that the effect only exists clearly in district 1 and is statistically significant at the 1% level. In other districts, the effect is still negative but very small and statistically insignificant.

## Q2: Tree modeling: dengue cases

The model we use as following:

total_cases \~ specific_humidity + tdtr_k + precipitation_amt

First, split into training and testing data.

### CART

1.  Fit the model on the training data and get a big tree.

![image](https://user-images.githubusercontent.com/112587000/228054788-061c272e-09e2-4205-9a99-8012a5ada7e7.png)

2.  Then, based on the 1SE rule, find the best cp and prune the tree.

The best cp:

![image](https://user-images.githubusercontent.com/112587000/228054941-e2e8e5b7-2330-40fc-892a-89e829f8526f.png)

The the pruned tree:

![image](https://user-images.githubusercontent.com/112587000/228055020-2a9825ee-653a-4199-b592-27487a26a93d.png)

3.  Prediction on the test set.

4.  RMSE:
[1] 37.91261

5.  Plot the Partial Dependence Plot.

Partial dependence of total cases on specific_humidity:

![image](https://user-images.githubusercontent.com/112587000/228055304-683da0ca-f298-4933-aa39-86c440af824e.png)

Partial dependence of total cases on tdtr_k:

![image](https://user-images.githubusercontent.com/112587000/228055385-3d46d932-9be5-4dca-8dc5-e76566ffa6c0.png)

Partial dependence of total cases on precipitation_amt:

![image](https://user-images.githubusercontent.com/112587000/228055482-b6251f8b-f72c-4cff-bb14-30f82874998d.png)

### Random forests

1.  Fitting Random Forest to the train data set

Shows out-of-bag MSE as a function of the number of trees used:

![image](https://user-images.githubusercontent.com/112587000/228055821-af8a13d8-79d5-453d-a1ad-3f3aac6bac61.png)

2.  Prediction

3.  RMSE on the test set:
[1] 25.42312

4.  Plot the Partial Dependence Plot.

Partial dependence of total cases on specific_humidity:

![image](https://user-images.githubusercontent.com/112587000/228056035-d2435176-c345-47e1-b138-be8ef648b26a.png)

Partial dependence of total cases on tdtr_k:

![image](https://user-images.githubusercontent.com/112587000/228056093-5c85f959-c52c-4a39-a430-54b1aa4f5ffd.png)

Partial dependence of total cases on precipitation_amt:

![image](https://user-images.githubusercontent.com/112587000/228056201-1ea3dda7-2bd7-491d-9102-0a3ccf1af06f.png)

### Gradient-boosted trees

1.  Fit the gbm model

![image](https://user-images.githubusercontent.com/112587000/228056439-fe9b5422-f1f8-4901-b40d-6fd625151ba3.png)

2.  Find the best ntree and prune.

ntree:

![image](https://user-images.githubusercontent.com/112587000/228056526-f749d434-628e-413d-8ae9-c58341fb7e78.png)

number of tree
[1] 131

Then use the best ntree.

3.  Prediction

Predict on testing data.

4.  RMSE:
[1] 36.62508

5.  Plot the Partial Dependence Plot

Partial dependence of total cases on specific_humidity:

![image](https://user-images.githubusercontent.com/112587000/228056830-e18334d5-c9c6-4794-b8eb-7004ae532fc2.png)

Partial dependence of total cases on tdtr_k:

![image](https://user-images.githubusercontent.com/112587000/228056893-6a50f2eb-7cfa-45f4-bbcc-f02b10e0ebe0.png)

Partial dependence of total cases on precipitation_amt:

![image](https://user-images.githubusercontent.com/112587000/228056942-b645aa85-c104-4712-b09c-a522f82e52c1.png)

### Compare RMSE on the test set:
[1] 37.91261

[1] 25.42312

[1] 36.62508

Comparing the RMSE, the random forest performs best on the test set with the lowest RMSE.



