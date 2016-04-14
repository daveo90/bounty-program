![alt text](https://github.com/bitDubai/media-kit/blob/master/MediaKit/Fermat%20Branding/Fermat%20Logotype/Fermat_Logo_3D.png "Fermat Logo")

# Supervision and Control tool for servers (Cloud Server)

## Introduction

The interconnection between systems, and distributed applications running on different devices is one of the basic needs in the era of globalization and the Internet , the need for sharing and finding information is solved through networks. Fermat does not escape this necessity and one of his first goals is to have a Peer-to-Peer Network (The Fermat Network) to exchange all their metadata, and information relevant to its operation.

P2P networks allow direct exchange of information, in any format, within the interconnected devices, a series of nodes that behave as equals, which provide the bandwidth and resources for the distributed computing that will operate the net. P2P networks have many great and important advantages, but one of their biggest problems is its implementation because of the complexity involved such as: most Internet nodes do not have a fixed or accessible IP address to other internet nodes, nodes connected through local networks like WiFi or Ethernet, for those who have some type of firewall and NAT.

In Fermat, as we develop and implement our peer-to-peer network (The Fermat Network), we have developed a preview of it based on a client-server architecture (Cloud Client and Cloud Server) which aims to temporarily solve the need for interconnection and Communications within the system. The client-server architecture is a distributed application model in which tasks are divided between resource providers or services, called servers, and the petitioner, called clients. A customer makes requests to another program, in this case the server, who gives an answer back.

## Reach

## Main purpose

The classic client-server paradigm does not have the strength of a P2P network. When a server is down, the client requests can not be met. In most P2P networks, resources are usually distributed across multiple network nodes. Although some leave or abandon the download; others can still end up getting data downloaded from other nodes on the network. This makes early monitoring important.

### Current development

Currently we have two components (plug-ins):

Server (Cloud Server) is a standalone program that can be executed on a computer, and has the responsibility to interact with all customers in order to transmit the desired data between them.

Client (Cloud Client) This plug-in is responsible for the interaction with the server and construction and interpretation of data packages needed to be sent and received from the server (Cloud Server).

### Bounty reach

#### Element charts or objective goals


---
| N° | Objective | Description | Percentage |
|:--:|:--------:|:-----------:|:-------------:|
| 1 |Monitoring	| Implement a monitoring tool where you could see the server status and basic information like: used up memory, CPU load, execution time, among others. | 15% |
| 2 | Alerts and Notifications | Implement an alerts and notifications mechanism when the server is down, fails or has little space in the disk.| 15% |
|3| Installation Guide | Create a detailed installation and configuration guide of the server in any computer | 10% |
|4| Monitoring Web App | Implement an internal web application for monitoring the server | 20% |
|5| Stress tests |Implement stress tests to verify the behavior and performance of the server according to traffic and overload requests, and make a final report with its results | 40% |

* Note: The Monitoring Web App item was designed to improve the quality of monitoring and was not included in the bounty, in the first agreement.

---

## Timeline

Based on the workload and the current resources available, delivery date for this reward (bounty) will be  **March 15th**.

## Evaluation

In order to consider it successful this reward (bounty) must pass the following:

* All the elements previously exposed must be performed.

* The test will be conducted based on the amount contributed by each of the developers. a mathematical calculation will be done to determine what has been the contribution of each person to complete the bounty, based of the number of elements performed successfully.

## Variables

* Engagement Level
* Key to reach goal
* Goal difficulty

| N° | Objective  | Developer | Description | Completed |
|:--:|:---------:|:-------------:| :-------------:| :-------------:|
| 1  | Monitoring | Roberto Requena | Install and Configure Monit on the AWS | 100% |
| 2  | Alerts and Notifications | Roberto Requena | Notifications via email and slack component | 100% |
| 3  | Installation guide | Roberto Requena | Documentation | 100% |
| 4  | Monitoring Web App | Roberto Requena | Angulajs application development and  rest web services| 100% |
| 5  | Stress test | Hendry Rodriguez | JMeter Stress Test and Documentation | 100% |

## Distribution

The total amount earn by this bounty is U$ 2,500 and it will be distributed as the following table shows:

| Github Username | Bounty Percentage |   U$S   |
|:---------------:|:-----------------:|:-------:|
| Hendry19901990  | 40 %              | U$ 1,000|
| Rart3001        | 60 %              | U$ 1,500|

## Demo Day

https://www.youtube.com/watch?v=94rhQMNO9mY

## Other links

* http://cloud.fermat.org
* http://fermat.org/cloud-server/fermat-cloud-server.tar.gz
