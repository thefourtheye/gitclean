gitclean
========

This is basically a `git clean` command's wrapper. This simple script will display the list of files which would be cleaned to the user and prompts for user's consent before cleaning. So accidental loss of untracked files (which are really needed) can be avoided. If you are interested in the motivation behind this script, please read about it in this blog [post](http://dfourtheye.blogspot.in/2013/06/gitclean-git-clean-wrapper.html).


Installation
------------

* Download the script

        wget https://raw.github.com/thefourtheye/gitclean/master/gitclean

* Change the permissions

        chmod 544 gitclean

* Run the script with install parameter
 
        ./gitclean install

These three steps will take care of the installation and restart of the terminal/session is required for gitclean to be available in the shell.

Configuration
-------------

Users can specify the extensions, gitclean has to report, in the `$HOME/.gitclean_extenstions` file. By default, gitclean will report the extension-less files and directories as well. But, it does not report the empty directory. Sample `.gitclean_extenstions` file

    cpp
    js
    
In this case, gitclean will consider the files with extension `.cpp` and `.js` as interesting files and report them.

Sample Runs
-----------

1. With no files changed

		~/gitclean$ gitclean
		
		Interesting Extensions found in [/home/thefourtheye/.gitclean_extensions] are as follows
		[cpp]
		[js]
		
		0 interesting files found, in total 0 files. Cleaning was not done. Exiting...
		
2. With one interesting file [Test.js]

		~/gitclean$ gitclean
		
		Interesting Extensions found in [/home/thefourtheye/.gitclean_extensions] are as follows
		[cpp]
		[js]
		
		Test.js
		
		1 interesting files found, in total 1 files. Are you sure want to clean? [y/Y - Yes, Any other Key - No] : n
		Cleaning was not done. Exiting...

3. With one interesting file [Test.js] and a non-empty directory 

		~/gitclean$ gitclean
		
		Interesting Extensions found in [/home/thefourtheye/.gitclean_extensions] are as follows
		[cpp]
		[js]
		
		Test.js
		Test/
		
		2 interesting files found, in total 2 files. Are you sure want to clean? [y/Y - Yes, Any other Key - No] : y
		Cleaning...
		
		~/gitclean$
		
4. With one interesting file [Test.js] and a non-empty directory and a non-interesting file [Test.txt] 

		~/gitclean$ gitclean
		
		Interesting Extensions found in [/home/thefourtheye/.gitclean_extensions] are as follows
		[cpp]
		[js]
		
		Test.js
		Test/
		
		2 interesting files found, in total 3 files. Are you sure want to clean? [y/Y - Yes, Any other Key - No] : y
		Cleaning...
		
		~/gitclean$ 
