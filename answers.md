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