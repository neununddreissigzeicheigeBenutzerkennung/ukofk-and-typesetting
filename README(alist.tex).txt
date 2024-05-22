Custom List Environment Script (Version 1.0)

Summary:
---------
The list.tex script defines a custom list environment (\list) in plain TeX. This environment allows for flexible formatting of list elements, including the option to automatically number them. It calculates the maximum width of the bullet points and adjusts the indentation of list items accordingly.

Dependencies:
--------------
This script has no external dependencies. It is designed to work with any TeX distribution that supports plain TeX.

Usage:
-------
To use the custom list environment:

1. Add the list.tex script to your TeX installation. Place the script in a directory where TeX searches for input files by default. Common directories include the current working directory, directories specified in the TEXINPUTS environment variable, or directories configured in your TeX distribution's settings.

2. Include list.tex in your TeX document using the \input command. Since the script is now part of your TeX installation, you won't need to specify the full path to the script every time you use \input. For example:

    \input list.tex

3. Define the list environment using the \list command, providing the desired bullet point format and the list content.

4. Optionally, customize the bullet point format and list content according to your requirements.

Example Usage:
--------------
Below is an example TeX document using the custom list environment:

\input list.tex

\list{\advance\listcount by 1 \number\listcount.\ }{
\item{First item}
\item{Second item with longer text}
\item{Third item}
}


In this example, the list environment is defined with automatic numbering of list items.

Contact:
---------
For any issues, suggestions, or contributions, please contact the author.

Author: ukofk
Email: ukofk@student.kit.edu
