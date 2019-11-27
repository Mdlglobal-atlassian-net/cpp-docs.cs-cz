---
title: Výjimky a uvolňování zásobníku v jazyce C++
ms.date: 11/19/2019
ms.assetid: a1a57eae-5fc5-4c49-824f-3ce2eb8129ed
ms.openlocfilehash: 11657206e86dbc81eb62c1e11b49fd87777f11d8
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246571"
---
# <a name="exceptions-and-stack-unwinding-in-c"></a>Výjimky a unwinding zásobníku v jazyce C++

V mechanismu výjimek jazyka C++ přesune ovládací prvek příkaz throw na první příkaz catch, který dokáže zpracovat vyvolaný typ. Když je dosaženo příkazu catch, všechny automatické proměnné, které jsou v rozsahu mezi příkazy throw a catch, jsou zničeny v procesu, který se označuje jako uvolnění *zásobníku*. V odvíjení zásobníku pokračuje provádění takto:

1. Ovládací prvek dosáhne příkazu **Try** při normálním sekvenčním provádění. Je proveden chráněný oddíl v bloku **Try** .

1. Pokud není vyvolána žádná výjimka během provádění chráněné části, nejsou provedeny klauzule **catch** , které následují blok **Try** . Provádění pokračuje na příkazu za poslední klauzulí **catch** , která následuje za přidruženým blokem **Try** .

1. Pokud je vyvolána výjimka během provádění chráněné části nebo v jakékoli rutině, kterou chráněný oddíl volá přímo nebo nepřímo, je vytvořen objekt výjimky z objektu, který je vytvořen operandem **throw** . (To znamená, že může být součástí kopírovacího konstruktoru.) V tomto okamžiku kompilátor vyhledá klauzuli **catch** ve vyšším kontextu spuštění, který může zpracovat výjimku typu, který je vyvolána, nebo pro obslužnou rutinu **catch** , která může zpracovat jakýkoli typ výjimky. Obslužné rutiny **catch** jsou zkontrolovány v pořadí podle jejich vzhledu po bloku **Try** . Pokud není nalezena žádná odpovídající obslužná rutina, je prověřen další dynamicky ohraničující blok **Try** . Tento proces pokračuje, dokud není vyšetřen nejvzdálenější ohraničující **testovaný** blok.

1. Není-li stále nalezena odpovídající obslužná rutina nebo nastane-li výjimka v průběhu procesu odvíjení, avšak před získáním ovládacího prvku obslužnou rutinou, je za běhu zavolána předdefinovaná funkce `terminate`. Dojde-li k výjimce poté, co je vyvolána výjimka, avšak před zahájením procesu odvíjení, je zavolán příkaz `terminate`.

1. Pokud je nalezena odpovídající obslužná rutina **catch** a zachytává podle hodnoty, je její formální parametr inicializován zkopírováním objektu Exception. Je-li zachycena na základě odkazu, je parametr inicializován pro odkázání na objekt výjimky. Po inicializaci parametru je zahájen proces odvíjení zásobníku. To zahrnuje zničení všech automatických objektů, které byly plně sestaveny, ale dosud nedošlo ke zrušení struktury – mezi začátkem bloku **Try** , který je přidružen k obslužné rutině **catch** , a s vyvoláním webu výjimky. Zničení nastane v obráceném pořadí vytvoření. Obslužná rutina **catch** se spustí a program pokračuje v provádění po poslední obslužné rutině – to znamená v prvním příkazu nebo konstruktoru, který není obslužným rutinou **catch** . Ovládací prvek může zadat pouze obslužnou rutinu **catch** prostřednictvím vyvolané výjimky, nikdy neprostřednictvím příkazu **goto** nebo popisku **case** v příkazu **Switch** .

## <a name="stack-unwinding-example"></a>Příklad zrušení zásobníku

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
