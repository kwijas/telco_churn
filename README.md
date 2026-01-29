# Predicting Churn 
Churn refers to those who decide to leave a company and take their business elsewhere. For a company, losing out on customers can be detramental to their future endevors. Therefore, it is imporant to understand the key components that drive a customer to leave in order to prevent churn from happening. Here, a random forest will be used to determine these leading factors. 

#### Data Cleaning
In order to prevent the ID of the customer from becoming a misleading imporant factor, it was removed from the dataset. 

## Random Forest
* The data was sourced from kaggle. For replication purposes a seed was set before any analysis was conducted. 
### Inital Model
To begin, the telco data was split into a training and testing set. Then, a random forest was run on the training data with all varaibles included, omitting the missing values in the dataset. 

<p align="center">
  <img width="469" height="239" alt="Screenshot 2026-01-28 at 2 16 11 PM" src="https://github.com/user-attachments/assets/0c9f7054-3449-47ff-81ae-09b465ed5ad5" />

</p>

From here we are able to conclude the following about the model:
- It is good at predicting those who will **not** leave (9.36% error rate)
- It is failing at recognizing those who are leaving, as the model missed 750 people who left (50.30% error rate)

In investigating why the "Yes" error is so high, it can be seen that there is a large number of those who do not churn, which makes it easier for the model to guess that a person will not leave since they are more likely to stay. Therefore, the next step to improve this model would be to put more pressure on the model to recognize those who churn. 

### Increased Sensitiviy 
Since the goal is to stop being from leaving, we will let the model be more sensitive to those who are leaving in order to help identitfy why they are doing so. Thus, we will make the tree contain equal amount of "No" and "Yes."

When running this model we see: 
<p align="center">
<img width="514" height="218" alt="Screenshot 2026-01-28 at 2 41 54 PM" src="https://github.com/user-attachments/assets/530d02ab-a58c-4c11-95e9-2b3c391d15a8" />
</p>

Here is what we have learned about this new model:
- It has done a much better job at catching those who leave. The error rate dropped from 50.3% to 26.2%, meaning it identifies around 74% of those who are leaving.
- Now we can figure out why these people are leaving. 

## Impact 
By creating a varible imporantance plot, we are able to see the imporant characteristics to those who are leaving. 
<p align="center">

<img width="500" height="400" alt="Screenshot 2026-01-28 at 2 48 30 PM" src="https://github.com/user-attachments/assets/a2072de8-4e75-4398-b0e5-a31a4684caa1" />

</p>

Here we are able to see tenure and total charges are the most impactful, followed by the type of contract the customer is in. 

In taking a closer look at these specific traits (*with the help of PowerBI*):
1. Tenure
   - The longer someone is with a company, the less likey they are to leave. Thus, a company should focus on newer customers in order to make sure they stay. 
<p align="center">
 <img width="400" height="350" alt="Screenshot 2026-01-28 at 3 13 29 PM" src="https://github.com/user-attachments/assets/5f6c1220-3729-444a-b064-04555251fee9" />

</p>

2. Total Charges
   - Total cha
<p align="center">
 <img width="400" height="300" alt="Screenshot 2026-01-28 at 3 17 01 PM" src="https://github.com/user-attachments/assets/3e7b199a-8601-492d-90fa-f51e144b3444" />
</p>
3. Contract
<p align="center">
 <img width="399" height="400" alt="Screenshot 2026-01-28 at 3 11 23 PM" src="https://github.com/user-attachments/assets/0727cebe-9c7e-45ce-89ed-43813147b19d" />

  </p>


## Recommendations 
