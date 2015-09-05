# awswhoami
A small tool to find the IAM user and AWS account which owns a configured set of AWS access keys.
#### Usage
The tool assumes you have AWS credentials set in your environment, like below in bash:

    export AWS_SECRET_ACCESS_KEY=xxxxxxxxxxxxxxx
    export AWS_ACCESS_KEY_ID=yyyyyyyyyyyyyy
With these set, the tool will report the AWS account and IAM user that these credentials map to:

    $ awswhoami
    arn:aws:iam::111111111111:user/zvickery [my account]
    
This output is the ARN of the IAM user and the AWS account alias, if one can be determined.
#### Configuration
The AWS account alias will be used if the user has access to query this.  It is possible to configure the AWS account aliases used by the tool.  To do this, create a file called `~/.awswhoamirc` with JSON content like below:

    { 
      "111111111111": "dev account",
      "222222222222": "test account",
      "333333333333": "prod account"
    }
This capability allows customizing the AWS account name output regardless of the configured AWS account alias or rights to query it.
#### Compatibility
The tool is compatible with both python 2.7 and python 3.4.
#### Bugs
The tool has been tested with a wide range of AWS IAM user permissions.  It's possible something has been missed of course.
