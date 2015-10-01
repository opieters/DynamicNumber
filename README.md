Dynamic Number
==============

What is it?
-----------

Dynamic Number dynamically typesets values generated in different kinds of scripts in LaTeX. The aim is to reduce errors resulting from out-of-date numbers by directly setting them in the number generating file and importing a symbolic link in the LaTeX source file.

It can be used to import not only numerical values into LaTeX, but even strings and pieces of code are possible. The main repository is located in [this]() repository.

Installation
------------

Depending on your desires, one or more might not be applicable. All the supported languages have a file in the `languages` folder. Currently only MATLAB and Python are supported to produce Dynamic Number (dn) list files.

### LaTeX

Currently the package is also available on CTAN. This is the preferred way of installing LaTeX packages. You can thus download it using your favourite (La)TeX package manager. The instructions below are thus obsolete.

#### Linux and OS X

Run the installation file in terminal: `source install.sh`.

#### Windows

For Windows, there is not yet a script. You must install it manually and add it to MiKTeX.

1. Open the command line (`CTRL-R` and type `cmd`).
2. Create the package with: `latex dn.ins`.
3. Extract the documentation to pdf with: `pdflatex dn.dtx`.
4. Use the instructions in [this](http://tex.stackexchange.com/questions/2063/how-can-i-manually-install-a-package-on-miktex-windows)

### MATLAB

Add the necessary functions to MATLAB's path.

1. Clone the directory in your MATLAB folder (`Documents/MATLAB`).
2. Now the contents should be in `Documents/MATLAB/DynamicNumber`.
3. Open MATLAB.
4. Set path to include the cloned folder. The Set path can be found in the File menu on older MATLAB installations or HOME, Environment in newer installations.

### Python

**TODO** Add to PyPI if stable.

For the moment, add it to your project directory.

Quick start
-----------

### LaTeX

LaTeX usage is very straightforward. Load the package with `\usepackage{dn}` and next load a dyamic number list with `\dnreadfile{list}`. Now you can start using your dynamic variables with `\dnget{variable}`.

More information and additional commands can be found in the documentation.

**Attention!** Do not attempt to create a `pgfkey` with the name `dynamicnumber`, it will conflict with the internal workings of the package.

### MATLAB and Python

Create a dynamic number list with the `dn()` command, then add symbolic links with the `add`-method.

The `add`-method requires at least 2 arguments: the symbolic link name and a value (either numerical or string). The optinal third can specify a unit for the value. The symbolic link will be stored to typeset both number and unit in a nice way, with the `units` package (`\unit{<value}{<unit>}`).

Example (in Python, MATLAB code is almost identical)

```python
# Some computations and sensor readout to predict temperature tomorrow:
temperature = 23.4
temp_predictions = dn('TemperaturePredictions')
temp_predictions.add('tomorrow',temparture,'C') # or \\Celcius instead of C
```

**Note!**: If you wish to use special LaTeX commands such as `\Celcius` or `\metre`, your need to be careful with the use of the backslash. In MATLAB you only need to add one backslash because of the way it is parsed, but in Python you need to add two of them! This is needed because the backslash is also used for escape sequences.

### Contributions

The libraries are basic in a sense that they do not have a lot of features or options. This is intentional. Users can easily adopt them to suit their own needs without having to go through 100s of lines of code and the learning curve is very small. So the main goal is to have a library that support many platforms, is (almost) identical on all these platforms and is simple to use.

Bug fixes and small feature improvements are always welcome, you can use a pull request to add must-have features or perform bug fixes.

### License

See the `LICENSE` file.