

:help vim.keymap
   or <leader>sk to search with telescope
Shift + K to go to a help page
   Not limited to vim


View current setting:
   setting:
      :lua print(vim.o.tabstop)
   table:
      :lua print(vim.inspect(vim.g.termfeatures))
   See mappings
      :nmap g to see all mappings that start with g
      :map or :verbose map for all 
   vim.o is for basic data, vim.opt lets you work with tables or use things like "append" 
      vim.o is global, but vim.bo or vim.wo can be scoped to buffer or window


Todo learn/fix:
Block select:
   removed surround because I thought it was breaking block insert, but apparently that has to be capital I
   set ve=block
   Block paste doesn't seem to work for me, probably something I've broken with my many remaps
   doing $ to select the end of the line will append to the end of each selected line, without whitespace problems.  Looks like it works with ve=block, it's just a little slower maybe
quickfix list?
Surround - mini.surround, visual select
   vi) or vi) or vib will select (within parenthesees)  This conflicts with block insert
   g[/] for "around"?  
Matt used the cool `gw` two letter jump in helix.  i think this is hop.vim or mini-jump2d
recording macros
   q[register] to start recording
   q to end recording
   @[register] to execute recording
      @@ to execute the last run one
      Q to execute the last recorded one
better session handling?
gotta learn diffs so I can troll brett
undo/redo
   undo tree?
Is there like a history view of where I've jumped to and from?
   <leader>sj
Remap ctrl pgup/down for tabs.  maybe Ctrl ,. 
   That doesn't seem to work without remapping those in wezterm
      I have to make sure I don't collide with whatever I map them to
         zellij only supports up to F12, Wezterm only supports up to F24
   Unclear about C-h and C-S-h, but that would be good too
   Capital L/H for now, but idk how I feel about that
   :tabn :tabN
Fix capital K
   I guess this is because of the treesitter main/master branch
Quickfix list:
   Example:  
      - Use telescope for a list of imports or something
      - :cdo to rename them all
make J/K into 5j and 5k, set gj and gk to J and K


misc:
   In cmd or search mode, Ctrl F will do something similar to Ctrl X Ctrl E in bash.  Combination of history and current line
      Ctrl C to exit without running
   [<space> to insert line above
   ]<space> to insert line below
   Ctrl A to increment a number
   Ctrl X to decrement a number
   I could maybe do a record a register to copy/paste a line and increment the number.  could be neat
   )/( will jump to previous/next sentence

Session saves folding, it looks like


Substitute:
   mapped, write these down.  Looks like %s started above the cursor


netrw:
   :Ex to enter
   % for new file
   v for open in vertical split
   o for open in horiz split
   Need to learn neotree equivalent

paste in command/insert mode:
Ctrl+R [register]
      " for unnamed
      / last search


tabs
   :help tabpage
   hotkey to make a new tab
      :tab split	   " opens current buffer in new tab page
         <leader> w T
      Switching
         g TAB to toggle between the last 2
         gt for next tab, wraps
            or gT for previous
         ctrl pgup/down
            what can I remap those to?  ctrl ,. maybe?  
      :tabs to see them
   :tabm [argument]
      if [argument] has +/-, moves relative to current location
      If 0, moves to the beginning
      if blank, moves to the end
      if number without +/-, moves to that location, only if it's farther to the right
         So to move from 4 to 3, you can either do :tabm -1 or :tabm 0 :tabm 3

panes / windows
^w as first key
   map to space w? - done
   s/v for split horizontal/vertical
   hjkl to select panes
   = to distribute them
   previews:
      } show tag in preview
      z close preview

   ^hjkl to just jump directly

buffers
   :ls to view
   :b space tab to switch
      or space space to fuzzyfind
marks
auto complete
   ^y to accept, or maybe just keep typing.  Is ^x anything?
   ^n/p to cycle

Searching
   * or # to search for highlighted text or active word
   \< and \> indicate start and end of word
   fzf:
      Ctrl + Enter: refine results from current string
      ! before a string to exclude it
   
Switch buffers
   double space - fuzzy find open buffers
   Switching buffers:

Navigate within Buffer
   ' to jump around
      '' - last place jumped from 
      '[] - beginning/end of previously changed/yanked text
      '" - line you were at last exiting this buffer
      '. - for last change in this buffer
      '^ - for last insert mode
   leader / - fuzzy find

   <number>gg - jump to line number

   ]] to next function in theory


   gv to repeat your last visual select
   gi to insert at last insert location

   {/} go to next/previous blank line?
      beginning/end of paragraph

   % to go to matching parenthesee

   gO for symbol list
   gW for workspace symbol list?


   Follow link in help  ^]



multi-clipboard
   " lists them, select the letter/number, then y/d/p


folding
   za

marks
   m{a-zA-z} to set and '{a-zA-z} to jump to.
   Looks like lower case is for just setting/jumping to marks in the current buffer and upper case or number is for setting/jumping across buffers.
   Then you can run :marks to see all set marks.

   no "next mark", but I can see them all with telescope.  Including the like "last line exited this buffer" type automagic ones




Diff Mode:
   ]c / [c to go to next/prev change
   dp :diffput
   do :diffget (obtain)
   Align by putting the same mark in both files, then doing :set diffanchors='a
   :diffoff to exit
   need to add vertical to diffopt?

