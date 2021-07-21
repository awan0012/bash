# bash

1. Special Variables:

The following are the other unique preset variables:

$#: number of command line parameters that were passed to the script.
$@: All the parameters sent to the script.
$?: The end status of the last process to execute.
$$: The Process ID of the current script.
$USER: The user executing the script.
$HOSTNAME: The hostname of the machine executing the script.
$SECONDS: The number of seconds the script has been running for.
$RANDOM: Returns a random number.
$LINENO: Returns the current line number of the script.

------------------------------------------------------------------------------------------------------------------------------------------------------------------

25. System Maintenance
This little Linux shell script upgrades and cleans the system automatically instead of doing it manually.

#!/bin/bash

echo -e "\n$(date "+%d-%m-%Y --- %T") --- Starting work\n"

apt-get update
apt-get -y upgrade

apt-get -y autoremove
apt-get autoclean

echo -e "\n$(date "+%T") \t Script Terminated"

#You need to run this script as a root user.
------------------------------------------------------------------------------------------------------------------------------------------------------------------
24. Display Server Stats
This example will show you a quick server stats. As a system administrator, this bash script will help you get important details like uptime, last logins, disk, and memory usage for a Linux machine.

#!/bin/bash
date
echo "uptime:"
uptime
echo "Currently connected:"
w
echo "--------------------"
echo "Last logins:"
last -a | head -3
echo "--------------------"
echo "Disk and memory usage:"
df -h | xargs | awk '{print "Free/total disk: " $11 " / " $9}'
free -m | xargs | awk '{print "Free/total memory: " $17 " / " $8 " MB"}'
echo "--------------------"

#You need to run the script as a root user.
----------------------------------------------------------------------------------------------------------------------------------------------------------------
20. Print Number of Files and Folders
In our next example, the Linux bash script finds the number of files or folders present inside a given directory. It uses the Linux ‘find‘ command. Users will be asked to input the directory name where you want to search for files from the command-line.

#!/bin/bash

if [ -d "$@" ]; then
echo "Files found: $(find "$@" -type f | wc -l)"
echo "Folders found: $(find "$@" -type d | wc -l)"
else
echo "[ERROR] Please try again."
exit 1
fi
-----------------------------------------------------------------------------------------------------------------------------------------------------------------
19. Print Files With Line Count
In our example, we shall write a bash script that will print all files with there line count in the current directory.

#!/usr/bin/env bash
for F in *
do
if [[ -f $F ]]
then
echo $F: $(cat $F | wc -l)
fi
done
#You can see that we used a for loop to get the file and then used the cat command to count lines.
------------------------------------------------------------------------------------------------------------------------------------------------------------------
18. Deleting Files
Using a bash script, you can delete a file as well. In the example, the user will be asked to provide the filename as input and will delete it if it exists. It uses the Linux rm command for the deletion here.

#!/bin/bash
echo -n "Enter filename ->"
read name
rm -i $name
echo "File Deleted"
#deleting files made easy
------------------------------------------------------------------------------------------------------------------------------------------------------------------
17. Reading Files
Using Bash you can read files very effectively. The below example will showcase how to read a file using shell scripts. Create a file called ‘companies.txt’ with the following contents.
#!/bin/bash
file='companies.txt'
while read line; do
echo $line
done < $file
#Reading Files
------------------------------------------------------------------------------------------------------------------------------------------------------------------
Case -->

# !/bin/bash

# Take user Input
echo "Enter Two numbers : "
read a
read b

# Input type of operation
echo "Enter Choice :"
echo "1. Addition"
echo "2. Subtraction"
echo "3. Multiplication"
echo "4. Division"
read ch

# Switch Case to perform
# calculator operations
case $ch in
1)res=`echo $a + $b | bc`
;;
2)res=`echo $a - $b | bc`
;;
3)res=`echo $a \* $b | bc`
;;
4)res=`echo "scale=2; $a / $b" | bc`
;;
esac
echo "Result : $res"


















