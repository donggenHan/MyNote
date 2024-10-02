# Chapter 1. Repositories and Branches
- The best way to get one is by using the **git-clone** command to download a copy of an existing repository.
```
$ git clone git://git.kernel.org/pub/scm/git/git.git
```

- The clone command creates a new directory named after **the project** . 
- After you cd into this directory, you will see that it contains a copy of the project files, called the [working tree](https://mirrors.edge.kernel.org/pub/software/scm/git/docs/user-manual.html#def_working_tree), together with a special top-level directory named `.git`, which contain**s all the information about the history of the project**.

- Git is best thought of as a tool for **storing the history of a collection of files**. It stores the history **as a compressed collection of interrelated snapshots of the project’s contents**. In Git each such version is called a [commit](https://mirrors.edge.kernel.org/pub/software/scm/git/docs/user-manual.html#def_commit).
- Those snapshots aren’t necessarily all arranged in a single line from oldest to newest; instead, work may simultaneously proceed along parallel lines of development, called [branches](https://mirrors.edge.kernel.org/pub/software/scm/git/docs/user-manual.html#def_branch), which may merge and diverge.