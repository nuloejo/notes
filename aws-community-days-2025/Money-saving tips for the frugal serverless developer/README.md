# Money-saving tips for the frugal serverless developer

<a href=https://awscommunityday.cz/2025/sessions/acd200>Money-saving tips for the frugal serverless developer</a>

<a href="https://www.linkedin.com/in/theburningmonk/">By Yan Cui</a>

## How to keep CloudWatch logs cost under control

* Do structured logging. Log at INFO or above in production.
* Sample DEBUG logs in production. eg. 5% of services.
* Set log retetion of logs to 30 days.
* In case of further log processing with CloudWatch as middleman
* Remember system messages.

## Right Sizing the lambda functions.

* Use ARM Architecture
    * ARM is about 25% cheaper
* No lambda-to-lambda invocations
* Synchronous lambda to lambda are almost always a sign of bad design
    * Run everything in the same function
* Asynchronous invocations

## Caching

_Caching is a cheat code for building performant & scalable applications._

* Client side caching
* CF edge caching
* Application level caching
    * Momento instead of ElastiCache

## Choose the right service for your workload

_Every architectural decision is a ***buying decision***_

* Services that charge by uptime are orders of magnitude cheaper at scale.

### Laws of serverless architecture

1. make cost a Non-Functional Requirement
2. Systems that Last Align Cost to Business
3. Architecting is a Series of Trade-offs
4. Unobserved Systems Lead to Unknown Costs
5. Cost Aware Architectures Implement Cost Control
6. Cost Optimization is Incremental
7. Unchalenged Success Leads to Assumptions
