# Tarea de compiladores

Definir los tipos de dato
Definir la asignación a variables
Definir la reasignación a variables (en especial por los arreglos)
Usar keyword para indicar que es una palabra reservada
Literal es para valores explicitos. Por ejemplo la definición de un entero
Operador es para el símbolo de ese operador
Símbolos (números, operadores, etc cosas sueltas para luego llamarlas)
<left_parenthesis> ::= “є”
<right_parenthesis> ::= “э”
<wall_comment> ::= “|”
<left_exclamation> ::= “!”
<right_exclamation> ::= “¡”
<left_block> ::= “¿”
<right_block> ::= “?”
<plus_operator> ::= “+”
<minus_operator> ::= “-“
<multiplication_operator> ::= “*”
<division_operator> ::= “/”
<int_division_operator> ::= “//”
<modulo_operator> ::= “%”
<power_operator> ::= “^”
<increment_operator> ::= "++"
<decrement_operator> ::= "--"
<assignment_operator> ::= "="  
<digit1to9_literal> ::= [1-9]
<decimal_digit_literal> ::= [0-9]
<zero_literal> ::= 0
<bool_literal> ::= “true” | “false”
<dot_literal> ::= “.”
<letter_or_underscore> ::= [a-zA-Z_]
<identifier_char> ::= [a-zA-Z0-9_]
<int_keyword> ::= “int”
<float_keyword> ::= “float”
<bool_keyword> ::= “bool”
<char_keyword> ::= “char”
<string_keyword> ::= “string”
<let_keyword> ::= “let”
<input_keyword> ::= “input”
<output_keyword> ::= “output”
<numeric_type> ::= <int_keyword> | <float_keyword>
<text_type> ::= <char_keyword> | <string_keyword>
<greater_operator> ::= “>”
<greater_equal_operator> ::= “>=”
<less_equal_operator> ::= “<=”
<equal_operator> ::= “==”
<not_equal_operator> ::= “!=”
<delimiter> ::= “$”
<line_break> ::= “\n”

## Tipos de datos literales
<int_literal> ::=  <minus_operator>? <digit1to9_literal> <decimal_digit_literal>*
<int_literal> ::= <zero_literal>
<float_literal> ::= <zero_literal> <dot_literal> <zero_literal>
<float_literal> ::=  <minus_operator>? <zero_literal> <dot_literal> <decimal_digit_literal>* <digit1to9_literal>+
<float_literal> ::= <minus_operator>? <digit1to9_literal> <decimal_digit_literal>* <dot_literal> (<decimal_digit_literal>* <digit1to9_literal>+ | <zero_literal>)
<char_literal> ::= ‘\.’\ NO ESTOY SEGURO
<string_literal> ::= “\.*”\ NO ESTOY SEGURO
Identificador
<identifier> ::= <letter_or_underscore> <identifier_char>*


## Operaciones aritméticas
<unary_negative> ::= <minus_operator> (<int_literal> | <float_literal>)
<postfix_expression> ::= < identifier > (<increment_operator> | <decrement_operator>)
<arithmetic_expression> ::= <arithmetic_expression> (<plus_operator> | <minus_operator>) <term>  | <term>
<term> ::= <term> (<multiplication_operator> | <division_operator> | <int_division_operator> |  <modulo_operator>) <power> | <power>
<power> ::= <factor> <power_operator> <power>| <factor>
<factor> ::= <left_parenthesis> <arithmetic_expression> <right_parenthesis> | <arithmetic_operands>
<arithmetic_operands> ::= <int_literal> | <float_literal> | <identifier> | <unary_negative> | <postfix_expression>
Operaciones lógicas
Esto vease como: 5 > 3, x == 4
<relational_expression> ::= <arithmetic_expression> <relational_operator> <arithmetic_expression>
<relational_operator> ::= <greater_operator> | <less_operator> | <less_equal_operator>  | <greater_equal_operator>  | <equal_operator> | <not_equal_operator>
<logical_operator> ::= "~" | "@"
Esto permite cosas como (5+2 @ 3 ) @ False o también 5 > 2
<condition> ::= <contion_simple> ( <logical_operator> <condition_simple> )*
<condition_simple> ::=  <relational_expression> | <bool_literal> | <identifier> | <left_ parenthesis > <condition>   <right _ parenthesis > 
<not_logical_operator> ::= ”Σ”
<not_condicion> ::= <not_logical_operator> <condicion_simple>


## Declaración de variables 
Pero ya seria algo como Let int x = 5$
<declaration> ::= <let_keyword> <type> <identifier> <assignment_operator> <literal> <delimiter>
<type> ::= <int_keyword> | <float_keyword> | <bool_keyword> | <char_keyword> | <string_keyword>
/// AQUI TAL VEZ QUITAMOS EL BOOL
<literal> ::= <int_literal> | <float_literal> | <bool_literal> | <char_literal> | <string_literal>

## REASIGNACIÓN  aqui no contemplamos x += 2 o y *= 2 preguntar al profe sino algo así (suponga que ya declaro x) x = 2$
<Reassignment> ::= <identifier>  <assignment_operator> <literal> <delimiter>




## Comentarios 
// Tomando a dot_literal como un punto que en REGEX es cualquier cosa menos salto de linea
<simple_comment> ::= <wall_comment> <dot_literal>* 
<multiple_comment> ::= <left_exclamation> ( <dot_literal> | <line_break>  )* <right_exclamation>

## CREACION IF o intento  - ME FALTAN COSAS POR DEFINIR
<controlIf> ::= "IF" <left_parenthesis> <condition> <right_parenthesis> ( <block> | <statements>)*
<block> ::= <left_block> <statements>* <right_block>
<statements> ::= <declaration> | <reassignment> | <controlIf> |
