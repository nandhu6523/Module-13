# Exp.No:32  
## CONVERSION OF INFIX TO POSTFIX



### AIM  
To write a Python program to convert a given Infix expression to Postfix expression by following the precedence and associative rules. The input expression contains only Division, Subtraction, and Bitwise AND operators. A dictionary is used to set the priority for operators, and a set is used to hold the operators used in the given expression.



### ALGORITHM

1. **Start the program.**
2. **Initialize an empty stack** and an empty output string.
3. **Iterate through each character** in the infix expression:
   - If the character is **not an operator**, append it directly to the output string.
   - If the character is an **open parenthesis '('**, push it onto the stack.
   - If the character is a **close parenthesis ')'**, pop from the stack and append to the output until encountering a left parenthesis '('.
   - If the character is an **operator**, handle it based on precedence:
     - While there’s an operator at the top of the stack with higher or equal precedence, pop the stack and append those operators to the output.
     - Push the current operator onto the stack.
4. **Use a priority dictionary** to define operator precedence, ensuring higher precedence operators are placed before lower precedence ones.
5. Once the expression is fully processed, continue popping any remaining operators from the stack and append them to the output.
6. **Return the final postfix expression.**
7. **Print the result.**
8. **End the program.**



### PROGRAM

```
precedence = {'/': 2, '-': 1, '&': 0}  

operators = {'/', '-', '&'}  
stack = []  # Stack to hold operators
output = []  # List to store postfix expression
used_operators = set()  # Set to hold operators found in the expression

for char in expression:
    if char.isalnum():  # Operand
        output.append(char)
    elif char in operators:  # Operator
        used_operators.add(char)
        while (stack and precedence.get(stack[-1], -1) >= precedence[char]):
            output.append(stack.pop())
        stack.append(char)
    elif char == '(':  # Left parenthesis
        stack.append(char)
    elif char == ')':  # Right parenthesis
        while stack and stack[-1] != '(':
            output.append(stack.pop())
        stack.pop()  # Remove '(' from stack
    else:
        continue  # Ignore spaces or invalid characters

while stack:
    output.append(stack.pop())

print("infix notation: ", expression)
print("postfix notation: ", ''.join(output))
return ''.join(output)
```

### OUTPUT
![442497183-1f232d9a-6527-4cd7-90dd-4059ee0fb225](https://github.com/user-attachments/assets/4f53d292-5041-4bcc-a196-2afbc384a3d4)



### RESULT
Thus a Python program to convert a given Infix expression to Postfix expression was done successfully.
