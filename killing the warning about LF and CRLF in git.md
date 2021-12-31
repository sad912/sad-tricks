# 干掉 Git 中关于 LF 和 CRLF 的警告

在重装 win11 之后，Git 在使用的过程中又在报之前我一直忽略的警告了，如下。

```
$ warning: LF will be replaced by CRLF in README.md
$ The file will have its original line endings in your working directory
```

是时候干掉这可恶的 warning 了！

## [Git 相关文档](https://git-scm.com/book/en/v2/Customizing-Git-Git-Configuration)

### Formatting and Whitespace
Formatting and whitespace issues are some of the more frustrating and subtle problems that many developers encounter when collaborating, especially cross-platform. It’s very easy for patches or other collaborated work to introduce subtle whitespace changes because editors silently introduce them, and if your files ever touch a Windows system, their line endings might be replaced. Git has a few configuration options to help with these issues.

**core.autocrlf**

If you’re programming on Windows and working with people who are not (or vice-versa), you’ll probably run into line-ending issues at some point. This is because Windows uses both a carriage-return character and a linefeed character for newlines in its files, whereas macOS and Linux systems use only the linefeed character. **This is a subtle but incredibly annoying fact of cross-platform work**; many editors on Windows silently replace existing LF-style line endings with CRLF, or insert both line-ending characters when the user hits the enter key.

Git can handle this by auto-converting CRLF line endings into LF when you add a file to the index, and vice versa when it checks out code onto your filesystem. You can turn on this functionality with the core.autocrlf setting. If you’re on a Windows machine, set it to true — this converts LF endings into CRLF when you check out code:

```
$ git config --global core.autocrlf true
```
If you’re on a Linux or macOS system that uses LF line endings, then you don’t want Git to automatically convert them when you check out files; however, if a file with CRLF endings accidentally gets introduced, then you may want Git to fix it. You can tell Git to convert CRLF to LF on commit but not the other way around by setting core.autocrlf to input:
```
$ git config --global core.autocrlf input
```

This setup should leave you with CRLF endings in Windows checkouts, but LF endings on macOS and Linux systems and in the repository.

If you’re a Windows programmer doing a Windows-only project, then you can turn off this functionality, recording the carriage returns in the repository by setting the config value to false:
```
$ git config --global core.autocrlf false
```

看完文档感觉都没有什么可总结的了，官网文档已经把 tricks 总结好了。
我再自己查阅总结一下吧。
## LF 和 CRLF 是什么？
LF（Line Feed）是 ASICII 码中的第 10 位控制字符，表示换行；CR 是 ASICII 码中的第 13 位控制字符，表示回车。

顾名思义，LF 意味 换行，而 CRLF 则为回车换行。

> 现代 Windows 计算机一直使用 CRLF 作为行尾。同时，从一开始，Unix 就使用 LF 来表示行尾，为了一致性和简单性而放弃了 CRLF。 Apple 最初仅在 Mac Classic 上使用 CR，但最终在 OS X 上改用了 LF，与 Unix 一致。 ——[知乎用户 不知味之味](https://zhuanlan.zhihu.com/p/380574688)

## 解决令人讨厌的换行！

由于上述历史问题，在协同开发时会出现由系统的差异导致文件行尾的不同的问题。

>This is a subtle but incredibly annoying fact of cross-platform work

为解决这个问题 Git 也有关于此问题的相关配置选项，那就是 `core.autocrlf`。

tricks 如下:

1. 如果你使用以 LF 作为结尾符号的 Linux 或 MacOS 系统，你可以设置 `core.autocrlf = input` 使得 Git 不会转换 LF 且转换 CRLF 为 LF。

```
$ git config --global core.autocrlf input
```
2. 如果你使用以 CRLF 作为结尾符号的 Windows 系统，你可以设置 `core.autocrlf = true` 使得 Git 自动转化 LF 为 CRLF。

```
$ git config --global core.autocrlf true
```
3. 而如果你所有项目只会在 Windows 系统环境中进行开发，则可以设置 `core.autocrlf = false` 使得 Git 保持以 CRLF 进行结尾。
```
$ git config --global core.autocrlf false
```

使用第三种方法就可以干掉令人讨厌的 Warning 了，但还是不推荐这样做，除非你能保证该项目只会在 Windows 系统上进行开发。



