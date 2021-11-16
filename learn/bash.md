# Public Key 
Enter ls -al ~/.ssh to see if existing SSH keys are present.
```
ls -al ~/.ssh
```



start `pwd -W`

echo "`ls -lrt`"

clear


## Colorize the ls output ##

### Colorize the ls output ##
alias ls='ls --color=auto'

## Use a long listing format ##
alias ll='ls -la'

## Show hidden files ##
```
alias l.='ls -d .* --color=auto'
```

dircolors --print-database  | clip


## Date Time Zones
```
awk -F',' '/Asia\/Kolkata/ {print $1 $4}'  data/gis/timeZones.csv
```

To copy myfile.txt to /foo/bar/myfile.txt, use:

mkdir -p /foo/bar && cp myfile.txt $_



Copy from source to an non existing path
```
mkdir –p /destination && cp –r /source/ $_
```
NOTE: this command copies all the files
cp –r for copying all folders and its content
$_ work as destination which is created in last command





mkcp() {
    test -d "$2" || mkdir -p "$2"
    cp -r "$1" "$2"
}

E.g If you want to copy 'test' file to destination directory 'd' Use,

mkcp test a/b/c/d

mkcp will first check if destination directory exists or not, if not then make it and copy source file/directory.



# Images

%w 	current width in pixels
%h 	current image height in pixels
%x 	x resolution (density)
%y 	y resolution (density)
%B 	file size of image read in bytes
%C 	image compression type

identify -format '%w %h %x %y %B %C' public/media/jpg/cto.jpg | awk '{print $5/1024}'




sort -t, -nk3 user.csv

where

    -t, - defines your delimiter as ,.

    -n - gives you numerical sort. Added since you added it in your attempt. If your user field is text only then you dont need it.

    -k3 - defines the field (key). user is the third field.


awk -F, '{ print $1/1024 $0 }' sizes | sort -nk1 > sorted



awk -F, '{ print $3, $0 }' user.csv | sort -nk2 

and for reverse order

awk -F, '{ print $3, $0 }' user.csv | sort -nrk2 


# Only files
```
find . -type f -print0 | du --files0-from=-

du -ch files*
$ du -sh ./public/
```


cd ~
code .bash_profile

create a new file called “.bash_profile” in user folder 
`(C:\Users\[User Name])`. This file is your Bash startup script file.


```
alias ls='ls --color=auto'
```
alias ls='LC_COLLATE=C ls -h --group-directories-first --color=auto'


heroku run bash

# remove folder with all contents
rm Heroku -rf

rmdir dirName


# Bash in the Visual Studio Code integrated terminal

1. Install Git from https://git-scm.com/download/win
2. Open Visual Studio Code and press and hold Ctrl + ` to open the terminal.
3. Open the command palette using Ctrl + Shift + P.
4. Type - Select Default Profile
5. Select Git Bash from the options
6. Click on the + icon in the terminal window
7. The new terminal now will be a Git Bash terminal. Give it a few seconds to load Git Bash
8. You can now toggle between the different terminals as well from the dropdown in terminal.






# Copy / Write / Append
# You can redirect the output of a command to a file:
```
cat file > copy_file
```
# or append to it
```
cat file >> copy_file
```
#If you want to write directly the command is echo 'text'
```
echo 'Hello World' > file



#!/bin/bash
```

# bash
```
alias ls='LC_COLLATE=C ls -h --group-directories-first --color=auto'
```


# Set default editor
# export EDITOR=code


# Git
alias gitc='git add . && git commit'
alias gitp='git push'
alias gith='git push heroku'


# npm
alias nrs='npm run start'
alias nrd='npm run dev'
alias nrb='npm run build'


# JQ = JSON Query
alias jq='jq-win64'



# Show current weather

# curl wttr.in/Houston?format=4
# curl wttr.in/London?format=4
# curl wttr.in/Berlin?format=4
# curl wttr.in/Pune?format=4

# wttr=$(curl -s wttr.in/Houston?format=4)
# wttr="${wttr/🌬️/" "}"
# echo 'Houston:' ${wttr:8:${#wttr}}

# wttr=$(curl -s wttr.in/London?format=4)
# wttr="${wttr/🌬️/" "}"
# echo 'London: ' ${wttr:7:${#wttr}}

# wttr=$(curl -s wttr.in/Berlin?format=4)
# wttr="${wttr/🌬️/" "}"
# echo 'Berlin: ' ${wttr:7:${#wttr}}

# wttr=$(curl -s wttr.in/Pune?format=4)
# wttr="${wttr/🌬️/" "}"
# echo 'Pune:   ' ${wttr:6:${#wttr}}

# echo 'Moon:   ' $(curl -s wttr.in/Pune?format=%m)





# Display the weather using wttr.in
```
weather() {
    location="$1"
    if [ -z "$location" ]; then
        location="pnq"
    fi

    # curl http://wttr.in/$location?lang=en
    curl http://wttr.in/$location?0
    # curl http://wttr.in/$location?format=4
   
}
```
```
weatherCity(){
   location="$1"
    if [ -z "$location" ]; then
        location="pnq"
    fi
    
    # curl -s wttr.in/$location?format=4

    wttr=$(curl -s wttr.in/$location?format=4)
    wttr="${wttr/🌬️/" "}"
    CT=`printf "%-7.7s" "$1"`           # Trailing Space
    LN=$(expr ${#1} + 1)
    echo "$CT": ${wttr:$LN:${#wttr}}

}
```

# echo "$json" | jq -r '.access_token'
```
repeat(){
    for ((i = 1; i <= $2; i++)); do
        echo $1
    done
}
```


# 0; reset
# 1; lighter than normal
# 2; darker than normal
# 3; italic
# 4; underline
# 5; blinking (slow)
# 6; blinking (fast)
# 7; reverse
# 8; hide
# 9; cross-out

NS=`printf '\033[0;m'`              # No Style
HC=`printf '\033[8;32m'`            # hide character
    
BK=`printf '\033[1;30m'`            # bold Black
BR=`printf '\033[1;31m'`            # bold Red
BG=`printf '\033[1;32m'`            # bold Green
BY=`printf '\033[1;33m'`            # bold Orange/Yellow
BB=`printf '\033[1;34m'`            # bold Blue
BP=`printf '\033[1;35m'`            # bold Purple/Magenta
BC=`printf '\033[1;36m'`            # bold Cyan
BW=`printf '\033[1;37m'`            # bold White

# High Intensity
HBK=`printf '\033[1;90m'`            # bold Black
HBR=`printf '\033[1;91m'`            # bold Red
HBG=`printf '\033[1;92m'`            # bold Green
HBY=`printf '\033[1;93m'`            # bold Orange/Yellow
HBB=`printf '\033[1;94m'`            # bold Blue
HBP=`printf '\033[1;95m'`            # bold Purple/Magenta
HBC=`printf '\033[1;96m'`            # bold Cyan
HBW=`printf '\033[1;97m'`            # bold White



# Background
BBK=`printf '\033[40m'`            # bold Black
BBR=`printf '\033[41m'`            # bold Red
BBG=`printf '\033[42m'`            # bold Green
BBY=`printf '\033[43m'`            # bold Orange/Yellow
BBB=`printf '\033[44m'`            # bold Blue
BBP=`printf '\033[45m'`            # bold Purple/Magenta
BBC=`printf '\033[46m'`            # bold Cyan
BBW=`printf '\033[47m'`            # bold White

# Background
HBBK=`printf '\033[100m'`            # bold Black
HBBR=`printf '\033[101m'`            # bold Red
HBBG=`printf '\033[102m'`            # bold Green
HBBY=`printf '\033[103m'`            # bold Orange/Yellow
HBBB=`printf '\033[104m'`            # bold Blue
HBBP=`printf '\033[105m'`            # bold Purple/Magenta
HBBC=`printf '\033[106m'`            # bold Cyan
HBBW=`printf '\033[107m'`            # bold White




weatherJson() {
    location="$1"
    if [ -z "$location" ]; then
        location="pnq"
    fi

    wttrA=$(curl -s wttr.in/$location?format=j2)
    T=$(echo "${wttrA}" | jq-win64 -r '.current_condition[0].temp_C')
    F=$(echo "${wttrA}" | jq-win64 -r '.current_condition[0].FeelsLikeC')
    H=$(echo "${wttrA}" | jq-win64 -r '.current_condition[0].humidity')
    P=$(echo "${wttrA}" | jq-win64 -r '.current_condition[0].pressure')
    W=$(echo "${wttrA}" | jq-win64 -r '.current_condition[0].precipMM')
    U=$(echo "${wttrA}" | jq-win64 -r '.current_condition[0].uvIndex')
    A=$(echo "${wttrA}" | jq-win64 -r '.current_condition[0].windspeedKmph')
    
    
    # CT=`printf "%7.7s" "$1"`            # Leading Space
    CT=`printf "%-7.7s" "$1"`           # Trailing Space

    TT=`printf %s%02d%s%02d%s 'T: ' $T '(' $F ')'`  ## Temp(feels)
    RH=`printf %s%02d 'H: ' $H`     # Relative Humidity
    PP=`printf %s%04d 'P: ' $P`     # Pressure
    UV=`printf %s%02d 'U: ' $U`     # UV Index
    WS=`printf %s%02d 'W: ' $A`     # Wind Speed
    RW=`printf %s%3.3f 'R: ' $W`    # Rain Water
    
    
    # echo $1 $'\t' T: $T'('$F')' H: $H P: $P R: $R U: $U W: $W
    echo $BBW $BK "$CT" $NS\
    $BR $TT$NS\
    $BG $RH$NS\
    $BY $PP$NS\
    $BP $UV$NS\
    $BB $WS$NS\
    $BC $RW$NS 
    
}




# date=$(date '+%Y-%m-%d %H:%M:%S')

date=$(date '+%A / %B %-d, %Y / %H:%M:%S')

# echo 'Today:' $(date '+%H:%M:%S %p / %A / %B %-d, %Y')


echo
echo 'Today:' $date
echo 
echo $BG'Welcome' $BR $USERNAME $NS






# weather 'Pune'

# weatherCity 'Houston'
# weatherCity 'London'
# weatherCity 'Berlin'
# weatherCity 'Pune'

echo 
echo Today\'s weather is
echo
# weatherJson 'Houston'
# weatherJson 'London'
# weatherJson 'Berlin'
weatherJson 'Pune'

echo 


# echo "pwd: `pwd`"
# echo "\$0: $0"
# echo "basename: `basename $0`"
# echo "dirname: `dirname $0`"
# echo "dirname/readlink: $(dirname $(readlink -f $0))"


filePath=$(dirname $(readlink -f $0))
fileName=$(basename $0)
thisFile=$filePath/$fileName
copyFile=$(echo "source '"$thisFile"'")
bashFile='~/.bash_profile'
echo $thisFile

# echo "source '"$thisFile"'">> ~/.bash_profile

# sed -n -e '/^source "'"$thisFile"'"'/!p' -e '$a''$copyFIle' '$bashFile'


# sed -n -e '/^FOOBAR=/!p' -e '$aFOOBAR=newvalue' ~/.bash_profile

# sed '/^FOOBAR=/{h;s/=.*/=newvalue/};${x;/^$/{s//FOOBAR=newvalue/;H};x}' ~/.bash_profile



#-----------------------------------
#### TO REPLACE VARIABLE VALUE
# sed -i '/^FOOBAR=/{h;s/=.*/=newValue/};${x;/^$/{s//FOOBAR=newValue/;H};x}' ${varFile}
# sed -i '/^FOOBAR=/{h;s/=.*/='${newValue}'/};${x;/^$/{s//FOOBAR='${newValue}'/;H};x}' ${varFile}

varFile=~/.bash_profile
varName=script
varValu="'star/aa/vv/dir/'"      
varValu="'"$filePath/$fileName"'"

varValu=$(echo "$varValu" | sed "s/\//\\\\\//g")
sed -i '/^'${varName}'=/{h;s/=.*/='"${varValu}"'/};${x;/^$/{s//'${varName}'='"${varValu}"'/;H};x}' ${varFile}

#-----------------------------------



#-----------------------------------
#### TO REPLACE STRING IN A FILE

# sed -i "s|my/path|my/other/path|g" myFileOfPaths.txt
# sed -i 's|/home/saeid/public_html|/home/saeid/www/domain.com/html|g' ${varFile}
varFile=~/.bash_profile
oldPath='/home/saeid/public_html'
# oldPath='/home/saeid/domain.html'
# newPath='/home/saeid/domain.html'
oldPath=$filePath/$fileName
newPath=$filePath/$fileName
sed -i 's|'${oldPath}'|'${newPath}'|g' ${varFile}
#-----------------------------------
