# git-sticky
This is a digital stick notes app. To be used through ssh connection on remote server (like a personal git server). Can definitely be improved (and will be) 
 but is nice as a sync-able, readable, searchable, and permanent light storage device, where thumb drives and the like feel too over kill. 
 Small things, like sticky notes


QUICK START:
- Establish passwordless ssh connection between clients and server (see 'ESTABLISHING SSH below')
- Install repo on both client and server computers in 'Documents' directory 
- Fill out USER and ADDRESS fields for your ssh server. ie USER@ADDRESS
- Add git-sticky folder to path (located in /etc/environment; will require reboot)
- Have fun!


HOW TO IMPLEMENT:
- Set up server and computer(s) with ssh connection 
  - we will call the username and address of this server USER and ADDRESS. with the full USER@ADDRESS being referred to as SERVER_ADDRESS
  - Hiehgly recommended to establish a passwordless ssh as the password will get very annoying very quickly
- Install the project anywhere on the computer. This locaiton with be referred to as CLIENT_FOLDER_LOCATION
- Install the project anywhere on the server. This locaiton with be referred to as SERVER_FOLDER_LOCATION
- Edit file 'client-config' as follows:
  - Fill out USER and ADDRESS variables in the file with the values specified by USER and ADDRESS above 
  - Fill out SERVER_FOLDER_LOCATION to match FULL PATH of SERVER_FOLDER_LOCATION specified above. 
    - NOTE: using ~ in this address will not work as it will try to index the server's home folder using the client's home folder location
- OPTIONAL: You can fill out the CLIENT_FOLDER_LOCATION. THis is optional because it comes preloaded with a script to find its current location
- Add git-sticky folder to path (located in /etc/environment; will require reboot)
- QED


COMMANDS:
-new-sticky: takes flags -t (title), -b (text body), -c (filterable categories for finding later). Will return the ID# of that particular sticky
-add-sticky: a wrapper for new-sticky becuase I can never remember what I set it to
-edit-sticky: takes ID# of sticky you want to edit as first arg. Then accepts -t (title), -b (test body), and -c (categories) for any values you 
              would like to change. If you do not specify a field to be changed it won't be. There is currently no system to append fields. 
-git-sticky: Can take no arguments and will return all stickies currently saved. Also take -t (Title), -b (Text body), -c (Categories), -id (ID#) 
              If t,b,c flags are specified it will return all sticky notes which contain the matching string. This makes searching for them rather easy 
-print-sticky: This take single argument of sticky note to print. Prints the sticky note to the console in nice format 
-rm-sticky: This take single argument of sticky note to delete. NOTE: Deleted Sticky notes are not recoverable (well maybe they are but I have no system for it)


ESTABLISHING SSH:
-NOTE: You will want to set up passwordless ssh on your SERVER, this takes a lot of the friction out of the program.
-How to enable SSH on Ubuntu: https://linuxize.com/post/how-to-enable-ssh-on-ubuntu-18-04/
-How to enable SSH on Raspberry Pi: https://www.raspberrypi.org/documentation/remote-access/ssh/
-How to enable passwordless SSH on Raspberry Pi: https://www.raspberrypi.org/documentation/remote-access/ssh/passwordless.md

