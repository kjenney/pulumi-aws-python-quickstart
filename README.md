# pulumi-aws-python-quickstart

Pulumi stack on AWS with Python

Following: https://www.pulumi.com/docs/get-started/aws/begin/

From Scratch on a new OS with Homebrew and Python via pyenv:

1. Install `Pulumi`

    ```bash
    brew install pulumi
    ````

2. Create AWS access key for me

    ```bash
    aws-vault add me
    ````

3. Create AWS access key for ken1

    ```bash
    aws-vault add ken1
    ````

4. Create quickstart directory

    ```bash
    mkdir quickstart && cd quickstart
    ````

5. Create new Pulumi stack

    ```bash
    pulumi new aws-python
    ```
    
6. Create a new pulumi token to get started, enter it at the prompt

7. Deploy stack

    ```bash
    aws-vault exec ken1 -- pulumi up
    ```

8. Verify that the bucket is created by logging in with ken1 creds

9. Modify the code to add a bucket object per the doc, apply

10. Get the bucket name from the stack output:

    ```bash
    aws-vault exec ken1 -- aws s3 ls $(pulumi stack output bucket_name)
    ```

11. Modify the code to set a static website from bucket, apply

12. Use curl to make an HTTP request to the bucket endpoint:
    
    ```bash
    curl $(pulumi stack output bucket_endpoint)
    ```

13. Destroyed stack and app history:
    
    ```bash
    aws-vault exec ken1 -- pulumi destroy
    pulumi stack rm dev
    ```

## Reproducing

1. git clone repo
2. cd into it
3. Initialize the stack:
    
    ```bash
    pulumi stack init dev
    ```