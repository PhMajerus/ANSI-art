# ANSI-art
Random ANSI-art files

![Screenshot](Sample%20AnsiArt.png)

.txt files are UTF-8. These can be displayed simply using curl with their raw URL. For example:

```bash
curl -s 'https://raw.githubusercontent.com/PhMajerus/ANSI-art/master/Lxss-VTArt-Red.txt'
```

.ans and .asc files are CP437 (MS-DOS US) files, sometimes containing a SUB as an end-of-file. These can be displayed using curl piped to iconv to convert CP437 to UTF-8 and then to sed to trim anything from SUB. For example:

```bash
curl -s 'https://raw.githubusercontent.com/PhMajerus/ANSI-art/master/Super%20Mario%20castle%20(wide)%20(256%20colors).ans' | iconv -f CP437 | sed 'H;$!d;x;s/\x1A.*$//'
```

In cmd.exe, simply use the "type" command with local copies of the files, using "chcp 437" first for CP437 .ans and .asc files and "chcp 65001" for UTF-8 .txt files.

In ActiveScript Shell, use the following functions:

JavaScript:

```JavaScript
function getAnsi(url) { var xhr = new XMLHttpRequest(); xhr.open("GET",url,false); xhr.send(); return Encodings.binaryToText(xhr.responseBody,437).trimSUB(); }
```

```JavaScript
echo(getAnsi("https://raw.githubusercontent.com/PhMajerus/ANSI-art/master/Super%20Mario%20castle%20(wide)%20(256%20colors).ans"));
```
VBScript:

```VBScript
Function GetAnsi(URL): Dim XHR: Set XHR=CreateObject("MSXML2.XMLHTTP.6.0"): XHR.Open "GET",URL,False: XHR.Send: GetAnsi=TrimSUB(Encodings.BinaryToText(XHR.ResponseBody,437)): End Function
```

```VBScript
Echo GetAnsi("https://raw.githubusercontent.com/PhMajerus/ANSI-art/master/Super%20Mario%20castle%20(wide)%20(256%20colors).ans")
```

____

## For Windows Users:

### tl;dr | In PowerShell on Windows:

```PowerShell
Invoke-WebRequest -URI 'https://raw.githubusercontent.com/PhMajerus/ANSI-art/main/Unicode/Sonic%20(8-bit)%20(Octants).txt' | Select-Object -Expand Content
```

### Detailed Version:

If:

```bash
cat "Sonic (8-bit) (Octants).txt
```

Renders as:

```bash
Â Â ðœ´†ðœ´£â–—ðœ´£â–†ðœµ™Â Â 
Â ðœ·‹ðœ·¥â–›ðœ´‚â–—ðœ·žðœ´·ðœµˆÂ 
ðœº«ðŸ®‚ðœ·šâ–™ðœº â–„â–‚ðœ·‹ðœ·¤Â 
Â ðœ´±ðŸ®…ðŸ®…ðœº«ðœ´¦ðŸ®…ðœ´—ðœº¨Â 
Â Â ðœ·¡ðœ´‚ðœ·¡ðœº¨ðœº«ðœ¶»Â Â 
Â Â ðŸ®‚ðœ¶ªðœµ®ðœ´…ðœ´‚â–‚ðœ´Â 
Â Â Â ðœ·‹â–‚â–Ÿðœ·€Â Â Â 
Â Â â–ðœ¶­ðœ¶®ðœ¶­ðœ¶¶ðœ·šâ–†â––
```

and

```bash
curl -s 'https://github.com/PhMajerus/ANSI-art/blob/main/Unicode/Sonic%20(8-bit)%20(Octants).txt'
```

Gives:

```bash
cmdlet Invoke-WebRequest at command pipeline position 1
Supply values for the following parameters:
Uri: https://github.com/PhMajerus/ANSI-art/blob/main/Unicode/Sonic%20(8-bit)%20(Octants).txt
curl : Cannot find drive. A drive with the name 'https' does not exist.
At line:1 char:1
+ curl -s 'https://github.com/PhMajerus/ANSI-art/blob/main/Unicode/Soni ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (https:String) [Invoke-WebRequest], DriveNotFoundException
    + FullyQualifiedErrorId : DriveNotFound,Microsoft.PowerShell.Commands.InvokeWebRequestCommand
```

Then from the following sources:

- [Laravel Sail Curl command is asking for uri](https://laracasts.com/discuss/channels/laravel/laravel-sail-curl-command-is-asking-for-uri)

- [curl in PowerShell](https://www.educative.io/answers/curl-in-powershell)

- [Display all content with Invoke-WebRequest](https://stackoverflow.com/questions/40702328/display-all-content-with-invoke-webrequest)

Do this:

```PowerShell
Invoke-WebRequest -URI 'https://raw.githubusercontent.com/PhMajerus/ANSI-art/main/Unicode/Sonic%20(8-bit)%20(Octants).txt' | Select-Object -Expand Content
```
