# Commands

## Unix name 

```
root@047cca61b24a:~# uname
Linux
```
## Scenario 1
Imagine you are a junior developer , figure out application logs . 
### PWD
```
root@047cca61b24a:~# pwd
/root
```
### Ls -l 
You can display files in a directory and their necessary permissions. 
```
root@047cca61b24a:~# ls -l 
total 8
-rw-r--r-- 1 root root 66 Jan 23 11:48 db_response.txt
-rw-r--r-- 1 root root 86 Jan 23 11:48 health_response.txt
```
** Identify files as - , directory as d and virtual links as i. 
### cat 
Display the content of a file. Cat means concatanate. 
```
root@047cca61b24a:~# cat db_response.txt 
HTTP/1.1 200 OK
Server: PostgreSQL
Content-Type: application/json
```
#### Cat 2 
Combine the contents of multiple files. 
```
root@047cca61b24a:~# cat db_response.txt health_response.txt > merged_response.txt
```
### grep 
Filter out all the contents of the file
```
cat merged_response.txt | grep memory
root@047cca61b24a:~# cat merged_response.txt | grep memory
{"status": "healthy", "database": "connected", "cache": "available", "memory": "65%"}
```
### Grep 2
Output the contents of the grep into a file
```
root@047cca61b24a:~# cat merged_response.txt | grep memory > memory_logs.txt
root@047cca61b24a:~# cat me
memory_logs.txt      merged_response.txt  
root@047cca61b24a:~# cat memory_logs.txt 
{"status": "healthy", "database": "connected", "cache": "available", "memory": "65%"}
```

### CP
copy file into backup not in same directory
#### Command
```
cp merged_response.txt alpha/merged_response_backup.txt
```
#### Response
```
root@047cca61b24a:~# cat alpha/merged_response_backup.txt 
HTTP/1.1 200 OK
Server: PostgreSQL
Content-Type: application/json
{"status": "healthy", "database": "connected", "cache": "available", "memory": "65%"}
```
###  Count errors wc Word Count
#### Command 
```
cat alpha/merged_response_backup.txt | grep "connected" | wc -l
```
#### Response
````
1
````
### Find the conf file 
#### Find the file in the current directory
```
find . -name "*me*"   
```
#### Find the file in root directory
```
find / -name "*me*"
```
#### Response
```
./alpha/merged_response_backup.txt
./memory_logs.txt
./merged_response.txt
```
#### Search the conf file 
```
find . -name "*me*" | grep memory
```
#### Response
```
./memory_logs.txt
```
### Diff between 2 files 
#### 
```
diff s1.txt s2.txt 
```
### Get metadata about a running server 
Gets you metadata from the running server. 
#### Request 
```
curl -I http://localhost:5432
```
#### Response
```
HTTP/1.1 200 OK
Server: PostgreSQL
Content-Type: application/json
```
#### Text Editor Commands
- start file -  vim  
- go back - :q! / :wq
- save if changes exist :x 
- save and quit :wq / ZZ

#### File permissions
All read permissions for user, group and others
```
chmod 444 db.conf 
```
Read write and execute 
```
chmod 777 db.conf
```
Read and write

```
chmod 666 db.conf
```

### Curl commands 

1. curl -LsSf https://astral.sh/uv/install.sh
This part fetches a script from the URL. The flags mean:

-L: Follow redirects (in case the URL redirects somewhere else).

-s: Silent mode (don’t show progress meter).

-S: When used with -s, it makes curl show errors if they occur.

-f: Fail silently on server errors (like 404 or 500).

So this part silently tries to download the script located at https://astral.sh/uv/install.sh, and errors out cleanly if it fails.

2. | sh
This pipes (|) the downloaded script to the sh shell, meaning the script will be executed immediately in a shell environment.






