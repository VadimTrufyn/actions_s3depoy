# actions_s3depoy
Deploying a Web App on AWS S3 Using GitHub Actions

Step 1: Create a new GitHub repository
Create a new GitHub repository where you will host your web app code.

Step 2: Add your web app code to the repository
![repo](https://github.com/VadimTrufyn/actions_s3depoy/assets/148262369/125cf24f-6809-48ca-8ca2-bbab023e0392)

Step 3: Create an S3 bucket

Create an S3 bucket to store your web app files.

Step 4: Configure bucket policy for public access

To allow public access to the objects in your S3 bucket, you need to set up a bucket policy. Navigate to the bucket’s properties, select “Permissions,” and click on “Bucket Policy.” Add the following policy:
![policy](https://github.com/VadimTrufyn/actions_s3depoy/assets/148262369/74ccab1d-e6cf-4c14-a953-0f398027d3e9)

Step 5: Create an IAM user and generate security credentials
![user1](https://github.com/VadimTrufyn/actions_s3depoy/assets/148262369/48d8d85f-45a7-4d7a-b8a5-874871d804b3)
![user2](https://github.com/VadimTrufyn/actions_s3depoy/assets/148262369/598ea0bf-c61c-45ab-91b7-fb07e5e0f571)

Step 6: Set up GitHub Secrets for AWS credentials
![Secrets](https://github.com/VadimTrufyn/actions_s3depoy/assets/148262369/dff9424e-ef44-45bf-9cb2-13702d1f14f1)

Step 7: Create the GitHub Actions workflow

```
name: Upload Website

on:
  push:
    branches:
    - demo

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@master
    - uses: jakejarvis/s3-sync-action@master
      with:
        args: --acl public-read --follow-symlinks --delete --exclude '.git*/*'
      env:
        AWS_S3_BUCKET: ${{ secrets.AWS_S3_BUCKET }}
        AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
        AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
```
Step 8: Commit changes and trigger deployment

![job](https://github.com/VadimTrufyn/actions_s3depoy/assets/148262369/03694a10-56e3-45d3-93de-f1e739d76995)

![statick](https://github.com/VadimTrufyn/actions_s3depoy/assets/148262369/b525aff1-fd44-4079-90c9-9707b81bcc52)

![browser](https://github.com/VadimTrufyn/actions_s3depoy/assets/148262369/ab38c759-3039-4e48-a857-a4701108e2fc)









