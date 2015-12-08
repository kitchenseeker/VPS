#!/bin/bash
# script to sync your transmission downloade files with google drive
# then move the data away from your vps gdrive folder
j=0
deldir=/del #your deletion folder

cd /gdrive
for x in *
  do
    file[$j]=${x}
    j=$((j+1))
  done
j=0
for y in "${file[@]}"
  do
    TID[$j]=$(cat ~/butterfly.txt | grep "$y" | awk '{print $1}')
    j=$((j+1))
  done

for z in ${!file[@]}
  do
    drive push "${file[$z]}" && transmission-remote -n ${username}:${password} -t ${TID[$z]} -move $deldir"
  done
