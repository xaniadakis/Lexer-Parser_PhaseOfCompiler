# Lexer and Parser phase of a Compiler + Translator 

In this project I implement a parser and translator for a language supporting string operations. 
The language supports the concatenation (+) operator over strings, function definitions and calls, conditionals (if-else i.e, every "if" must be followed by an "else"), and the following logical expressions:

is-prefix-of (string1 prefix string2): Whether string1 is a prefix of string2.
is-suffix-of (string1 suffix string2): Whether string1 is a suffix of string2.

All values in the language are strings.

The precedence of the operator expressions is defined as: precedence(if) < precedence(concat).

My parser, based on a context-free grammar, translates the input language into Java. I use JavaCUP for the generation of the parser combined either with a generated lexer(using JFlex).

The output language is a subset of Java so it can be compiled using javac and executed using java, if you want to test your output.

My program accepts input programs from stdin and print output Java programs to stdout.


Example

Input:

    name()  {
        "John"
    }

    surname() {
        "Doe"
    }

    fullname(first_name, sep, last_name) {
        first_name + sep + last_name
    }

    name()
    surname()
    fullname(name(), " ", surname())

Output (Java):

    public class Main {
        public static void main(String[] args) {
            System.out.println(name());
            System.out.println(surname());
            System.out.println(fullname(name(), " ", surname()));
        }

        public static String name() {
            return "John";
        }

        public static String surname() {
            return "Doe";
        }

        public static String fullname(String first_name, String sep, String last_name) {
            return first_name + sep + last_name;
        }
    }
    
    
The program can be compiled and run as follows:

    make clean compile execute
    
It then waits for user input from the keyboard, where you should type the input program and then press Ctrl-D once or twice to signal EOF. 
    
One can infer the desired syntax of the input language from the example above and the specifications of the language in the beggining.

