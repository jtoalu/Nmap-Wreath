# Utilize certain options of Nmap to reveal great information
Recently I performed the ***Wreath*** challenge on TryHackMe. One of the challenge/question is to find the OS running in the target machine. The hint of the question is:
> This will be given by the webserver. Note that Nmap is unlikely to get a valid result with -O, so use the headers from the webserver to ascertain the OS.

nmap -p 80,443 -O 10.200.101.200 returns
> Too many fingerprints match this host to give specific OS details

![](https://github.com/jtoalu/Nmap-Wreath/blob/main/Screenshot%202024-07-15%20142502.png)

To circumvent this problem, the following Nmap options were utilized

$${\color{red} nmap \space \color{lightgreen} -sC \space \color{lightblue} -sV \space{lightgreen} -O \space \color{lightblue} -p- \space \color{lightgreen} -oN wreath \space \color{orange} 10.200.101.200}$$

-sC

Performs a script scan using the default set of scripts. It is equivalent to --script=default. Some of the scripts in this category are considered intrusive and should not be run against a target network without permission. More information on https://nmap.org/book/man-nse.html

-sV (Version detection)

Enables version detection, as discussed above. Alternatively, you can use -A, which enables version detection among other things. More information on https://nmap.org/book/man-version-detection.html

-O (Enable OS detection)

Enables OS detection, as discussed above. Alternatively, you can use -A to enable OS detection along with other things. More information on https://nmap.org/book/man-os-detection.html

-p \<port ranges> (Only scan specified ports)

This option specifies which ports you want to scan and overrides the default. Individual port numbers are OK, as are ranges separated by a hyphen (e.g. 1-1023). The beginning and/or end values of a range may be omitted, causing Nmap to use 1 and 65535, respectively. So you can specify ***-p-*** to scan ports from 1 through 65535. Scanning port zero is allowed if you specify it explicitly. For IP protocol scanning (-sO), this option specifies the protocol numbers you wish to scan for (0–255). More information on 
https://nmap.org/book/man-port-specification.html

-oN <filespec> (normal output)

Requests that normal output be directed to the given filename. As discussed above, this differs slightly from interactive output. More information on https://nmap.org/book/man-output.html

These ***options*** gave the result/anwer of the challenge/question in TryHackMe.

![](https://github.com/jtoalu/Nmap-Wreath/blob/main/Screenshot%202024-07-13%20225320.png)

-on saved the result in a ***text*** file.

![](https://github.com/jtoalu/Nmap-Wreath/blob/main/Screenshot%202024-07-13%20225257.png)


Note to Self: https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax and https://stackoverflow.com/questions/11509830/how-to-add-color-to-githubs-readme-md-file
