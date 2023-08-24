# Cohere-Movie-Search

This is a demo of a Multilingual Movie Search application using [Cohere Multilingual Embedding Model](https://aws.amazon.com/marketplace/pp/prodview-z6huxszcqc25i?sr=0-1&ref_=beagle&applicationId=AWSMPContessa) on [AWS Marketplace](https://aws.amazon.com/marketplace) and [Amazon SageMaker JumpStart](https://docs.aws.amazon.com/sagemaker/latest/dg/studio-jumpstart.html). The application is edited from [Cohere Application examples](https://docs.cohere.com/page/application-examples) to make it suitable for demo in Amazon SageMaker Studio.

You can watch a video demonstration of this application on YouTube: https://www.youtube.com/watch?v=LnnReiK176Q. 
For more in-depth information, refer to my blog post at: https://medium.com/@james_yi/build-a-movie-recommendation-app-using-cohere-multilingual-embedding-model-on-aws-8f75e5d8625c


![](https://github.com/jameszhyi/Cohere-Movie-Search/blob/main/pics/Cohere-Movie-AWS-Architecture.png)

In this app, you can just describe the movie you would like to watch, and the app will suggest movies that are a perfect match for you. You can even describe a movie in a variety of languages since the app will perform a multilingual search. We'll use Cohere’s multilingual models to embed movie descriptions into language-invariant embeddings.

![](https://github.com/jameszhyi/Cohere-Movie-Search/blob/main/pics/Cohere-Movie-Search-01.png)



## 1. Deploy cohere multilingual Model Package from AWS Marketplace
You can subscribe [cohere multilingual Model on AWS Marketplace](https://aws.amazon.com/marketplace/pp/prodview-z6huxszcqc25i?sr=0-1&ref_=beagle&applicationId=AWSMPContessa)  and invoke the real-time endpoint by launching AWS CloudFormation template. You can give the endpoint name as "Endpoint-Cohere-Multilingual-Embedding-Model-1" which will be used in the next step.

## 2. Run the Streamlit application in Amazon SageMaker Studio
Now we’re ready to run the Streamlit web application for Multilingual Movie Search.

Amazon SageMaker Studio provides a convenient platform to host the Streamlit web application. The following steps describes how to run the Streamlit app on Studio. Alternatively, you could also follow the same procedure to run the app on your laptop.

- Open Studio and then open a new system terminal.
- Run the following commands on the terminal to clone the code repository for this post and install the Python packages needed by the application:
```
git clone https://github.com/jameszhyi/Cohere-Movie-Search/

cd Cohere-Movie-Search

pip install -r requirements.txt
```
- Ensure that the endpoint name in movies.py matches the one you created in the previous step. Then run the following command to start a Streamlit app on Studio:
```
streamlit run movies.py
```
- When the application runs successfully, you’ll see the URL:Port Number from the system terminal. The port number (typically 8501) from the output will be used as part of the URL for app in the next step.
- You can access the app in a new browser tab using a URL that is similar to your Studio domain URL. For example, if your Studio URL is `https://d-randomidentifier.studio.us-east-1.sagemaker.aws/jupyter/default/lab?` then the URL for your Streamlit app will be `https://d-randomidentifier.studio.us-east-1.sagemaker.aws/jupyter/default/proxy/8501/` (notice that `lab` is replaced with `proxy/8501/`). If the port number noted in the previous step is different from 8501 then use that instead of 8501 in the URL for the Streamlit app.