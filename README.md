# pulumi

Pulumi stacks on AWS with Python

Following: https://www.pulumi.com/docs/get-started/aws/begin/

From Scratch on a new OS with Homebrew and Python via pyenv:

1. `brew install pulumi`
2. Create AWS access key for me - `aws-vault add me`
3. Create AWS access key for ken1 - `aws-vault add ken1`
4. `mkdir quickstart && cd quickstart`
5. `pulumi new aws-python`
6. Create a new pulumi token to get started, enter it at the prompt
7. `aws-vault exec ken1 -- pulumi up`
8. Verify that the bucket is created by logging in with ken1 creds
9. Modify the code to add a bucket object per the doc, apply
10. `aws-vault exec ken1 -- aws s3 ls $(pulumi stack output bucket_name)`
11. Modify the code to set a static website from bucket, apply
12. `curl $(pulumi stack output bucket_endpoint)`
12. Destroyed stack and app history:
     `aws-vault exec ken1 -- pulumi destroy`
     `pulumi stack rm dev`