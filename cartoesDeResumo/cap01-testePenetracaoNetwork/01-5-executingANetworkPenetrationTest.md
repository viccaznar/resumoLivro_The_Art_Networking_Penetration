Identifique o raciocínio contido no texto. Organize os conceitos em tópicos explicativos, com resumo objetivo, robusto e simples. Para cada conceito, insira um exemplo lúdico rico e explicativo que ilustre a ideia dos conceitos mais difícieis. Insira um capítulo sobre boas práticas e cenários reais onde o que é explicado acontece com frequência em um negócio. Organize os tópicos em capítulos e subcapítulos decorados com emoticons que condizem com o que está sendo abordado. Inclua uma seção de exercícios para fixar o conteúdo, junto com a solução. Coloque o resultado em um único bloco no formato Markdown. Se houver exemplos de códigos, envolva-o entre quotes junto com o nome da linguagem de programação:

 1.5
 Executing a network penetration test
 So, you’ve gone through all the questions and determined that your organization
 needs a network penetration test. Good! What’s next? Up to now, I’ve discussed pene
tration testing as a service that you would typically pay a third-party consultant to con
duct on your behalf. However, more and more organizations are building internal red
 teams to conduct these types of exercises on a routine basis. 
DEFINITION Red team—A specialized subset of an organization’s internal secu
rity department, focused entirely on offensive security and adversarial attack
simulation exercises. Additionally, the term red team is often used to describe a
 specific type of engagement that is considered as realistic as possible, simulat
ing advanced attackers and using a goal-oriented, opportunistic approach
 rather than a scope-driven methodology
 I’m going to make an assumption from here on that you’ve been or you’re hoping to
 be placed in a role that would require you to perform a penetration test for the com
pany you work for. Maybe you have even done a handful of penetration tests already
 but feel like you could benefit from some additional guidance and direction.
 My intention in writing this book is to provide you with a “start-to-finish” methodol
ogy that you can use to conduct a thorough INPT, targeting your company or any
 other organization from which you receive written authorization to do so.
 You’ll learn the same methodology that I have matured over a decades-long career
 and used to successfully and safely execute hundreds of network penetration tests tar
geting many of the largest companies in the world. This process for executing con
trolled, simulated cyber-attacks that mimic real-world internal breach scenarios has
 proved successful in uncovering critical weaknesses in modern enterprise networks
 across all vertices. After reading this book and working through the companion exer
cises, you should have the confidence to execute an INPT, regardless of the size or
 industry of the business you’re attacking. You will work through the four phases of my
 INPT methodology using the virtual Capsulecorp Pentest network that I have set up as
 a companion to this book. Each of the four phases is broken into several chapters
 demonstrating different tools, techniques, and attack vectors that penetration testers
 use frequently during real engagements. 
1.5.1 Phase 1: Information gathering
 Imagine the engineers who designed the entire corporate network sitting down with
 you and going over a massive diagram, explaining all the zones and subnets, where
 everything is, and why they did it that way. Your job during phase 1, the information
gathering phase of a penetration test, is to come as close as you can to that level of
 understanding without the network engineers’ help (figure 1.2). The more informa
tion you gain, the better your chances of identifying a weakness. 
Throughout the first few chapters of this book, I’ll teach you how to gather all of
 the information about the target network that is necessary for you to break in. You’ll
Executing a network penetration test
 9
 Host discovery
 Identify host-specific info:- IP address- DNS name- Operating system
 Service discovery
 Enumerate listening services:- Service protocol- Software name and version- NSE script output
 targets.txt
 Final
 output
 A.
 ignore.txt
 Final
 output
 B.
 Vulnerability discovery
 Test for security weaknesses:- Missing, weak, or default credentials- Missing security updates (patches)- Insecure service configuration
 Figure 1.2 The information-gathering phase
 Protocol-specific 
target lists
 Final
 output
 C.
 List of available
 attack vectors
 learn how to perform network mapping using Nmap and discover live hosts within a
 given IP address range. You’ll also discover listening services that are running on net
work ports bound to those hosts. Then you’ll learn to interrogate these individual ser
vices for specific information, including but not limited to the following:
  Software name and version number
  Current patch and configuration settings
  Service banners and HTTP headers
  Authentication mechanisms 
In addition to using Nmap, you’ll also learn how to use other powerful open source
 pentest tools such as the Metasploit framework CrackMapExec (CME), Impacket, and
 many others to further enumerate information about network targets, services, and
 vulnerabilities that you can take advantage of to gain unauthorized access to restricted
 areas of the target network. 
1.5.2 Phase 2: Focused penetration
 Let the fun begin! The second phase of an INPT is where all the seeds planted during
 the previous phase begin to bear fruit (figure 1.3). Now that you have identified vul
nerable attack vectors throughout the environment, it’s time to compromise those
 hosts and start to take control of the network from the inside.
 During this section of the book, you’ll learn several types of attack vectors that will
 result in some form of remote code execution (RCE) on vulnerable targets. RCE means
10
 CHAPTER 1 Network penetration testing
 Deploy backdoor web shells
 Authentication,
 configuration, and patching
 vulnerabilities
 Compromise vulnerable
 database servers
 Access remote management
 services (SSH, RDP, WMI,
 SMB…)
 Exploit missing software
 patches
 Gain initial foothold into
 restricted network areas
 (Level 1)
 Figure 1.3 The focused 
penetration phase
 you can connect to a remote command prompt and type commands to your compro
mised victim that will be executed and will send output back to you at your prompt. 
I’ll also teach you how to deploy custom web shells using vulnerable web applica
tions. By the time you’re finished with this phase of the book, you’ll have successfully
 compromised and taken control over database servers, web servers, file shares, work
stations, and servers residing on Windows and Linux operating systems. 
1.5.3 Phase 3: Post-exploitation and privilege escalation
 One of my favorite security blogs is written and maintained by a respected penetration
 tester named Carlos Perez (@Carlos_Perez). The heading at the top of his page
 (https://www.darkoperator.com) absolutely fits for this section of the book: “Shell is
 only the beginning.”
 After you’ve learned how to compromise several vulnerable hosts within your tar
get environment, it’s time to take things to the next level (figure 1.4). I like to refer to
 these initial hosts that are accessible via a direct access vulnerability as level-1 hosts. This
 phase of the engagement is all about getting to level-2.
 Level-2 hosts are targets that were not initially accessible during the focused pene
tration phase because you couldn’t identify any direct weaknesses within their listen
ing services. But after you gained access to level-1 targets, you found information or
Executing a network penetration test
 11
 C. Repeat password guessing
 using discovered credentials
   to unlock access to level-2
   targets.
 B. Locate clear-text and hashed
 credentials from all level-1
 targets.
 A. Establish a persistent Meterpreter
    that automatically connects 
    back if the session dies.
 Figure 1.4 The privilege escalation phase
 Level 2: Newly accessible targets
 Move laterally
 Harvest credentials
 Maintain reliable re-entry
 Use credentials to access
 new targets
 Harvest clear-text credentials
 Harvest domain cached
 credentials
 Harvest local account password
 hashes
 Install persistent back-door
 executable
 Level 1: Compromised targets
 vectors previously unavailable to you, which allowed you to compromise a newly acces
sible level-2 system. This is referred to as pivoting.
 In this section, you’ll learn post-exploitation techniques for both Windows- and
 Linux-based operating systems. These techniques include harvesting clear-text and
 hashed account credentials to pivot to adjacent targets. You’ll practice elevating non
administrative users to admin-level privileges on compromised hosts. I’ll also teach
 you some useful tricks I’ve picked up over the years for searching passwords inside
 hidden files and folders, which are notorious for storing sensitive information. Addi
tionally, you’ll learn several different methods of obtaining a domain admin account
 (a superuser on a Windows Active Directory network).
 By the time you’ve finished with this section of the book, you’ll understand exactly
 why we say in this industry that it takes only a single compromised host for you to spread
 through a network like wildfire and eventually capture the keys to the kingdom.
 1.5.4 Phase 4: Documentation
 I realized early in my career that hiring a professional consulting firm to execute a
 network penetration test is kind of like buying a $20,000 PDF document. Without the
 report, the penetration test means nothing. You broke into the network, found a
 bunch of holes in their security, and elevated your initial access as high as it could go.
 How does that benefit the target organization? Truth be told, it doesn’t, unless you
 can provide detailed documentation illustrating exactly how you were able to do it
 and what the organization should do to ensure that you (or someone else) can’t do it
 again (figure 1.5).
 I’ve written hundreds of pentest deliverables, and I’ve had to learn—sometimes
 the hard way—what clients want to see in a report. I’ve also come to the realization
12
 CHAPTER 1 Network penetration testing
 Phase 4: Documentation
 A. Gather evidence/screenshots
 Proof of every system compromised
 Too many is usually not enough.
 C. Create final deliverable
 B. Create linear attack narratives
 Step-by-step, how you penetrated the network
 Written so non-technical readers can understand
 Detailed recommendations to fix what you found
 This is what clients pay money for.
 Figure 1.5 The documentation phase
 that they’re the ones paying thousands of dollars to read the report, so it’s probably a
 good idea to make sure they’re impressed.
 In addition to showing you exactly what to put in an engagement deliverable, I’ll
 also share some efficiency habits I’ve learned over the years that have saved thousands
 of production hours of my time—time I was then able to spend doing things I enjoy, like
 breaking into corporate networks (rather than staring at a Word document editor).
 What makes this book different from other penetration testing books?
 Looking at this book’s table of contents, you may be wondering why topics you’ve
 seen covered in other penetration testing books are missing: social engineering,
 evading antivirus software, wireless hacking, mobile and web application testing, lock
 picking—I could go on, but you get the point. In reality, all of these topics deserve
 their own books, and covering them in a single chapter doesn’t do justice to the
 breadth of information that’s available on each one. 
The purpose of this book is to arm you with the tools necessary to conduct a typical
 internal network penetration test (INTP). This engagement is sold by every pentesting
 firm out there and is the most common type of engagement you will perform, should
 you end up in a career as a professional penetration tester.
 During typical INTPs (where you will spend at least 80% of your time), you will not be
 asked (or even allowed) to touch your client’s wireless infrastructure or send email
 phishing messages to the company’s employees or try to tailgate into its physical
 datacenters. You won’t have the time or resources to properly build custom payloads
 designed to bypass the organization’s specific EDR solution.
 Rather than gloss over subjects that are interesting and definitely have value in other
 engagements, this book chooses to focus solely on the topic at hand.