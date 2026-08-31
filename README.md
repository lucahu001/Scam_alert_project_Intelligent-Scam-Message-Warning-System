Intelligent Scam Message Warning System
# Project Title

AI SCAM ALERT 

## Project Description

Social-commerce platforms such as Facebook Marketplace, group-buying pages, and third-party services like 7-Eleven MyShip, Shopee, and PChome now dominate online shopping in Taiwan. Fraud has surged in these spaces. Criminal Investigation Bureau data for October 2024 list online-shopping scams as the second most common fraud type, accounting for 14.41 percent of all reported cases, just behind investment scams. Therefore, our model is quite important in nowadays network environment.

This model uses a total 210 images (screenshots) of normal and scam online conversations as the database for training our model. It uses two different models: gpt-3.5-turbo and gpt-4o to compare which is the best fit for our ai scam alert. We used OCR method to extract the text in those images for our models to identify, classify, and in the end provide an answer advicing our users whether the screenshots they uploaded are more likely fraud conversations that should be aware of, or it is just a normal conversations that the user can continue chatting without fear.


## Getting Started

Several items should be installed before running our model, including 104 original images for preliminary training and 106 images for testing our model. Moreover, the program requires you to install openai and Tesseract OCR engine to successfully run our model.

## File Structure

We organized our files using a consistent naming convention: scam conversation samples were labeled as “詐騙對話-XX.jpg” and normal conversation samples as “正常對話-XX.jpg.” These labeled files were then uploaded to Google Drive, allowing for efficient access and organization of the dataset. This approach facilitates the seamless retrieval of data during model development and programming, ensuring that the training process remains systematic and well-structured.


## Analysis

We found out that gpt-4o has came out a better result comparing to the one that was handled by gpt-3.5-turbo. Gpt-4o delivered as accuracy rate of 89.42% in the preliminary training process and 77.36% in the final testing process. While gpt-3.5-turbo only came up with 70.19% in the preliminary training process and 37.74% in the final testing process.

During initial training with the gpt-3.5-turbo model using our dataset of 104 conversation samples, we observed an accuracy rate of 70.19%. However, when we revisited the same model a few weeks later, the reported accuracy unexpectedly increased to 94.17%, despite no changes to the training data. This sudden and significant fluctuation left us uncertain about the underlying cause—whether it stemmed from improvements in the model’s internal capabilities or was a symptom of overfitting.

## Results

Moreover, while we attempted to optimize the OCR process for gpt-3.5-turbo—including techniques such as enlarging images and applying grayscale filters to reduce noise—these adjustments had limited impact on improving accuracy. The inherent dependence on OCR ultimately constrained gpt-3.5-turbo’s ability to produce consistent and reliable results. Given these limitations, gpt-4o stands out as the more effective and practical choice for our project.

## Contributors

111ZU1002 黃天慧 Alani (PM)
111ZU1010 胡楚逸 Luca (programme)
111ZU1058 黃芊婷 Patricia (programme)
111ZU1061 黃晟恩 Andy (poster design)


## Acknowledgments

We would like to express our sincere gratitude to our instructor, Professor Pien Chung-pei, and our teaching assistant for their invaluable support throughout this project. Their guidance was instrumental during both the brainstorming and programming stages, and their insights greatly contributed to the overall success of our work.

