all: compile

compile:
	jflex scanner.flex
	java -jar ../java-cup-11b.jar -interface -parser Parser parser.cup
	javac -cp ../java-cup-11b-runtime.jar *.java

execute:
	@java -cp ../java-cup-11b-runtime.jar:. Driver #> exec/Main.java

clean:
	rm -f *.class *~ exec/Main.java exec/Main.class Parser.java Scanner.java sym.java
