# Deploying Smaller Open Source Large Language Model on AWS Lambda

## Overview
Large Language Models (LLMs) are cutting-edge technology that I'm experimenting with. While managed services like OpenAI offer cost-effective LLM usage, there are scenarios where running an LLM locally becomes necessary. This may be due to handling sensitive data or needing high-quality outputs in languages other than English. Open source LLMs match the quality of major players like OpenAI but often demand significant compute resources. Deploying smaller models on platforms like AWS Lambda can offer cost-effective alternatives.

## Project Goal
My goal with this project is to deploy a smaller open-source LLM, specifically Microsoft Phi-2, a 2.7 billion parameter model that rivals outputs from larger open-source models. I'll explore LLMs, and docker-based lambdas, evaluate performance, and assess costs for real-world applications.

## Steps

### 1. Environment Setup (AWS, Docker, and Python)
Ensure the necessary tools are installed, including an AWS account, AWS CLI, Docker, and Python.

### 2. Set up Lambda Function Locally with Docker
- Create a basic Python Lambda function handler in a `lambda_function.py` file.
- Define dependencies in `requirements.txt`, starting with the AWS library (`boto3`).
- Create a `Dockerfile` specifying the Docker image composition.
- Set up `docker-compose.yml` for running and building the container.
- Build and start the container locally using `docker-compose up`.

### 3. Run an LLM Inside the Container
- Add `llama-cpp-python` to `requirements.txt`.
- Introduce a Docker build stage for llama-cpp installation and model download.
- Modify my Lambda code to run LLM inference.

### 4. Test Locally
Rebuild the container and test with a real prompt using `curl`.

### 5. Deploy to AWS Lambda
Execute the deployment using the provided script (`deploy.sh`). This involves creating or checking the ECR repository, IAM role, Docker-ECR authentication, Docker image construction, ECR image upload, IAM role ARN acquisition, Lambda function verification, configuration, and deployment.

### 6. Test Remotely
Use the Lambda function URL obtained during deployment to test with a prompt.

## Prerequisites
Working knowledge of programming, Docker, AWS, and Python.

## Notes
- All files should be stored in a single project directory without subfolders.

Feel free to explore, modify, and run the provided scripts to deploy and test open-source LLM on AWS Lambda.

## References
1. [Hugging Face](https://huggingface.co/)
2. [AWS](https://aws.amazon.com/)
3. [Horosin - Deploy a Language Model (LLM) on AWS Lambda](https://horosin.com/deploy-a-language-model-llm-on-aws-lambda)
4. [Medium - Deploying the Hugging Face LLM in Amazon SageMaker](https://medium.com/technology-nineleaps/deploying-the-hugging-face-llm-in-amazon-sagemaker-37b71cd74aca)
