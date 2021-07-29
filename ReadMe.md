## Quick Instructions

First of all, we need to Install MARS Environment. 

We need to perform the following steps without usings sudo (to avoid generating files and folders owned by root). Now, open the Terminal or Command Prompt and follow the following steps step-by-step.

0) Install the dependencies of [Autoproj](https://github.com/rock-core/autoproj):

```   
   $ apt-get update
   $ apt-get install -y build-essential ruby ruby-dev sudo wget
```

1) Create a folder where your environment will be checked out and installed.
```
   $ mkdir mars_dev
   $ cd mars_dev
```
From here on, perform the steps from the newly created directory.

          
2) Download the autoproj bootstrap script

```
   $ wget http://rock-robotics.org/autoproj_bootstrap
```          
    
3) Run the boostrap script and provide the repository address

If your user has set up his/her keys in the github and gitlab account, then use this command

```
   $ ruby autoproj_bootstrap git git@github.com:envire4mars/simulation-buildconf.git branch=envireMars
``` 
 
If the user has not generated the SSH key and set it up in his/her github and gitlab account then use this command

```
    $ ruby autoproj_bootstrap git https://github.com/envire4mars/simulation-buildconf.git branch=envireMars
```        

Answer "whether C++11 should be enabled for Rock packages [false]" with "true" and the other with default (just hit enter)    
    
4) Source your environment

```
    $ source env.sh
```

5) Check out updates
```      
    $ autoproj update
```          
6) Build your environment
```      
    $ autoproj build        
```    
This step will start building everything.
    
7) Check for instance that mars_app is installed. To launch the mars application: 
```
    $ mars_app          
```    

In mars_app you can load different environments and robots of your choice.
    
 ## TroubleShooting Section:
 
1- No Access Right:

Sometimes you may face the problems like "No Access Rights to your repository": Make sure you have corrected generated the SSH Key for both GitLab and GitHub
    
Similarly, sometimes you don't have access to the specific Repository forexample:
"No Access Rights to git@git.hb.dfki.de/models-environments" 
In this case, you have to make an access request to the maintainer/owner of that Repository. 

2- PROGRAM STUCKS AFTER ENTERING ` autoproj update `

If you are on step NO:05 and your program got stuck while checking out Models Environment and Models Robots. 

You can checkout each robot/environment separately to overcome this problem.

Let say  we need to install spacebot_cup robot.
Todo so use:
```    
    $ autoproj update models/environments/spacebot_cup
```              
Similarly do same for all the other robots like asguard_v4 etc.

    
3- AFTER ENTERING ` autoproj build `.

Maybe you get an error "CMake fails to compile the simple test".
There are two possibilites to overcome this problem: 

First of all install build essential using the correspondent command:
```    
    $ sudo apt install build-essential
```              
If you are still having the same error, then you can try by removing ccache. The default configuration does not use ccache but sometimes errors are triggered if it installed but not selected for use. You can remove ccache with
```
     $ apt-get remove ccache
```
To do add documentation
