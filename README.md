[![Build Status](https://travis-ci.org/cfn-modules/kinesis-data-stream.svg?branch=master)](https://travis-ci.org/cfn-modules/kinesis-data-stream)
[![NPM version](https://img.shields.io/npm/v/@cfn-modules/kinesis-data-stream.svg)](https://www.npmjs.com/package/@cfn-modules/kinesis-data-stream)

# cfn-modules: AWS Kinesis data stream

AWS Kinesis data stream with encryption, and [alerting](https://www.npmjs.com/package/@cfn-modules/alerting).

## Install

> Install [Node.js and npm](https://nodejs.org/) first!

```
npm i @cfn-modules/kinesis-data-stream
```

## Usage

```
---
AWSTemplateFormatVersion: '2010-09-09'
Description: 'cfn-modules example'
Resources:
  DataStream:
    Type: 'AWS::CloudFormation::Stack'
    Properties:
      Parameters:
        AlertingModule: !GetAtt 'Alerting.Outputs.StackName' # optional
        KmsKeyModule: !GetAtt 'Key.Outputs.StackName' # optional
        RetentionPeriodHours: 24 # optional
        ShardCount: 1 # optional
      TemplateURL: './node_modules/@cfn-modules/kinesis-data-stream/module.yml'
```

## Examples

none

## Related modules

* [lambda-event-source-kinesis-data-stream](https://github.com/cfn-modules/lambda-event-source-kinesis-data-stream)
* [sqs-queue](https://github.com/cfn-modules/sqs-queue)

## Parameters

<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Description</th>
      <th>Default</th>
      <th>Required?</th>
      <th>Allowed values</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>AlertingModule</td>
      <td>Stack name of <a href="https://www.npmjs.com/package/@cfn-modules/alerting">alerting module</a></td>
      <td></td>
      <td>no</td>
      <td></td>
    </tr>
    <tr>
      <td>KmsKeyModule</td>
      <td>Stack name of <a href="https://www.npmjs.com/package/@cfn-modules/kms-key">kms-key module</a></td>
      <td></td>
      <td>no</td>
      <td></td>
    </tr>
    <tr>
      <td>RetentionPeriodHours</td>
      <td>The number of hours for the data records that are stored in shards to remain accessible</td>
      <td>24</td>
      <td>no</td>
      <td>[24-168]</td>
    </tr>
    <tr>
      <td>ShardCount</td>
      <td>The number of shards that the stream uses</td>
      <td>1</td>
      <td>no</td>
      <td>[1-N]</td>
    </tr>
  </tbody>
</table>

## Limitations

* Scalable: Auto scaling is not yet implemented
