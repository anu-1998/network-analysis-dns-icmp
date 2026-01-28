
Analyst: Anaswara raj 

Date/Time of Incident:1.24pm

Tool Used: tcpdump

Client: YummyRecipesForMe.com


# Part 1 :  ANALYSIS REPORT
--------------------------

## 1. Incident Description

Customers were unable to access the client’s website www.yummyrecipesforme.com. 
Users reported receiving a “destination port unreachable” error.

## 2. Investigation

The analyst attempted to access the website and replicated the issue.
Network packet capture was performed using tcpdump during the attempted connection.
Packet data showed outbound UDP packets from the client machine to the DNS server at IP 203.0.113.2 on port 53.
In response, ICMP error messages were returned with the message "udp port 53 unreachable".


## 3. Findings

The DNS request from the browser failed because UDP traffic to port 53 
could not reach the destination server.
ICMP messages indicated that the DNS service was unavailable at that moment.
As DNS resolution failed, the browser could not translate the domain name into an IP address, 
leading to the website being inaccessible.

## 4. Impact

Website users experienced downtime.
DNS resolution for the domain was unavailable.
Potential customer dissatisfaction or business interruption.

## 5. Root Cause

DNS service not running or port 53 blocked by a firewall.
The issue affected UDP port 53, the default port for DNS queries.

## 6. Recommendation

Verify that the DNS server process is running on 203.0.113.2.
Ensure firewall rules allow UDP traffic on port 53.
Monitor DNS service availability using uptime or ICMP probes.
Implement DNS redundancy (secondary DNS server).

## 7. Network protocols used

| Protocol | Layer     | Function                                |
| -------- | --------- | --------------------------------------- |
| UDP      | Transport | Used to send DNS query                  |
| ICMP     | Internet  | Used to report “Port Unreachable” error |

-----------------------------------------------------



# Part 2: a summary of the problem found in the tcpdump log
----------------------------------------------------------------

The cybersecurity team providing IT services to their client organization are 
currently investigating the issue so customers access the website again.
as the part of investigation  did a tcpdump and computer send a udp dns 
request to dns server and  
requesting the IP address of yummyrecipesforme.com
The DNS server responded with an ICMP error message:
"udp port 53 unreachable"
UDP was the transport protocol being used for DNS queries.
The DNS server’s port 53 was closed or unreachable.
The error was delivered using ICMP (Internet Control Message Protocol), 
which reports network-level delivery issues.
So, the affected network service = DNS,
and the protocol involved = UDP, with ICMP used for the error response.
The ICMP message tells us no process is listening on port 53 at the destination (the DNS server).
This could mean:
The DNS service crashed or was turned off.
A firewall is blocking UDP port 53.
Misconfiguration on the DNS server.


---------------------


## Part 3: Explaination of analysis of the data and provide at least one cause of the incident.

---------------------------------------------------------------------------------------

Several customers of clients reported that they were not able to access the client company website www.yummyrecipesforme.com, 
and saw the error “destination port unreachable” after waiting for the page to load. 
as per this me and my technical team started investigating the issue.
we tried to get on to the site but recived the same error msg. . The cybersecurity team providing IT services to their client organization are 
currently investigating the issue so customers access the website again.
as the part of investigation  did a tcpdump and computer send a udp dns request to dns server and  
requesting the IP address of yummyrecipesforme.com
The DNS server responded with an ICMP error message:
"udp port 53 unreachable"
 The next step is to identify whether the DNS server is down or traffic to port 53 is blocked by the firewall. T
he DNS server might be down due to a successful Denial of Service attack or a misconfiguration. 










