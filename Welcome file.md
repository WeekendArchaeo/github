# Ana's How to git

Hi! As a dummie user of github, and a total newbie to git, this is my personal view of how to manage with both software tools. This is a simple guideline that helps me (and, hopefully, you) to work with this control version software. There are a lot of books that you can check in order to master this software; I have used these:

 - *"[Aprende git... y de camino, Github](https://www.amazon.es/Aprende-Git-y-camino-GitHub-ebook/dp/B00K515GL2/ref=as_li_ss_tl?s=digital-text&ie=UTF8&qid=1411621815&sr=1-2&linkCode=sl1&tag=atalaya-21&linkId=1472ae4e394e2660f266093f4cf06fd1)", Pablo Hinojosa and JJ Merelo. I have linked the Amazon version (is very cheap), but you can also get it free from the [github page of the book](https://github.com/JJ/aprende-git).
 - "*[Pro Git](https://git-scm.com/book/es/v2)*", Scott Chacon and Ben Straub.
 - asdf
 Of course, any mistake you may find is mine (and only mine :P)

# Create repository
First, you should configure your repository with your user and email address. So, go to the folder where you will create your repository, and type:
- *git config --global user.name YourUserName*
- *git config --global user.email YourEmail*
You can check that everything went ok with *git config --list*

Now you have to create your repository. There are two options: 

 1. Create local repository: *git init*
	 You can check that everything is ok if you list all the files in the folder (including hidden files) and you find a *.git* file. The files in that folder should not be changed ***ever***.
 2. Clone remote repository

# General local workflow

Work folder -> Index (or stage) -> Head (or repository) 
                           -> *git add*               -> *git commit*

It is a good idea to check the status of your local repository with *git status* before you commit your changes.
If you need to know the whole history of the repository, that is, you have the *log* command, with several interesting options:

 - *git log* -> verbose log
 - *git log --oneline* -> it shows only one line of info per change
 - *git log --graph* -> it shows a (very basic) graph of the changes

## Adding files to your repository
There are two stages when you add files to your repository. First, you have to put them on the index (or stage, in some books). Then, when are are sure that you want them to be included into the repository, you have to commit those files (or folders).

As I said, the first step is adding files/folders to the index:

 - *git add* YourFiles. You can check the status of your repository (this is very useful at many times) with *git status*. Of course, you cand add only a file, or just a few of them (use wildcards), or a folder.
 
 And then, if you are completely sure that everything in the index is fit to work, you have to commit those files/folders:
 
 - *git commit -m Message*. Again, you may commit one or several files. The message has to be a short description of the main changes that are included in that commit.
 Keep in mind that commits are inmutable!!

## Basic catastrophe handling :)

There are several options for deleting files, depending on where you want to delete them:

 - *git rm filename* -> deletes the file from the work folder **and** the Index.
 - *git rm --cached filename* -> deletes the file only from the Index, but it keeps it in the work folder.
 - *git reset HEAD filename* -> same as the previous command

If you *commit* some changes and then notice you have missed something, you can:

 - *git commit -amend" -> when you just want to modify the comments of the *commit*.
 - *git add filename* + *git commit --amend* -> when you forgot to add a file to the Index before the *commit*

If you have messed up a file on your work folder:

 - *git checkout filename* -> if you want to discard changes of a file in your work folder and get back to the version in your Index.

## Synchronization with remote repositories

In case you work with a remote repository (i.e., github), first you have to configure git in order to recognize that remote repository:

 - *git remote add RemoteRepositoryName*. The default remote repository name used by Github is *origin*, but you can change it. You can have more than one remote repository.
 - *git remote* and *git remote -v* gives information about the remote repositories you have configured.
 - *git remote rm RemoteRepositoryName* deletes a particular remote repository from your list of remote repositories.

Once you have set your remote repositories, you can:
 - *git pull* to download the contents of the remote repository to your local repository
	 - If the remote files are newer than yours, yours will be lost.
	 - If the remote files are older than yours, you keep your files.
 - *git push* to upload the contents of your local repository to the remote repository (***do not forget to commit in your local repository before you push to the remote repository***)
	 - If the remote repository is newer than your last pull, an error will arise.
Since 2013, github does not work on a simple user/passwd basis to push contents to a remote repository. Insteado of a password, you have to create a token and use it as a password, as explained [here](https://docs.github.com/en/get-started/getting-started-with-git/about-remote-repositories#cloning-with-https-urls).

## To sum up

This image from [Oliver Steele's blog](https://blog.osteele.com/2008/05/my-git-workflow/) clearly sums up all the process
![](https://images.osteele.com/2008/git-transport.png)

# TO DO
- Comentarios
- Resolución de conflictos
- Qué ficheros debe estar en el repositorio (binarios no)
- Cada persona sólo debe ver y acceder a los ficheros con los que trabaja.
- Organización del repositorio


