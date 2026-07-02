---
title: "Week 11 Worklog"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.11. </b> "
---

### Week 11 Objectives:

* Implement asynchronous messaging using Amazon SNS and Amazon SQS.
* Configure monitoring and logging with Amazon CloudWatch.
* Test and validate the messaging workflow and system monitoring.
* Prepare the project for final deployment and demonstration.

### Tasks to be carried out this week:

| Day | Task                                                                                                                                                              | Start Date | Completion Date | Reference Material                                                   |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------- | -------------------------------------------------------------------- |
| 72  | - Study Amazon SNS concepts and notification workflow<br>- Create SNS Topic and configure subscriptions<br>- Test message publishing                              | 06/29/2026 | 06/29/2026      | https://docs.aws.amazon.com/sns/                                     |
| 73  | - Study Amazon SQS concepts (Standard Queue, FIFO Queue, DLQ)<br>- Create and configure SQS queues<br>- Test sending and receiving messages                       | 06/30/2026 | 06/30/2026      | https://docs.aws.amazon.com/sqs/                                     |
| 74  | - Integrate Amazon SNS with Amazon SQS<br>- Configure queue access policies<br>- Verify end-to-end message delivery                                               | 07/01/2026 | 07/01/2026      | https://docs.aws.amazon.com/sns/latest/dg/sns-sqs-as-subscriber.html |
| 75  | - Configure Amazon CloudWatch Logs and Metrics<br>- Create CloudWatch Alarms to monitor application health<br>- Verify log collection                             | 07/02/2026 | 07/02/2026      | https://docs.aws.amazon.com/cloudwatch/                              |
| 76  | - Perform end-to-end testing of the messaging workflow<br>- Analyze CloudWatch metrics and logs<br>- Resolve configuration issues and finalize the implementation | 07/03/2026 | 07/03/2026      | https://docs.aws.amazon.com/                                         |

### Week 11 Achievements:

* Successfully implemented Amazon SNS to publish notifications between application components.

* Configured Amazon SQS queues to support reliable asynchronous message processing.

* Integrated Amazon SNS with Amazon SQS and verified successful message delivery.

* Configured Amazon CloudWatch to collect application logs, monitor metrics, and trigger alarms for abnormal system behavior.

* Tested the complete messaging workflow and confirmed that messages were processed correctly.

* Improved understanding of event-driven architecture using AWS messaging services.

* Enhanced system observability through CloudWatch monitoring, logging, and alerting.

* Completed the implementation and testing of the messaging and monitoring components, preparing the project for the final presentation and deployment.
