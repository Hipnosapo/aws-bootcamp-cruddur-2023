# Week 0 — Billing and Architecture


Created Lucid Charts account

Created HoneyComb account

Created Rollbar account

Created Momento account

Created Github account

Created Gitpod account

Created new AWS account for the BootCamp, ID: 111111

Created new IAM user for administrator: xxxxxx

Changed account name to xxxxxx

    url IAM login

        https://xxxxxx.signin.aws.amazon.com/console

        https://111111.signin.aws.amazon.com/console


Checked IAM access

Created aws cli access

created access keys


Created github repository from template:
    https://github.com/Hipnosapo/aws-bootcamp-cruddur-2023

    repo name: aws-bootcamp-cruddur-2023


Open gitpod, ask to install vscode or open in browser

create snapshot

add repo and install

sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

sudo zypper ar https://packages.microsoft.com/yumrepos/vscode vscode

sudo in code

Vscode installed, problem connecting to gitpod instance by authentication. Looks there are some problems with kwallet in KDE so I install gnome-keyring, but still no connection.
For the moment we continue with the browser, we will solve it.Ok, you have to hit continue and enter the ssh key. I'm an idiot, gnome-keyring unninstalled.


Launched gitpod instance and install aws cli:

    curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"

    unzip awscliv2.zip

    sudo ./aws/install


Configure connection:

    aws configure

Created files in /aws/json/ to automatize aws cli installation

added variables to gitpod account
    AWS_ACCESS_KEY_ID="xxxxxx"
    AWS_SECRET_ACCESS_KEY="xxxxxx"
    AWS_DEFAULT_REGION="xxxxxx"
    AWS_ACCOUNT_ID="xxxxxx"

Created by aws cli from gitpod connection:

    -Budget

        aws budgets create-budget \
            --account-id $AWS_ACCOUNT_ID \
            --budget file://aws/json/budget.json \
            --notifications-with-subscribers file://aws/json/budget-notifications-with-subscribers.json


    -SNS Topic

        aws sns create-topic --name billing-alarm


    -Subscription to the Topic

        aws sns subscribe \
            --topic-arn xxxxxxxxxx \
            --protocol email \
            --notification-endpoint xxxxxx@email.com

    -Alarm

        aws cloudwatch put-metric-alarm --cli-input-json file://aws/json/alarm-config.json




