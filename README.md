# AWS-S3-Weather-Dashboard

This project fetches weather data for multiple cities using the OpenWeather API and stores the data in an Amazon S3 bucket. It provides an easy way to store real-time weather data and access it later.

Features:
Fetches real-time weather data for multiple cities.
Stores the weather data as JSON files in an Amazon S3 bucket.
Provides basic error handling and logging to track the process.


Requirements:
Python 3.x
AWS account with S3 access
OpenWeatherMap API key

Troubleshooting Issues that occured and how to resolve: 
1. S3 bucket issues: Make sure your AWS credentials are correctly set up and that you have the necessary permissions to access the S3 bucket.


2. Missing or Incorrect Environment Variables
If the .env file is missing or incorrectly configured, the script won't be able to access your OpenWeather API key (OPENWEATHER_API_KEY) or AWS bucket name (AWS_BUCKET_NAME), causing errors.

You might see errors like AttributeError: 'NoneType' object has no attribute 'get' when trying to load OPENWEATHER_API_KEY or AWS_BUCKET_NAME.
The weather data may not be fetched from the OpenWeather API, or the program won't interact with AWS S3.

- Ensure that the .env file exists in the root directory of your project and contains the correct environment variables.
- Specify the Path to the .env File Manually
You can explicitly specify the path to the .env file in the load_dotenv() function by passing the dotenv_path parameter.

3. Error related to the putObject operation in the AWS CLI or AWS SDK
    - One of the most common causes for a putObject error is insufficient permissions. If your IAM role or user doesn't have the correct permissions to write to the S3 bucket, you'll get an error.
Solution: Ensure that the IAM user or role has the s3:PutObject permission for the specific bucket. You can attach a policy to the user or role like this:
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:PutObject",
      "Resource": "arn:aws:s3:::your-bucket-name/*"
    }
  ]
}

HAPPY CODING ! 
