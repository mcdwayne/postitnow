# postitnow


Utility scripted in Bash to post markdown files from either your local environment or your github repo to a site on Pantheon.  
If posting from Github, find the last saved file in my blog drafts folder and post that if synced, fail otherwise.


I am going to ask for the following: 
    > Permalink you prefer, default is title
    > The Featured Image



## Requirements!!
- Bash  (with cURL working)

- Permissions turned to "Read for Everyone" for the files you want to drag/drop into the terminal locally

- An existing Pantheon site

- Pantheon's Terminus

- Content files in Markdown 
	- File names can not contain spaces (not going to deal with regex for now)
	- The first line will be used as the title
	- The rest will populate the body field

- 'markdown-editor' plugin (or something on your site that can interpret markdown for the post as it is created by the WP-CLI via Terminus)

- A Github account where you sync your local content folder. 


## Also Included:

#### postit_installer 

Bash script to copy the script and set it in the user/bin/
for both postit and postitnow


## Installation:

1. Clone down the repo or grab and unpack the zip

2. Modify postitnow in place with the following variables

	`SITENAME=<sitename>`  -  sitename is the name of the site on Pantheon, no spaces
	
	`ENV=PantheonEnvironment` - the environment we are posting to on Pantheon 

	If you want to use the 'post last thing synced to Github' feature you need to additionally set

	`LOCALREPO=/localfolder` - your local folder synced to GITHUBREPO

	`GITHUBREPO='https://raw.githubusercontent.com/user/master/remotefolder/' ` - your github synced to LOCALREPO

	

3. Run the following from bash terminal

```
cd PATH/postit
chmod +x postit_installer 
./postit_installer
```

4. To run, type `postitnow` and feed it what it asks for


### Usage

If installed via path above, simply type `postitnow` into the terminal and feed it what it asks for:

1. A file location.  If left blank, going to pull from Github.
	- Expecting a file written in markdown 
	- First line should be title you want
	- Rest is stuffed into Body field


2. Permalink you prefer, default is filename

3. The Featured Image

4. Alt text for Image - fail if not set

5. Tags for the posts, is expecting slugs, if new slug will create term that is equal to slug


### Example 
```
~/Documents/postit $postit
Where is the RAW file? (Must be RAW) : https://raw.githubusercontent.com/mcdwayne/postit/master/README.md
What should the permalink be? : this-is-a-valid-permalink
Drag and drop your image here now (typing might work too) : /Users/dwaynemcdaniel/Downloads/glogo7.png 
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  2106  100  2106    0     0   9323      0 --:--:-- --:--:-- --:--:-- 10855
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  2106  100  2106    0     0  12995      0 --:--:-- --:--:-- --:--:-- 13245
 [notice] Command: mcdwaynedotcom.dev -- wp post create [Exit: 0]
Success: Updated post 636..
 [notice] Command: mcdwaynedotcom.dev -- wp post update 636. [Exit: 0]
building file list ... 
1 file to consider
glogo7.png
        6167 100%    0.00kB/s    0:00:00 (xfer#1, to-check=0/1)

sent 6234 bytes  received 42 bytes  1141.09 bytes/sec
total size is 6167  speedup is 0.98
Imported file 'https://dev-mcdwaynedotcom.pantheonsite.io/wp-content/uploads/glogo7.png' as attachment ID 638 and attached to post 636. as featured image.
Success: Imported 1 of 1 images.
 [notice] Command: mcdwaynedotcom.dev -- wp media import https://dev-mcdwaynedotcom.pantheonsite.io/wp-content/uploads/glogo7.png [Exit: 0]
Connected to appserver.dev.affe2860-9992-421f-b6c5-3dbf3d9a1b25.drush.in.
sftp> rm files/glogo7.png
Removing /srv/bindings/70d0efaa94d54d808b93650a4ed34b95/files/glogo7.png
 
 
 
Thanks for using postit to post your post
 
Site link is here
https://dev-mcdwaynedotcom.pantheonsite.io/this-is-a-valid-permalink


```


Have fun and enjoy!!!!

# Author mcdwayne 
# email 1dwayne.mcdaniel @ gmail.com

No, I will not support this beyond making it work for me.  No warranty or guarantees implied or given.   
