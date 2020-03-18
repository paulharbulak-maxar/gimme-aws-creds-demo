# Role-based AWS CLI Access Using gimme-aws-creds

## Install and Configure

* Install gimme-aws-creds Python package:

    ```
    pip3 install --upgrade gimme-aws-creds
    ```

* Backup AWS credentials file

    ```
    mv ~/.aws/credentials ~/.aws/credentials.orig
    ```

* Save gimme-aws-creds config file (~/.okta_aws_login_config) or skip to step 4 to manually configure
    ```conf
    [DEFAULT]
    okta_org_url = https://maxar.okta.com
    okta_auth_server = 
    client_id = 
    gimme_creds_server = appurl
    aws_appname = 
    aws_rolename = 
    write_aws_creds = True
    cred_profile = acc-role
    okta_username = pharbula
    app_url = https://maxar.okta.com/home/amazon_aws/0oa2jgnr1452OC2PW2p7/272
    resolve_aws_alias = True
    include_path = False
    preferred_mfa_type = push
    remember_device = True
    aws_default_duration = 3600
    device_token = 
    output_format = export
    ```

* Manually configure gimme-aws-creds

    ```
    gimme-aws-creds --action-configure
    ```

## Get Credentials for AWS CLI

* Execute `gimme-aws-creds`

![gimme-aws-creds screenshot](./screenshot.png "Prompt for roles to configure")

* Use profile for executing AWS CLI commands

```
aws s3 ls --profile utap-Admins
```

* Or set default profile to one of the profiles updated by gimme-aws-creds

```
export AWS_DEFAULT_PROFILE=utap-Admins
aws s3 ls
```