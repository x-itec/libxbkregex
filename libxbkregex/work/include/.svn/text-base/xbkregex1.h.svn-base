#ifndef xbkregex_
#define xbkregex_
#include <sys/types.h>
#include <regex.h>
#include <iostream>
#include <cstdlib>
#include <string>
using namespace std;

class xbkregex
{
private:
string mypattern;  //Regex-Ausdruck
string *myresults; //Array mit den Ergebnissen
regex_t preg;	   //compilierter regex Ausdruck
regmatch_t *pmatch;//Zeiger auf die Ergebniskoordinaten

int regexresult;   //Status nach regexec oder regcomp
char *text;
char *kopie;

public:
void comp(string pattern);
void exec(string text);

int error();//liefert Fehlercode als Zahl zurueck
string error(int regexresult);//liefert Fehlermeldung als Text zurueck

int  matches();//liefert Anzahl Ergebnisse zurueck

string& operator[](int i);//liefert Element i zurueck!



};

#endif
