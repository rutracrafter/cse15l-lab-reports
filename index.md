# Introduction
Hello there! This will be a step by step tutorial on how to connect to the UCSD basement remotely using your student credentials!

# Table of Contents
- [Setting up Credentials](#setting-up-credentials)
- [Installing VSCode](#installing-vscode)
- [Remotely Connecting](#remotely-connecting)
- [Trying Some Commands](#trying-some-commands)
- [Conclusion](#conclusion)

# Setting up Credentials
Let's begin by [setting up your credentials](https://sdacs.ucsd.edu/~icc/index.php) to login to the UCSD basemenent remotely. \
\
Upon clicking the link above, you will be brought to a page that looks like this: \
\
![Image](https://rutracrafter.github.io/cse15l-lab-reports/assets/student-lookup.png) \
\
Please fill out the fileds and submit the form.\
\
You will then be taken to a page that looks like this: \
\
![Image](https://rutracrafter.github.io/cse15l-lab-reports/assets/home-page.png) \
\
Once here, you should select your account for this course, which will be done by clicking the button that has "cs15lwi23zz" where the zz is a placeholder that represents the characters at the end that are specific to your account. \
\
After clicking on that box, you will be taken to a page where you can manage your different UCSD accounts' passwords. It is up to you if you want to change all of your passwords to the new one, or if you only want to change the password to this specific account.\
\
After making your decision, follow the instruction given on that page to continue and finish the password change process. \
\
**NOTE:** Sometimes even if you leave the global password change box deselected, there is a chance that all of your passwords will be changed to the new one anyway, just be aware that this is something that can and has happened to some people. \
\
**IMPORTANT: IT CAN TAKE AROUND 15 MINUTES FOR THE PASSWORD CHANGE TO COME INTO EFFECT** \
\
You are now done setting up your UCSD account credentials!

# Installing VSCode
Now we need to [download and install Visual Studio Code](https://code.visualstudio.com/) (VSCode for short). \
\
Once you click the above link, you will be taken to the VSCode home page where you can click the big blue download button to begin the download. \
\
**Note:** Make sure that you download the correct VSCode version for your Operating System (Windows, MacOS, Linux)! \
\
Now, once the download is done, double click the executable file to begin the installation process. Follow the on-screen instructions to complete the installation. \
\
Once that's done, you should be able to open VSCode and be brought to a window that looks like this: \
\
![Image](https://rutracrafter.github.io/cse15l-lab-reports/assets/vscode-window.png) \
\
You are now done downloading and installing VSCode!

# Remotely Connecting
We will now be using SSH to connect to the UCSD basement remotely. \
\
Inside of your VSCode, press "CTRL + \` (tilde, to the left of the 1 key) " (for windows) or click "Terminal" on the top left, and then click on "New Terminal" to open a new Terminal Window. \
\
Then, in the terminal, run the following command `$ ssh cs15lwi23zz@ieng6.ucsd.edu` but replace the zz with your account's corresponding characters. \
\
If this is your first time connecting, you should then see some text that looks like this:
```
The authenticity of host 'ieng6.ucsd.edu (128.54.70.227)' can't be established.
RSA key fingerprint is SHA256:ksruYwhnYH+sySHnHAtLUHngrPEyZTDl/1x99wUQcec.
Are you sure you want to continue connecting (yes/no/[fingerprint])?
```
You can just type yes and press enter to continue forward with connecting. \
\
You will now be prompted for a password, which you will not be able to see as you type it in, so go ahead and type in your password and press enter to connect to the server. \
\
*Bam!* You should now be greeted with a message similar to this: \
\
![Image](https://rutracrafter.github.io/cse15l-lab-reports/assets/welcome-screen.png)
\
You have now successfully connected to the UCSD basement using your UCSD account's credentials!

# Trying Some Commands
Now give some commands a try to make sure that everything is working as expected!

Some command ideas include: \
`cd /` \
`cd ~` \
`ls` \
`ls -la` \
`pwd` \
\
Here is an example of what this command will output: \
`cat /home/linux/ieng6/cs15lwi23/public/hello.txt` \
\
![Image](https://rutracrafter.github.io/cse15l-lab-reports/assets/test-command.png)

# Conclusion
Hooray!! You now know how to remotely connect to the UCSD basement using you UCSD account's credentials! \
\
The final step, and this is the most important, is to have fun while you continue to learn!
