**Introduction**
Working with professor Megan Hofmann -> https://www.megan-hofmann.com/

who is the developer of the python library -> https://pypi.org/project/knit-script/

Knit Script is a specialized programming language tailored for creating instructions for V-bed knitting machines. This language draws inspiration from Python 3 conventions but incorporates features to control knitting machines. The code you write in Knit Script is translated into knitout format, which can then be processed into instructions suitable for various types of knitting machines.

**Setting Up:**

To get started, you can install the development version from the local source code using these commands:

```shell
$ git clone https://github.com/mhofmann-Khoury/knit_script.git
$ pip install -e .
```

This will clone the repository to your local machine and install the system for active development, making Knit Script accessible from anywhere on your machine as a standard Python library.

For updating the distribution, use these commands from the repo directory:

```shell
$ python setup.py sdist
$ python -m build
$ twine upload dist/*
```

Alternatively, you can install the stable version from PyPI with:

```shell
$ pip install knit-script
```

**Adding Your DAT Compiler:**

Please note that the DAT compiler used for controlling Shima Seiki machines is copyrighted and not provided with this distribution. You can install your own DAT compiler under the `dat_compiler` folder in your installation. Name the JavaScript entry point `knitout-to-dat.js` and ensure that the main method accepts two arguments for the knitout file name and the output DAT file name.

**Kniterate Compiler:**

While the provided samples haven't been tested on a Kniterate machine, the knitout to Kniterate compiler is available and should work with standardized knitout files.

**Testing Your Installation:**

You can verify your installation by using the `installation_test.ks` and `installation_test.py` files. Running `installation_test.py` should generate two files: `stst_10.k` and `stst_10.dat` (if you have included a DAT compiler). Similarly, you can convert `installation_test.ks` into the same files using the provided entry points.

**Using Knit Script from the Command Line (Unix):**

You can utilize Knit Script from the command line on Unix-like systems with the following command format:

```shell
$ knit-script -k <name for knitout to generate> -d <name for dat file to generate, optional> <name of knit_script file>
```

For example, to convert `installation_test.ks`, you would use:

```shell
$ knit-script -k stst_10.k -d stst_10.dat installation_test.ks
```

**Using Knit Script from the Command Line (Windows):**

On Windows, you can access Knit Script by running `knit_script.bat` or adding it to your system's PATH. The command format is similar:

```shell
$ knit_script.bat -k <name for knitout to generate> -d <name for dat file to generate, optional> <name of knit_script file>
```

For example:

```shell
$ knit_script.bat -k stst_10.k -d stst_10.dat installation_test.ks
```

**Using Knit Script Interpreter from Python:**

To generate a knitout file from Knit Script using Python, you can utilize the following code:

```python
from knit_script.interpret import knit_script_to_knitout

knit_graph = knit_script_to_knitout('<pattern file>', '<knitout file name>')
```

To also generate a DAT file, use:

```python
from knit_script.interpret import knit_script_to_knitout_to_dat

knit_graph = knit_script_to_knitout_to_dat('<pattern file>', '<knitout file name>', '<dat file name>')
```

Additional examples of accessing the interpreter can be found in the test package.

**Knit Script DSL:**

Knit Script is designed as a scripting language that combines the convenience of standard languages like Python 3 with features tailored for V-bed machine knitting. It introduces variables, control structures, functions, access to imported Python libraries, and more. Knit Script translates down to knitout operations that are validated and should run smoothly on your knitting machine.

**Carriage Passes:**

The fundamental control structure in Knit Script is the carriage pass. A carriage pass represents a sequence of consecutive needle operations (e.g., knit, tuck, miss, split, drop, xfer) that occur in one pass of the knitting machine's carriage. The direction of the carriage pass determines the order of these operations.

Knit Script allows you to disambiguate which needles to operate on from the direction of the carriage pass within control structures. V-bed knitting permits two types of carriage passes: those involving yarn carriers and those that don't. You can mix operations involving yarn carriers within a single carriage pass.

**Directed Carriage Passes:**

A directed carriage pass is defined by a direction and a list of operations applied to specific needles. For example, you can knit even-numbered front needles in a left
