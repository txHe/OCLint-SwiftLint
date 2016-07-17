<h2>OCLint</h2>
<h3>1、OCLint简介：</h3>
OCLint is a static code analysis tool for improving quality and reducing defects by inspecting C, C++ and Objective-C code and looking for potential problems like:

Possible bugs - empty if/else/try/catch/finally statements
Unused code - unused local variables and parameters
Complicated code - high cyclomatic complexity, NPath complexity and high NCSS
Redundant code - redundant if statement and useless parentheses
Code smells - long method and long parameter list
Bad practices - inverted logic and parameter reassignment
...

简单解释下，就是OCLint是一个静态的代码分析工具，目的是用于提升代码的质量和减少代码可能存在的缺陷。主要是用于C、C++和Objective-c语言，同时解决一些潜在的问题：
(1)可能的bug - 空的if/else/try/catch/finally状态表达式
(2)未使用的代码 - 指的是定义了得变量或参数，却未曾使用
(3)复杂度较高的代码 - 高圈复杂度的代码
(4)复杂的代码 - if语句条件太多，同时很多无用的括号
(5)不好的代码表达 - 方法定义的太长，同时参数列表过长
(6)错误的代码实践 - 反转逻辑等

**圈复杂度注解：**
圈复杂度（一种代码复杂度衡量标准），用于衡量一个模块判定结构的复杂程度，数量上表现为独立线性条数，也可理解为覆盖所有可能情况最少使用的测试用例数。

<h3>2、OCLint特性：</h3>
Static code analysis is a critical technique to detect defects that aren't visible to compilers. OCLint automates this inspection process with advanced features:

Relying on the abstract syntax tree of the source code for better accuracy and efficiency; False positives are mostly reduced to avoid useful results sinking in them.

Dynamically loading rules into system, even in the runtime.

Flexible and extensible configurations ensure users in customizing the behaviors of the tool.
Command line invocation facilitates continuous integration and continuous inspection of the code while being developed, so that technical debts can be fixed early on to reduce the maintenance cost.

静态的代码分析是一项严格的技术用于检测那些对编译器不可见的代码缺陷，OCLint自动的检测，有以下的特性：
(1)依赖于源码的抽象句法树来提升准确性和效率。
(2)动态的加载规则到系统内，即使是在runtime运行时阶段
(3)灵活而且可扩展的设置，确保用户自我定制一些行为，集成了命令行等等

<h3>3、OCLint安装：</h3>
官网的方法，需要自行下载release版本文件并添加路径

1、直接加入路径。通过创建.bashrc或.bash_profile文件，加入路径在实现。

2、拷贝OCLint 到系统路径

每次运行后，生成报告，html文件，查看不符合rules的代码的信息汇总。为了能在xcode中直接显示出来，可以尝试以下方法。

<h3>个人推荐,比较方便，目前只在我的电脑上实验成功：</h3>

1、使用Homebrew安装

设置brew的第三方库: brew tap oclint/formulate
然后安装OCLint: brew install oclint

2、添加脚本文件

在target -> build phrase -> add Run Script

<h3>4、OCLint 详细添加教程:</h3>
在已有的项目中添加OCLint

![xcode_screenshot_1.png][1]

![xcode_screenshot_2.png][2]

![xcode_screenshot_3.png][3]

<h3>在script中加入脚本,脚本很难找！，找了好久，试了好久，改了不少，终于找到一份，我创了个链接：</h3>

[脚本链接][4]

![xcode_screenshot_6.png][5]

![xcode_screenshot_8.png][6]

<h3>5、OCLint规则：</h3>

官方地址：http://docs.oclint.org/en/stable/rules/index.html

某些文件不需要做静态代码分析的，比如一些第三方库，可以这样设置，以忽略它的文件夹。

-e pods

自定义规则的实现

主要是通过设置一些阈值(Thresholds)来达到自定义某些规则的目的。

可以通过命令行来设置，添加在脚本的参数中。

**Available Thresholds(阈值)**

![图片1.png][7]

<h3>6、禁用规则和使用规则</h3>

<h4>禁用一些规则</h4>

-disable-rule=InvertedLogic \
 -disable-rule=CollapsibleIfStatements \ 
-disable-rule=UnusedMethodParameter \ 
-disable-rule=LongLine \
…

<h4>更改阈值</h4>

##--命名
##变量名字最长字节
##-rc=LONG_VARIABLE_NAME=20 \ 
##--size 圈复杂度
##-re=CYCLOMATIC_COMPLEXITY=10 \
##每个类最多行数 
##-rc=LONG_CLASS=700 \ 
##每个方法行数
##-rc=LONG_METHOD=80 \
##嵌套深度 
##-rc=NESTED_BLOCK_DEPTH=5 \
…


  [1]: http://www.hetianxiong.com/usr/uploads/2016/07/2309300051.png
  [2]: http://www.hetianxiong.com/usr/uploads/2016/07/4005666696.png
  [3]: http://www.hetianxiong.com/usr/uploads/2016/07/2746610061.png
  [4]: http://pan.baidu.com/s/1gfPnvDx
  [5]: http://www.hetianxiong.com/usr/uploads/2016/07/3334172824.png
  [6]: http://www.hetianxiong.com/usr/uploads/2016/07/3758901080.png
  [7]: http://www.hetianxiong.com/usr/uploads/2016/07/3503392709.png