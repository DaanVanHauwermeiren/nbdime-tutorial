# nbdime-tutorial
tutorial for usage of nbdime

nbdime
Tools for diffing and merging of Jupyter notebooks.
https://github.com/jupyter/nbdime

## dependencies

This tutorial is written and tested on the following versions:

    python      3.6.6
    notebook    5.7.0
    nbdime      1.0.3

This does not work with the following combination:

    python      2.7.12
    notebook    4.2.3
    nbdime      1.0.3

[reference](https://nbdime.readthedocs.io/en/latest/installing.html#dependencies)

## why

Jupyter notebooks are useful, rich media documents stored in a plain text JSON format. This format is relatively easy to parse. However, primitive line-based diff and merge tools do not handle well the logical structure of notebook documents

**nbdime**, on the other hand, provides “content-aware” diffing and merging of Jupyter notebooks. It understands the structure of notebook documents. Therefore, it can make intelligent decisions when diffing and merging notebooks, such as:

* eliding base64-encoded images for terminal output
* using existing diff tools for inputs and outputs
* rendering image diffs in a web view
* auto-resolving conflicts on generated values such as execution counters

[reference](https://nbdime.readthedocs.io/en/latest/index.html)

## installation

    pip install nbdime

```Note: when using anaconda as your python installation toolbox, make sure you install it in the desired environment. Because of integration into the jupyter extensions, installation in the same environment as your jupyter notebook installation is strongly advised. If you are unsure which environment this is, it is probably the base environment. If needed, switch to the desired environment by:```

    source activate ENV_NAME #linux, macos
    activate ENV_NAME #windows

[reference](https://nbdime.readthedocs.io/en/latest/index.html#quickstart)

## console commands

nbdime provides the following CLI commands:

    nbshow
    nbdiff
    nbdiff-web
    nbmerge
    nbmerge-web
    mergetool
    config-git

### nbshow

**nbshow** gives you a nice, terminal-optimized summary view of a notebook. You can use it to quickly peek at notebooks without launching the full notebook web application.

available options:

    ignorables:
    Set which parts of the notebook (not) to show.

    -s, --sources, -S, --ignore-sources
        show/ignore sources.
    
    -o, --outputs, -O, --ignore-outputs
        show/ignore outputs.
    
    -a, --attachments, -A, --ignore-attachments
        show/ignore attachments.
    
    -m, --metadata, -M, --ignore-metadata
        show/ignore metadata.
    
    -d, --details, -D, --ignore-details
        show/ignore details not covered by other options.

quickref:

    # view code, ignoring output and any metadata:
    nbshow -M -O THE_NOTEBOOK.ipynb

    # view output, ignoring code and metadata
    nbshow -M -S -D THE_NOTEBOOK.ipynb

### diffing

nbdime offers two commands for viewing the diff between two notebooks:

* **nbdiff** for command-line diffing
* **nbdiff-web** for rich web-based diffing of notebooks

#### nbdiff

**nbdiff** does a terminal-optimized rendering of notebook diffs. Pass it the two notebooks you would like to compare, and it returns a nice, readable presentation of the changes in the notebook.

available options: see [nbshow](###nbshow)

quickref:

    # purely compare code, ignoring output and metadata changes
    nbdiff -M -O -D THE_NOTEBOOK_1.ipynb THE_NOTEBOOK_2.ipynb

    # look for code and output changes, ignoring metadata changes
    nbdiff -M -D THE_NOTEBOOK_1.ipynb THE_NOTEBOOK_2.ipynb

    # look for output changes, ignoring metadata and code changes
    nbdiff -M -S -D THE_NOTEBOOK_1.ipynb THE_NOTEBOOK_2.ipynb

#### nbdiff-web

Like **nbdiff**, **nbdiff-web** compares two notebooks.

Instead of a terminal rendering, **nbdiff-web** opens a web browser, compares the two notebooks, and displays the rich rendered diff of images and other outputs.

available options: see [nbshow](###nbshow)

quickref: see [nbdiff](####nbdiff) (replace nbdiff with nbdiff-web)

### merging

possibly redundant: check git integration?

[reference](https://nbdime.readthedocs.io/en/latest/cli.html)

## notebook extensions

To install and enable the nbdime jupyter extensions, run:

    nbdime extensions --enable --sys-prefix

After installing the extensions, one or two buttons should show up in the notebook toolbar. 

Clicking the git button will open a new tab showing the diff between the last commit and the currently saved version of the notebook. Note that this button will only be visible if the notebook is currently in a git repository.

Clicking the checkpoint button will similarly show the diff between the checkpointed and currently saved versions of the notebook.

[reference](https://nbdime.readthedocs.io/en/latest/extensions.html)

## version control integration (GIT)

Git integration of nbdime is supported in two ways:

* through drivers for diff and merge operations, where nbdime takes on the responsibility for performing the diff/merge:

    * Diff driver
    * Merge driver

* through defining nbdime as diff and merge tools, which allow nbdime to display the diff/merge to the user without having to actually depend on git:

Diff web tool
Merge web tool

Configure git integration by editing the .gitconfig (or .git/config) and .gitattributes in each git repository or in the home/etc directory for global effect.

To configure all diff/merge drivers and tools, simply call:

    # locally in one git repo
    nbdime config-git --enable
    # global / system configuration
    nbdime config-git --enable --global|--system

Once configured, the diff/merge drivers should simply work out of the box. For example, the normal git diff command should give you the standard diff for any non-notebook files, but use nbdime’s command-line diff for all ```.ipynb``` files. Nbdime will also be used for all merges on notebook files (no specific commands needed).

For more details, see the reference

[reference](https://nbdime.readthedocs.io/en/latest/vcs.html)

## configuration

https://nbdime.readthedocs.io/en/latest/config.html

## glossary

https://nbdime.readthedocs.io/en/latest/glossary.html