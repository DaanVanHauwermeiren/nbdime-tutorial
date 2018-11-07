# nbdime-tutorial
tutorials for usage of nbdime

nbdime
Tools for diffing and merging of Jupyter notebooks.
https://github.com/jupyter/nbdime

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

```Note: when using anaconda as your python installation toolbox, make sure you install it in the desired environment. If needed, switch to the desired environment by:```

    source activate ENV_NAME #linux, macos
    activate ENV_NAME #windows

[reference](https://nbdime.readthedocs.io/en/latest/index.html#quickstart)

## console commands

https://nbdime.readthedocs.io/en/latest/cli.html

## notebook extensions

https://nbdime.readthedocs.io/en/latest/extensions.html

## version control integration

https://nbdime.readthedocs.io/en/latest/vcs.html

## configuration

https://nbdime.readthedocs.io/en/latest/config.html

## glossary

https://nbdime.readthedocs.io/en/latest/glossary.html