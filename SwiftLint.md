<h2>SwiftLint</h2>

前面一篇文章已经介绍了OCLint的安装和使用教程。

<h3>SwiftLint安装</h3>

1、使用Homebrew安装

 brew install swiftlint

2、然后在Project->Targets->Add Run Script
 
3、加入脚本就Ok了。

![screenshot.png][1]

<h3>推荐插件安装</h3>

一款SwiftLintXcode插件，从恶魔岛安装。提供autocorrect功能。

<h3>自定义SwiftLint规则</h3>

规则很多是一些社区总结的，还在完善中。

查看可以定制的规则 swiftlint rules

Colon (colon): Colons should be next to the identifier when specifying a type. 
Comma Spacing (comma): One space before and no after must be present next to any comma. 
Control Statement (control_statement): if,for,while,do statements shouldn't wrap their conditionals in parentheses. 
Force Cast (force_cast): Force casts should be avoided. 
...

**当需要自定义规则时，首先需要在项目的根目录下创建一个.swiftlint.yml**

disabled_rules: Disable rules from the default enabled set.
opt_in_rules: Some rules are opt-in.
whitelist_rules: Can not be specified alongside disabled_rules or opt_in_rules. Acts as a whitelist, only the rules specified in this list will be enabled.

加入disabled_rules:

disabled_rules:
	- todo
	- force_cast

type_body_length:
	-100
	-200

这个意思就是body里的代码行数超过100时会出现warning，当超过200行时，会报error。

  [1]: http://www.hetianxiong.com/usr/uploads/2016/07/3991851365.png