# Chapter 1. Repositories and Branches
- The best way to get one is by using the **git-clone** command to download a copy of an existing repository.
```
$ git clone git://git.kernel.org/pub/scm/git/git.git
```

- The clone command creates a new directory named after the project (`git` or `linux` in the examples above). After you cd into this directory, you will see that it contains a copy of the project files, called the [working tree](https://mirrors.edge.kernel.org/pub/software/scm/git/docs/user-manual.html#def_working_tree), together with a special top-level directory named `.git`, which contains all the information about the history of the project.