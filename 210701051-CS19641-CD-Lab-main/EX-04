%{
#include <stdio.h> #include <stdlib.h>
int num1, num2; char op;
void dig(char c) { if (isdigit(c))
yytext[0] = c;
}
%}
%int yywrap
%%
[0-9]+ { dig(*yytext); printf("\033[0;32mNumber: %s\033[0m\n", yytext); } [-+*/] { op = *yytext;
printf("\033[0;32mOperator: %s\033[0m\n", yytext); }
\n { printf("\033[0;34mEnter arithmetic expression (e.g., 2 + 3 * 4):\033[0m\n"); } [ \t] { /*
ignore whitespace */ }
. { printf("\033[0;31mInvalid character: %s\033[0m\n", yytext); }
%%
int main() {
printf("\033[0;34mEnter arithmetic expression (e.g., 2 + 3 * 4):\033[0m\n"); yylex();
num1 = atoi(yytext);
num2 = atoi(yytext + strlen(yytext) + 1);
switch(op) { case '+':
printf("\033[0;34mResult: %d\n\033[0m", num1 + num2); break;
case '-':
printf("\033[0;34mResult: %d\n\033[0m", num1 - num2); break;
case '*':
printf("\033[0;34mResult: %d\n\033[0m", num1 * num2); break;
case '/':
if (num2 != 0)
printf("\033[0;34mResult: %.2f\n\033[0m", (float)num1 / num2); else
printf("\033[0;31mError: Division by zero\n\033[0m"); break;
default:
printf("\033[0;31mError: Invalid operator\n\033[0m"); break;
}
return 0;
}
int yywrap(void) {
}
