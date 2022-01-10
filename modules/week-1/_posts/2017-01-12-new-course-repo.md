---
title: New Repo for This Course
module: 1
jotted: false
---

<div class="tab">
    <button class="tablinks active" onclick="openTab(event, 'Overview')">Overview</button>
    <button class="tablinks" onclick="openTab(event, 'Clone')">Clone Site</button>
    <button class="tablinks" onclick="openTab(event, 'TextEditor')">Text Editor</button>
   
</div>

<div id="Overview" class="tabcontent" style="display:block" markdown="1">

**Create a New Repository for This Course**

Before we dive into the assignment for the week, I want to walk you through creating a new Git repository for use in this course. We will also turn this repository "on", as a GitHub-Pages site.

First, we will create a new repo directly on GitHub.com. We will then turn it on as a GH-Pages site. Finally, we will "clone" it to our local machine, add some necessary files, and then push those back to the remote host on GitHub.com.

1. Go to [GitHub.com](https://github.com)
2. If you are not signed in, sign in to your GitHub account
3. Find the green "New repository" button and press it.
![new repo button on guthub.com](../imgs/Screen5.png)
4. Give your repository a great name, like "_MART220_".
    - Optionally, give this repo a description, like "_Homework repo for UMontana Media Arts, Creative Coding 2 (MART220) course._".
5. Keep this as a "Public" repo.
6. Select the "Initialize this repository with a README" box.
7. Finally press the "Create Repository" button.

![Create repo window](../imgs/Screen6.png)


<br />

Your browser will now show you the brand new repository!
</div>
<div id="Clone" class="tabcontent" markdown="1">

**Clone Your New Repo**

1. To clone your repository, go back to the main page of the new repo.
2. Select the "Code" button on this main page.
3. If you are using the GitHub Desktop app, then you simply need to press the "Open with GitHub Desktop" button. If instead you are using another app, copy the git URL that pops up.

![Open in Desktop Button](../imgs/Screen10.png)

#### For GitHub Desktop Users

1. After pressing "Open in Desktop" the browser should ask permission to "allow this page to open GitHub Desktop.app?"
2. Select "Allow"
3. When GitHub Desktop.app open the "Clone a Repository" window, select the "Choose..." button to navigate to a location on your system where you want this repository saved. (This is just picking a "parent" directory, not naming the directory itself.)
4. GitHub Desktop.app will suggest a directory name that is based on the repo name. Feel free to change that in the "Local Path" line to something else.
5. Finally, click "Clone".

![Clone a Repository Box](../imgs/Screen11.png)

#### For Other App Users

1. In your Git client, select the appropriate "Clone Repository" option
2. Where the app asks for the Repository URL, past in the one copied from github.com.

#### For CLI Users

1. CLI (i.e. terminal) users should first navigate to the location where they want the repo saved.
2. Then use the "git clone" command to clone the repo (i.e. `git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git` )

</div>
<div id="TextEditor" class="tabcontent" markdown="1">

**Open The Repo Directory in your Text Editor**

Finally, you should open the new local copy of the repo directory in your text editor. If you are using GitHub Desktop.app, you can select the "Open in Atom" or "Open in Visual Studio Code" option from the "Repository" dropdown menu (depending on the text editor you have installed and setup with GitHub Desktop.app)

![Open in Atom option](../imgs/Screen12.png)
</div>