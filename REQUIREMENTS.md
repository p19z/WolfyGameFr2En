# Requirements on Windows for MD2PDF

## Ideal installation

The ideal installation steps for building the PDF files:

+ `choco install -y pandoc` // << INSTALLS AS ROOT
+ `choco install -y rsvg-convert`
+ `choco install -y miktex` // << FAILED, APR 16, 2020
+ `choco install -y pdflatex`

But, as you may see on the comments, we have two problems; as of APR 16, 2020:

+ "Pandoc" is installed as Root, in C:\Users\Root\AppData\Local and is not accessible by default to a standard user.
+ The automated install of MiKTeX does not work via Chocolatey. See further below for a WORKAROUND.


## Workaround 1

We need a command like this:

+ `$> CACLS files /e /p {USERNAME}:{PERMISSION}`

So in this case:

+ `$> cd C:\Users\Administrator\AppData\Local\Pandoc`
+ `$> CACLS * /e /p MyStandardUserName:R`

Source:

+ "Windows change access permissions from the command line - nixCraft"<br/>
("https://www.cyberciti.biz/tips/windows-change-access-permissions-from-the-command-line.html")


## Workaround 2

In 3 steps:


+ Browse to [http://mirrors.ircam.fr/pub/CTAN/systems/win32/miktex/setup/windows-x64/](http://mirrors.ircam.fr/pub/CTAN/systems/win32/miktex/setup/windows-x64/)
+ download **"basic-miktex-2.9.7386-x64.exe"** (or the latest version available)
+ and run this executable as an Administrator (it will install in **"C:\Progra~1\MiKTeX 2.9"**)
