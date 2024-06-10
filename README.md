It is completed.... FFJ:
The key here is this:
a. The most important thing is that npm install @aws-cdk/core     HAS TO BE LOCAL. NO NO NO -g paramter.  MUST MUST MUST USE V2 and never V1 of AWS-CDK.
b. you may howerver to do a global on typescript ( > inpm install typescript -b)
c. next and really the first thing is to do (> npm install ) which will install everything for you.
d.  MUST MUST MUST cdk must be v2 or look at your ~/.zshrc and use CDK2 ALIAS .. CDK should also point to V2.  sor CDK and CDK2 must be equal.
e. aws configure       ( It should be local no profile)
f. MUST MUST DO cdk bootstrap command next to connect it to your AWS. (> cdk bootstrap aws://636090713215/us-east-1)
g. CDK synth
h. CDK deploy
i. CDK destroy


STEPS:

cd into your dir

npm install @aws-cdk/core

npm install typescript -g

npm i

cdk bootstrap aws://636090713215/us-east-1

cdk synth

cdk deploy

cdk destroy

WORKS PERFECTLY FFJ

# EventBridge No Match Rule

AWS EventBridge does not natively provide a way to catch events which do not match any rules defined on an event bus. This AWS CDK project defines a custom construct, `NoMatchRule`, which captures unmatched events and forwards them to an SQS queue of your choosing.

This works by creating a rule which matches on **all** events and forwards the event to a Lambda function. The Lambda function fetches all rules from the event bus and tests the event against each rule's pattern. If no rules match the event is then sent to the SQS queue.

Note you must instantiate `NoMatchRule` at most **once** for a given event bus.

![Architecture diagram](./diagram.png)

## Commands FREDJ

- `npm run build` compile typescript to js
- `npm run watch` watch for changes and compile
- `npm run test` perform the jest unit tests
- `cdk deploy` deploy this stack to your default AWS account/region
- `cdk diff` compare deployed stack with current state
- `cdk synth` emits the synthesized CloudFormation template
