# git_intro
Tiny repository to showcase a few git principles


## Challenges:

**A) THE BASICS**
1) create an empty directory on your computer and initialize a git repository:
```git init```
2) Navigate into the directory. Create a random textfile (myfile.txt) with some random content. 
3) Find out what has changed by running ``git status``

```diff
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	myfile.txt

nothing added to commit but untracked files present (use "git add" to track)


```

4) Tell git to track this file:
``git add myfile.txt``
5) Find out what has changed by running ``git status``: Your file is now in the **staging area**

```diff
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

	new file:   myfile.txt


```
6) commit the file. Specify a helpful commit message for future reference with ``-m`` : ``git commit -m "add random input to first file" ``

```
[master (root-commit) 2f13b9e] add random input to first file
 1 file changed, 1 insertion(+)
 create mode 100644 myfile.txt
```

7) add more random content to your file. Run ``git status`` and see what happens. 

```diff 
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   myfile.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

8) Find out what the difference between your commited version of ``myfile.txt`` and the current version in your **working directory** is by running ``git diff myfile.txt``

```diff
diff --git a/myfile.txt b/myfile.txt
index d83ec6b..8eb01e5 100644
--- a/myfile.txt
+++ b/myfile.txt
@@ -1 +1,2 @@
 1223457
+12345678
```
9) Add the changes to the staging area: ``git add myfile.txt``
10) Try running ``git diff myfile.txt`` again. It won't show anything, even though your changes are only *staged*, not *committed*. To see the difference to your commited version of ``myfile.txt`` and the currently staged version, run ``git diff --staged``. (This can be useful if you want to make extra sure you know what you are committing)
```diff
diff --git a/myfile.txt b/myfile.txt
index d83ec6b..8eb01e5 100644
--- a/myfile.txt
+++ b/myfile.txt
@@ -1 +1,2 @@
 1223457
+12345678

```
[If you would want to **unstage** changes, run ``git reset HEAD myfile.txt``]

11) commit the changes. Don't forget the commit message! ``git commit -m "even more randomness to this file!" ``
12) Check the history of your repository: ``git log`` (if you have it installed, use ``tig`` - its much prettier)

```diff
commit 33516ffbc3cbc973958fe5fda665406923390784 (HEAD -> master)
Author: Adina Wagner <adina.wagner@t-online.de>
Date:   Thu Jun 20 15:18:38 2019 +0200

    even more randomness to this file

commit 2f13b9ee08fb4aaa625802a70b8d5694d26b91ee
Author: Adina Wagner <adina.wagner@t-online.de>
Date:   Thu Jun 20 15:03:21 2019 +0200

    add random input to first file
```

13) put more files into your repository: Call the first file ``nena.txt`` and add the lyrics to ["99 Luftballons"](https://www.nena.de/de/99-luftballons). Add the [first 300 digits of pi](http://digitsofpi.com/Top-300-Digits-Of-Pi.htm) to ``pi.txt``
    
14) add and commit these files *subsequently*, e.g. by adding + committing and specifiying the file name explicitly (``git add nena.txt``, ``git commit nena.txt``)

15) Delete the last verse from 99 Luftballons. Show the difference with ``git diff``, then add and commit your changes.
```diff
diff --git a/nena.txt b/nena.txt
index 77edda7..6256cbb 100644
--- a/nena.txt
+++ b/nena.txt
@@ -34,11 +34,3 @@ Mann, wer hätte das gedacht
 Dass es einmal soweit kommt
 Wegen 99 Luftballons
 
-99 Jahre Krieg
-Ließen keinen Platz für Sieger
-Kriegsminister gibt’s nicht mehr
-Und auch keine Düsenflieger
-Heute zieh ich meine Runden
-Seh’ die Welt in Trümmern liegen
-Hab’ ‘nen Luftballon gefunden
-Denk’ an dich und lass’ ihn fliegen
```

16) you realize your second commit ("even more randomness to this file!") did not make sense. Find this commit in the ``git log`` and copy the first 6-10 characters from the 40 character long ``hash`` git identifies the file in that version with. (here it is ``33516ffbc3c``)
```
git log

commit fcc49d7dafedec835bcd1019c59b5cec4fcdd3e0 (HEAD -> master)
Author: Adina Wagner <adina.wagner@t-online.de>
Date:   Thu Jun 20 15:42:39 2019 +0200

    delete last verse from 99 Luftballons

commit 900dd3a52a6c6d2b09e93b2afbec1e44985d54d4
Author: Adina Wagner <adina.wagner@t-online.de>
Date:   Thu Jun 20 15:33:30 2019 +0200

    add 300 digits of pi

commit 17504ee02ff232886c6ceaef1aaf36b1e5dc3bde
Author: Adina Wagner <adina.wagner@t-online.de>
Date:   Thu Jun 20 15:33:14 2019 +0200

    add 99 Luftballons songtext

commit 33516ffbc3cbc973958fe5fda665406923390784
Author: Adina Wagner <adina.wagner@t-online.de>
Date:   Thu Jun 20 15:18:38 2019 +0200

    even more randomness to this file

commit 2f13b9ee08fb4aaa625802a70b8d5694d26b91ee
Author: Adina Wagner <adina.wagner@t-online.de>
Date:   Thu Jun 20 15:03:21 2019 +0200

    add random input to first file


```

17) Revert this commit: ``git revert <hash>``

18) you are looking for the number ``99`` in this repository. Instead of opening all files and looking through them, you can run ``git grep 99`` (The output would highlight 99s in your terminal):

```diff
nena.txt:Von 99 Luftballons
nena.txt:Von 99 Luftballons
nena.txt:99 Luftballons
nena.txt:Nur 99 Luftballons
nena.txt:99 Düsenflieger
nena.txt:Auf 99 Luftballons
nena.txt:99 Kriegsminister
nena.txt:Wegen 99 Luftballons
pi.txt:141592653589793238462643383279502884197169399375105
pi.txt:82097494459230781640628620899862803482534211706798
```

**B) FORKING, CLONING, REMOTES AND PULL REQUESTS**

1) Fork this repository to your own account (click the fork button in the top right corner)

2) Clone **your fork** of this repository (if you have an SSH key, clone via SSH)
`` git clone https://github.com/<USERNAME>/git_intro.git ``

3) This clone currently has one ``remote``: Your fork on your Github user account. You can see this by listing the remotes: ``git remote -v``

```
origin	git@github.com:<USERNAME>/git_intro.git (fetch)
origin	git@github.com:<USERNAME>/git_intro.git (push)
```

4) Lets make your clone aware of the original Github repository by adding it as a remote:
with SSH: ``git remote add gh-adswa git@github.com:adswa/git_intro.git``
with HTTP: ``git remote add gh-adswa https://github.com/adswa/git_intro.git``

5) In the directory ``files/``, create a textfile. The name of your textfile should be your first name. The content of the file should be a link to your favourite webcomic. Add and commit this file to the repo.

6) Open the json file ``zenodo.json`` in an editor of your choice.
**Add a (random) affiliation, (random) name, and (random) orcid to your assigned spot**, and then **add** and
**commit** the change.

7) **push** the new file and the change to ``zenodo.json`` to your fork: ``git push``

8) go to your Github account and your fork of this repository. Submit a pull request.

9) on your computer, integrate the changes we collaboratively made to this repository with ``git pull gh-adswa``


**BRANCHING & MERGING**
1) **Within** the cloned repository (on your local machine), you want to create a new ``branch``. List all existing branches with ``git branch -a``

```diff
* master
  remotes/upstream/master
```

2) Create a new branch that you name like your last name, and *move* (``checkout``) this branch: 
```
git branch Wagner 
git checkout Wagner
  Switched to branch 'Wagner'

```
[There is a shortcut for the above: ``git checkout -b Wagner``]


3) on this branch, create a new file, add it to the staging area, and commit it.
4) To create a pull request from this branch (**as is good practice for pull requests**): push it to your local fork:
``git push --set-upstream origin Wagner``
```
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 305 bytes | 305.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
remote: 
remote: Create a pull request for 'Wagner' on GitHub by visiting:
remote:      https://github.com/adswa/git_intro/pull/new/Wagner
remote: 
To github.com:adswa/git_intro.git
 * [new branch]      Wagner -> Wagner
Branch 'Wagner' set up to track remote branch 'Wagner' from 'origin'.

```
5) Lets say you want to merge this branch into your master branch locally:
```
git checkout master
git merge Wagner
```

## Here are a few git resources:

- a condensed summary of git principles and commands in [our docs](https://docs.inm7.de/tools/git/): https://docs.inm7.de/tools/git/
- The git [cheat sheet](https://github.github.com/training-kit/downloads/github-git-cheat-sheet.pdf): https://github.github.com/training-kit/downloads/github-git-cheat-sheet.pdf
- a well-made git [tutorial](https://swcarpentry.github.io/git-novice/): https://swcarpentry.github.io/git-novice/
- [Pro git](https://git-scm.com/book/en/v2), a comprehensive book on everything git: https://git-scm.com/book/en/v2
- a [game](https://learngitbranching.js.org/) to learn branching with: https://learngitbranching.js.org/
