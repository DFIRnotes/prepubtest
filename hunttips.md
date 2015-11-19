---
title: This is my title
layout: post
---

Hunting investigations should be SMART, and more over must have a scope and a terminating condition.
Measurement can be simple success/fail (did we find it?) or the number of incidents and/or SIEM/IPS rules generated or updated.

*In fact, one of the chief goals of hunting should be to improve your automated detection capabilities by prototyping new ways to detect malicious activity and turning those prototypes into production detection capabilities.* -- David Bianco, "A Simple Hunting Maturity Model"

Hunting starters
----

* With a small collection of network traffic/logs/flows, for a particular zone, time-bounded:
  * Characterise the traffic as a whole.
    * Explain everything, and note anything you cannot explain.
  * Isolate any possible incidents and report them, note any potential follow-on hunts.
    
* With a given system:
  * Assume compromise by reasonably competent attackers. 
    * Select a scenario if needed such as "email phish-to exe, system compromise". 
    * Look for the detectable artifacts of the attack phases, techniques
      * Is there suspicious download or upload activity?
      * Autoruns and scheduled tasks?
      * Was there any scanning or sweeping of unrelated network resources?
      
* With business critical data (of a specific type):
  * Where should it be in the network?
  * Where shouldn't it be (in the clear?) ?
    * Can you find it there anyway?
  * Isolate any possible incidents and report them, note any potential follow-on hunts.

* With a hosting platform:
  * What vulnerable applications can you find from Internet sources (external scan, open source intel?)
    * Can you find uploaded malware or tools? Were they executed? Successfully?
  * Isolate any possible incidents and report them, note any potential follow-on hunts.
    
(Slightly) advanced techniques:
----

* Port/protocol mismatches : non-HTTP on 80, non-TLS on 443, ...
* Least frequent (long tail) analysis of a data set eg :  DNS queries, autoruns, services, port usage, user-agents, banners ... (Ref: SEC511)
* Long running network sessions : possible exfil or tunnel traffic
* Periodic sessions or connections (every hour, every day, every third thursday if the moon is waxing) : possible beaconing or C2
* After closing a case, take the new indicators back to historical log and packet data in other scopes (ref: HMM1)


Refs, Sources
----

* Eric Conrad, Seth Misenar, & SANS Institute. *SEC511 : Continuous Monitoring and Security Operations* (2015) [course information](https://www.sans.org/course/continuous-monitoring-security-operations) as well as SEC504, SEC503, FOR572, FOR508
* David Bianco, "A Simple Hunting Maturity Model" *Detect Respond Blog* [direct link](http://detect-respond.blogspot.com/2015/10/a-simple-hunting-maturity-model.html)
* Carson Zimmerman & MITRE. Ten Strategies of a World Class Cybersecurity Operations Center. "Chapter 11: Strategy 9: Be a Sophisticated Consumer
and Producer of Cyber Threat Intelligence" [book download](http://www.mitre.org/publications/all/ten-strategies-of-a-world-class-cybersecurity-operations-center) (aka RedQueen book) 
* Michael McFail and Ben Actis, Mitre, & OST.info *Network Flow Analysis and Hunting* [course information, downloads](http://opensecuritytraining.info/Flow.html) (aka FLOW)
* Reid Gilman, Mitre, & OST.info *PCAP Analysis and Hunting*, [course information, downloads](http://opensecuritytraining.info/Pcap.html) (aka PCAP)
