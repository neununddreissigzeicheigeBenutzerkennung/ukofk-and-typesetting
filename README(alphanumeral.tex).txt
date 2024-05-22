Alphanumeral Macro Package
Version 1.0

Summary:
---------
The alphanumeral.tex script provides TeX macros for converting numbers into alphabetical characters. It converts numbers to a sequence of lowercase or uppercase letters similar to spreadsheet column labeling (e.g., 0 -> 'a', 1 -> 'b', ..., 25 -> 'z', 26 -> 'aa', 27 -> 'ab', etc.).

Dependencies:
-------------
This script has no external dependencies. It is designed to work with any TeX distribution that supports plain TeX.

Usage:
-------
To use the Alphanumeral Macro Package:

1. Add the alphanumeral.tex script to your TeX installation. Place the script in a directory where TeX searches for input files by default. Common directories include the current working directory, directories specified in the TEXINPUTS environment variable, or directories configured in your TeX distribution's settings.

2. Include alphanumeral.tex in your TeX document using the \input command. Since the script is now part of your TeX installation, you won't need to specify the full path to the script every time you use \input. For example:

    \input alphanumeral.tex

3. Use the \alphanumeral macro to convert numbers to lowercase alphabetical characters, and \ALPHANUMERAL for uppercase alphabetical characters.

Example Usage:
--------------
Below is a minimal example demonstrating the usage of the Alphanumeral Macro Package in a TeX document:

\input alphanumeral.tex

\alphanumeral{0}, \alphanumeral{1}, \alphanumeral{25}, \alphanumeral{26}, \alphanumeral{27}
\ALPHANUMERAL{0}, \ALPHANUMERAL{1}, \ALPHANUMERAL{25}, \ALPHANUMERAL{26}, \ALPHANUMERAL{27}

This example prints the lowercase and uppercase alphabetical characters corresponding to the input numbers.

Contact:
---------
For any issues, suggestions, or contributions, please contact the author.

Author: ukofk
Email: ukofk@student.kit.edu
