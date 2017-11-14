# Week 9 Project: Honeypots

For this project, we deployed a few honeypots using the Modern Honeypot Network. We deployed 4 f1-micro instances on Google Compute Engine running Ubuntu 14.04. One of these was used as the admin VM, while the other three were deployed as honeypots. The following honeypots were deployed:
* Dionaea (honeypot-1)
* Snort (honeypot-3)
* p0f (honeypot-4)

## Issues Encountered

I also attempted to deploy Cowrie onto a fourth honeypot; however, I ran into some issues with a specific error being emitted by a dependency (about the Python version) while it was installing. When I ran the installer a second time, it seemed to finish successfully, but the honeypot did not seem to be picking up anything (or working).

## Summary of Data

The three honeypots were deployed and kept open for a 4-hour period (at night Eastern time). Honeypot 1 (Dionaea) was kept open for about 45 minutes more. The following statistics were gleaned from the export and the dashboard's data:
* There were **624** total attacks across all 3 honeypots (dionaea: 395, p0f: 157, snort: 72).
* The top attacked port was **port 80** (HTTP, 156 attacks), followed by port 23 (Telnet, 105 times), port 5060 (SIP, 45 times), port 445 (Microsoft Active Directory, 43 times), and port 22 (SSH, 26 times).
* Two of the top 5 attacker IPs are **based in France with a whopping 116 attacks**! One from Spain attacked 62 times and another two from Russia attacked a total of 27 times.
* Of the attack signatures obtained by the Snort honeypot, the signature most detected was **"ET DROP Dshield Block Listed Source group 1" (19 attacks)**. The second most detected signature was "ET CINS Active Threat Intelligence Poor Reputation IP TCP group 4" (8 times).

It seems that a signature of "ET DROP Dshield Block Listed Source group 1" signifies that the originating IP is an emerging threat, while the other signature ("ET CINS Active Threat Intelligence Poor Reputation IP TCP group 4") denotes that the IP already has a bad reputation with Sentinel IPS's CINS Intelligence System.

## Other Notes/Questions

None.
