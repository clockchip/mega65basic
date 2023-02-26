![mega65basic logo](https://github.com/clockchip/mega65basic/blob/main/images/mega65basic_logo.png)

# **** MEGA65 Basic Language **** (mega65basic) Visual Studio Code Extension

This extension helps with the creation of programs in "Basic 65 V920377" (.prg or .bas extension) for the "MEGA65 Personal Computer System" within Visual Studio Code. It offers a range of useful features, including syntax highlighting, code snippets, file icons, theme options, and rulers.

This extension is developed using the code and tools available in the following GitHub repositories:
- [Yo Code- Extension and Customization Generartor](https://github.com/microsoft/vscode-generator-code)
- [c64basicv2 Visual Studio Code Extension](https://github.com/gverduci/c64basicv2)

Rules for snippets come from the following pages of C64-Wiki & Mega65 Filehost:
- [Mega65 BASIC 65 Reference](https://files.mega65.org/files/m/mega65-basic65-reference_PeK0ek.pdf) 
- [Control character](https://www.c64-wiki.com/wiki/control_character) 

To transfer and execute the code written using this extension to your MEGA65, you will require the following tools:
- [petcat tool from VICE Emulator](https://vice-emu.sourceforge.io/)
- [Xemu](https://github.lgb.hu/xemu/)
- [Mega65 Tools](https://github.com/MEGA65/mega65-tools)

You might follow this process to develop your program:
1. create a folder structure like this:

        \    -> root dir
        \bin -> converted programs
        \src -> source programs

2. write the program; 
3. tokenize and convert the source *.bas file into a *.prg file, by using the following command in the Terminal window of Visual Studio Code:
        
        petcat -w65 -o ./bin/outputfile.prg -- ./src/inputfile.src

3. test it with [Xemu](https://github.lgb.hu/xemu/) using the "Run PRG directly" command;
4. Connect your MEGA65 with the computer which is running the MEGA65 Tools;
5. Transfer the output.prg file to a disk on your MEGA65 by using the "mega65_ftp" command;
6. run it on the real c64 hardware.

## Features

The provided features are:

- Syntax highlighting
- Snippets for the all commands and control characters
- File icons
- Theme
- Rulers: 40th and 80th column
- Keyboard Shortcuts

### Syntax highlighting
An example of syntax highlighting is:

![mega65basic highlighting](https://github.com/clockchip/mega65basic/blob/main/images/mega65basic_syntaxhigh.png)

### Snippets

Snippets suggest to you the syntax of the commands:

![REM Snippets](https://github.com/clockchip/mega65basic/blob/main/images/snippets1.gif)

![Command Snippets](https://github.com/clockchip/mega65basic/blob/main/images/snippets2.gif)

### Snippets for Control characters
Special characters in MEGA65 BASIC are referred to as control characters, such as:

![Clears screen](https://github.com/clockchip/mega65basic/blob/main/images/01.png)
![Place cursor in top left corner](https://github.com/clockchip/mega65basic/blob/main/images/02.png)
![Cursor one step right](https://github.com/clockchip/mega65basic/blob/main/images/03.png)
![Cursor one step to the left](https://github.com/clockchip/mega65basic/blob/main/images/04.png)
![Cursor one position down](https://github.com/clockchip/mega65basic/blob/main/images/05.png)
![Cursor one position up](https://github.com/clockchip/mega65basic/blob/main/images/06.png)

Books and old magazines use a specific syntax to represent special characters, which involves enclosing the name of the control character in curly braces. For instance, the control character that clears the screen is represented as {clr}.

When you include such a control character in a print statement (for example, print "{clr}"), it causes the MEGA65 to clear the screen.

A comprehensive list of control characters can be found on this page: [Control character](https://www.c64-wiki.com/wiki/control_character).

Snippets of code for transforming the control character strings (e.g., {clr}) into the corresponding command (chr$(xxx)) are available. For example, {clr} can be transformed into chr$(147).

But pay attention: Inside print statement you have to remove the double apex, print "{clr}" become print {clr} and then print chr$(147).

However, it's important to note that within a print statement, the double quotes must be removed so that "{clr}" becomes {clr}, and then print chr$(147).

![c64basicv2 Control Character Snippet](https://raw.githubusercontent.com/gverduci/c64basicv2/main/images/c64basicv2_ctrlcharsnippets.gif)

An alternative option is to use petcat to directly write the following Control characters without needing to convert them to chr$.

{clear}             {home}              {right}         {left}              {up}                {down}
{reverse on}        {reverse off}       {black}         {white}             {red}               {cyan}
{purple}            {green}             {blue}          {yellow}            {orange}            {brown}
{pink}              {dark gray}         {gray}          {light green}       {light blue}        {light gray}
{f1}                {f2}                {f3}            {f4}                {f5}                {f6}
{f7}                {f8}                {space}         {pi}

[petcat src](https://github.com/svn2github/vice-emu/blob/524c58c4c2159dbe82520d36b7dde6a082eeddf7/vice/src/petcat.c#L683)

## Release Notes

[CHANGELOG.md](./CHANGELOG.md)
