# Java Calculator Using Different Algorithms

This is a calculator application built using Java Swing. It performs basic arithmetic operations including addition, subtraction, multiplication, and division __using different algorithms__. The calculator follows the MDAS (Multiplication, Division, Addition, Subtraction) rule for operator precedence.

## Features
- __Basic Arithmetic Operations:__ Supports addition, subtraction, multiplication, and division.
- __Different Algorithms:__
  - __Addition and Subtraction:__ Implemented using recursion.
  - __Multiplication:__ Implemented using the Russian Peasant method.
  - __Division:__ Implemented using the shift and subtract method.
- __Input Validation:__ Ensures that the input expression is valid.
- __Infix to Prefix Conversion:__ Converts infix expressions to prefix notation before evaluation.
- __Evaluation of Prefix Expressions.__
- __Detailed Solution Display:__ Shows detailed steps of the computation for each operation.

## Sample Output
![Screenshot 2024-07-26 154445](https://github.com/user-attachments/assets/fdeaf57a-67c6-4def-99cf-6d7c38fd39af)


## Algorithms Explained
__Addition Using Recursion__ - the addition algorithm adds two numbers by incrementing the first number and decrementing the second number recursively until the second number is zero.
     
      public double sum(double num1, double num2) {
          if (num2 == 0) {
              textAreaSolAdd.setText(textAreaSolAdd.getText() + "Sum: " + num1);
              return num1;
          } else {
              String pnum1 = df.format(num1 + 1);
              String pnum2 = df.format(num2 - 1);
              textAreaSolAdd.setText(textAreaSolAdd.getText() + "Num 1= " + pnum1 + " Num 2= " + pnum2 + " \n");
              return sum(num1 + 1, (int) num2 - 1);
          }
      }

__Subtraction Using Recursion__ - the subtraction algorithm subtracts two numbers by decrementing both the first and the second number recursively until the second number is zero.

      public double sub(double num1, double num2) {
          if (num2 == 0) {
              textAreaSolSub.setText(textAreaSolSub.getText() + "Difference: " + num1);
              return num1;
          } else {
              String pnum1 = df.format(num1 - 1);
              String pnum2 = df.format(num2 - 1);
              textAreaSolSub.setText(textAreaSolSub.getText() + "Num 1= " + pnum1 + " Num 2= " + pnum2 + " \n");
              return sub(num1 - 1, (int) num2 - 1);
          }
      }

__Multiplication Using the Russian Peasant Method__ - the Russian Peasant multiplication algorithm multiplies two numbers by doubling one number and halving the other, adding the doubled number to the result whenever the halved number is odd.

      public double russianPeasantMultiply(double num1, double num2) {
          double result = 0;
          boolean isNegative = false;
      
          if (num1 < 0) {
              num1 *= -1;
              isNegative = true;
          }
      
          if (num2 < 0) {
              num2 *= -1;
              isNegative = !isNegative;
          }
      
          while ((int) num2 > 0) {
              if ((int) num2 % 2 == 1) {
                  result += num1;
                  textAreaSolMul.setText(textAreaSolMul.getText() + "Result: " + result + "\n");
              }
      
              num1 *= 2;
              num2 = num2 / 2;
              textAreaSolMul.setText(textAreaSolMul.getText() + "Num 1= " + num1 + " Num 2= " + num2 + " \n");
          }
      
          if (isNegative) {
              result *= -1;
          }
          textAreaSolMul.setText(textAreaSolMul.getText() + "Product: " + result);
          return result;
      }

__Division Using Shift and Subtract__ - the division algorithm divides two numbers by shifting and subtracting. It shifts the divisor left until it's larger than the dividend, then subtracts it from the dividend and shifts right, accumulating the quotient.

      public double shiftAndSub(double dividend, double divisor) {
          if (divisor == 0.0) {
              // Handle division by zero
          }
          double quotient = 0.0;
          remainder = 0;
          boolean negativeResult = false;
      
          if (dividend < 0.0) {
              negativeResult = !negativeResult;
              dividend = -dividend;
          }
          if (divisor < 0.0) {
              negativeResult = !negativeResult;
              divisor = -divisor;
          }
      
          for (int i = 5; i >= 0; i--) {
              remainder = ((int) remainder << 1) + ((int) dividend >> i & 1);
              textAreaSolDiv.setText(textAreaSolDiv.getText() + "Remainder: " + remainder + "\n");
              if (remainder >= divisor) {
                  remainder -= divisor;
                  quotient += 1 << i;
              }
          }
      
          if (negativeResult) {
              quotient = -quotient;
          }
          rem = remainder / divisor;
          textAreaSolDiv.setText(textAreaSolDiv.getText() + "Quotient: " + quotient + "\n");
          return quotient;
      }




