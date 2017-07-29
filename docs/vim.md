# Vim

##	Running Vim for the First Time

To start Vim, enter this command:

	gvim file.txt

In UNIX you can type this at any command prompt.  If you are running Microsoft
Windows, open an MS-DOS prompt window and enter the command.
   In either case, Vim starts editing a file called file.txt.  Because this
is a new file, you get a blank window. This is what your screen will look
like:

	+---------------------------------------+
	|#					|
	|~					|
	|~					|
	|~					|
	|~					|
	|"file.txt" [New file]			|
	+---------------------------------------+
		('#" is the cursor position.)

The tilde (~) lines indicate lines not in the file.  In other words, when Vim
runs out of file to display, it displays tilde lines.  At the bottom of the
screen, a message line indicates the file is named file.txt and shows that you
are creating a new file.  The message information is temporary and other
information overwrites it.


THE VIM COMMAND

The gvim command causes the editor to create a new window for editing.  If you
use this command:

	vim file.txt

the editing occurs inside your command window.  In other words, if you are
running inside an xterm, the editor uses your xterm window.  If you are using
an MS-DOS command prompt window under Microsoft Windows, the editing occurs
inside this window.  The text in the window will look the same for both
versions, but with gvim you have extra features, like a menu bar.  More about
that later.

##	Inserting text

The Vim editor is a modal editor.  That means that the editor behaves
differently, depending on which mode you are in.  The two basic modes are
called Normal mode and Insert mode.  In Normal mode the characters you type
are commands.  In Insert mode the characters are inserted as text.
   Since you have just started Vim it will be in Normal mode.  To start Insert
mode you type the "i" command (i for Insert).  Then you can enter
the text.  It will be inserted into the file.  Do not worry if you make
mistakes; you can correct them later.  To enter the following programmer's
limerick, this is what you type:

	iA very intelligent turtle
	Found programming UNIX a hurdle

After typing "turtle" you press the <Enter> key to start a new line.  Finally
you press the <Esc> key to stop Insert mode and go back to Normal mode.  You
now have two lines of text in your Vim window:

	+---------------------------------------+
	|A very intelligent turtle		|
	|Found programming UNIX a hurdle	|
	|~					|
	|~					|
	|					|
	+---------------------------------------+


WHAT IS THE MODE?

To be able to see what mode you are in, type this command:

	:set showmode

You will notice that when typing the colon Vim moves the cursor to the last
line of the window.  That's where you type colon commands (commands that start
with a colon).  Finish this command by pressing the `<Enter> key` (all commands
that start with a colon are finished this way).
   Now, if you type the "`i`" command Vim will display --INSERT-- at the bottom
of the window.  This indicates you are in Insert mode.

	+---------------------------------------+
	|A very intelligent turtle		|
	|Found programming UNIX a hurdle	|
	|~					|
	|~					|
	|-- INSERT --				|
	+---------------------------------------+

If you press `<Esc>` to go back to Normal mode the last line will be made blank.


GETTING OUT OF TROUBLE

One of the problems for Vim novices is mode confusion, which is caused by
forgetting which mode you are in or by accidentally typing a command that
switches modes.  To get back to Normal mode, no matter what mode you are in,
press the <Esc> key.  Sometimes you have to press it twice.  If Vim beeps back
at you, you already are in Normal mode.

==============================================================================

##	Moving around

After you return to Normal mode, you can move around by using these keys:


	h   left						*hjkl*
	j   down
	k   up
	l   right

At first, it may appear that these commands were chosen at random.  After all,
who ever heard of using `l` for right?  But actually, there is a very good
reason for these choices: Moving the cursor is the most common thing you do in
an editor, and these keys are on the home row of your right hand.  In other
words, these commands are placed where you can type them the fastest
(especially when you type with ten fingers).

	Note:
	You can also move the cursor by using the arrow keys.  If you do,
	however, you greatly slow down your editing because to press the arrow
	keys, you must move your hand from the text keys to the arrow keys.
	Considering that you might be doing it hundreds of times an hour, this
	can take a significant amount of time.
	   Also, there are keyboards which do not have arrow keys, or which
	locate them in unusual places; therefore, knowing the use of the hjkl
	keys helps in those situations.

One way to remember these commands is that `h` is on the left, `l` is on the
right and `j` points down.  In a picture:

		       k
		   h     l
		     j

The best way to learn these commands is by using them.  Use the "i" command to
insert some more lines of text.  Then use the hjkl keys to move around and
insert a word somewhere.  Don't forget to press <Esc> to go back to Normal
mode.  The |vimtutor| is also a nice way to learn by doing.

For Japanese users, Hiroshi Iwatani suggested using this:

			Komsomolsk
			    ^
			    |
	   Huan Ho	<--- --->  Los Angeles
	(Yellow river)	    |
			    v
			  Java (the island, not the programming language)

==============================================================================

##	Deleting characters

To delete a character, move the cursor over it and type "x".  (This is a
throwback to the old days of the typewriter, when you deleted things by typing
xxxx over them.)  Move the cursor to the beginning of the first line, for
example, and type xxxxxxx (seven x's) to delete "A very ".  The result should
look like this:

	+---------------------------------------+
	|intelligent turtle			|
	|Found programming UNIX a hurdle	|
	|~					|
	|~					|
	|					|
	+---------------------------------------+

Now you can insert new text, for example by typing:

	iA young <Esc>

This begins an insert (the i), inserts the words "A young", and then exits
insert mode (the final <Esc>).	The result:

	+---------------------------------------+
	|A young intelligent turtle		|
	|Found programming UNIX a hurdle	|
	|~					|
	|~					|
	|					|
	+---------------------------------------+


DELETING A LINE

To delete a whole line use the "dd" command.  The following line will
then move up to fill the gap:

	+---------------------------------------+
	|Found programming UNIX a hurdle	|
	|~					|
	|~					|
	|~					|
	|					|
	+---------------------------------------+


DELETING A LINE BREAK

In Vim you can join two lines together, which means that the line break
between them is deleted.  The "J" command does this.
   Take these two lines:

	A young intelligent 
	turtle 

Move the cursor to the first line and press "J":

	A young intelligent turtle 

==============================================================================

##	Undo and Redo

Suppose you delete too much.  Well, you can type it in again, but an easier
way exists.  The "u" command undoes the last edit.  Take a look at this in
action: After using "dd" to delete the first line, "u" brings it back.
   Another one: Move the cursor to the A in the first line:

	A young intelligent turtle 

Now type xxxxxxx to delete "A young".  The result is as follows:

	 intelligent turtle 

Type "u" to undo the last delete.  That delete removed the g, so the undo
restores the character.

	g intelligent turtle 

The next u command restores the next-to-last character deleted:

	ng intelligent turtle 

The next u command gives you the u, and so on:

	ung intelligent turtle 
	oung intelligent turtle 
	young intelligent turtle 
	 young intelligent turtle 
	A young intelligent turtle 

	Note:
	If you type "u" twice, and the result is that you get the same text
	back, you have Vim configured to work Vi compatible.  Look here to fix
	this: |not-compatible|.
	   This text assumes you work "The Vim Way".  You might prefer to use
	the good old Vi way, but you will have to watch out for small
	differences in the text then.


REDO

If you undo too many times, you can press CTRL-R (redo) to reverse the
preceding command.  In other words, it undoes the undo.  To see this in
action, press CTRL-R twice.  The character A and the space after it disappear:

	young intelligent turtle 

There's a special version of the undo command, the "U" (undo line) command.
The undo line command undoes all the changes made on the last line that was
edited.  Typing this command twice cancels the preceding "U".

	A very intelligent turtle 
	  xxxx				Delete very

	A intelligent turtle 
		      xxxxxx		Delete turtle

	A intelligent 
					Restore line with "U"
	A very intelligent turtle 
					Undo "U" with "u"
	A intelligent 

The "U" command is a change by itself, which the "u" command undoes and CTRL-R
redoes.  This might be a bit confusing.  Don't worry, with "u" and CTRL-R you
can go to any of the situations you had.  More about that in section |32.2|.

Reference: http://vimdoc.sourceforge.net/htmldoc/usr_02.html
