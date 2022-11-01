# 10 Linux commands with example

## [apropos]()
#### apropos - quick to search for command using keyword
``` 
apropos git
```
![apropos](https://github.com/InvisibleAB/Altschool-exercise-/blob/main/Screenshot%202022-11-01%20at%2015.20.06.png)

## [sed]()
#### sed - stream editor for filtering and transforming text
###### Example: replace every 'yes' to 'no' in workbook file
``` 
sed 's/yes/no/g' workbook
```
![sed](https://github.com/InvisibleAB/Altschool-exercise-/blob/main/Screenshot%202022-11-01%20at%2015.30.51.png)

## [sort]()
#### sort - sort lines of text files
###### Example: sort workbook file
``` 
sort workbook
```
![sort](https://github.com/InvisibleAB/Altschool-exercise-/blob/main/Screenshot%202022-11-01%20at%2015.39.13.png)

## [chown]()
#### chown - change file ownership 
###### Example: chnage workbook file owner to root and group to root 
``` 
sudo chown root:root workbook
```
![chwon](https://github.com/InvisibleAB/Altschool-exercise-/blob/main/Screenshot%202022-11-01%20at%2015.42.12.png)

## [lsattr]()
#### lsattr- list file attributes 
###### Example: list workbook file attribute
``` 
sudo lsattr workbook
```
![lsattr](https://github.com/InvisibleAB/Altschool-exercise-/blob/main/Screenshot%202022-11-01%20at%2015.44.52.png)

## [chattr]()
#### chattr- change file attributes 
###### Example: change workbook file attribute
``` 
sudo chattr +i workbook
```
![chattr](https://github.com/InvisibleAB/Altschool-exercise-/blob/main/Screenshot%202022-11-01%20at%2015.45.43.png)


## [ip route]()
#### ip route- list ip routes 
``` 
ip route
```
![ip](https://github.com/InvisibleAB/Altschool-exercise-/blob/main/Screenshot%202022-11-01%20at%2015.47.26.png)

## [tar]()
#### tar - archive utility  
###### Example: archive workbook file
``` 
sudo tar cfP  archive.tar workbook
```
![tar](https://github.com/InvisibleAB/Altschool-exercise-/blob/main/Screenshot%202022-11-01%20at%2015.53.46.png)

## [gzip]()
#### gzip- compress file to gzip  
###### Example: compress workbook file
``` 
gzip workbook
```
![gzip](https://github.com/InvisibleAB/Altschool-exercise-/blob/main/Screenshot%202022-11-01%20at%2017.48.25.png)

## [scp]()
#### scp- copy file to another host  
###### Example: copy hello.txt file to another host
``` 
scp hello.txt username@ip:/home/bob/
```
![scp](https://github.com/InvisibleAB/Altschool-exercise-/blob/main/Screenshot%202022-11-01%20at%2017.51.18.png)

