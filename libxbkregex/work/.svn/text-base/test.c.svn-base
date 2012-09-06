#include <sys/types.h>
#include <stdio.h>
#include <xbk/xbkregex/xbkregex1.h>
int main()
{
xbkregex xtest;
string text;
int x;

text = "bla bla hallo(123,456)";
string compstring="(hallo\\()([0-9]*)(\\,)([0-9]*)(\\))";
xtest.comp(compstring);
x=xtest.error();
//cout << xtest.error(x);

xtest.exec(text);
for (x=0;x<xtest.matches();x++)
 { 
  cout << xtest[x]; 
  cout << "\n";
 }
}
