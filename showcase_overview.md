**problem 1**

> you have two versions of a notebook, created in a long forgotten time. Which one is which and how do they differ?

**solution 1**

> make a diff

**problem 2**

> standard diffing between notebooks is quite unpleasing for the eye

standard diffing on *nix systems:

    diff 1.ipynb 2.ipynb

**solution 2**

> ignoring all the json mumbo jumbo, all the outputs of the cells, and the metadata.

**problem 2**

> how to do this easily?

**solution 3**:

> nb-dime

diffing using nb-dime

    # [optional] setting the correct conda environment
    source activate ENVIRONMENT
    # nb-dime example
    # command line interface
    nbdiff -s 1.ipynb 2.ipynb
    # Web interface
    nbdiff-webb 1.ipynb 2.ipynb

showing a notebook in a terminal

    cat 1.ipynb
    nbshow -OMD 1.ipynb 

**comparison from jupyter**

> nb-dime notebook extension