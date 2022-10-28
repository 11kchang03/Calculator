Kyle Chang
kchang27@u.rochester.edu

Using the Shunting Yard algorithm, URCalculator will take in an expression and print out the result of said expression.
The first obstacle that I encountered was separating the parentheses of the input file from the numbers, as well as
maintaining decimal numbers as doubles. I solved this problem by first splitting the input into a string array, using
regular expression "\\s+" to separate the input by any number of spaces. I then made sure to iterate through an array
of all possible operators and replaced each "operator" with " operator ", leaving spaces before and after them. Finally,
I added the elements of this string array into a string and split it once more. What this did was effectively cover the cases
for any expression, regardless of the spacing (which I show in my exp_additional test cases). 

I then encountered my next obstacle when I had to come up with a way to gracefully cover exceptions, as I had never
done that before. But once I learned how to do so, I was able to use try-catch to not break the code when an error
was reached. Another thing that I implemented was allowing the calculator to continue calculating regardless of the
error. This would, for the most part, give the correct answer (for simple typos at least), though the accuracy does
get thrown off once the typos begin to get more ridiculous (covered in expr_additional)

expr_additional
	"25 % 7 +25.65 * sin(5 + 7 ^ 2 * (4 % 3)) + cos(50)-tan(cos(50))"
		weird spacing test
	"365.4 - -(5 * !0 + 4.32 ^ 2.222)"
		testing logical not
	"-tan(cos5  0)"
		unary minus test
	"-tan (   -  cos(50) + 2 * 4 ^ 2.454)"
		weird spacing and unary minus
	"- - 1 + - 1"
		multiple unary minuses
	"-sin2*3+12- (2+6)"
		no parentheses with trig functions test
	" ( 5   .  40 32 q) + ( 444.  65  20 1 * 34 ) "
		wrong input test
		should print out an error message, followed by URCalculator's best guess

URLinkedList.java
Stack.java
Queue.java
URCalculator.java
GUI.java - the gui implementation
	
EXTRA CREDIT SECTION
	supports modulo, unary minus, sine, cosine, and/or tangent operators
	gracefully handles invalid expressions
	GUI implementation
	handles weird spacing