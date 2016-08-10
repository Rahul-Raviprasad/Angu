# Abstract Syntax Tree (AST)

In computer science, an abstract syntax tree (AST), or just syntax tree, is a tree representation of the abstract syntactic structure of source code written in a programming language. Each node of the tree denotes a construct occurring in the source code. The syntax is "abstract" in not representing every detail appearing in the real syntax. For instance, grouping parentheses are implicit in the tree structure, and a syntactic construct like an if-condition-then expression may be denoted by means of a single node with three branches.

This distinguishes abstract syntax trees from concrete syntax trees, traditionally designated parse trees, which are often built by a parser during the source code translation and compiling process. Once built, additional information is added to the AST by means of subsequent processing, e.g., contextual analysis.

Abstract syntax trees are also used in program analysis and program transformation systems.

Application in Compilers

Abstract syntax trees are data structures widely used in compilers, due to their property of representing the structure of program code. An AST is usually the result of the syntax analysis phase of a compiler. It often serves as an intermediate representation of the program through several stages that the compiler requires, and has a strong impact on the final output of the compiler.

### Motivation
Being the product of the syntax analysis phase of a compiler, the AST has several properties that are invaluable to the further steps of the compilation process.

Compared to the source code, an AST does not include certain elements, such as inessential punctuation and delimiters (braces, semicolons, parentheses, etc.).
A more important difference is that the AST can be edited and enhanced with information such as properties and annotations for every element it contains. Such editing and annotation is impossible with the source code of a program, since it would imply changing it.
At the same time, an AST usually contains extra information about the program, due to the consecutive stages of analysis by the compiler, an example being the position of an element in the source code. This information may be used to notify the user of the location of an error in the code.

### Design
The design of an AST is often closely linked with the design of a compiler and its expected features.

Core requirements include the following:

Variable types must be preserved, as well as the location of each declaration in source code.
The order of executable statements must be explicitly represented and well defined.
Left and right components of binary operations must be stored and correctly identified.
Identifiers and their assigned values must be stored for assignment statements.
These requirements can be used to design the data structure for the AST.

Some operations will always require two elements, such as the two terms for addition. However, some language constructs require an arbitrarily large number of children, such as argument lists passed to programs from the command shell. As a result, an AST used to represent code written in such a language has to also be flexible enough to allow for quick addition of an unknown quantity of children.

Another major design requirement for an AST is that it should be possible to unparse an AST into source code form. The source code produced should be sufficiently similar to the original in appearance and identical in execution, upon recompilation.

### Design patterns
Due to the complexity of the requirements for an AST and the overall complexity of a compiler, it is beneficial to apply sound software development principles. One of these is to use proven design patterns to enhance modularity and ease of development.

Different operations don't necessarily have different types, so it is important to have a sound node class hierarchy. This is crucial in the creation and the modification of the AST as the compiler progresses.

Because the compiler traverses the tree several times to determine syntactic correctness, it is important to make traversing the tree a simple operation. The compiler executes a specific set of operations, depending on the type of each node, upon reaching it, so it often makes sense to use the visitor pattern.


This has been directly taken from Wikipedia : https://en.wikipedia.org/wiki/Abstract_syntax_tree
