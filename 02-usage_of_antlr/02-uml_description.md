# UML Description of The Generated Code


Assumptions
* The description is based on the `Golang`
* The generated package named `syntax`
* Info about the application
    * Programmer file name APP.g4
    * Application layer package named `app`
    * 
    * 

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

interface RuleContext
RuleNode <|-- RuleContext : implement

class BaseRuleContext
RuleContext <|.. BaseRuleContext : implement


interface ParserRuleContext
RuleContext <|-- ParserRuleContext : inherite

class BaseParserRuleContext
ParserRuleContext <|.. BaseParserRuleContext : implement

RuleContext *-- RuleNode : owns
BaseRuleContext *-- RuleNode : owns

interface ParseTreeListener 
class BaseParseTreeListener 
ParseTreeListener <|.. BaseParseTreeListener : implements
}

package parser {
interface APPListener
class BaseAPPListener
ParseTreeListener <|-- APPListener : inherite
APPListener <|.. BaseAPPListener : implemenet

}

package syntax {
interface IExpressionQueryContext
class ExpressionQueryContext 
IExpressionQueryContext <|.. ExpressionQueryContext : implements
}


BaseParserRuleContext  <|-- ExpressionQueryContext : inherite


package app {

class RealAppListener
BaseAPPListener <|-- RealAppListener : inherite
}


@enduml
```

## Sequence Diagram


