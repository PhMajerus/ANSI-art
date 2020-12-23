# ANSI-art
Random ANSI-art files

![Screenshot](Sample%20AnsiArt.png)

.txt files are UTF-8. These can be displayed simply using curl with their raw URL. For example:
`curl -s 'https://raw.githubusercontent.com/PhMajerus/ANSI-art/master/Lxss-VTArt-Red.txt'`

.ans and .asc files are CP437 (MS-DOS US) files, sometimes containing a SUB as an end-of-file. These can be displayed using curl piped to iconv to convert CP437 to UTF-8 and then to sed to trim anything from SUB. For example:
`curl -s 'https://raw.githubusercontent.com/PhMajerus/ANSI-art/master/Super%20Mario%20castle%20(wide)%20(256%20colors).ans' | iconv -f CP437 | sed 'H;$!d;x;s/\x1A.*$//'`

In cmd.exe, simply use the "type" command with local copies of the files, using "chcp 437" first for CP437 .ans and .asc files and "chcp 65001" for UTF-8 .txt files.

In ActiveScript Shell, use the following functions:\
JScript\
`function getAnsi(url) { var xhr = new XMLHttpRequest(); xhr.open("GET",url,false); xhr.send(); return binaryToString(xhr.responseBody,"CP437").trimSUB(); }`\
`echo(getAnsi("https://raw.githubusercontent.com/PhMajerus/ANSI-art/master/Super%20Mario%20castle%20(wide)%20(256%20colors).ans"));`\
VBScript\
`Function GetAnsi(URL): Dim XHR: Set XHR=CreateObject("MSXML2.XMLHTTP.6.0"): XHR.Open "GET",URL,False: XHR.Send: GetAnsi=TrimSUB(BinaryToString(XHR.ResponseBody,"CP437")): End Function`\
`Echo GetAnsi("https://raw.githubusercontent.com/PhMajerus/ANSI-art/master/Super%20Mario%20castle%20(wide)%20(256%20colors).ans")`
