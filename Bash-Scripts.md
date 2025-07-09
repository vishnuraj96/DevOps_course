# Bash Scripts Assignments

Bash-Scripts

## Assignment 1: Software installation

### Script 1: Write a program to install the curl package on different Linux distros (debain, redhat, alpine). Use the case condition in the program, to check/install package. The program should exit with the stderr "Distro not identified" if the OS is different than the list.
```bash
#!/bin/bash
if [ -f /etc/os-release ]; then
. /etc/os-release
distro=$ID
else
echo "Distro not identified"
exit 1
fi
case "$distro" in
debian|ubuntu)
sudo apt update && apt install -y curl
echo "Installation completed successfully"
;;
rhel|centos)
sudo dnf makecache && dnf install -y curl
echo "Installation completed successfully"
;;
alpine)
sudo apk update && apk add curl
echo "Installation completed successfully"
;;
*)
echo "Distro not identified"
;;
esac
```


**Output:**


## Assignment 2:

### Script 1: Write a script that takes a directory path as an argument and lists all the files in that directory.
```bash
#!/bin/bash
DIR="Directory"
read -p "Enter the directory path:" DIR
if [ -d "$DIR" ]; then
echo "Listing the file:" $DIR
ls "$DIR"
else
echo "Directory '$DIR' does not exist"
fi
```


**Output:**


### Script 2: Create a script that renames all files in a directory with a .txt extension to have a prefix "backup_" (e.g., file.txt becomes backup_file.txt).
```bash
#!/bin/bash
DIR="Directory"
read -p "Enter the directory path:" DIR
if [ -d "$DIR" ]; then
for file in "$DIR"/*.txt; do
if [ -f "$file" ]; then
back=$(basename "$file")
mv "$file" "backup_$back"
fi
done
echo "Listing the file:" $DIR
ls "$DIR"
else
echo "Directory '$DIR' does not exist"
fi
```


**Output:**


### Script 3: Write a script that takes two file paths as arguments and compares them. If they are identical, print a message saying so; otherwise, display the differences.
```bash
#!/bin/bash
read -p “Enter first file path:” file1
read -p “Enter second file path:” file2
if [ ! -f “$file1” ]; then
echo “’$file1’ does not exist”
if
if [ ! -f “$file2” ]; then
echo “’$file2’ does not exist”
if
if cmp -s “$file1” “$file2”; then
echo “Both files are identical”
else
echo “’$(basename $file1)’ and ‘$(basename $file2)’ are differ. The differences are:’
diff “$file1” “$file2”
fi
```


**Output:**

If the files were the same
If the files were the differ

## Assignment 3: System Information

### Script 1: Develop a script that displays information about the system, including the operating system, kernel version, CPU information, and available memory.
```bash
#!/bin/bash
echo "======================="
echo "	System Info"
echo "======================="
echo "--------OS Information--------"
if [ -f /etc/os-release ]; then
.  /etc/os-release
echo "OS Name:	$NAME"
echo "OS Version:	$VERSION"
fi
echo "--------Kernal Information--------"
echo "Kernal Name:	$(uname -s)"
echo "Hostname:	$(uname -n)"
echo "Kernal Release:	$(uname -r)"
echo "--------CPU Information--------"
grep "model name" /proc/cpuinfo
echo "--------Memory Information--------"
grep -E 'MemTotal|MemFree|MemAvailable' /proc/meminfo
```


**Output:**


### Script 2: Write a script that checks if a specific process is running. If it is, print a message; otherwise, start the process.
```bash
#!/bin/bash
echo
read -p "Enter the process: " process
owner=$(ps aux | grep "$process" | grep -v grep | awk -F '{print $1}' | sort | uniq)
if [ -n "$owner" ]; then
echo "Process '$process' is running under user '$owner'"
else
echo "Process '$process' is not running"
echo "Attempting to start '$process'..."
sleep2
new_owner=$(ps aux | grep "$process" | grep -v grep | awk -F '{print $1}' | sort | uniq)
if [ -n "$new_owner" ]; then
echo "Process '$process' started successfully under user(s): $new_owner"
else
echo "Process failed to start"
fi
fi
```


**Output:**


### Script 3: Create a script that monitors the disk space usage of a particular partition and sends an email alert if the usage exceeds a specified threshold.
```bash
#!/bin/bash
PARTITION="/dev/sda2"
THRESHOLD=50
EMAIL="vishnuraj784@gmail.com"
USAGE=$(df -h | grep "$PARTITION" | awk '{print $5}' | sed 's/%//')
if [ "$USAGE" -ge "$THRESHOLD" ]; then
echo "Warning: The partition $PARTITION has reached ${USAGE}% disk usage. Take necessary action to free up space."
SUBJECT="Disk Space Alert: $PARTITION usage at ${USAGE}%"
MESSAGE="Warning: The partition $PARTITION has reached ${USAGE}% disk usage.\nTake necessary action to free up space."
echo -e "$MESSAGE" | mail -s "$SUBJECT" "$EMAIL"
fi
```


**Output:**

Email alert: -

## Assignment 4: Data Manipulation

### Script 1: Write a script that reads a CSV file (comma-separated values) and prints the sum of values in a specific column.
```bash
#!/bin/bash
echo
read -p "Enter the file name: " file
files=$file.csv
if [ ! -f "$files" ]; then
echo "File not found"
exit 1
fi
read -p "Enter the column number to sum:" col
sum=$(awk -v col="$col" '{ sum += $col } END { print sum }' "$files")
echo "Sum of column $col: $sum"
echo
CSV file details: -
```


**Output:**


### Script 2: Develop a script that reads a log file and extracts IP addresses that made more than a specified number of requests.
```bash
#!/bin/bash
echo
echo "IP address more than 1 specified number of requests"
echo "count	IP address"
awk '{print $1}' ip.log | sort | uniq -c | awk '$1>1'
“ip.log” file details: -
```


**Output:**


### Script 3: Create a script that takes a sentence as input and prints the number of occurrences of each word.
```bash
#!/bin/bash
read -p "Enter the sentence: " word
echo "$word" \ | tr '[:upper:]' '[:lower:]' \
| tr -d '[:punct:]' \
| tr ' ' '\n' \
| grep -v '^$' \
| sort \
| uniq -c \
| awk '{printf "%s: %d\n", $2, $1}'
```


**Output:**


## Assignment 5: Network Operations

### Script 1: Write a script that checks if a list of remote servers is reachable over SSH.
```bash
#!/bin/bash
while IFS= read -r server; do
if ssh -o BathMode=yes -o ConnectTimeout=2 your_user@"$server" "exit" 2>/dev/null; then
echo "$server is accessible"
else
echo "$server is not accessible"
fi
done < server.txt
server.txt details :-
```


**Output:**


### Script 2: Develop a script that pings a list of IP addresses and reports the average response time.
```bash
#!/bin/bash
echo
read -p "Enter the IP Address: " IP
avg=$(ping -c 1 "$IP" | tail -1 | awk -F '/' '{print $5}')
if [ -z "$avg" ]; then
echo "$IP no response"
else
echo "$IP average response time is $avg"
fi
```


**Output:**


### Script 3: Create a script that checks if a website is up by sending an HTTP request and analysing the response.
```bash
#!/bin/bash
echo
read -p "Enter the website with full address (eg:www.exapmle.com): " website
status=$(curl -o /dev/null -s -w "%{http_code}\n" "$website")
if [ "$status" -eq 200 ]; then
echo "$website is active"
else
echo "$website is not active"
fi
```


**Output:**


## Assignment 6: User Management

### Script 1: Write a script that adds a new user to the system with a specified username, home directory and password.
```bash
#!/bin/bash
echo
read -p "Enter the username: " USERNAME
read -p "Enter the home directory(eg:/directory_path): " DIR
read -s -p "Enter the password: " PWD
echo
if id "$USERNAME" &>/dev/null; then
echo "User '$USERNAME' already exists."
exit 1
fi
sudo useradd -p -m -d "$DIR" "$USERNAME"
echo "$USERNAME:$PWD" | sudo chpasswd
echo
echo "Username:" $USERNAME
echo "User directory path:" $DIR
grep "^$USERNAME:" /etc/passwd
```


**Output:**


### Script 2: Develop a script that checks the strength of a user's password.
```bash
#!/bin/bash
echo "*Password length should be minimum 8 character";
echo "*At least one uppercase and lowercase letter";
echo "*At least one digit";
echo "*At least one special character";
echo
read -p "Enter password:" pwd
echo
if ! [[ "$pwd" =~ [A-Z] ]]; then
echo "Password must contain atleast one uppercase letter."
fi
if ! [[ "$pwd" =~ [a-z] ]]; then
echo "Password must contain atleast one lowercase letter."
fi
if  [[ ${#pwd} -it 8 ]]; then
echo "Password must contain minimum 8 characters."
fi
if ! [[ "$pwd" =~ [^a-zA-Z0-9] ]]; then
echo "Password must contain atleast one special character."
fi
if ! [[ "$pwd" =~ [0-9]]]; then
echo "Password must contain atleast one digit."
exit 1
fi
echo "Password is strong."
```


**Output:**


### Script 3: Create a script that lists all users in the system and their login times.
```bash
#!/bin/bash
echo "Username	Last Login"
lastlog | awk 'NR == 1 {next}
$0~ /Never logged in/ {next}
{
printf "%-18s %s %s %s \n", $1, $(NF-4), $(NF-3), $(NF-2), $(NF-1), $NF
}'
```


**Output:**

