# ANSI-art
Random ANSI-art files

![Screenshot](Sample%20AnsiArt.png)

.txt files are UTF-8. These can be displayed simply using curl with their raw URL. For example:
`curl 'https://raw.githubusercontent.com/PhMajerus/ANSI-art/master/Lxss-VTArt-Red.txt'`

.ans and .asc files are CP437 (MS-DOS US) files, sometimes containing a SUB as an end-of-file. These can be displayed using curl piped to sed to trim anything from SUB, and then to iconv to convert CP437 to UTF-8. For example:
`curl 'https://raw.githubusercontent.com/PhMajerus/ANSI-art/master/Super%20Mario%20castle%20(wide).ans' | sed 'H;$!d;x;s/\x1A.*$//' | iconv -f CP437`

In cmd.exe, simply use the "type" command with local copies of the files, using "chcp 437" first for CP437 .ans and .asc files and "chcp 65001" for UTF-8 .txt files.
