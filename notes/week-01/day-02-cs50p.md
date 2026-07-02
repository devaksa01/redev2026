- **Text editor** is used to write the python code, and the one we use is Visual Studio Code
- VSCode can be opened by writing `code main.py` which create/open file named main.py in VSCode
- **Function** is an action that the computer will know how to perform
- or in the short said that **Function** is these that take inputs and produce outputs for us.
- print is a function to show text to terminal
- input is a function to take user input in the terminal
- to run python code, open terminal window and type `python main.py`
- function take **arguments** that will affect their behavior
- parameters are arguments that a function can accept.
- **Bugs** are mistakes that resulted in error, often hint are shown in the error. 
- **Debugging** is act of fixing bugs.
- **Comments** is part of code that doesnt affect the program, in python to write comments use `# Something here` . Comments used to describe something, perhaps about the code itself.
- **Variable** is a container for a value, to be more exact, it is your custom name for a specific place in memory where after that u can fill the place with specific values. 
- in python, to make a variable, use `name = value`, the equal symbol mean assign what is on the right to what is on the left
- **string** is a sequence of text.
- input function is returning string type value
- print has an attribute called `end=`, we can modify it to `end=""` so the next print will printed on the same line
- careful of `"he said "wow""` because it will resulted in an error, we should use `\` in each quotation mark to avoid error, so the right one is `"He said \"wow\""`
- ways to print a string variable:
```python
username="satriaadhyaksa"
print("Hi, ", username)
#or
print("Hi, " + username)
#or
print(f"Hi, {username}")
```
where the last one is called formatting.
- you can remove whitelines from a string using .strip()
- you can capitalize first letter of each word using .title()
- you can add all together like this `FullName = FullName.strip().title()`
- you can convert string to integer using `int()`
- you can convert string to float using `float()`
- float can be rounded by using:
1. `round(floatVariable)` or more specifically `round(floatVariable,2)` to round a float by 2 decimal places.
2. `print(f"{floatVariable:.2f}")`
- you can write a thousand or more automatically with commas via float with following code `print(f"{floatVariable:,}")`
- use `def` to make our own function, eg.
```python
def sum(x,y):
	print(x+y)
x=5
y=6
sum(x,y)
```
or you can bring your main code to the top but u need to make a main function and call it on the bottom, like:
```python
def main():
	sum(5,6)

def sum(x,y):
	print(x+y)

main()
```
also, to make a function that passes back a value (or so called return value), use `return`, e.g.
```python
def main():
	sum(5,6)
	
def sum(x,y):
	return x+y

main()
```
- Also, python is and indented language so it is necessary to make space or indent in the right place.
- **Side-effect** is when a function changes something or some state outside of it's own local environment than just simply returning a value. A function without any side-effects are called pure function. We should minimize side-effects. 
- `print()` also is a side-effect.