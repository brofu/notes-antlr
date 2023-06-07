# UML Description of The Generated Code

The examples of `Class Diagram` and `Sequence Diagram` for a use case of `Antlr` based on `Goloang` language

**Some Assumptions**
* Code orgnization
    ```
    parser/syntax
    |--EXAMPLE.g4
    |--EXAMPLE.interp
    |--EXAMPLE.tokens
    |--example_base_listener.go
    |--example_lexer.go
    |--example_listener.go
    |--example_parser.go
    |--EXAMPLELexer.interp
    |--EXAMPLELexer.tokens
    |--README.md
    example 
    |--real_app_lister.go
    ```

## Class Diagram
```uml
@startuml

package antlr {

interface Tree
interface SyntaxTree 
interface ParseTree
Tree <|-- SyntaxTree : inherite
SyntaxTree <|-- ParseTree : inherite

interface RuleNode
interface ErrorNode
interface TerminalNode

ParseTree <|-- RuleNode : inherite 
ParseTree <|-- TerminalNode : inherite 
TerminalNode <|-- ErrorNode : inherite 


interface Parser
interface Recognizer  
class BaseParser {
    + BuildParseTrees
}
Parser <|.. BaseParser : implement
BaseRecognizer <|-- BaseParser : inherite

interface RuleContext
RuleNode <|.. RuleContext : implement

class BaseRuleContext
RuleContext <|.. BaseRuleContext : implement


interface ParserRuleContext {
    + EnterRule(ParseTreeListener)
    + ExitRule(ParseTreeListener)
}

RuleContext <|-- ParserRuleContext : inherite

class BaseParserRuleContext
ParserRuleContext <|.. BaseParserRuleContext : implement

RuleContext *-- RuleNode : owns
BaseRuleContext *-- RuleNode : owns

interface ParseTreeListener 
class BaseParseTreeListener 
ParseTreeListener <|.. BaseParseTreeListener : implements
}

package syntax {

interface EXAMPLEListener
class BaseEXAMPLEListener
ParseTreeListener <|-- EXAMPLEListener : inherite
EXAMPLEListener <|.. BaseEXAMPLEListener : implemenet


class EXAMPLEParser 
BaseParser <|-- EXAMPLEParser : inherite

interface IExpressionQueryContext
ParserRuleContext <|-- IExpressionQueryContext : inherite
class ExpressionQueryContext 
IExpressionQueryContext <|.. ExpressionQueryContext : implements
BaseParserRuleContext  <|-- ExpressionQueryContext : inherite


interface IExpressionContext 
ParserRuleContext <|-- IExpressionContext : inherite

class ExpressionContext 
IExpressionContext <|.. ExpressionContext : implements
BaseParserRuleContext <|-- ExpressionContext : inherite

class FromLogicalExpressionContext 
class FromNotExpressionContext 
class FromRelationalExpressionContext 
class FromParenthesesExpressionContext

IExpressionContext <|.. FromLogicalExpressionContext : inherit
IExpressionContext <|.. FromNotExpressionContext : inherit
IExpressionContext <|.. FromRelationalExpressionContext : inherit
IExpressionContext <|.. FromParenthesesExpressionContext: inherit

ExpressionContext <|-- FromLogicalExpressionContext : inherit
ExpressionContext <|-- FromNotExpressionContext : inherit
ExpressionContext <|-- FromRelationalExpressionContext : inherit
ExpressionContext <|-- FromParenthesesExpressionContext: inherit

interface IRelationalExpressionContext 
ParserRuleContext <|-- IRelationalExpressionContext : inherite

class RelationalExpressionContext
IRelationalExpressionContext  <|.. RelationalExpressionContext : implements
BaseParserRuleContext <|-- RelationalExpressionContext : inherite

class FromIdStaticValueRelationalExpression1Context 
class FromIdInStaticValueRelationalExpression2Context 
class FromIdInStaticValueRelationAlExpression3Context 
class FromParenthesesRelationalExpressionContext
class FromArithmeticStaticValueExpression1Context
class FromArithmeticInExpression2Context
class FromArithmeticInExpression3Context

RelationalExpressionContext <|-- FromIdStaticValueRelationalExpression1Context : inherite
RelationalExpressionContext <|-- FromIdInStaticValueRelationalExpression2Context : inherite
RelationalExpressionContext <|-- FromIdInStaticValueRelationAlExpression3Context : inherite
RelationalExpressionContext <|-- FromParenthesesRelationalExpressionContext : inherite
RelationalExpressionContext <|-- FromArithmeticStaticValueExpression1Context : inherite
RelationalExpressionContext <|-- FromArithmeticInExpression2Context : inherite
RelationalExpressionContext <|-- FromArithmeticInExpression3Context : inherite


interface IArithmeticExpressionContext 
ParserRuleContext <|-- IArithmeticExpressionContext : inherite
class ArithmeticExpressionContext 
BaseParserRuleContext <|-- ArithmeticExpressionContext : inherite
IArithmeticExpressionContext <|.. ArithmeticExpressionContext : implements

class FromAtomArithmeticExpressionContext
class FromParenthesesArithmeticExpressionContext 
ArithmeticExpressionContext  <|-- FromAtomArithmeticExpressionContext : inherite
ArithmeticExpressionContext  <|-- FromParenthesesArithmeticExpressionContext : inherite
}




package example {

interface expressionBuilder
class realExpressionBuilder 
expressionBuilder <|.. realExpressionBuilder : implements 

class RealExampleListener
BaseEXAMPLEListener <|-- RealExampleListener : inherite
realExpressionBuilder <|-- RealExampleListener : inherite
}
@enduml
```

## Sequence Diagram


