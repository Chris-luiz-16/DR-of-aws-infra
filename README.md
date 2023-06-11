# DR-of-aws-infra

This documentation provides an overview of the ALB (Application Load Balancer) setup for disaster recovery. The configuration involves two ALBs located in the Ohio and North Virginia regions. The ALB endpoints are pointed to the a one common domain, which serves as the entry point for the application.

To ensure high availability and mitigate the impact of outages, the domain is load balanced using a weighted route policy in a 50:50 ratio. This means that incoming traffic is evenly distributed between the ALBs in any of the 2 regions. [Let's say Virginia and Ohio region]

In the event of a failure or outage in one region, the traffic is automatically routed to the other region, providing seamless failover and uninterrupted service. This setup enhances the resilience of the infrastructure and ensures continuous availability of the application.

![DR](https://github.com/Chris-luiz-16/DR-of-aws-infra/assets/128575317/5cabb8a0-a998-4e3e-a928-e413a7b54cac)


## Disaster Recovery

This ALB setup described here serves as a disaster recovery (DR) mechanism. In the event of a failure or outage in one region, the traffic can automatically failover to the other region, ensuring continuous availability of your application.

By distributing the traffic across multiple regions, you enhance the resilience of your infrastructure. If one region becomes unavailable, the other region can handle the incoming traffic and minimize the impact on your users.

Once any region is completely down, then we can trasfer 100% of the incoming traffic to the unaffected region thereby minimizing the downtime.

![infra](https://github.com/Chris-luiz-16/DR-of-aws-infra/assets/128575317/068ade49-5f8b-4ae7-8afa-e39d940f04c6)



## Usage

To set up the ALB configuration for disaster recovery in your own environment, follow these steps:

```
1. Configure the ALBs in both the Ohio and North Virginia regions.
2. Point the ALB endpoints via aliasing to a common dommain name
3. Set up the weighted route policy in both regions with a 50:50 ratio.
```

Let's say suppose I'm having a domain name shopping.chrisich.fun and my route53 record will look like this 
<br />

![image](https://github.com/Chris-luiz-16/DR-of-aws-infra/assets/128575317/6e2aa8db-b4d7-4ab0-b7cb-60b1ea16ed53)

If N.Virginia is down, then we can change the weighted route policy to 100% in the ohio-region which will handle the incoming traffic and minimize the impact on your users.

## Contributors

- [Chris Luiz](https://github.com/Chris-luiz-16) - Project Owner
