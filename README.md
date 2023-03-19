![mega65basic logo](/images/mega65basic_logo.png)

# MEGA65 BASIC Language VSCode Extension

Welcome to my GitHub project! In this repository, you will find a Visual Studio Code language extension for the BASIC of the MEGA65 Personal Computer System. I must admit, this computer has a lot of charm, and the team that developed it has done a fantastic job. 

For many developers, it may be sacrilege not to program directly on the hardware, despite the perfect keyboard that the MEGA65 offers. However, there are many developers who are used to modern development environments and want to take advantage of Visual Studio Code's benefits. That's why I decided to write this extension, to enable comfortable development of BASIC programs and, at the same time, to utilize the many features of Visual Studio Code for managing source code.

I see this as another contribution to helping the MEGA65 get additional software, as development environments make software writing easier. I hope this extension will be useful for those of you who use the MEGA65 and want to develop your BASIC programs in Visual Studio Code.

## Project Description

This extension helps with the creation of programs in "Basic 65 V920377" (.prg or .bas extension) for the "MEGA65 Personal Computer System" within [Visual Studio Code](https://code.visualstudio.com/). It offers a range of useful features, including syntax highlighting, code snippets, file icons, theme options, and rulers.

This extension is developed using the code and tools available in the following GitHub repositories:
- [Yo Code - Extension and Customization Generator](https://github.com/microsoft/vscode-generator-code)
- [c64basicv2 Visual Studio Code Extension](https://github.com/gverduci/c64basicv2)

Rules for snippets come from the following pages of C64-Wiki & Mega65 Filehost:
- [MEGA65 BASIC 65 Reference](https://files.mega65.org/files/m/mega65-basic65-reference_PeK0ek.pdf) 
- [Control character](https://www.c64-wiki.com/wiki/control_character) 

## Things you need

To transfer and execute the code written using this extension to your MEGA65, you will require the following tools:
- [petcat tool from VICE Emulator](https://vice-emu.sourceforge.io/)
- [Xemu](https://github.lgb.hu/xemu/)
- [M65Connect](https://github.com/MEGA65/m65connect)

For using the petcat tool from the VICE emulator to tokenize your BASIC program written in VSCode, it is important to use a version that includes the latest support for Mega65 Basic commands. This will ensure that your programs are fully compatible with your Mega65 system.

To use the latest version of petcat with Mega65 Basic command support, simply [download](https://github.com/VICE-Team/svn-mirror/blob/main/vice/src/tools/petcat/petcat.c) and compile the most recent version of the tool. The following picture displays the code lines of the petcat.c file, highlighting the added support for Mega65 Basic commands.

![petcat.c code](/images/petcat.png)

## Usage

You might follow this process to develop your program:

1. Before you start coding select one of the provided themes to ensure proper syntax highlighting.

![select theme](/images/themeselect.png)

2. Create a folder structure like this:

        \    -> root dir
        \bin -> converted programs
        \src -> source programs
3. Write the program in VSCode and save it under the \src folder.
   

4. Tokenize and convert the source *.bas file into a *.prg file, by using the following command in the Terminal window of Visual Studio Code:
        
        petcat -w65 -o ./bin/outputfile.prg -- ./src/inputfile.bas

5. Test the program with [Xemu](https://github.lgb.hu/xemu/) using the "Run PRG directly" command.

![use Xemu](/images/petcat.gif)

6. Connect your MEGA65 using a [JTAG](https://dansanderson.com/mega65/welcome/using-jtag.html) connector to the computer which is running the M65Connect.

7. Transfer the output.prg file to the MEGA65 using M65Connect.

8. Enjoy running your programm on the real MEGA65 hardware.

## Project Features

The provided features are:

- Syntax highlighting
- Snippets for all commands and control characters
- File icons
- Themes
- Rulers: 40th and 80th column

### Syntax highlighting
An example of syntax highlighting is:

![mega65basic highlighting](/images/mega65basic_syntaxhigh.png)

### Snippets

Snippets suggest to you the syntax of the commands:

![REM Snippets](/images/snippets1.gif)

### Using Syntax Suggestions and Optional Parameters

When entering a BASIC command, you encounter syntax suggestions displayed on the screen. To ignore these suggestions enter the command and press the SPACE bar.

![Usage1](/images/circle1.gif)

To select different parameters of a command, press the TAB key. This will allow you to cycle through and select the desired parameter for your command.

![Usage2](/images/circle2.gif)

Some BASIC commands may have optional parameters.

![Command](/images/circle.png)

f you do not want to use these optional parameters, simply delete them using the BACKSPACE key.

![Usage3](/images/circle3.gif)

If you do want to use the optional parameters of a command, press TAB twice. This will allow you to enter and specify the desired parameter for your command.

![Usage4](/images/circle4.gif)

### Snippets for Control characters
Special characters in MEGA65 BASIC are referred to as control characters, such as:

![Clears screen](/images/01.png)
![Place cursor in top left corner](/images/02.png)
![Cursor one step right](/images/03.png)
![Cursor one step to the left](/images/04.png)
![Cursor one position down](/images/05.png)
![Cursor one position up](/images/06.png)

Books and old magazines use a specific syntax to represent special characters, which involves enclosing the name of the control character in curly braces. For instance, the control character that clears the screen is represented as {clr}.

When you include such a control character in a print statement (for example, print "{clr}"), it causes the MEGA65 to clear the screen.

A comprehensive list of control characters can be found on this page: [Control character](https://www.c64-wiki.com/wiki/control_character).

Snippets of code for transforming the control character strings (e.g., {clr}) into the corresponding command (chr$(xxx)) are available. For example, {clr} can be transformed into chr$(147).

But pay attention: Inside print statement you have to remove the double apex, print "{clr}" become print {clr} and then print chr$(147).

However, it's important to note that within a print statement, the double quotes must be removed so that "{clr}" becomes {clr}, and then print chr$(147).

![c64basicv2 Control Character Snippet](/images/control_chr.gif)

An alternative option is to use petcat to directly write the following Control characters without needing to convert them to chr$.

{clear}             {home}              {right}         {left}              {up}                {down}
{reverse on}        {reverse off}       {black}         {white}             {red}               {cyan}
{purple}            {green}             {blue}          {yellow}            {orange}            {brown}
{pink}              {dark gray}         {gray}          {light green}       {light blue}        {light gray}
{f1}                {f2}                {f3}            {f4}                {f5}                {f6}
{f7}                {f8}                {space}         {pi}


## Release Notes

[CHANGELOG.md](./CHANGELOG.md)
