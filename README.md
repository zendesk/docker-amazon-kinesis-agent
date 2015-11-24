Introduction
============
This repository contains a Docker image source for the AWS Kinesis Streaming Agent.

More information about the agent can be found
(here)[http://docs.aws.amazon.com/kinesis/latest/dev/writing-with-agents.html].

How to use
==========
Use this image as the `FROM` value in your Dockerfile.  Then install a
customized configuration file into `/etc/aws-kinesis/agent.json`.

The configuration file format is documented
(here)[http://docs.aws.amazon.com/kinesis/latest/dev/writing-with-agents.html#agent-config-list].

**Note**: Do not fill in the values for `awsAccessKeyId` and
`awsSecretAccessKey` in your configuration file.  This could result in your
credentials being insecurely stored in your version control system.  Instead,
set the `AWS_SECRET_ACCESS_KEY` and `AWS_ACCESS_KEY_ID` environment variables
when launching your container.

Environment variables
=====================
The following environment variables are discussed
(here)[http://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html#cli-environment]:

* `AWS_ACCESS_KEY_ID`
* `AWS_SECRET_ACCESS_KEY`
* `AWS_DEFAULT_REGION`

Additional environment variables:

* `LOG_LEVEL`: Log level. Can be `TRACE`, `DEBUG`, `INFO`, `WARN`, or `ERROR`.  (Default: `INFO`)
* `JAVA_VERSION`: Major version of Oracle JDK
* `JAVA_UPDATE`: Update version of Oracle JDK
* `JAVA_BUILD`: Build version of Oracle JDK
* `JAVA_START_HEAP`: Java initial heap size (default: `32m`)
* `JAVA_MAX_HEAP`: Java maximum heap size (default: `512m`)
