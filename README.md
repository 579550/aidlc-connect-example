# aidlc-connect-example
testing ai-dlc

## Simple Amazon Connect flow

`simple-flow.yaml` is a CloudFormation template creating one contact flow: greeting, "Press 1" menu to a queue, replay up to 2 times on invalid/no input, then goodbye and disconnect. Uses built-in blocks only.

Deploy (existing instance and queue required):

```
aws cloudformation deploy --template-file simple-flow.yaml --stack-name simple-connect-flow \
  --parameter-overrides InstanceArn=<instance-arn> QueueArn=<queue-arn>
```

Test: assign the flow to a phone number, then call. (1) Press 1 -> reaches the queue. (2) Press nothing or another key -> menu replays twice, then goodbye and disconnect.
