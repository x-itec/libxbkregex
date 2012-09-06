#include "../include/xbkregex1.h"

void xbkregex::comp(string pattern)
{
mypattern=pattern;//String kopieren
regexresult=regcomp(&preg,mypattern.c_str(),REG_EXTENDED);
}

void xbkregex::exec(string text)
{
register int x;
char *minibuffer;
const char *textkopie = text.c_str();
minibuffer = new char[strlen(text.c_str())];
pmatch = new regmatch_t[strlen(text.c_str())];

regexresult=regexec(&preg,text.c_str(),preg.re_nsub,pmatch,0);
if(regexresult==0)
{
//Anzahl Strings anlegen
myresults = new string[preg.re_nsub+1];
for(x=0;x<=preg.re_nsub;x++)
 {
 strncpy(minibuffer,textkopie+pmatch[x].rm_so,pmatch[x].rm_eo-pmatch[x].rm_so);
 minibuffer[pmatch[x].rm_eo-pmatch[x].rm_so]=0;
 myresults[x]=minibuffer;//mal schauen 
}//for 
}//regexresult==0
}

int xbkregex::matches()
{
return preg.re_nsub;
}

string& xbkregex::operator[](int i)
{
return myresults[i];
}

int xbkregex::error()
{
return regexresult;
}

string xbkregex::error(int regexresult)
{
int x;
char *puffer;
x=regerror(regexresult,&preg,NULL,0);
puffer= new char[x];
regerror(regexresult,&preg,puffer,x);
return puffer;
}

