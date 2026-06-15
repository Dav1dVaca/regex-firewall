## Task 1

Command:
grep -Ecv '^#' firewall.log

Result:
100000

Explanation:
The regex ^# matches header lines that begin with #. The -v option excludes those lines and -c counts only the firewall events.