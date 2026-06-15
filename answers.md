## Task 1

Command:
grep -Ecv '^#' firewall.log

Result:
100000

Explanation:
The regex ^# matches header lines that begin with #. The -v option excludes those lines and -c counts only the firewall events.

## Task 2

Command:
grep -Ec '^[0-9-]+ [0-9:]+ (DROP|REJECT) ' firewall.log

Result:
60156

Explanation:
The group (DROP|REJECT) uses alternation to match either blocked action. The spaces ensure the match occurs in the action field.

## Task 3

Command:
grep -Ec '^[0-9-]+ [0-9:]+ [A-Z]+ [A-Z]+ 11\.' firewall.log

Result:
33217

Explanation:
The expression 11\. matches source IP addresses beginning with 11. The dot is escaped so it is treated as a literal period.

## Task 4

Command:
grep -Ec '[0-9]{7}$' firewall.log

Result:
2343

Explanation:
The regex [0-9]{7} matches exactly seven digits and the $ anchor ensures that the packet size field is at the end of the line.