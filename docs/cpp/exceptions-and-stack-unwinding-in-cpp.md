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

V mechanismu výjimek jazyka C++ přesune ovládací prvek příkaz throw na první příkaz catch, který dokáže zpracovat vyvolaný typ. When the catch statement is reached, all of the automatic variables that are in scope between the throw and catch statements are destroyed in a process that is known as *stack unwinding*. V odvíjení zásobníku pokračuje provádění takto:

1. Control reaches the **try** statement by normal sequential execution. The guarded section in the **try** block is executed.

1. If no exception is thrown during execution of the guarded section, the **catch** clauses that follow the **try** block are not executed. Execution continues at the statement after the last **catch** clause that follows the associated **try** block.

1. If an exception is thrown during execution of the guarded section or in any routine that the guarded section calls either directly or indirectly, an exception object is created from the object that is created by the **throw** operand. (This implies that a copy constructor may be involved.) At this point, the compiler looks for a **catch** clause in a higher execution context that can handle an exception of the type that is thrown, or for a **catch** handler that can handle any type of exception. The **catch** handlers are examined in order of their appearance after the **try** block. If no appropriate handler is found, the next dynamically enclosing **try** block is examined. This process continues until the outermost enclosing **try** block is examined.

1. Není-li stále nalezena odpovídající obslužná rutina nebo nastane-li výjimka v průběhu procesu odvíjení, avšak před získáním ovládacího prvku obslužnou rutinou, je za běhu zavolána předdefinovaná funkce `terminate`. Dojde-li k výjimce poté, co je vyvolána výjimka, avšak před zahájením procesu odvíjení, je zavolán příkaz `terminate`.

1. If a matching **catch** handler is found, and it catches by value, its formal parameter is initialized by copying the exception object. Je-li zachycena na základě odkazu, je parametr inicializován pro odkázání na objekt výjimky. Po inicializaci parametru je zahájen proces odvíjení zásobníku. This involves the destruction of all automatic objects that were fully constructed—but not yet destructed—between the beginning of the **try** block that is associated with the **catch** handler and the throw site of the exception. Zničení nastane v obráceném pořadí vytvoření. The **catch** handler is executed and the program resumes execution after the last handler—that is, at the first statement or construct that is not a **catch** handler. Control can only enter a **catch** handler through a thrown exception, never through a **goto** statement or a **case** label in a **switch** statement.

## <a name="stack-unwinding-example"></a>Stack unwinding example

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
