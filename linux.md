file [file] - see basic info about file
exiftool [file.jpg] - see file exif data  (not installed it lookes like)


Put my SSH keys on another computer:  ssh-copy-id linuxdev@rdulab-ud8
open nvim remotely with my config:  nvim scp://linuxdev@rdulab-ud8//home/linuxdev/Downloads/
   allegedly - untested


Can I add a zellij/wezterm hotkey that maps to CtrlX CtrlE?
I should convert all these to md and fix my 4 spaces
Update fzf to match whatever nvim is doing.  rg?  fd?


Log terminal output with it still visible in the terminal
   Doesn't get created until command is done running
   command |& tee output.txt
   Appends instead of overwrites:  command |& tee -a output.txt
   https://askubuntu.com/questions/420981/how-do-i-save-terminal-output-to-a-file



Memeblast:
   ~/Downloads$ w #lists displays, probably only one, use the number for the next command
   ~/Downloads$ export DISPLAY=:1
   ~/Downloads$ eog trash_bureaucrat.png

   xmessage "hello world" displays a pop up I think



get into mounted build from command line
   docker exec -it [deployable name] bash


get size of folder:  du -hs /path/to/directory


find files:
   rg --files | rg filename
      can be a regexp?

   find . -name "*.map"
      Then I can pipe that into a grep .map for highlighting I guess
      exclude with exclamation point:   find -name "*.bit*" ! -path "*path*"
      I think I have to do something else to get it to follow simlinks


      print them all:  for file in $(find -name "*.crc*"); do cat "$file"; echo; done

   or just fzf enter and then start typing
   or Ctrl+T to do autocomplete with fzf


Command line history "event designators"

   !! - whole line of last command (command and all args)
   !* - all arguments of last command
   !$ - first argument of last command  (is that right?  seems like last would make more sense)

   s performs substitutions. For example, to change “foo” with “bar” in the last argument:
   ls /tmp/foo.txt
   echo !$:s/foo/bar/

   gs substitutes all occurrences, not just the first one:
   echo foo foo foo
   echo !*:gs/foo/bar

   p is a somewhat special modifier that is useful for cautious users. It prints the final command but does not execute it: 
   ls /tmp/foo.txt
   echo !$:s/foo/bar/:p
   Not Rename:  mv filename.txt !#:1:p:r.log


   Range of args:
   Imagine you run a command, and realise that the arguments were correct, but
   $ grep '(ping|pong)' afile
   I wanted to match ping or pong in a file, but I used grep rather than egrep.
   I start typing egrep, but I don’t want to re-type the other arguments, so I can use the !:1-$ shortcut to ask for all the arguments to the previous command from the second one (remember they’re zero-indexed) to the last one (represented by the $ sign):
   $ egrep !:1-$
   egrep '(ping|pong)' afile
   This can also be used with any other numbers


   !#:1 – The ‘The Current Line’ One
   I spent years occasionally wondering if I could reference an argument on the current line before finally looking it up and learning it. I wish I’d done so well before.
   I most commonly use it to make backup files
   $ cp /path/to/some/file !#:1.bak
   cp /path/to/some/file /path/to/some/file.bak


   Backup:  cp /path/to/some/file !#:1.bak
   Rename:  mv filename.txt !#:1:r.log


Remount fstab things: mount -a

Chaining commands
  ; to do the next command regardless
  && only if the previous one passed
  || only if the previous one failed


Shellcheck is a tool to "compile" shell scripts



look up curly brace expansion
https://www.geeksforgeeks.org/linux-unix/bash-brace-expansion-in-linux-with-examples/
cp -v file1.txt{,.bak}



Ctrl+x, Ctrl+e to open your current line in $EDITOR
fc to open your previous line in $EDITOR


batch rename:
for f in *.txt; do mv -- "$f" "new_$f"; done


To run a script at startup:
   From Matt:

   If you already have the standalone script written, you can just create a file at /etc/systemd/system/myscript.service that looks like this:
   [Unit]
   Description=My startup script
   After=network-online.target
   Wants=network-online.target
   
   [Service]
   Type=oneshot
   ExecStart=/usr/local/bin/myscript.sh
   
   [Install]
   WantedBy=multi-user.target 

   Then to enable it:
   sudo systemctl daemon-reload
   sudo systemctl enable --now myscript.service




Adjust brightness:
xrandr --output eDP-1 --brightness .5


untar:  tar -xzvf archive.tar.gz
   or ouch


symlink:
   ln -s [file i want to make a shortcut to] .



apps to download for new setups:
   ranger
   nvim
      fd
      ripgrep
      fzf
   ouch
   ascii-matrix
   zellij
   OpenComic?  yomikiru?
   nerdfont
   wezterm
   batcat
   tldr
   btop


put my git config in github?
