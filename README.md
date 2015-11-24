Introduction
============
This repository contains a Docker image source for the [AWS Kinesis Streaming
Agent](http://docs.aws.amazon.com/kinesis/latest/dev/writing-with-agents.html).

How to use
==========
Use this image as the `FROM` value in your `Dockerfile`.  Then install a
customized configuration file into `/etc/aws-kinesis/agent.json`.

The configuration file format is documented
[here](http://docs.aws.amazon.com/kinesis/latest/dev/writing-with-agents.html#agent-config-list).

If you're running in a region other than us-east-1, you'll need to specify
values for the CloudWatch and Kinesis service endpoints in your `agent.json`
file.  (The Java SDK doesn't yet support the `AWS_DEFAULT_REGION` environment
variable.)  You can find a table of regional endpoints
[here](http://docs.aws.amazon.com/general/latest/gr/rande.html).

Security note
-------------
Do not fill in the values for `awsAccessKeyId` and
`awsSecretAccessKey` in your configuration file.  This could result in your
credentials being insecurely stored in your version control system.  Instead,
set the `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` environment variables
when launching your container.

Environment variables
=====================
The following environment variables are discussed
[here](http://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html#cli-environment):

* `AWS_ACCESS_KEY_ID`
* `AWS_SECRET_ACCESS_KEY`

Additional environment variables:

* `AWS_IAM_ROLE`: If set to a valid IAM role name, obtain AWS access
  credentials using instance metadata.  This can be used in lieu of setting the
  `AWS`-prefixed environment variables above.
* `LOG_LEVEL`: Log level. Can be `TRACE`, `DEBUG`, `INFO`, `WARN`, or `ERROR`.  (Default: `INFO`)
* `JAVA_START_HEAP`: Java initial heap size (default: `32m`)
* `JAVA_MAX_HEAP`: Java maximum heap size (default: `512m`)
