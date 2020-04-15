---
title: friend (C++)
ms.date: 07/15/2019
f1_keywords:
- friend_cpp
helpviewer_keywords:
- member access, from friend functions
- friend classes [C++]
- friend keyword [C++]
ms.assetid: 8fe9ee55-d56f-40cd-9075-d9fb1375aff4
ms.openlocfilehash: 20116674feffaa5b4bbddf707dd3a4d0c1d9ad98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364434"
---
# <a name="friend-c"></a>friend (C++)

V některých případech je vhodnější udělit přístup na úrovni člena k funkcím, které nejsou členy třídy nebo všem členům v samostatné třídě. Pouze implementátor třídy může deklarovat, kdo jsou jeho přátelé. Funkce nebo třída se nemůže deklarovat jako přítel jakékoli třídy. V definici třídy použijte klíčové slovo **friend** a název funkce bez člena nebo jiné třídy, abyste mu udělili přístup k soukromým a chráněným členům vaší třídy. V definici šablony může být parametr typu deklarován jako přítel.

## <a name="syntax"></a>Syntaxe

```
class friend F
friend F;
```

## <a name="friend-declarations"></a>Prohlášení přátel

Je-li deklarována přátelská funkce, která předtím deklarována nebyla, je tato funkce exportována do ohraničujícího netřídního oboru.

Funkce deklarované v deklaraci přítele jsou považovány za, jako by byly deklarovány pomocí klíčového slova **extern.** Další informace naleznete [v tématu extern](extern-cpp.md).

Přestože lze funkce s globálním rozsahem deklarovat jako přátelské s předností před jejich prototypy, nelze členské funkce deklarovat jako přátelské před objevením deklarace jejich úplné třídy. Následující kód ukazuje důvod selhání:

```cpp
class ForwardDeclared;   // Class name is known.
class HasFriends
{
    friend int ForwardDeclared::IsAFriend();   // C2039 error expected
};
```

Předchozí příklad zadá do rozsahu název třídy `ForwardDeclared`, ale úplná deklarace – konkrétně část deklarující funkci `IsAFriend` – není známa. Proto deklarace **přítele** `HasFriends` ve třídě generuje chybu.

Počínaje C++ 11 existují dvě formy deklarace friend pro třídu:

```cpp
friend class F;
friend F;
```

První formulář zavádí novou třídu F, pokud nebyla v nejvnitřnějším oboru názvů nalezena žádná existující třída s tímto názvem. **C++11**: Druhý formulář nezavádí novou třídu; lze použít, když třída již byla deklarována a musí být použita při deklarování parametru typu šablony nebo typedef jako přítele.

Použijte, `class friend F` pokud odkazovaný typ ještě nebyl deklarován:

```cpp
namespace NS
{
    class M
    {
        class friend F;  // Introduces F but doesn't define it
    };
}
```

```cpp
namespace NS
{
    class M
    {
        friend F; // error C2433: 'NS::F': 'friend' not permitted on data declarations
    };
}
```

V následujícím příkladu odkazuje `F` na třídu, `friend F` která je deklarována mimo rozsah NS.

```cpp
class F {};
namespace NS
{
    class M
    {
        friend F;  // OK
    };
}
```

Slouží `friend F` k deklarování parametru šablony jako přítele:

```cpp
template <typename T>
class my_class
{
    friend T;
    //...
};
```

Slouží `friend F` k deklarování typedef jako přítele:

```cpp
class Foo {};
typedef Foo F;

class G
{
    friend F; // OK
    friend class F // Error C2371 -- redefinition
};
```

Je-li třeba deklarovat dvě třídy, které jsou navzájem spřáteleny, celá druhá třída musí být zadána jako přátelská třída první třídy. Důvod tohoto omezení je, že kompilátor má dostatek informací pro deklarování jednotlivých přátelských funkcí pouze v případě, kdy je deklarována druhá třída.

> [!NOTE]
> Ačkoli celá druhá třída musí být přátelskou třídou první třídy, je možné vybrat, které funkce první třídy budou přáteli druhé třídy.

## <a name="friend-functions"></a>friend – funkce

Funkce **friend** je funkce, která není členem třídy, ale má přístup k soukromým a chráněným členům třídy. Spřátelené funkce nejsou považovány za členy třídy. Jsou to normální externí funkce, kterým jsou přiřazena zvláštní přístupová oprávnění. Přátelé nejsou v oboru třídy a nejsou voláni pomocí operátorů výběru členů (**.** a**>**- ), pokud nejsou členy jiné třídy. Funkce **friend** je deklarována třídou, která uděluje přístup. Prohlášení **přítele** lze umístit kdekoli v deklaraci třídy. Není ovlivněna klíčovými slovy řízení přístupu.

Následující příklad ukazuje třídu `Point` a spřátelenou funkci `ChangePrivate`. Funkce **friend** má přístup k privátnímu datovému členu objektu, `Point` který obdrží jako parametr.

```cpp
// friend_functions.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class Point
{
    friend void ChangePrivate( Point & );
public:
    Point( void ) : m_i(0) {}
    void PrintPrivate( void ){cout << m_i << endl; }

private:
    int m_i;
};

void ChangePrivate ( Point &i ) { i.m_i++; }

int main()
{
   Point sPoint;
   sPoint.PrintPrivate();
   ChangePrivate(sPoint);
   sPoint.PrintPrivate();
// Output: 0
           1
}
```

## <a name="class-members-as-friends"></a>Členové třídy jako přátelé

Členské funkce třídy mohou být v jiných třídách deklarovány jako přátelské funkce. Uvažujte následující příklad:

```cpp
// classes_as_friends1.cpp
// compile with: /c
class B;

class A {
public:
   int Func1( B& b );

private:
   int Func2( B& b );
};

class B {
private:
   int _b;

   // A::Func1 is a friend function to class B
   // so A::Func1 has access to all members of B
   friend int A::Func1( B& );
};

int A::Func1( B& b ) { return b._b; }   // OK
int A::Func2( B& b ) { return b._b; }   // C2248
```

V předchozím příkladu je do třídy `A::Func1( B& )` udělen přátelský přístup pouze funkci `B`. Proto je přístup k `_b` soukromému `Func1` členu správný ve třídě, `A` ale ne v `Func2`.

Třída `friend` je třída, jejíž všechny členské funkce jsou přátelské funkce třídy, jejíž členské funkce mají přístup k soukromým a chráněným členům jiné třídy. Předpokládejme, že by deklarace `friend` v třídě `B` byla:

```cpp
friend class A;
```

V takovém případě by všem členským funkcím třídy `A` byl udělen přátelský přístup k třídě `B`. Následující kód je příkladem přátelské třídy:

```cpp
// classes_as_friends2.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class YourClass {
friend class YourOtherClass;  // Declare a friend class
public:
   YourClass() : topSecret(0){}
   void printMember() { cout << topSecret << endl; }
private:
   int topSecret;
};

class YourOtherClass {
public:
   void change( YourClass& yc, int x ){yc.topSecret = x;}
};

int main() {
   YourClass yc1;
   YourOtherClass yoc1;
   yc1.printMember();
   yoc1.change( yc1, 5 );
   yc1.printMember();
}
```

Přátelství není vzájemné, pokud není výslovně uvedeno. V předchozím příkladu nemohou členské funkce `YourClass` získat přístup k soukromým členům `YourOtherClass`.

Spravovaný typ (v jazyce C++/CLI) nemůže mít žádné funkce přítele, třídy přátel nebo rozhraní friend.

Přátelství není zděděno, což znamená, že třídy odvozené z `YourOtherClass` nemohou získat přístup k soukromým členům `YourClass`. Přátelství není přenosné, takže třídy, které jsou přátelé `YourOtherClass`, nemohou získat přístup k soukromým členům `YourClass`.

Následující obrázek znázorňuje čtyři deklarace třídy: `Base`, `Derived`, `aFriend` a `anotherFriend`. Pouze třída `aFriend` má přímý přístup k soukromým členům `Base` (a ke všem členům, které byly zděděny `Base`).

![Důsledky přátelského vztahu](../cpp/media/vc38v41.gif "Důsledky přátelského vztahu") <br/>
Důsledky přátelského vztahu

## <a name="inline-friend-definitions"></a>Definice vřádících přátel

Friend funkce mohou být definovány (dané tělo funkce) uvnitř deklarace třídy. Tyto funkce jsou vložené funkce a chovají se podobně jako vložené členské funkce, jako by byly definovány ihned po zjištění členů třídy, ale ještě před uzavřením oboru třídy (konec deklarace třídy). Přítel funkce, které jsou definovány uvnitř deklarace třídy jsou v oboru ohraničující třídy.

## <a name="see-also"></a>Viz také

[Klíčová slova](../cpp/keywords-cpp.md)
