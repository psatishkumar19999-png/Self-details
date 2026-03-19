# Self-details


#Self Introduction

Hi, my name is Satish, and I am from Andhra Pradesh. I completed my B.Sc. in Computer Science from Adi Kavi Nannayya University.

I started my career as a Cloud Engineer at V2 Solutions, and currently I am working with SID Global Solutions as a Site Reliability Engineer (SRE). I am currently supporting the iMobile application for ICICI Bank.

In our day-to-day operations, we use ServiceNow for ticketing, JIRA for deployments, and Microsoft Teams channels for alerts and communication.

I work mainly on application and production support, focusing on Kubernetes, networking, and platform stability. I manage and support Kubernetes clusters across multiple data centers to ensure applications run smoothly and traffic is distributed properly.

My responsibilities include Kubernetes cluster upgrades, cluster health checks, and maintaining etcd backups to ensure system stability and disaster recovery readiness.

I also handle traffic routing and ingress configurations using NGINX and Citrix load balancers. In addition, I work with Apigee API Gateway, where I perform application creation, policy configuration, and backend integrations.

As part of daily operations, I manage SSL/TLS certificate rotations, URL whitelisting, and connectivity validations to prevent production issues. I also collaborate with development teams to support JIRA-based deployments and production releases.

We often receive tasks such as pulling logs and traces, creating and updating KVM entries, performing connectivity checks, managing URL whitelisting and telnet connectivity those are related to applications.

=====================================================

Project Description (Apigee DMZ Architecture)

We are working on a banking API platform, where different internal and external applications communicate through APIs.

The setup is deployed in multiple data centers (PROD, DR, NDR) to ensure high availability and backup in case of failure.

The system has two main flows:

Inbound (External → Internal)

Outbound (Internal → External)

🔹 Inbound Flow

External users or partner systems send requests to our APIs.

The request first goes to DNS, which converts the domain into an IP address.

Then GSLB routes the request to the correct data center (PROD / DR / NDR).

After that, the request passes through multiple security layers like DDOS, Firewall, IDS/IPS, and WAF to block any unsafe traffic.

The request then reaches Citrix, which distributes the traffic to available servers.

Next, it goes to Nginx, which forwards the request to Apigee.

Apigee processes the request by applying policies like authentication and routing.

Finally, the request goes through the internal Firewall and reaches the backend application, which sends the response back.

🔹 Outbound Flow

Internal applications like
igateway.icicibankltd.com,
im-igateway.icicibankltd.com,
stg-igateway.icicibankltd.com
send requests to external APIs.

The request goes to GSLB, which selects the correct data center.

Then it goes to Citrix, which distributes the traffic.

The request enters Kubernetes through MetalLB, which handles internal routing.

It then reaches Apigee Ingress and moves to Apigee Runtime, where API rules are applied.

After that, the request goes through the Firewall to check if it is allowed.

Then it passes through the FW Proxy, which logs and monitors the request.

Next, it goes through the Internet Firewall, which is the final security check.

Finally, the request reaches the external API, and the response comes back the same way.
==================================================================================================
Short:

🎤 Interview Style Answer

I am working as an SRE for the iMobile application, which is a large-scale banking application. In our project, we manage both inbound and outbound API traffic across multiple data centers like PROD, DR, and NDR to ensure high availability and reliability.

For inbound traffic, it is mainly used by internal users like ICICI employees. The request comes from the user, goes through DNS and GSLB, then passes through multiple security layers like DDOS, firewall, IDS/IPS, and WAF. After that, it reaches the Citrix load balancer, then Nginx, and Apigee where API policies are applied before reaching backend systems.

For outbound traffic, it is mainly for external communication. Internal applications send requests, which go through GSLB and Citrix, then enter Kubernetes using MetalLB and Apigee Ingress. Apigee runtime processes the request, and then it passes through firewall, proxy, and internet firewall before reaching external systems.

We are using Apigee Hybrid deployed on Kubernetes clusters managed by Anthos on bare metal servers, which helps us achieve scalability, security, and centralized management.


