## Mercurial, not Subversion! ##

We use the distributed version control system Mercurial for our source code control instead of svn. Since GoogleCode only supports svn, we use bitbucket.org to host our sourcecode.


## How to get the source ##

To simply browse through the source code, go to http://www.bitbucket.org/mercurysquad/xnu-speedstep/src/

To download the source code for building yourself, or making changes, you need to install Mercurial (preferred way).
An alternative is to simply download a tarball of the source. You can do so by choosing the "Download" link from the Bitbucket page, or from the link on the front page. You will need to manually create the patch using diff -Naur.

Download Mercurial from here: http://mercurial.berkwood.com/  Once you have it installed, start a terminal, go to the folder where you keep your source code etc. and type:

```
hg clone https://bitbucket.org/mercurysquad/xnu-speedstep/
```

This will clone our repository, ready for you to hack on. Once you're done making changes, do:
```
hg commit
hg export tip > filename.diff
```

Then attach it and post it to use from the Issues page! More info on how to use Mercurial is at http://www.selenic.com/mercurial/wiki/index.cgi/QuickStart

**Note**: If after cloning the repository you don't see a proper directory structure (Source, Reference..), try `hg update -C autothrottle-magic`. We are working on that branch currently and will merge it back to default once it's done.