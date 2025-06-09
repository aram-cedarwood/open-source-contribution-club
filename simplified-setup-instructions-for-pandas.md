# Simplified Set-Up Instructions for pandas Contribution

* https://github.com/pandas-dev/pandas
* https://pandas.pydata.org/docs/development/contributing.html

## Set up initially

1. If you're on a Windows machine, find a MacOS or Linux machine. Or install a [VM](https://www.virtualbox.org/). Anything but Windows.
1. Fork the pandas repo.
	* [ ] On `https://github.com/pandas-dev/pandas`, hit the `Fork` button on the top right.
	* [ ] Uncheck the checkbox for "Copy the main branch only."
	* [ ] Hit `Create Fork`.
1. On your local machine, install git, if you haven't already.
	* [ ] Run `~$ sudo apt install git`.
	* [ ] If it tells you to set up your Github Personal Access Token, do whatever it tells you to do.
1. Clone the pandas repo and connect your repository to the upstream pandas repository.
	* [ ] Run `~$ git clone https://github.com/<your-user-name>/pandas.git` on your local machine. (But change `<your-user-name>` with your user name, obviously.)
	* [ ] Run `~$ cd pandas`
	* [ ] Run `~/pandas$ git remote add upstream https://github.com/pandas-dev/pandas.git`.
	* [ ] Run `~/pandas$ git fetch upstream`
1. Install Mamba.
	* [ ] Run `~/pandas$ uname -a` to check Linux architecture, to download mamba.
	* [ ] On `https://github.com/conda-forge/miniforge`, download the installer that corresponds to your architecture.
	* [ ] Run `~/pandas$ bash ~/Downloads/Miniforge3-Linux-x86_64.sh`. (But change `~/Downloads/Miniforge3-Linux-x86_64.sh` with the path to the file you just downloaded, obviously.)
	* [ ] To `Do you wish the installer to initialize Miniforge3 by running conda init?`, answer `yes`.
	* [ ] Close and reopen terminal.
	* [ ] Run `(base) ~/pandas$ mamba update mamba`.
	* [ ] Run `(base) ~/pandas$ mamba env create --file environment.yml`.  
	If the above did not work, try one of these:
		* [ ] Run `(base) ~/pandas$ mamba env remove -n pandas-dev`.
		* [ ] Run `(base) ~/pandas$ mamba clean --all`.
	* [ ] Run `(base) ~/pandas$ mamba activate pandas-dev`. (Later, we can deactivate with `mamba deactivate`.)
1. Build C extensions.
	* [ ] Run `(pandas-dev) ~/pandas$ python setup.py build_ext --inplace -j 4`. `-j` specifies the number of cores for parallelization. If you have trouble, try reducing that number.
	* [ ] Run `(pandas-dev) ~/pandas$ python -m pip install -ve . --no-build-isolation --config-settings editable-verbose=true`.
1. To verify that our set-up is successful, see if we can import pandas.
	* [ ] Run `(pandas-dev) ~/pandas$ python`.
	* [ ] Run `>>> import pandas as pd`.
1. To verify that our set-up is successful, see if we can run tests.
	* [ ] Run `(pandas-dev) ~/pandas$ python -m pytest pandas/tests/test_take.py`. (Replace `pandas/tests/test_take.py` with any test file you want to run. You may replace it with `pandas/tests` to run all tests, but keep in mind that will take a very long time to run.)
1. Install pre-commit.
	* [ ] Run `(pandas-dev) ~/pandas$ pre-commit install`. Each time you `git commit` changes, all styling checks will run. When any check fails, `git commit` will not go through.

## Find and assign yourself to an issue

1. Find and assign yourself to an issue. (Please do NOT take more than 2 at a time.)
	* [ ] Find an issue to work on on https://github.com/pandas-dev/pandas/issues.
	* [ ] Assign yourself to an issue by commenting `take` (Once you do, a bot will assign you to the issue).

## Sync before you hack

1. git merge
	* [ ] Run `(base) ~/pandas$ git checkout main`.
	* [ ] Run `(base) ~/pandas$ git pull upstream main`.
	* [ ] Run `(base) ~/pandas$ git push origin main`.
	* [ ] Run `(base) ~/pandas$ git checkout -`.
	* [ ] Run `(base) ~/pandas$ git merge main`.
1. Update and activate mamba.
	* [ ] Run `(base) ~/pandas$ mamba update mamba`.
	* [ ] Run `(base) ~/pandas$ mamba activate pandas-dev`. (Later, we can deactivate with `mamba deactivate`.)
1. Build C extensions.
	* [ ] Run `(pandas-dev) ~/pandas$ python setup.py build_ext --inplace -j 4`. `-j` specifies the number of cores for parallelization. If you have trouble, try reducing that number.
	* [ ] Run `(pandas-dev) ~/pandas$ python -m pip install -ve . --no-build-isolation --config-settings editable-verbose=true`.
1. To verify that your set-up is successful, see if you can import pandas.
	* [ ] Run `(pandas-dev) ~/pandas$ python`.
	* [ ] Run `>>> import pandas as pd`.
1. To verify that your set-up is successful, see if you can run tests.
	* [ ] Run `(pandas-dev) ~/pandas$ python -m pytest pandas/tests/test_take.py`. (Replace `pandas/tests/test_take.py` with any test file you want to run. You may replace it with `pandas/tests` to run all tests, but keep in mind that will take a very long time to run.)

## Create a pull request

1. Update whatsnew
	* [ ] Update doc/source/whatsnew/vx.y.z.rst https://pandas.pydata.org/docs/development/contributing_codebase.html#documenting-your-code
1. Create a pull request.
	* [ ] Follow the convention for title prefixes: https://pandas.pydata.org/docs/development/contributing.html#making-a-pull-request
