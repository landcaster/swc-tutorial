---
title: "Post Import"
teaching: 0
exercises: 0
questions:
- "What other house keeping needs to be done?"
objectives:
- "Change repository default branch in github"
- "Access Mana via Open OnDemand"
- "Start an interactive deskop view"
- "Setup your Mana SSH key for github"
- "Clone your repository to Mana and initialize the lesson"
---
## Setting up the default branch
Once the repository has been imported into your github account
we want to make it simple to be in the right branch when we
clone the repository for local editing.

{% include figure.html url="" max-width="30%"
   file="/fig/04.png"
   alt="Changing branch in github" caption="" %}

## Accessing Mana via Open OnDemand
Now that the repository has the right defauly branch set, we need to 
get into an environement that we can use to initialize the lesson repository.

> The intial imported repository is missing key files to generate pages on github.
> The initialization step will create these files, but it requires python
{: .callout}

So that everyone is in a common environment, we will use Open OnDemand and connect
to a Desktop session on Mana
{% include figure.html url="" max-width="30%"
   file="/fig/01.png"
   alt="Changing branch in github" caption="" %}
{% include figure.html url="" max-width="30%"
   file="/fig/02.png"
   alt="Changing branch in github" caption="" %}

## Setup your Mana SSH key for github

Now that you have a desktop on Mana, open up a terminal.  The first step we want to 
deal with is setting up github with our SSH key so we no longer need to use our password
when using git from Mana and our github account.  We are looking for your public key on Mana.
~~~
cd ~/.ssh
ls id_*.pub
~~~
You should see a file named "id_rsa.pub" or "id_ed25519.pub"  This file would represent
your default SSH key public.  We wan to copy this content and add it as a SSH key in github
{% include figure.html url="" max-width="30%"
   file="/fig/07.png"
   alt="Setting up SSH key" caption="Upper right, click on user icon and go into settings" %}


> For security some users like to put a password on SSH keys.
> On Mana the default key is passwordless, but users can create a differnt 
> key with a password, jut making sure to not overwrite the existing key.
> Using a non-default key is outside the scope of this tutorial.
{: .callout}

## Clone your repository to Mana and initialize the lesson

Now that we should have our key setup, with our still open terminal, create a directory on Mana where we can put the cloned respoistory
~~~
cd 
mkdir hidsi
cd hidsi
~~~

Once in the directory let us get the SSH version of the clone address for our repository
and clone it locally.
~~~
git clone git@github.com:landcaster/swc-tutorial.git
~~~

Once the repository is local, we can now initilize it.
~~~
cd ~/hidsi/swc-tutorial
python3 bin/lesson_initialize.py
~~~

A few new files should now be present in our repository
~~~
git status
~~~

Finally, add the new files, commit the changes and push it back to github
~~~
git add --all
git commit -m "initialized"
git push
~~~


{% include links.md %}
