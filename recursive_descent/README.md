# Homework: Evaluation of Arithmetic Expressions (Recursive Descent Parser)

1. Consider the following grammar for arithmetic expressions. It is similar to the one discussed in class.
<p align="center">
expr	→ term { + term | - term } </br>
term	→ factor { * factor | / factor } </br>
factor	→ ( expr ) | digit-seq </br>
digit-seq	→ digit { digit } </br>
digit	→ 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 </br>
</p>
<p>
The recursive descent parser to evaluate syntactically valid arithmetic expressions has five methods corresponding to each of the five non-terminal symbols of this grammar. A tokenizer is not used for this parser. Instead, each method gets input characters from a StringBuilder parameter called source. You can assume that the source argument does not contain any white space or any other characters not part of the expression except for at least one "sentinel" character after the end of the expression to mark the end. In other words, any proper prefix of the argument can contain only characters from the set {'0', '1', '2', '3', '4', '5', '6', '7', '8', '9', '(', ')', '+', '-', '*', '/'}. You can further assume that the input is syntactically valid, so that no error checking is necessary.</p>


Here are few more hints:
- A string s1 being a proper prefix of a string s2 means both that the length of s1 is strictly less than (less than but not equal to) the length of s2 and that s1 is a prefix of s2.
- The instance methods charAt(int) and deleteCharAt(int) defined in StringBuilder will be useful to manipulate the input.
- The static methods isDigit(char) and digit(char, int) in class Character can be used to check if a character is a digit and to convert a digit character into the corresponding integer value, respectively.

Write the code for the following 5 methods making sure you use the grammar above as a guide.

```Java
/**
 * Evaluates an expression and returns its value.
 * 
 * @param source
 *            the {@code StringBuilder} that starts with an expr string
 * @return value of the expression
 * @updates source
 * @requires <pre>
 * [an expr string is a proper prefix of source, and the longest
 * such, s, concatenated with the character following s, is not a prefix
 * of any expr string]
 * </pre>
 * @ensures <pre>
 * valueOfExpr =
 *   [value of longest expr string at start of #source]  and
 * #source = [longest expr string at start of #source] * source
 * </pre>
 */
public static int valueOfExpr(StringBuilder source) {...}
 
/**
 * Evaluates a term and returns its value.
 * 
 * @param source
 *            the {@code StringBuilder} that starts with a term string
 * @return value of the term
 * @updates source
 * @requires <pre>
 * [a term string is a proper prefix of source, and the longest
 * such, s, concatenated with the character following s, is not a prefix
 * of any term string]
 * </pre>
 * @ensures <pre>
 * valueOfTerm =
 *   [value of longest term string at start of #source]  and
 * #source = [longest term string at start of #source] * source
 * </pre>
 */
private static int valueOfTerm(StringBuilder source) {...}
 
/**
 * Evaluates a factor and returns its value.
 * 
 * @param source
 *            the {@code StringBuilder} that starts with a factor string
 * @return value of the factor
 * @updates source
 * @requires <pre>
 * [a factor string is a proper prefix of source, and the longest
 * such, s, concatenated with the character following s, is not a prefix
 * of any factor string]
 * </pre>
 * @ensures <pre>
 * valueOfFactor =
 *   [value of longest factor string at start of #source]  and
 * #source = [longest factor string at start of #source] * source
 * </pre>
 */
private static int valueOfFactor(StringBuilder source) {...}
 
/**
 * Evaluates a digit sequence and returns its value.
 * 
 * @param source
 *            the {@code StringBuilder} that starts with a digit-seq string
 * @return value of the digit sequence
 * @updates source
 * @requires <pre>
 * [a digit-seq string is a proper prefix of source, which
 * contains a character that is not a digit]
 * </pre>
 * @ensures <pre>
 * valueOfDigitSeq =
 *   [value of longest digit-seq string at start of #source]  and
 * #source = [longest digit-seq string at start of #source] * source
 * </pre>
 */
private static int valueOfDigitSeq(StringBuilder source) {...}
 
/**
 * Evaluates a digit and returns its value.
 * 
 * @param source
 *            the {@code StringBuilder} that starts with a digit
 * @return value of the digit
 * @updates source
 * @requires 1 < |source|  and  [the first character of source is a digit]
 * @ensures <pre>
 * valueOfDigit = [value of the digit at the start of #source]  and
 * #source = [digit string at start of #source] * source
 * </pre>
 */
private static int valueOfDigit(StringBuilder source) {...}
```

## Credits
https://web.cse.ohio-state.edu/software/2231/web-sw2/assignments/homeworks/expression-evaluator.html