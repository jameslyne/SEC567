# SEC567
This repository contains files and tools relating to the SEC567, SANS Social Engineering for Penetration Testers course. This repository is not an exhaustive copy of the tools provided, but houses utilities such as the SSET (Simple Social Engineering Tool), CTF solution guide and the increasing repository of nicely styled login screens for cloning. It will be updated in line with the course and is a resource for alumni, but others are welcome to use the tools and resources too. We wish you happy and fruitful SE.

Huge thanks to Hashem Saddedin, Matt Pass, Jake Barwell and Tim Aikin for their contributions, past, present and future to the project (and generally for being awesome).

##SSET
The Simple Social Engineering toolkit is a simple tool to allow you to collect the results of a number of very common SE activities. It is easy to wrapper in to payloads such as Python, or Powershell which can in turn be combined with executable wrappers, autoruns and so on for testing anything from e-mail click rates to USB handling. We've even integrated these as fake full disk encryption helpers and left them with hard drives with a sticky attached.

The payloads of the SSET tool are purposefully very and simple. The goal of these payloads is not to rival, or even come close to the myriad of excellent backdoors and pwnage shells out there, quite the opposite in fact. The payloads are supposed to be easy to read, even for the scripting unfamiliar and provide very clear and simple functionality so that you can use them on a large scale in a company without fear they have ulterior motives. They provide scalable testing with a sensible degree of risk management. We typically will use conventional tools to demonstrate attacker capabilities, then in the same test use these tools to show the breadth of attack surface without comparable risk to 1000 Meterpreter instances floating around a large network. Lastly, the tool has generic post back capabilities so you can modify your payloads to collect some specific information for your test (e.g. a document path or username). This can be handy if you need to execute a test and customize it to prove a specific point, but avoid collecting too much information in line with new data protection regulations, or the scope.

For deployment you will want to use a web server that is routable for all your targets, either inside the company boundaries or on the Internet. The broad setup procedure is as follows:
1. Configure a web server with MySQL and PHP (latest 5.x or 7). We prefer nginx but you can use your preferred tool.
2. Create a MySQL database, e.g. mysql -u root -p; create database social_engineering. We also recommend creating a specific user for this database for the tool to use.
3. Initialize the database. Under the 000-build directory there is an init.sql file. Execute this file to reconstruct a stating state database, e.g. mysql -u root -p < init.sql
4. Edit the db.php file in the live section to match your credentials for the database. You could also elect to use server/environment variables as per the dev example if you wish.
5. Access http://server/admin and sign up, verify your account and then log in.

From here you can create your payloads, track your results and report on them.
