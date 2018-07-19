---
title: Výjimky a uvolnění zásobníku v jazyce C++ | Dokumentace Microsoftu
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
ms.openlocfilehash: 32558413dd0dc6f7288493067d7373a14e520e29
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947696"
---
# <a name="exceptions-and-stack-unwinding-in-c"></a>Výjimky a unwinding zásobníku v jazyce C++
V mechanismu výjimek jazyka C++ přesune ovládací prvek příkaz throw na první příkaz catch, který dokáže zpracovat vyvolaný typ. Pokud je dosažen příkaz catch, všechny automatické proměnné, které jsou v rozsahu mezi throw a catch – příkazy jsou zničeny v procesu, který se označuje jako *odvíjení zásobníku*. V odvíjení zásobníku pokračuje provádění takto:  
  
1.  Ovládací prvek dosáhne **zkuste** příkaz normálním sekvenčním prováděním. Chráněné části v **zkuste** je blok proveden.  
  
2.  Pokud není vyvolána žádná výjimka za běhu chráněné části **catch** klauzule, které následují **zkuste** bloku již nebudou provedeny. Provádění pokračuje na příkazu za poslední **catch** klauzuli, která následuje přidružený **zkuste** bloku.  
  
3.  Pokud je vyvolána výjimka při provádění chráněné části nebo v jakékoli rutině, kterou chráněná část volá přímo nebo nepřímo, je vytvořen objekt výjimky z objektu, který je vytvořen **throw** operand. (To znamená možné zahrnutí konstruktoru kopie.) V tomto okamžiku kompilátor hledá **catch** klauzule ve vyšším kontextu spuštění, který může zpracovat výjimku, která je vyvolána, nebo pro **catch** obslužná rutina, která dokáže zpracovat výjimky libovolného typu. **Catch** obslužné rutiny jsou zkoumány podle pořadí jejich vzhledu po **zkuste** bloku. Pokud je nalezena žádná odpovídající obslužná rutina, další dynamicky uzavírající **zkuste** bloku je zkontrolován. Tento proces pokračuje, dokud prozkoumán vnější uzavírající **zkuste** bloku je zkontrolován.  
  
4.  Není-li stále nalezena odpovídající obslužná rutina nebo nastane-li výjimka v průběhu procesu odvíjení, avšak před získáním ovládacího prvku obslužnou rutinou, je za běhu zavolána předdefinovaná funkce `terminate`. Dojde-li k výjimce poté, co je vyvolána výjimka, avšak před zahájením procesu odvíjení, je zavolán příkaz `terminate`.  
  
5.  Pokud odpovídající **catch** obslužná rutina se nachází a zachycena hodnotou, její parametr je inicializován zkopírováním objektu výjimky. Je-li zachycena na základě odkazu, je parametr inicializován pro odkázání na objekt výjimky. Po inicializaci parametru je zahájen proces odvíjení zásobníku. To zahrnuje zničení všech automatických objektů, které byly plně sestaveny –, ale dosud zničeny – mezi začátkem **zkuste** blok, který je přidružený **catch** obslužné rutiny a Vyvolejte lokality výjimky. Zničení nastane v obráceném pořadí vytvoření. **Catch** obslužná rutina se spustí a program pokračuje v provádění po poslední obslužné rutiny – to znamená, v prvním příkazu nebo konstrukci, která není **catch** obslužné rutiny. Ovládací prvek může vstoupit **catch** obslužná rutina skrze vyvolanou výjimku, nikdy prostřednictvím **goto** příkaz nebo **případ** popisku v **přepnout** příkaz.  
  
## <a name="stack-unwinding-example"></a>Příklad odvíjení zásobníku  
 Následující příklad ukazuje odvíjení zásobníku po vyvolání výjimky. Spuštění ve vlákně přejde z příkazu throw v `C` k příkazu catch v `main` a odvine každou funkci, na kterou narazí. Všimněte si pořadí, v jakém jsou objekty `Dummy` vytvářeny a následně zničeny při mizení z rozsahu. Všimněte si také, že žádná funkce není dokončena, s výjimkou funkce `main`, která obsahuje příkaz catch. Funkce `A` se nikdy nevrátí ze svého volání `B()` a `B` se nikdy vrátí ze svého volání `C()`. Po odstranění komentářů řádku definice ukazatele `Dummy` a odpovídajícího příkazu odstranění a po následném spuštění programu si všimněte, že ukazatel není nikdy odstraněn. To ukazuje, co se může stát, když funkce neposkytují záruku výjimky. Další informace naleznete v tématu Postup: Návrh výjimek. Zakomentováním příkazu catch lze sledovat, co se stane, když program skončí kvůli neošetřené výjimce.  
  
```cpp 
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