Table of Contents
====

```ruby
Foreword to the Third Edition
Preface
 	Why Ruby?
 	Ruby Versions
 	Changes in the Book
 	Resources
 	Acknowledgments
 	Notation Conventions
Road Map
I. Facets of Ruby
 	1.	Getting Started
 	 	1.1	The Command Prompt
 	 	1.2	Installing Ruby
 	 	1.3	Running Ruby
 	 	1.4	Ruby Documentation: RDoc and ri
 	2.	Ruby.new
 	 	2.1	Ruby Is an Object-Oriented Language
 	 	2.2	Some Basic Ruby
 	 	2.3	Arrays and Hashes
 	 	2.4	Symbols
 	 	2.5	Control Structures
 	 	2.6	Regular Expressions
 	 	2.7	Blocks and Iterators
 	 	2.8	Reading and ’Riting
 	 	2.9	Command-Line Arguments
 	 	2.10	Onward and Upward
 	3.	Classes, Objects, and Variables
 	 	3.1	Objects and Attributes
 	 	3.2	Classes Working with Other Classes
 	 	3.3	Access Control
 	 	3.4	Variables
 	4.	Containers, Blocks, and Iterators
 	 	4.1	Arrays
 	 	4.2	Hashes
 	 	4.3	Blocks and Iterators
 	 	4.4	Containers Everywhere
 	5.	Sharing Functionality: Inheritance, Modules, and Mixins
 	 	5.1	Inheritance and Messages
 	 	5.2	Modules
 	 	5.3	Mixins
 	 	5.4	Iterators and the Enumerable Module
 	 	5.5	Composing Modules
 	 	5.6	Inheritance, Mixins, and Design
 	6.	Standard Types
 	 	6.1	Numbers
 	 	6.2	Strings
 	 	6.3	Ranges
 	7.	Regular Expressions
 	 	7.1	What Regular Expressions Let You Do
 	 	7.2	Ruby’s Regular Expressions
 	 	7.3	Digging Deeper
 	 	7.4	Advanced Regular Expressions
 	8.	More About Methods
 	 	8.1	Defining a Method
 	 	8.2	Calling a Method
 	9.	Expressions
 	 	9.1	Operator Expressions
 	 	9.2	Miscellaneous Expressions
 	 	9.3	Assignment
 	 	9.4	Conditional Execution
 	 	9.5	case Expressions
 	 	9.6	Loops
 	 	9.7	Variable Scope, Loops, and Blocks
 	10.	Exceptions, catch, and throw
 	 	10.1	The Exception Class
 	 	10.2	Handling Exceptions
 	 	10.3	Raising Exceptions
 	 	10.4	catch and throw
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