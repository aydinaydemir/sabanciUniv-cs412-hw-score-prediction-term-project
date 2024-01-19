
# Homework Grade Prediction from ChatGPT 3.5 Chat History
This project is a part of the CS412 Machine Learning course at Sabancı University, focusing on the application of machine learning techniques to predict student grades. Our team has developed a model that utilizes ChatGPT chat histories, obtained during homework sessions, as the primary data source for predicting the academic performance of students. The idea stems from the hypothesis that the interaction patterns and content within these chat logs can provide insightful indicators of a student's understanding and engagement with the subject matter.

In this project, we meticulously gathered and processed HTML chat histories, linking them to the actual grades received by students. By employing various machine learning algorithms, we aimed to create a predictive model that not only serves an educational purpose but also showcases the practical application of machine learning in real-world scenarios. This endeavor represents a unique blend of technology and education, highlighting the potential of machine learning in enhancing educational processes and outcomes. The project's outcomes are intended to provide valuable insights for educators and students alike, offering a novel perspective on how student-teacher interactions, even in a digital format, can influence academic performance.
## Collaborators

- [@aydinaydemir](https://www.github.com/aydinaydemir) Aydin Aydemir - 28686 - aydinaydemir@sabanciuniv.edu
- [@aycaataer](https://www.github.com/aycaataer) Ayca Ataer - 28156 - aycaataer@sabanciuniv.edu
- [@colakhalil](https://www.github.com/colakhalil) Halil Ibrahim Umut Colak - 28879 - colakhalil@sabanciuniv.edu
- [@oykuakmaz](https://www.github.com/oykuakmaz) Biray Oyku Akmaz - 27776 - birayoyku@sabanciuniv.edu
- [@aycaaktas](https://www.github.com/aycaaktas) Ayca Elif Aktas - 27802 - aycaaktas@sabanciuniv.edu

## Run Locally

Clone the project:

```bash
  git clone https://github.com/aydinaydemir/sabanciUniv-cs412-hw-score-prediction-term-project.git
```

Navigate to the project directory:
```bash
  cd sabanciUniv-cs412-hw-score-prediction-term-project
```

Before running the project, you need to install the necessary dependencies. Ensure you have Python installed on your system and then run the following command:
```bash
  pip install -r requirements.txt
```

## Overview of the files
- data
    - bonus : Including the html files of the bonus assignment
    - html : Including the html files that is used to train the model
    - labeled_data
        - trained_data.csv: This csv is for matching prompts to related questions. For simplicity, only assignment prompts are matched with the question numbers. Further researchs may provide more prompt-questionNo pairs to improve the model performance.
    - scores.csv : This csv includes the (html_code - actual_grade) pairs. (labels)

- hw_score_predict.ipynb : This python notebook file includes our roadmap. The draft version of the model. You can see the draft computations (like measuring the correlations of the features with scores) used for building the final model. Also, it includes some feature engineering and our draft model. It's also a complete model, but, we as a team decided to choose the model in model.ipynb. But there is also a working model in this file with tones of extracted features. Other model is more creative than this one, so we choose to continue with the other model.

- model.ipynb : This python notebook file includes our very final version of the model. Details will be explained in other sections.

- requirements.txt : This txt includes the dependencies and corresponding versions used.



## Results with Cross Validation 5-folds
You can see the measurements from our model.

Fold 1:
- Mean Squared Error (MSE): 209.99563204274682
- Root Mean Squared Error (RMSE): 14.491226036562496
- Mean Absolute Error (MAE): 11.067610262076935
- R-squared (R2): -0.8038548066008824


Fold 2:
- Mean Squared Error (MSE): 121.34306435154114
- Root Mean Squared Error (RMSE): 11.015582796726695
- Mean Absolute Error (MAE): 8.475187912891604
- R-squared (R2): -0.876892641222581


Fold 3:
- Mean Squared Error (MSE): 91.87167838417702
- Root Mean Squared Error (RMSE): 9.584971485830149
- Mean Absolute Error (MAE): 8.209266475392896
- R-squared (R2): -1.121719980146234


Fold 4:
- Mean Squared Error (MSE): 411.80269839793806
- Root Mean Squared Error (RMSE): 20.292922372047308
- Mean Absolute Error (MAE): 11.414473291560885
- R-squared (R2): -0.11531577753617461


Fold 5:
- Mean Squared Error (MSE): 110.11370036776776
- Root Mean Squared Error (RMSE): 10.493507534078763
- Mean Absolute Error (MAE): 8.017180871129762
- R-squared (R2): -1.5073328356986968


-----------------
- Average MSE:  189.0253547088342
- Average RMSE:  13.175642045049083
- Average MAE:  9.436743762610416
- Average R2:  -0.8850232082409137
-----------------

#### Important Note:
This results can be improved by:
- Providing more labeled html - score data
- Providing more prompt - related_question data
- Additionally, the high MSE is due to some outliers. For example the GPT history consists of 3 prompts, but the grade is 100. Or oppositely, gpt history is good but grade is around 15.
- The effect of outliers is high.


## ML Algorithm in High-Level

Our model employs a sophisticated multi-step approach to predict student grades based on ChatGPT chat histories. The process begins by iterating through each user prompt within the chat logs. For each prompt, the model predicts a corresponding question number ranging from 1 to 8. This prediction associates the prompt with one of the predefined questions, indicating the specific topic or area of discussion.

Once the question number is determined for each prompt, the model calculates the cosine similarity between the prompt and other prompts associated with the same question. This similarity measure helps in assessing the relevance and quality of the student's interaction in relation to the specific question. The model then assigns a grade for each question based on these similarity scores.

The final stage involves aggregating these individual question grades. The model computes a weighted average for each question, where weights are predefined based on the significance of the questions. The sum of these weighted averages yields the overall predicted grade for the student's chat history, scaled between 1 and 100. This comprehensive approach allows the model to evaluate the student's performance holistically, considering various aspects of their interactions during the homework sessions.

## ML Algorithm in High-Level (the one in the hw_score_predict.ipynb)

- XXXX

## Acknowledgments
Special thanks to Onur Varol and his CS412 team for the semester.


