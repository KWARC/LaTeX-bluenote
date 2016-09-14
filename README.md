bluenote.sty: KWARC blue notes

Copyright(c) 2012 Michael Kohlhase
The package is distributed under the terms of the LaTeX Project Public License (LPPL)

The development version of this package can be found at
https://github.com/KWARC/LaTeX-bluenote

# Using this repo in a paper repository
We write most of our papers in ```git``` repositories, there it is usually a good idea to
make this repository into an external sub-repository that can be updated as necessary. In
the instructions below we assume that you - as the paper repos maintainer - want to add the
KWARC LaTeX-bluenote as a sub-repository at path ```LaTeX-bluenote``` from the top of the paper
repository.
## The best way for GIT
is via the ```git-subrepo``` extension of ```git```. Unfortunately this is not part of git
(yet). So you as the paper repos maintainer have to
[install it first](https://github.com/git-commands/git-subrepo#readme) if you want to
install the KWARC LaTeX-bluenote as a subrepos. Your users do not, they will get the subrepos
automatically on ```git clone``` or ```git pull```. 

1. go to the top of your paper preository: ```cd path/to/top``` (you can only make a
  "subrepo" from there) 
2. add the KWARC LaTeX-bluenote repos as a "subrepo": ```git subrepo clone git@github.com:KWARC/LaTeX-bluenote.git LaTeX-bluenote```

Note that under ```git-subrepo``` the "external" is not updated automatically, a
maintainer has to "pull" it. This can be seen as a feature and not a bug (there is less of
a chance to break things).

1. go to the top of your paper preository: ```cd path/to/top``` (you can only pull from there)
2. pull the KWARC LaTeX-bluenote repos as a "subrepo": ```git subrepo pull LaTeX-bluenote```

To contribute changes back to the the KWARC LaTeX-bluenote repository, you analogously do 

1. go to the top of your paper preository: ```cd path/to/top``` (you can only push from there)
2. pull the KWARC LaTeX-bluenote repos as a "subrepo": ```git subrepo push LaTeX-bluenote```

easypeasy!

## The second best way for GIT
is via ```git subtree```. 

1. go to the top of your paper repository: ```cd path/to/top```
2. add the KWARC LaTeX-bluenote repos as a remote: ```git remote add LaTeX-bluenote
    git@github.com:KWARC/LaTeX-bluenote.git``` under the name ```LaTeX-bluenote```.
3. add the remote ```LaTeX-bluenote```  as a subtree: ```git subtree add --prefix=LaTeX-bluenote LaTeX-bluenote master --squash```
  (here under the path ```LaTeX-bluenote```). The ```--squash``` reduces history noise. 

When you want to update the subrepository to the newest version, you have to "subtree
pull" as above: 

1. go to the top of your paper repository: ```cd path/to/top```
2. subtree-pull: ```git subtree pull --prefix=LaTeX-bluenote LaTeX-bluenote master --squash```
  this is a bit inconvenient, but works well.

Contributing back to the KWARC LaTeX-bluenote repository is somewhat more complex; RTFM!

## Externals in SVN
In a subversion repository you can must make an external by

1. go to the top of your paper preository: ```cd path/to/top```
2. make the ```lib``` subdir if necessary: ```mkdir lib```
3. add the external: ```svn propedit svn:externals lib```
4. an editor will appear, add the line ```LaTeX-bluenote LaTeX-bluenote https://github.com/KWARC/LaTeX-bluenote/trunk```
5. commit your work: ```svn commit -m'adding external for the KWARC LaTeX-bluenote'```

Note that in SVN any ```snv update``` will update the KWARC LaTeX-bluenote in the external as well. 
