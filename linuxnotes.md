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

