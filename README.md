# Build Artifact Downloader

## Description
**Build Artifact Downloader** is a GitHub Action that downloads and extracts build artifacts from an AWS S3 bucket. This action helps streamline CI/CD workflows by automating the process of retrieving stored artifacts.

## Usage
To use this action in your GitHub workflow, add the following step in your `workflow.yml`:

```yaml
- name: Build Artifact Download
  uses: anilrajrimal1/artifact-downloader@v1.0.0
  with:
    aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
    aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
    aws-region: ${{ env.AWS_REGION }}
    project-name: ${{ env.PROJECT_NAME }}
    s3-base-path: "s3://your-bucket-name"
    target-directory: "."
```

## Inputs
| Name | Required | Default | Description |
|------|----------|---------|-------------|
| `aws-access-key-id` | ✅ | - | AWS access key ID |
| `aws-secret-access-key` | ✅ | - | AWS secret access key |
| `aws-region` | ✅ | `ap-south-1` | AWS region |
| `project-name` | ✅ | - | Name of the project used during upload |
| `s3-base-path` | ✅ | - | Base S3 path used during upload |
| `target-directory` | ❌ | `.` | Directory to extract the artifact |

## How It Works
1. Configures AWS credentials.
2. Downloads the artifact ZIP file from the specified S3 path.
3. Extracts the ZIP file to the specified `target-directory`.
4. Cleans up the downloaded ZIP file after extraction.

