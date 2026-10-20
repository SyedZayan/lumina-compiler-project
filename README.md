# Lumina Lang - Interactive Compiler Construction Project
**Course:** Compiler Construction  
**Submission:** First Week of November  
**Implementation:** Modern Web-based Compiler & Virtual Machine + Standalone Reference Engine  

---

## 1. Project Overview
This project presents an interactive web application that implements and visualizes the complete 5-stage compilation process for **Lumina Lang**, designed in Lab 02:
1. **Lexical Analysis (Scanner):** Tokenizes source text, matches Lab 02 regex tokens, builds a detailed token table with line/column coordinates, and tracks statistics.
2. **Syntax Analysis (Parser):** Validates source structure using a Recursive Descent Parser adhering to the formal Context-Free Grammar (CFG) and builds an Abstract Syntax Tree (AST) with both interactive visual tree and structured JSON views.
3. **Semantic Analysis:** Constructs a comprehensive Symbol Table, enforces scope isolation, validates declaration-before-use, checks type safety on assignments and operators, and checks condition booleans and dead-code warnings.
4. **Intermediate Code Generation (ICG):** Translates the AST into Three-Address Code (TAC) and emits a formal Quadruples table (`(op, arg1, arg2, result)`).
5. **Final Output & Virtual Machine (LVM):** Executes the quadruples in a simulated browser VM, displays standard output in a terminal console for `Turnout` statements, provides memory inspection, and generates target JavaScript code.

---

## 2. Language Grammar (EBNF)
```ebnf
<Program>          ::= <StatementList> <EOF>
<StatementList>    ::= <Statement>*
<Statement>        ::= <VarDeclStmt> | <AssignStmt> | <PrintStmt> | <IfStmt> | <WhileStmt> | <HaltStmt> | <BlockStmt>
<VarDeclStmt>      ::= ("Bindint" | "Bindstrng" | "Bindbool") <Identifier> ":=" <Expression>
<AssignStmt>       ::= <Identifier> ":=" <Expression>
<PrintStmt>        ::= "Turnout" <Expression>
<IfStmt>           ::= "examine" <Condition> <Statement> [ "otherwise" <Statement> ]
<WhileStmt>        ::= "noose" <Condition> <Statement>
<Condition>        ::= <Expression>
<BlockStmt>        ::= "{" <StatementList> "}"
<HaltStmt>         ::= "halt"
<Expression>       ::= <RelationalExpr>
<RelationalExpr>   ::= <AdditiveExpr> [ ( ">>" | "<<" | ">=;" ) <AdditiveExpr> ]
<AdditiveExpr>     ::= <MultiplicativeExpr> ( ( "++>" | "<--" ) <MultiplicativeExpr> )*
<MultiplicativeExpr>::= <PrimaryExpr> ( ( "***" | "://" ) <PrimaryExpr> )*
<PrimaryExpr>      ::= <NUMBER> | <STRING> | "True" | "False" | <Identifier> | "(" <Expression> ")"
```

---

## 3. How to Run
- **Web Application:** Double-click or open `index.html` in any modern web browser (Chrome, Firefox, Edge, Safari). No web server, node installation, or build step is required!
- Select any preset from the dropdown (or paste custom Lumina code) and click **Compile & Run**.
"# lumina-compiler-project" 
