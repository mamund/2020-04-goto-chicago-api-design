# Installing

Excerpt from [**"Design and Build Great Web APIs"**](http://g.mamund.com/greatwebapis) by Mike Amundsen from Pragmatic Publishers

The examples and exercises in this book rely in a handful of handy tools and utilities. This appendix is a short guide to locating and safely installing these tools on your local machine. Most of the install routines are pretty straightforward. However, a couple are a bit involved since the tools are supported on many different operating systems and involve multiple versions. I try to provide additional advice along the way to help steer you through any potential problems.

I also advise you stick to installing these tools from the web locations mentioned in this appendix. Many of these utilities are free, open-source software and some version of them may be hosted on private web pages. There is a slight chance that these unofficial download pages are serving up versions of the software with added trackers or even malicious code injected into the download. For that reason, be careful when you install software from non-standard locations on the web.

All the instructions assume you have access rights to installing software on your local machine. In some cases, you may need to get additional permissions to do this. You may need to check with your local hardware administrator for details.

Finally, you don't need to install all the utilities mentioned here before you start reading the book. In fact, if you plan to just skim the book and/or not do the exercises at the end of the chapters, you may not need to install the software at all. One approach I encourage in my classroom versions of this content is to install each app along the way as needed. That spreads out the install effort a bit.

## curl {#chp.appendix.installing.curl}
The curl utility is basically a command-line browser. Discussed in [xxx](#chp.apifirst), we'll use curl to make API calls from the command line throughout the book.

### Checking for curl 
You may already have it installed on your machine. You can check on this by typing the following in a command line window:

~~~~
$> curl
~~~~

If it is installed you should get the following response:

~~~~
curl: try 'curl --help' or 'curl --manual' for more information
~~~~

### Installing curl
If you need to install curl, the best way to do this is to visit the home page for the curl utility and use the Download Wizard at that website to help you find the proper package to install for your operating system.

1. Start by going to this web page: <https://curl.haxx.se/dlwiz>. That should start the Download Wizard. To answer the first question, select the curl executable option.
2. At the next screen, select your operating system from the drop-down list and press the Select button.  For example, I selected the "Linux" option.
3. At the next screen, you need to select your Flavour and press the Select button. For example, I selected the "Ubuntu" option.
4. Depending on your selection to this point, you may see a page listing one or more download files or you may need to select your OS Version and press the Select button. For example, for my Linux -> Ubuntu selection, I need to select an OS Version and I would select "cosmic."
5. Depending on your selections you may see a page asking for you to select a CPU. Since I selected Linux to start, I don't see this CPU screen. Instead, I see the screen <xref linkend="installing.curl">shown</xref> that lists the download files.

<figure id="installing.curl">
  <imagedata fileref="images/installing/apx-a-curl-screen.png" width="100%" border="yes"/>
</figure>

Once you get to the the download listing page, you may see just one file to download along with some notes about how the install process will work. You may also see more than one download option. These options might point to various places to download the same file. There may also be options to download ZIP or executable versions of the package. Finally, there might be multiple release versions of curl available for your machine. You should usually pick the most recent version. It doesn't matter too much since we're not doing anything advanced with curl in this book.

Once you download the file, just follow along with the instructions in the notes to get your version of curl up and running. And, like before, you can test your install using the example at the start of this section (see [xxx](#chp.appendix.installing.curl)).


## git {#chp.appendix.installing.git}
We use git as the source control manager for all the projects in the book. It is first mentioned in [xxx](#chp.http), but almost every chapter after that has some git commands. 

### Checking for git
You may already have git installed on your machine. You can check on this by typing the following at the command line:

~~~~
git --version
~~~~

If git is installed you should see something like the following:

~~~~
git version 2.11.0 
~~~~

The exact version is not too important but I advise using version 2 or greater when working with the examples in this book.

### Installing git
If you need to install git, your best bet is to visit the official download page (<https://git-scm.com/downloads>), as shown in the following screenshot. Once you get there you should see a suggested download on the right. You can also click on the operating system links to download the latest releases. Depending on the operating system you select you'll see a list of commands for downloading the release or, in some cases, the download will automatically start. In either case, you just need to follow along with any instructions you see along the way to complete the install.

<figure id="installing.git">
  <imagedata fileref="images/installing/apx-a-git-screen.png" width="100%" border="yes"/>
</figure>

You can confirm the install using the same test mentioned earlier.
 
## GitHub and SSH
Several chapters include commands for accessing and modifying git repositories on the GitHub public website. You don't need to install any GitHub client, but you will need to make sure you have support for command-line level SSH and have generated a private/public key pair that will be used when you read and write data to GitHub from the command line on your local machine.

[aside info GitHub Account]
<p>You'll need to have a GitHub account and password to use this website.</p>
[/aside] 

### Adding your SSH Certificate to GitHub
In order to interact with the git engine on the GitHub website, you'll need an SSH certificate on your machine. This is how the GitHub server will be able to recognize you and will be used to control access rights to your repositories. In my experience, this process of generating an SSH key and getting onto GitHub is a bit fiddly. The exact process is different for each operating system (Windows, Mac, and Linux), too. I'll walk you through the process that I've been able to consistently use (with only slight variations for operating systems). However, you may _still_ need to refer to operating system specific instructions on the Web. If you're lucky, this has all been done already and you can skip it, but if not, here goes!

*Step 1*: First, at the command line (for windows, open `git bash`), check to see if you already have an SSH cert installed on your machine. To do that, type the following:
 
~~~~
ls -al ~/.ssh
~~~~

If you see the following files: `id_rsa` and `id_rsa.pub` you have a usable cert all set and ready to go. You can skip to Step 4 in this list.

*Step 2*: If you need to generate a new private/public SSH key pair, type the following in your command window:

~~~~
ssh-keygen -t rsa -b 4096 -C "your@email.com"
~~~~

Where `"your@email.com"` is the email address you want to use for this certificate. To keep things simple, I use the same email address I used to create my GitHub account. If you want to use a different one, that's fine, though.

You'll be prompted to enter a password for this generated certificate (you'll be asked twice) and then you'll see several lines of text on the screen that indicates the certificate was generated successfully.

*Step 3*: The next step is to store your certificate safely in memory on your machine to make is less tedious to check content in and out of GitHub. To do this, you will fire up the `ssh-agent` utility and then add your certificate to that utility's storage. For example, this is what I typed and along with the responses I got along the way:

~~~~
$> eval "$(ssh-agent -s)"
Agent pid XXXX
$>ssh-add ~/.ssh/id_rsa
Enter passphrase for /home/mca/.ssh/id_rsa:
Identity added: /home/mca/.ssh/id_rsa (/home/mca/.ssh/id_rsa
~~~~

At this point, you've created an SSH certificate and stored the private portion of it (`id_rsa`) safely in your machine's memory. Now, you need to copy the public portion of the key (`id_rsa.pub`) onto your machine's clipboard and then paste it into GitHub directly. That will complete the process of linking your machine to GitHub's servers.

*Step 4*: To copy the public portion of your SSH key onto your machine's clipboard, type the following in your command-line window:

On Linux:

~~~~
xclip -sel clip < ~/.ssh/id_rsa.pub
~~~~

On Mac:

~~~~
pbcopy < ~/.ssh/id_rsa.pub
~~~~

On Windows:

~~~~
clip < ~/.ssh/id_rsa.pub
~~~~

Now, you should have the public key copied onto your in-memory clipboard and are ready to paste it into GitHub. That will take a couple steps, too.

*Step 5*: In this final step, you'll log into the GitHub web site, navigate to the SSH key page, add your new key, and save it to GitHub's servers. 

* Open your browser and navigate to <http://github.com> and log in with your username and password.
* In the upper-right corner of the page, click on your profile icon.
* In the drop-down menu, find and select the "Settings" option.
* When the page loads, locate the "SSH and GPG Keys" option on the left and click on it. A new screen should load (the one showing all your registered SSH keys).
* Locate the "New SSH Key" or "Add SSH Key" button and click on it.
* You'll be prompted to enter to things: a title, and your SSH key. Type some memorable name for this key in the title box and then paste your SSH key into the big input box. 
* Finally, click on the "Add SSH Key" button to store all this onto GitHub's servers. <!--(See <xref linkend="installing.ssh"></xref>.)--> You might be asked to enter your GitHub password, too (not your certificate password!). 

<!--<figure id="installing.ssh">
  <imagedata fileref="images/installing/apx-a-ssh-screen.png" width="100%" />
</figure>-->

You should now be all set for passing data between your workstation and the GitHub website. If you want to be able to check content in and out of GitHub from another machine, you'll need to repeat this SSH setup process for each machine. I have about five or six machine keys registered in GitHub right now.

## NodeJS and npm {#chp.appendix.installing.npm}

We'll be using NodeJS and the related npm (Node Package Manager) utility throughout the book. For example, many of the sample command-line utilities are written in NodeJS and are installed and updated using npm. The first reference to these two important tools appears in [xxx](#chp.modeling).

### Checking for NodeJS
You may already have NodeJS and npm installed. You can check on this by typing one of  following the command line:

~~~~
node -v
~~~~

If NodeJS is installed, you should get a response that is the version number your release of NodeJS. For example, the response on my machine is:

~~~~
v10.14.10
~~~~

The exact version is not important but you should be using version 10 or above since that is the version used to write the code in this book.

### Checking for npm
When NodeJS gets installed, the latest version of npm should also get installed automatically, you can check on this with the following command:

~~~~
npm -v
~~~~

The response should be the current installed version on your machine. For example, the response on my machine is:

~~~~
6.4.1
~~~~

The exact version is not important, but you should use at least version 6 or above. You may also be prompted to update your npm instance and that's usually a good idea.

### Installing Nodejs and npm
Installing NodeJS on your machine is usually pretty simple. The best place to start is to go to the NodeJS home page (<http://nodejs.org>). Right on the home screen you should see one or more buttons prompting you to download the install package for NodeJS, as shown in the following screenshot. The first button will have the letters "LTS," which stands for Long Term Support. There may also be a button with the word "Current." I advise installing the LTS option since it will be the most stable and reliable release. The examples written for this book were created using LTS version 10.14.10. Any stable version above release 10 should be fine.

<figure id="installing.node">
  <imagedata fileref="images/installing/apx-a-nodejs-screen.png" width="100%" border="yes"/>
</figure>


If you're looking for a more options, you can visit the download page (<https://nodejs.org/en/download>) and you'll find lots of options. Since NodeJS is available on lots of platforms and in multiple releases, you'll need to take a minute to sort through these options if you want to do anything other than install the default option offered to you on the home page. My advice is to use the default option unless is does not work for you, then dive into the downloads page.

Once you complete the install, you should have both NodeJS and npm available. To conform this, use the instructions provided earlier for checking for NodeJS and checking for npm.

## Postman {#chp.appendix.installing.postman}
Postman is the platform we'll use to run our API tests. Unlike all the other apps you can  install for this book, Postman is a GUI app. That means to launch the app, you'll need to find it in your machine's application menu. This will be a bit different for each operating system.

The best way to install it is to go to the Postman download page (<https://www.getpostman.com/downloads>), as shown in the following screenshot. There, you should see a button on the screen that simply says "Download." This should be the proper release package for your operating system. If not, you'll find other links on the page to download and install the package you would like to install.

<figure id="installing.postman">
  <imagedata fileref="images/installing/apx-a-postman-screen.png" width="100%" />
</figure>

[aside info Postman Account]
<p>
I advise creating an account and password for your Postman tests. This makes it easier to get things done on the site and allows you to easily store tests and other things on Postman's servers.
</p>
[/aside]

## Newman {#chp.appendix.installing.newman}
The Newman command-line app can run the tests created by the Postman app. This makes running Postman tests really simple and it also makes it easy to include these tests in command-line driven build scripts.

### Checking for Newman 
You can check to see if you already have Newman installed by typing the following at the command line:

~~~~
newman -v
~~~~

If it is installed you'll get response which is the version number of your release of Newman. On my machine the response is:

~~~~
4.5.0
~~~~

### Installing Newman
You can install the Newman test running using the npm utility you installed earlier (see [xxx](#chp.appendix.installing.npm)). To do that, just type the following at the command line:

~~~~
npm -g install newman
~~~~

That's all you need to do. You can check to see if it was properly installed using the instructions in [xxx](#chp.appendix.installing.newman).

### Installing HTMLExtra
There is a handy add-on to the `newman` toolchain that produces good-looking HTML reports that show the results of your `newman` test run. It's called HTMLExtra. You can install this using npm with the following command:

~~~~
npm i newman-reporter-htmlextra
~~~~

This will come in handy when you want to post your latest test results for others to view.


## Heroku Client {#chp.appendix.installing.heroku}
Heroku is the deployment and runtime platform used for all the API services related to this book. For this book, in order to define applications and move code from your local machine to the Heroku platform you need to install the Heroku client command-line app.

[aside info Heroku Account]
<p>
You'll need to create an account and password on the Heroku platform in order to be able to use the client app to deploy your API code to Heroku.
</p>
[/aside]

### Check for Heroku Client
To see if you have the Heroku client already installed on your local machine just type the following into the command line:

~~~~
heroku -v
~~~~

If the app is available, you should see a response that includes version information for the installed release on your machine. For example, on my machine, the response looks like this:

~~~~
heroku/7.24.4 linux-x64 node-v11-14.0
~~~~

### Installing the Heroku Client
The best way to install the Heroku client app is to visit the Heroku CLI page (<https://devcenter.heroku.com/articles/heroku-cli#download-and-install>) where you'll see several buttons and prompts to download and install the version that is right for your operating system. You'll also see a handful of other alternate ways to install the Heroku client, but I advise you only use these alternates if you can't get one of the common OS options to work for you.

Once you have the Heroku client installed, you can test your results using the instructions provided in [xxx](#chp.appendix.installing.heroku).

