# ripgrep (rg) — 极速文件内容搜索

Fork from [BurntSushi/ripgrep](https://github.com/BurntSushi/ripgrep) · 许可证: Unlicense · 65,000+ GitHub Stars

## 是什么

在文件里搜关键字，比 grep 快 10-100 倍。Rust 编写，SIMD 加速，多线程并行。

## 安装

```bash
# Ubuntu/Debian
sudo apt install ripgrep

# CentOS/RHEL
sudo dnf install ripgrep

# macOS
brew install ripgrep

# 其他 Linux
cargo install ripgrep
```

## 日常用法

```bash
# 搜当前目录所有文件
rg "关键词"

# 搜指定目录
rg "关键词" /var/log/

# 只搜 .log 文件
rg "关键词" --type log

# 只搜文件名（不搜内容）
rg --files | grep "关键词"

# 忽略大小写
rg -i "关键词"

# 显示行号+文件名
rg -n "关键词"

# 只看匹配的文件名（不显示内容）
rg -l "关键词"

# 排除目录
rg "关键词" --glob '!node_modules'

# 搜压缩文件（需要安装 ripgrep-all: rga）
rga "关键词"
```

## 常见场景

| 需求 | 命令 |
|------|------|
| 找哪个配置文件写了数据库密码 | `rg "password" /etc/` |
| 搜日志里的错误 | `rg "ERROR" /var/log/` |
| 找所有 TODO 注释 | `rg "TODO" --type-add 'code:*.{py,js,java,go}' -t code` |
| 统计匹配次数 | `rg -c "关键词"` |
| 替换文本 | `rg "old" -l \| xargs sed -i 's/old/new/g'` |

## 为什么比 grep 快

- 自动跳过 `.gitignore` 里的文件
- 不搜二进制文件（除非指定）
- SIMD 加速字符串匹配（CPU 指令级优化）
- 多线程并行搜文件
- 默认不搜隐藏文件

## 许可证

Unlicense — 完全自由使用，无任何限制。公司环境放心用。
