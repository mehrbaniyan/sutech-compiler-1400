
# Sutech Compiler Project - 1400

## Introduction
This is the main repository for compiler design course project at university of technology of shiraz.

For more info please read **[Project Description.pdf](https://github.com/mehrbanian/sutech-compiler-1400/blob/main/Project%20Description.pdf)**.

## Project Essentials
### Inputs
You have to test your compiler test inputs, placed in **inputs** directory.

### Grammar
This is a sample MiniJava grammar (BNF notation) that you can use for your compiler's parser.

*Note: This grammar is just a sample. You can change it to your need according to your design in the first phase of project.* 
```java
Goal ::= MainClass ( ClassDeclaration )* <EOF>

MainClass ::= 
	"class" Identifier "{" 
		"public" "static" "void" "main" "(" "String" "[" "]" Identifier ")" "{" 
			Statement 
		"}" 
	"}"

ClassDeclaration ::=	
	"class" Identifier ( "extends" Identifier )? "{" 
		( VarDeclaration )* ( MethodDeclaration )* 
	"}"

VarDeclaration ::= Type Identifier ";"

MethodDeclaration ::= 
	"public" Type Identifier "(" ( Type Identifier ( "," Type Identifier )* )? ")" 
		"{" ( VarDeclaration )* ( Statement )* "return" Expression ";" 
	"}"

Type ::= 
	"int" "[" "]"
	| "boolean"
	| "int"
	| Identifier

Statement ::= 
	"{" ( Statement )* "}"
	| "if" "(" Expression ")" Statement "else" Statement
	| "while" "(" Expression ")" Statement
	| "System.out.println" "(" Expression ")" ";"
	| Identifier "=" Expression ";"
	| Identifier "[" Expression "]" "=" Expression ";"

Expression ::= 
	Expression ( "&&" | "<" | "+" | "-" | "*" ) Expression
	| Expression "[" Expression "]"
	| Expression "." "length"
	| Expression "." Identifier "(" ( Expression ( "," Expression )* )? ")"
	| <INTEGER_LITERAL>
	| "true"
	| "false"
	| Identifier
	| "this"
	| "new" "int" "[" Expression "]"
	| "new" Identifier "(" ")"
	| "!" Expression
	| "(" Expression ")"

Identifier ::= <IDENTIFIER>
```
## License
MIT
