
目录
====

```ruby
致第三版
前言
	为什么选择Ruby?
	Ruby版本
	本书的改进
	资源
	知识图
	提示约定
路线图
I.  Ruby的方方面面
	1.  入门
		1.1 命令行提示符
		1.2 安装Ruby
		1.3 运行Ruby
		1.4 Ruby文档：RDoc和ri
	2.  Ruby.new
		2.1 Ruby是一门面向对象语言
		2.2 Ruby基础知识
		2.3 数组和哈希
		2.4 符号
		2.5 控制结构
		2.6 正则表达式
		2.7 Blocks和迭代器
		2.8 读文件和写文件
		2.9 命令行参数
		2.10 更多内容
 3.  类，对象和变量
 		3.1 对象和属性
 		3.2 类与类之间协作
 		3.3 控制权限
 		3.4 变量
 	4.  容器、Blocks和迭代器
    4.1 数组
    4.2 哈希
    4.3 Block块和迭代器
    4.4 容器
  5.  分享方法：继承，模块和Mixin
  	5.1 继承和消息
  	5.2 模块
  	5.3 Mixin
  	5.4 迭代器和枚举类型
  	5.5 组合模块
  	5.6 继承和Mixin的选择 
  6.   标准类型
    6.1 数字
    6.2 字符串
    6.3 范围
  7.  正则表达式
    7.1 正则表达的用途
    7.2 Ruby的正则表达式
    7.3 深入正则表达式
    7.4 高级正则表达式
 	8. 方法的细节
		8.1  方法定义
		8.2  方法调用
	9.  表达式
	  9.1 运算表达式
	  9.2 多形式的表达式
	  9.3 赋值
	  9.4 条件表达式
	  9.4 case表达式
	  9.5 循环
	  9.6 变量作用域，循环以及Block
  10. 异常，捕获和抛出
    10.1 异常类
    10.2 处理异常
    10.3 引发异常
    10.4  捕获和抛出 
  11.	Basic Input and Output
 	 	11.1	What Is an IO Object?
 	 	11.2	Opening and Closing Files
 	 	11.3	Reading and Writing Files
 	 	11.4	Talking to Networks
 	 	11.5	Parsing HTML
 	12.	Fibers, Threads, and Processes
 	 	12.1	Fibers
 	 	12.2	Multithreading
 	 	12.3	Controlling the Thread Scheduler
 	 	12.4	Mutual Exclusion
 	 	12.5	Running Multiple Processes
 	13.	Unit Testing
 	 	13.1	The Testing Framework
 	 	13.2	Structuring Tests
 	 	13.3	Organizing and Running Tests
 	 	13.4	RSpec and Shoulda
 	 	13.5	Test::Unit assertions
 	14.	When Trouble Strikes!
 	 	14.1	Ruby Debugger
 	 	14.2	Interactive Ruby
 	 	14.3	Editor Support
 	 	14.4	But It Doesn’t Work!
 	 	14.5	But It’s Too Slow!
II. Ruby in Its Setting
 	15.	Ruby and Its World
 	 	15.1	Command-Line Arguments
 	 	15.2	Program Termination
 	 	15.3	Environment Variables
 	 	15.4	Where Ruby Finds Its Libraries
 	 	15.5	RubyGems Integration
 	 	15.6	The Rake Build Tool
 	 	15.7	Build Environment
 	16.	Namespaces, Source Files, and Distribution
 	 	16.1	Namespaces
 	 	16.2	Organizing Your Source
 	 	16.3	Distributing and Installing Your Code
 	17.	Character Encoding
 	 	17.1	Encodings
 	 	17.2	Source Files
 	 	17.3	Transcoding
 	 	17.4	Input and Output Encoding
 	 	17.5	Default External Encoding
 	 	17.6	Encoding Compatibility
 	 	17.7	Default Internal Encoding
 	 	17.8	Fun with Unicode
 	18.	Interactive Ruby Shell
 	 	18.1	Command Line
 	 	18.2	Commands
 	19.	Documenting Ruby
 	 	19.1	Adding RDoc to Ruby Code
 	 	19.2	Adding RDoc to C Extensions
 	 	19.3	Running RDoc
 	 	19.4	Ruby source file documented with RDoc
 	 	19.5	C source file documented with RDoc
 	20.	Ruby and the Web
 	 	20.1	Writing CGI Scripts
 	 	20.2	Using cgi.rb
 	 	20.3	Templating Systems
 	 	20.4	Cookies
 	 	20.5	Choice of Web Servers
 	 	20.6	Frameworks
 	21.	Ruby and Microsoft Windows
 	 	21.1	Running Ruby Under Windows
 	 	21.2	Win32API
 	 	21.3	Windows Automation
III. Ruby Crystallized
 	22.	The Ruby Language
 	 	22.1	Source File Encoding
 	 	22.2	Source Layout
 	 	22.3	The Basic Types
 	 	22.4	Names
 	 	22.5	Variables and Constants
 	 	22.6	Expressions, Conditionals, and Loops
 	 	22.7	Method Definition
 	 	22.8	Invoking a Method
 	 	22.9	Aliasing
 	 	22.10	Class Definition
 	 	22.11	Module Definitions
 	 	22.12	Access Control
 	 	22.13	Blocks, Closures, and Proc Objects
 	 	22.14	Exceptions
 	 	22.15	catch and throw
 	23.	Duck Typing
 	 	23.1	Classes Aren’t Types
 	 	23.2	Coding like a Duck
 	 	23.3	Standard Protocols and Coercions
 	 	23.4	Walk the Walk, Talk the Talk
 	24.	Metaprogramming
 	 	24.1	Objects and Classes
 	 	24.2	Singletons
 	 	24.3	Inheritance and Visibility
 	 	24.4	Modules and Mixins
 	 	24.5	Metaprogramming Class-Level Macros
 	 	24.6	Two Other Forms of Class Definition
 	 	24.7	instance_eval and class_eval
 	 	24.8	Hook Methods
 	 	24.9	One Last Example
 	 	24.10	Top-Level Execution Environment
 	 	24.11	The Turtle Graphics Program
 	25.	Reflection, ObjectSpace, and Distributed Ruby
 	 	25.1	Looking at Objects
 	 	25.2	Looking at Classes
 	 	25.3	Calling Methods Dynamically
 	 	25.4	System Hooks
 	 	25.5	Tracing Your Program’s Execution
 	 	25.6	Behind the Curtain: The Ruby VM
 	 	25.7	Marshaling and Distributed Ruby
 	 	25.8	Compile Time? Runtime? Anytime!
 	26.	Locking Ruby in the Safe
 	 	26.1	Safe Levels
 	 	26.2	Tainted Objects
 	 	26.3	Trusted Objects
 	 	26.4	Definition of the safe levels
IV. Ruby Library Reference
 	27.	Built-in Classes and Modules
 	28.	Standard Library
A1.	Support
 	A1.1	Web Sites
 	A1.2	Usenet Newsgroup
 	A1.3	Mailing Lists
 	A1.4	Bug Reporting
A2.	Bibliography
```