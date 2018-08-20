# Week-1

The plan for this week is to get an overview of the course, and delve into the first topic.
Every third week (more or less) we will have both Wednesday and Friday.
Typically Fridays will be workshop days.

## What to Read

Please open and skim:

OWASP Top 10 - 2017
The Ten Most Critical Web Application Security Risks
[PDF](../Documents/OWASP Top 10-2017.pdf)

## Learning Goals

After this week you will be able to:
* Explain the difference between prevention, detection and recovery for systems you develop.
* Set up a firewall on ubuntu and examine the log files.
* Set up a remote logging server, and use that to register logins to an ubuntu server.
* Plan how to use a cloud based logging service to enable anomaly detection.

## Exercises

An important thing to prevent attacks is to have a firewall in place. However, a firewall also allow us to see if our system is under attack by logging those attacks.

Ubuntu comes with a build in firewall called `ufw (**u**ncomplicated **f**ire**w**all).
* Create a droplet on digital ocean
* Enable the firewall ([instructions are here](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-with-ufw-on-ubuntu-16-04)).
  **WARNING**: make sure to allow SSH before starting the firewall 😀
* Enable logging for the firewall ([this answer gives the commands](https://serverfault.com/questions/516838/where-are-the-logs-for-ufw-located-on-ubuntu-server))
* Find the log, and find out
  ([this might be helpful](https://help.ubuntu.com/community/UFW) - look at the end)
  - From which IP addresses do you get visitors
  - What ports do your visitors attempt to use
  - Where are those IP addresses located
  - What services are behind those ports
* Let it run until Thursday and bring your answers to class.
This magic linux script will tell which ports were examined, the next from which address:
  - `grep -Po '(?<=DPT=)[^ ]*' /var/log/ufw.log | sort | uniq -c`
  - `grep -Po '(?<=SRC=)[^ ]*' /var/log/ufw.log | sort | uniq -c`
  - (see http://perldoc.perl.org/perlre.html for explanation)
