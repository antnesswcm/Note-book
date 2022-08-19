# Change default shell on MSYS2

在windows上使用MSYS2时，想把默认的bash换掉

查看安装的shell`/etc/shells`
```
➜  ~ cat /etc/shells
#
# /etc/shells
#

/usr/bin/zsh	//有zsh
/bin/zsh
...

# End of file
```
忘了什么时候安装了zsh，可是默认shell并不是zsh

由于msys2没有`/etc/passwd`文件，只能通过其他途径修改了

在msys2安装目录`D:\msys64`下`/etc/nsswitch.conf`文件中添加这行代码：

```
db_shell: /bin/zsh
```

现在通过 **msys.exe启动**就是默认zsh		//这句划重点

启动后，如果你的msys的shell依然没有改变，那么你大概不是直接打开的msys.exe,而是通过msys提供的快捷方式！

这个msys提供的默认快捷方式是通过安装目录下的`msys2_shell.cmd`来启动msys的，在`sys2_shell.cmd`中有这样一句：

```
4 | ...
5 |	set "LOGINSHELL=bash" //将bash替换为zsh即可改变快捷方式启动后的shell
6 | ...
```

将其中的bash替换为zsh即可改变通过快捷方式启动后的shell

## END thinks~



> 参考链接：
>
> [**Stack Exchange**](https://superuser.com/questions/961699/change-default-shell-on-msys2)