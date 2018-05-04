---
title: Výjimky a Unwinding zásobníku v jazyce C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: a1a57eae-5fc5-4c49-824f-3ce2eb8129ed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b05b2f6240876540cd9e67d83bcb88242b68827b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="exceptions-and-stack-unwinding-in-c"></a>Výjimky a unwinding zásobníku v jazyce C++
V mechanismu výjimek jazyka C++ přesune ovládací prvek příkaz throw na první příkaz catch, který dokáže zpracovat vyvolaný typ. Když je dosaženo příkaz catch, všechny automatické proměnné, které jsou v rozsahu mezi throw a catch příkazy jsou zničen v procesu, který se označuje jako *unwinding zásobníku*. V odvíjení zásobníku pokračuje provádění takto:  
  
1.  Ovládací prvek dosáhne příkazu `try` normálním sekvenčním prováděním. Je vykonán v chráněné části v bloku `try`.  
  
2.  Není-li při provádění chráněné části vyvolána žádná výjimka, nejsou provedeny klauzule `catch`, které následují blok `try`. Provádění pokračuje na příkazu za poslední klauzulí `catch`, která následuje přidružený blok `try`.  
  
3.  Je-li v průběhu provádění chráněné části nebo v jakékoli rutině, kterou chráněná část volá přímo nebo nepřímo, vyvolána výjimka, je vytvořen objekt výjimky z objektu vytvořeného pomocí operandu `throw`. (To znamená možné zahrnutí konstruktoru kopie.) V tomto okamžiku bude kompilátor hledat klauzuli `catch` ve vyšším kontextu spuštění, který umožňuje zpracování výjimky vyvolaného typu, nebo vyhledá obslužnou rutinu `catch`, jež umožňuje zpracování jakéhokoli typu výjimky. Obslužné rutiny `catch` jsou zkoumány podle pořadí jejich vzhledu po bloku `try`. Není-li nalezena žádná odpovídající obslužná rutina, je prozkoumán další dynamicky uzavírající blok `try`. Tento proces pokračuje, dokud není prozkoumán vnější uzavírající blok `try`.  
  
4.  Není-li stále nalezena odpovídající obslužná rutina nebo nastane-li výjimka v průběhu procesu odvíjení, avšak před získáním ovládacího prvku obslužnou rutinou, je za běhu zavolána předdefinovaná funkce `terminate`. Dojde-li k výjimce poté, co je vyvolána výjimka, avšak před zahájením procesu odvíjení, je zavolán příkaz `terminate`.  
  
5.  Je-li nalezena odpovídající obslužná rutina `catch` a zachycena na základě hodnoty, její parametr je inicializován zkopírováním objektu výjimky. Je-li zachycena na základě odkazu, je parametr inicializován pro odkázání na objekt výjimky. Po inicializaci parametru je zahájen proces odvíjení zásobníku. To zahrnuje zničení všech automatických objektů, které byly plně sestaveny – avšak nebyly dosud zničeny – mezi začátkem bloku `try`, jenž je spojen s obslužnou rutinou `catch`, a oblastí vyvolání výjimky. Zničení nastane v obráceném pořadí vytvoření. Spustí se obslužná rutina `catch` a program pokračuje v provádění po poslední obslužné rutině – tedy po prvním příkazu nebo konstrukci, která není obslužnou rutinou `catch`. Ovládací prvek může vstoupit do obslužné rutiny `catch` skrze vyvolanou výjimku, nikdy ne skrze příkaz `goto` nebo skrze popisek `case` v příkazu `switch`.  
  
## <a name="stack-unwinding-example"></a>Příklad odvíjení zásobníku  
 Následující příklad ukazuje odvíjení zásobníku po vyvolání výjimky. Spuštění ve vlákně přejde z příkazu throw v `C` k příkazu catch v `main` a odvine každou funkci, na kterou narazí. Všimněte si pořadí, v jakém jsou objekty `Dummy` vytvářeny a následně zničeny při mizení z rozsahu. Všimněte si také, že žádná funkce není dokončena, s výjimkou funkce `main`, která obsahuje příkaz catch. Funkce `A` se nikdy nevrátí ze svého volání `B()` a `B` se nikdy vrátí ze svého volání `C()`. Po odstranění komentářů řádku definice ukazatele `Dummy` a odpovídajícího příkazu odstranění a po následném spuštění programu si všimněte, že ukazatel není nikdy odstraněn. To ukazuje, co se může stát, když funkce neposkytují záruku výjimky. Další informace naleznete v tématu Postup: Návrh výjimek. Zakomentováním příkazu catch lze sledovat, co se stane, když program skončí kvůli neošetřené výjimce.  
  
```  
#include <string>  
#include <iostream>  
using namespace std;  
  
class MyException{};  
class Dummy  
{  
    public:  
    Dummy(string s) : MyName(s) { PrintMsg("Created Dummy:"); }  
    Dummy(const Dummy& other) : MyName(other.MyName){ PrintMsg("Copy created Dummy:"); }  
    ~Dummy(){ PrintMsg("Destroyed Dummy:"); }  
    void PrintMsg(string s) { cout << s  << MyName <<  endl; }  
    string MyName;   
    int level;  
};  
  
void C(Dummy d, int i)  
{   
    cout << "Entering FunctionC" << endl;  
    d.MyName = " C";  
    throw MyException();     
  
    cout << "Exiting FunctionC" << endl;  
}  
  
void B(Dummy d, int i)  
{  
    cout << "Entering FunctionB" << endl;  
    d.MyName = "B";  
    C(d, i + 1);     
    cout << "Exiting FunctionB" << endl;   
}  
  
void A(Dummy d, int i)  
{   
    cout << "Entering FunctionA" << endl;  
    d.MyName = " A" ;  
  //  Dummy* pd = new Dummy("new Dummy"); //Not exception safe!!!  
    B(d, i + 1);  
 //   delete pd;   
    cout << "Exiting FunctionA" << endl;     
}  
  
int main()  
{  
    cout << "Entering main" << endl;  
    try  
    {  
        Dummy d(" M");  
        A(d,1);  
    }  
    catch (MyException& e)  
    {  
        cout << "Caught an exception of type: " << typeid(e).name() << endl;  
    }  
  
    cout << "Exiting main." << endl;  
    char c;  
    cin >> c;  
}  
  
/* Output:  
    Entering main  
    Created Dummy: M  
    Copy created Dummy: M  
    Entering FunctionA  
    Copy created Dummy: A  
    Entering FunctionB  
    Copy created Dummy: B  
    Entering FunctionC  
    Destroyed Dummy: C  
    Destroyed Dummy: B  
    Destroyed Dummy: A  
    Destroyed Dummy: M  
    Caught an exception of type: class MyException  
    Exiting main.  
  
*/  
  
```