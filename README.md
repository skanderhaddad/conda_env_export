## Conda Export Tool

A simple tool that produces environment files for
easily sharing a conda environment. This script uses the PyYAML package.
Additionally, it was tested on Python 3.9 but I think it should work for
any version that supports f-strings.

The three main issues I wanted to solve about the built-in
conda env export tool are the following:

    - Not including pip installations when using flag `--from-history`
    - When using flag `--from-history`, package versions are often not
    included (depending on whether the user manually typed them)
    - When using --from-history flag, third-party channels are not included
    in the file.

I want to be able to do the following:
```sh
conda env export --from-history > environment.yml
```
and have a file that contains stricly the packages I installed (but including
those with pip). Additionally, those packages should have the version number
that was installed in the environment. This script solves that. 

First of all,activate your conda environment
```sh
conda activate your_env_name
```
and install pyyaml package

Run the script inside the conda environment you want to export:
It uses by default --from-history

```sh
python conda_export.py -o environment.yml
```

but including pip packages as well as conda channel.

Credits:
This script uses part of the gist you can find here:
https://gist.github.com/gwerbin/dab3cf5f8db07611c6e0aeec177916d8  
and this github repo: 
https://github.com/andresberejnoi/PublicNotebooks/tree/master/Conda%20Tools
