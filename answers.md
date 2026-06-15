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

## Task 5

Command:
sed -En 's/^([0-9-]+) [0-9:]+ ([A-Z]+) ([A-Z]+).*/\1 \2 \3/p' firewall.log | head -5

Result:
2018-05-25 FORWARD TCP
2018-02-22 FORWARD UDP
2018-03-20 REJECT UDP
2018-11-08 REJECT TCP
2018-07-24 REJECT TCP

Explanation:
The command uses capture groups to extract the date, action and protocol fields and rebuilds the output using backreferences.

## Task 6

Command:
grep -Ec '^.* ACCEPT TCP .* [0-9]+ 80 [0-9]+$' firewall.log

Result:
93

Explanation:
The regex combines ACCEPT, TCP and destination port 80 in a single pattern and anchors the destination port before the final size field.

## Task 7

Command:
grep -Ec '^[0-9-]+ 0[0-2]:' firewall.log

Result:
13138

Explanation:
The range 0[0-2] matches hours 00, 01 and 02. The expression is anchored immediately after the date field.