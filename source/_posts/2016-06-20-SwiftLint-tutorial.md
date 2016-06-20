---
layout: post
title: SwiftLint tutorial
date: 2016-06-20 15:31:34
categories: ios
tags: [xcode,swift]
---

# SwiftLint 是什么

A tool to enforce Swift style and conventions, loosely based on [ GitHub's Swift Style Guide ](https://github.com/github/swift-style-guide).


## 安装

[GitHub 地址](https://github.com/realm/SwiftLint)

```
brew install swiftlint
```

<!--more-->
## Xcode

### SwiftLintXcode

插件自动在保存文件时运行 `swiftlint`
[SwiftLintXcode](https://github.com/ypresto/SwiftLintXcode)

### Run Script Phase

```
if which swiftlint >/dev/null; then
swiftlint
else
echo "warning: SwiftLint not installed, install use `brew install swiftlint`
fi
```

<div style="width: 70%;">
![](https://github.com/realm/SwiftLint/raw/master/assets/runscript.png)
</div>


## git hook

`git commit` 时自动格式化加入stage的代码

- 将下面代码写入git仓库根目录 `pre-commit.sh` 文件

```
#!/bin/bash

# 这是一个pre-commit 的脚本

# Run SwiftLint
START_DATE=$(date +" %s")

echo $START_DATE

SWIFT_LINT=/usr/local/bin/swiftlint

# Run SwiftLint for given filename
run_swiftlint() {
local filename="${1}"
if [[ "${filename##*.}" == "swift" ]]; then
# echo ${filename}
${SWIFT_LINT} autocorrect --path "${filename}"
git add -- "${filename}"

# check lint
# ${SWIFT_LINT} lint --path "${filename}"
fi
}

if [[ -e "${SWIFT_LINT}" ]]; then
echo "SwiftLint version: $(${SWIFT_LINT} version)"
# Run for unstaged
# git diff --name-only | while read filename; do run_swiftlint "${filename}"; done

# Run for staged
git diff --cached --name-only | while read filename; do run_swiftlint "${filename}"; done
else
echo "${SWIFT_LINT} is not installed."
echo "Plz install swiftlint use brew"
echo "brew install swiftlint"
exit 0
fi

END_DATE=$(date +"%s")

DIFF=$(($END_DATE - $START_DATE))
echo "SwiftLint took $(($DIFF / 60)) minutes and $(($DIFF % 60)) seconds to complete."
```

- 生成link

```
ln -s pre-commit.sh .git/hooks/pre-commit
```

- 修改权限
-
```
chmod ug+x .git/hooks/pre-commit
```


## 修改规则

- `swiftlint rules` 查看所有规则
- `swiftlint rules rule_name` 查看规则详情

在git仓库根目录新建文件 `.swiftlint.yml` 作用于整个项目

* disabled_rules: Disable rules from the default enabled set.
* opt_in_rules: Some rules are opt-in.
* whitelist_rules: Can not be specified alongside disabled_rules or opt_in_rules. Acts as a whitelist, only the rules specified in this list will be enabled.

官方sample
```
disabled_rules: # rule identifiers to exclude from running
  - colon
  - comma
  - control_statement
opt_in_rules: # some rules are only opt-in
  - empty_count
  - missing_docs
  # Find all the available rules by running:
  # swiftlint rules
included: # paths to include during linting. `--path` is ignored if present.
  - Source
excluded: # paths to ignore during linting. Takes precedence over `included`.
  - Carthage
  - Pods
  - Source/ExcludedFolder
  - Source/ExcludedFile.swift

# configurable rules can be customized from this configuration file
# binary rules can set their severity level
force_cast: warning # implicitly
force_try:
  severity: warning # explicitly
# rules that have both warning and error levels, can set just the warning level
# implicitly
line_length: 110
# they can set both implicitly with an array
type_body_length:
  - 300 # warning
  - 400 # error
# or they can set both explicitly
file_length:
  warning: 500
  error: 1200
# naming rules can set warnings/errors for min_length and max_length
# additionally they can set excluded names
type_name:
  min_length: 4 # only warning
  max_length: # warning and error
    warning: 40
    error: 50
  excluded: iPhone # excluded via string
variable_name:
  min_length: # only min_length
    error: 4 # only error
  excluded: # excluded via string array
    - id
    - URL
    - GlobalAPIKey
reporter: "xcode" # reporter type (xcode, json, csv, checkstyle)
```


