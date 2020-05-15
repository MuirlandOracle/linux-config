#Prompt anonymisation and/or Timestamping
##Add the following function to .bashrc or .bash_aliases

```cpro () { usage () ( echo "Usage:"; echo "cpro +anon|-anon|+time|-time"; ); if [ $# -eq 0 ]; then usage; return; fi; time=0; anon=0; timelock=false; anonlock=false; for input in "$@"; do case "$input" in "+time") time=$(($time + 1)); if [ $timelock == true ]; then usage; return; else timelock=true; fi ;; "-time") time=$(($time - 1)); if [ $timelock == true ]; then usage; return; else timelock=true; fi ;; "+anon") anon=$(($anon + 1)); if [ $anonlock == true ]; then usage; return; else anonlock=true; fi ;; "-anon") anon=$(($anon - 1)); if [ $anonlock == true ]; then usage; return; else anonlock=true; fi;; *) usage; return; esac; done; if [ $anon == 1 ]; then export PS1="$(echo $PS1 | sed -e 's/\\\u/anon/g' -e 's/\\\h/anonymised-terminal/g') ";  elif [ $anon == -1 ]; then export PS1="$(echo $PS1 | sed -e 's/anon/\\u/g' -e 's/anonymised-terminal/\\h/g') "; fi; if [ $time == 1 ]; then export PS1="$(echo $PS1 | sed -e 's/\\\[\\033/\[\\D{%F %T}] \\\[\\033/') "; elif [ $time == -1 ]; then export PS1="$(echo $PS1 | sed -e 's/\[\\D{%F %T}] //g') "; fi}```


###Usage:
```cpro +anon|-anon|+time|-time```
* +anon     Anonymises terminal prompt
* -anon     Restores terminal prompt
* +time     Adds a timestamp at the start of the terminal prompt
* -time     Removes the timestamp from the start of the terminal prompt
