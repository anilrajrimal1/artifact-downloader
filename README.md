# Build Artifact Downloader

[![GitHub release (latest by date)](https://img.shields.io/github/v/release/anilrajrimal1/artifact-downloader)](https://github.com/anilrajrimal1/artifact-downloader/releases)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

A GitHub Action that downloads and extracts build artifacts from an AWS S3 bucket, simplifying CI/CD workflows by automating artifact retrieval.

## 📌 Overview

This action enables seamless integration of stored build artifacts into your CI/CD pipeline by fetching and extracting them from an S3 bucket.

## ✨ Features

- 🔹 Automates artifact retrieval from AWS S3
- 🔹 Secure authentication using AWS credentials
- 🔹 Extracts the artifact to a specified directory
- 🔹 Cleans up after extraction for optimized workflows

## 🚀 Usage

To use this action in your GitHub workflow, add the following step to your `workflow.yml`:

```yaml
- name: Download and Extract Build Artifact
  uses: anilrajrimal1/artifact-downloader@v1.0.0
  with:
    aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
    aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
    aws-region: ${{ env.AWS_REGION }}
    project-name: ${{ env.PROJECT_NAME }}
    s3-base-path: "s3://your-bucket-name"
    target-directory: "."
```

## 🔧 Inputs

| Name                   | Required | Default      | Description                                     |
|------------------------|----------|--------------|-------------------------------------------------|
| `aws-access-key-id`    | ✅ Yes   | -            | AWS access key ID for authentication           |
| `aws-secret-access-key`| ✅ Yes   | -            | AWS secret access key for authentication       |
| `aws-region`          | ✅ Yes   | `ap-south-1` | AWS region where the S3 bucket is located      |
| `project-name`        | ✅ Yes   | -            | Project name used for identifying artifacts    |
| `s3-base-path`        | ✅ Yes   | -            | Base S3 path where artifacts are stored       |
| `target-directory`    | ❌ No    | `.`          | Directory to extract the artifact             |

## 🔄 How It Works

1. Configures AWS credentials securely.
2. Downloads the artifact ZIP file from the specified S3 path.
3. Extracts the ZIP file to the given `target-directory`.
4. Cleans up the downloaded ZIP file after extraction.

## Security Notes

- Store your `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` as GitHub Secrets.
- Never hardcode sensitive credentials in workflow files.
- Uses AWS best practices for secure authentication.

## Requirements

- GitHub Actions runner with AWS CLI installed.
- An AWS Credentials with proper access to S3

## Contributing

Contributions are welcome! Feel free to submit a Pull Request.

## 📜 License

This project is licensed under the MIT License - see the LICENSE file for details.

## Author

Anil Raj Rimal

## Acknowledgements

- [AWS S3](https://aws.amazon.com/s3/) for providing scalable storage solutions.

