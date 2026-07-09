---
title: "Blog 2"
date: 2026-07-01
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---
# [AWS/SECURITY] HOW TO RUN TRADITIONAL WEB APPLICATIONS ON AWS NITRO ENCLAVES WITHOUT MODIFYING THE SOURCE CODE

Hello AWS Study Group VN!

While learning about AWS Nitro Enclaves, I came across an interesting article published by AWS describing how traditional web applications can be migrated into an Enclave environment with little to no changes to their source code.

Since the original article was published on the AWS China Blog, I read, translated, and summarized the key ideas. If there are any inaccuracies or missing points, I would greatly appreciate your feedback.

## WHAT IS AWS NITRO ENCLAVES?

AWS Nitro Enclaves is an isolated compute environment created from an Amazon EC2 instance using the AWS Nitro Hypervisor.

Its primary purpose is to securely process highly sensitive data such as:

- Encryption keys
- Financial data
- Healthcare records
- Personally identifiable information (PII)
- Other security-critical workloads

One of the unique characteristics of Nitro Enclaves is its strong isolation. An Enclave has:

- No IP address
- No Internet connectivity
- No direct SSH access
- No persistent storage

All communication with the Enclave must go through VSOCK and the parent EC2 instance.

This isolation provides a very high level of security, but it also makes migrating existing applications into an Enclave more challenging.

## THE CHALLENGE OF MIGRATING TRADITIONAL WEB APPLICATIONS

Most web applications communicate over TCP/IP using HTTP or HTTPS.

However, Nitro Enclaves do not support standard network communication. Instead, they rely exclusively on VSOCK.

If developers migrate an application directly into an Enclave, they would typically need to modify a significant amount of source code to replace TCP/IP communication with VSOCK.

For mature production systems or legacy applications, this process can be time-consuming and risky because it may affect the application's existing business logic.

## THE SOLUTION PROPOSED BY AWS

One of the most interesting ideas presented in the article is using **SOCAT** as a proxy layer to translate communication between HTTP and VSOCK.

The architecture consists of two proxy components:

- A proxy running on the parent EC2 instance accepts incoming HTTP connections and forwards them to the Enclave through VSOCK.
- Another proxy inside the Enclave converts VSOCK traffic back into HTTP so the application can process requests normally.

The same process works in reverse for outgoing responses.

If an application inside the Enclave needs to access external services, the proxy converts HTTP traffic into VSOCK, allowing the parent EC2 instance to perform the network communication on behalf of the Enclave.

With this approach, applications can continue operating almost as if they were running on a standard Linux server, requiring minimal or no modifications to their application logic.

## DEPLOYMENT PROCESS

According to the AWS article, the deployment process can be summarized as follows:

- Install the Nitro Enclaves CLI and Developer Tools.
- Build the application into a Docker image.
- Convert the Docker image into an EIF (Enclave Image File).
- Launch the Enclave using the Nitro CLI.
- Deploy two SOCAT proxy instances—one on the parent EC2 instance and one inside the Enclave.
- Access the application through the parent EC2 instance, where all traffic is forwarded into the Enclave via VSOCK.

## WHAT I FOUND INTERESTING

What impressed me most about this approach is that AWS does not require developers to rewrite an entire application simply because the communication mechanism changes.

Instead, introducing a lightweight proxy layer allows existing applications to be reused, significantly reducing both migration effort and implementation time when moving workloads into a more secure environment.

This is also a great example of combining an open-source tool like SOCAT with AWS services to solve compatibility challenges while preserving the isolation and security guarantees provided by Nitro Enclaves.

Of course, there are still several factors to consider, such as proxy performance, traffic monitoring, and the overall system architecture. Before deploying this solution in production, it is important to evaluate whether it meets the specific requirements of your application.

## CONCLUSION

In my opinion, AWS Nitro Enclaves is a fascinating service for anyone interested in cloud security or building systems that process sensitive information.

This article demonstrates a practical migration strategy: instead of rewriting an entire application to support Enclaves, developers can introduce a protocol translation layer that significantly reduces migration effort while still benefiting from the strong security isolation provided by Nitro Enclaves.

This is my first time researching and summarizing this topic. If I made any mistakes during the translation or interpretation of the original article, I would sincerely appreciate your feedback.

**Reference (Original Chinese Article):**

AWS China Blog – Running Traditional Web Application Migration Practices in AWS Nitro Enclaves

https://aws.amazon.com/cn/blogs/china/running-traditional-web-application-migration-practices-in-aws-nitro-enclaves/

![](/images/3-BlogsTranslated/Blog2-1.jpg)
![](/images/3-BlogsTranslated/Blog2-2.jpg)
