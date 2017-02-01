Emacs notes and tricks
======================

M-x align-regex =

M-; [un]comment-region

M-q - fill current paragraph

* set goal column to set position for C-n/C-p to jump to
C-x C-n set-goal-column

C-x h mark buffer
C-c C-r send marked region to scheme interpreter
C-x C-e send previous sexpr to scheme interpreter
C-l C-r load file

M-x set-variable ENTER fill-column
M-x align <!-- align equal signs -->

bookmarks
---------
C-x r m   set bookmark
C-x r b   jump to bookmark
C-x r l   list bookmarks

registers
---------
https://www.gnu.org/software/emacs/manual/html_node/emacs/Registers.html
C-x r SPACE r  save current position to register r
C-x r j r  jump to position saved in register r


From O'Riely Book
=================

miscellaneous
-------------
set mode per file
> -*-shell-script-*-

TAGS - first run build-tags script in source code directory
* M-. search for tag

file handling commands
----------------------
C-x C-f   find-file
C-x C-v   find-alternate-file
C-x i     insert-file
C-x C-s   save-buffer
C-x C-w   write-file
C-x C-c   save-buffers-kill-emacs

cursor movement commands
------------------------
C-f   forward-char
C-b   backward-char
C-p   previous-line
C-n   next-line
M-f   forward-word
M-b   backward-word
C-a   beginning-of-line
C-e   end-of-line
M-e   forward-sentence
M-a   backward-sentence
C-v   scroll-up
M-v   scroll-down

M-<   beginning-of-buffer
M->   end-of-buffer
()    goto-line
()    goto-char
M-n   digit-argument (repeat the next command n times)
C-u n universal-argument (same as above)

deleting, yanking, region, and clipboard commands
-------------------------------------------------
C-d   delete-char
Del   delete-backward-char
M-d   kill-word
M-Del backward-kill-word
C-w   kill-region (cut)
M-w   kill-ring-save (copy)
C-y   yank (paste)
M-y   yank-pop
C-x h mark-whole-buffer
C-Space set-mark-command (also C-Space)
C-x C-x exchange-point-and-mark
()    clipboard-kill-region
()    clipboard-yank
()    clipboard-kill-ring-save

text filling and reformatting commands
--------------------------------------
()   auto-fill-mode (formats paragraphs as you type)
M-q  fill-paragraph (reformat paragraph)
()   fill-region

stopping and undoing commands
-----------------------------
C-g  keyboard-quit
C-_  undo
()   revert-buffer

search and replace commands
---------------------------
C-s  isearch-froward
C-r  isearch-backward

regular expression search commands
----------------------------------
TODO

spell-checking commands
-----------------------
()   ispell-buffer
()   ispell-comments-and-strings
()   fly-spell-mode
()   fly-spell-buffer

buffer commands
---------------
C-x b  switch-to-buffer
C-x->  next-buffer
C-x<-  previous-buffer
C-x C-b list-buffers
C-x k  kill-buffer
()     kill-some-buffers

windows and frames
------------------
C-x 2  split-window-vertically
C-x 3  split-window-horizontally
C-x o  other-window
C-x 0  delete-window
C-x 1  delete-other-windows
C-x 4 f  find-file-other-window
C-x 4 b  switch-to-buffer-other-window
()     compare-windows
C-x 5 o  other-frame
C-x 5 0  delete-frame
C-x 5 2  make-frame
C-x 5 f  find-file-other-frame
C-x 5 r  find-file-read-only-other-frame
C-x 5 b  switch-to-buffer-other-frame

shell mode commands
-------------------
()   shell
C-c C-c comint-interrupt-subjob (Control C in terminal)
C-c C-z comint-stop-subjob
M-p  comint-previous-input
M-n  cimint-next-input

dired commands 
--------------
TODO

macro commands
--------------
TODO

outline mode commands 
---------------------
TODO

compilation mode commands 
-------------------------
C-x   next-error
M-n   compilation-next-error
M-p   compilation-previous-error
C-c C-c compilation-goto-error

basic indentation commands 
--------------------------
C-M-\  indent-region
M-m    back-to-indentation
M-^    delete-indentation

C motion commands 
-----------------
M-a   c-beginning-of-statement
M-e   c-end-of-statement
M-q   c-fill-paragraph (used within comments)
C-M-a beginning-of-defun
C-M-e end-of-defun
C-M-h c-mark-function
C-c C-q c-indent-defun
C-c C-u c-up-conditional (pre-processor)
C-c C-p c-backward-conditional
C-c C-n c-forward-conditional

SQL mode commands 
-----------------
TODO

Lisp commands 
-------------
TODO

VC commands
-----------
TODO

Ediff commands 
--------------
TODO

CUA mode commands 
-----------------
TODO

help commands 
-------------
C-h k  describe-key
C-h f  describe-function
C-h v  describe-variable
C-h m  describe-mode
C-h b  describe-bindings
C-h a  apropos-command
()     apropos-variable
()     apropas

documentation help 
------------------
C-h t  help-with-tutorial
C-h i  info
C-h r  info-emacs-manual
C-h K  info-goto-emacs-key-command-node
()     emacs-index-search
C-h p  finder-by-keyword
