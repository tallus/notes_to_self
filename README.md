notes_to_self
=============

Command tools for the the terminally distracted. Leave a note to yourself.
--------------------------------------------------------------------------

* Do you have a million tabs open and terminals covering every inch of your screen?
* Afraid to close anything because you might never remember where you were?
* Trying to work, but ooh shiny?
* Are you, too, a command line fiend with ADHD?

**Notes To Self** is a series of small scripts to help you remember things and not get distracted.It uses the magic of git to store things so you can easily move between computers. It is designed to tie into the shell so you can easily get reminders. It store the notes in text files. You can define different types of notes in the config file by giving them  a name and the name of the file you want that sort of note stored. You can add arbitrary files to the notes directory. Just add a note and it will take care of the rest.

### Use scenario

You are at work and you come across a program you want to install.

    % add-note -s 'Install note to self'  https://github.com/tallus/notes_to_self

Back home you open a terminal and up pops a reminder
    New Notes
You run 
    %get-notes 
and get back
    Install note to self
     https://github.com/tallus/notes_to_self
Now run
    % clear-notes
and you won't get reminded again.

You suddenly remember that book you wanted to buy but you are trying to work

    % add-note -S -t book Robert Walser Microscripts

You just made a shopping list
    
    % cp shopping.list ~/notes_to_self
    % add_note -S Do the shopping

### The files

*   nts.cfg      Configuration file. This is where you add note types
*   add-note     Add a note
*   clear-notes  Clear notifications
*   erase-notes   Clear notifications and erase notes
*   check-notes   Check for new notes
*   edit-notes   Edit notes in an editor
*   get-notes   Display notes

### Notes

copy nts.cfg to ~/.nts.cfg if you want to change any of the default values or define a note type.

The scripts use the readline library (via bash's implementation) so you have access to vi/emacs keybinding when adding notes.

check-notes can be called directly from the command line but it is really designed to be used in conjunction with other things, for example a cron job. The suggested use is adding something to your .bashrc .zshrc file. 

It returns 0 if new notes are present, 1 if only old notes, 2 if there are no notes. (4 for config error).

erase-notes erases all notes at the moment
clear-notes erases the logfile so you don't get notification, it leaves the actual notes in place.

### Requirements

requires bash and git i.e any unix/unix clone (i.e. Linux, OS X etc) You might need to instal git on you system.

It also require you to have somewhere where you can host a remote git repository.

To set this up do something like:

On your remote host

    % mkdir notes_to_self.git
    % cd notes_to_self.git
    % git --bare init

On your local host

    % git clone -o origin ssh://path/to/notes_to_self.git
    % git add remote origin ssh://path/to/notes_to_self.git
    % add-note

### TODO
* Allow selective deletion of notes
* Display last note only option
* Change get-notes to output summary note summary note... rather than summary summary... note note...

