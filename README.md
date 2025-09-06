# Identifier Validation using LEX (Valid & Invalid)

## 📌 Description
This LEX program checks whether a given input string is a **valid identifier** or **not an identifier**.  

- **Valid Identifier:** Must start with a letter (`a-z` or `A-Z`) and can be followed by letters or digits.  
- **Invalid Identifier:** If it starts with a digit, it is considered invalid.  

---

## program:

%{
#include<stdio.h>
%}

letter  [a-zA-Z]
digit   [0-9]

%%
{letter}({letter}|{digit})*  {printf("%s is an identifier\n",yytext);}
{digit}({letter}|{digit})*   {printf("%s is not identifer\n",yytext);}
%%

int main()
{
yylex();
return 0;
}



**How to Compile & Run**

Save the program as identifier.l

Run the following commands:

lex identifier.l
gcc lex.yy.c -o identifier
./identifier


Enter test inputs (press Ctrl+D after typing in Linux/Mac, or Ctrl+Z in Windows):

abc123
1abc
hello
99

📊 Sample Output
abc123 is an identifier
1abc is not identifier
hello is an identifier
99 is not identifier

✅ Conclusion

Identifiers starting with a letter are valid.

Identifiers starting with a digit are invalid.

Special symbols (like @, #, -) are not handled in this version and will be ignored.
