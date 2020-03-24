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
ms.openlocfilehash: 744d0dcf8aafdfe336db0c49307b8e1756b8cf7f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179923"
---
# <a name="friend-c"></a>friend (C++)

V některých případech je pohodlnější udělit přístup na úrovni členů funkcím, které nejsou členy třídy ani všem členům v samostatné třídě. Pouze Implementátor třídy může deklarovat, kdo má své přátele. Funkce nebo třída nemůže deklarovat sebe sama jako přítele libovolné třídy. V definici třídy použijte klíčové slovo **Friend** a název nečlenské funkce nebo jiné třídy, čímž udělíte přístup k soukromým a chráněným členům vaší třídy. V definici šablony může být parametr typu deklarován jako Friend.

## <a name="syntax"></a>Syntaxe

```
class friend F
friend F;
```

## <a name="friend-declarations"></a>Deklarace typu Friend

Je-li deklarována přátelská funkce, která předtím deklarována nebyla, je tato funkce exportována do ohraničujícího netřídního oboru.

Funkce deklarované v deklaraci typu Friend jsou považovány za, jako kdyby byly deklarovány pomocí klíčového slova **extern** . Další informace najdete v tématu [extern](extern-cpp.md).

Přestože lze funkce s globálním rozsahem deklarovat jako přátelské s předností před jejich prototypy, nelze členské funkce deklarovat jako přátelské před objevením deklarace jejich úplné třídy. Následující kód ukazuje důvod selhání:

```cpp
class ForwardDeclared;   // Class name is known.
class HasFriends
{
    friend int ForwardDeclared::IsAFriend();   // C2039 error expected
};
```

Předchozí příklad zadá do rozsahu název třídy `ForwardDeclared`, ale úplná deklarace – konkrétně část deklarující funkci `IsAFriend` – není známa. Proto deklarace **typu Friend** ve třídě `HasFriends` vygeneruje chybu.

Počínaje C++ 11 existují dvě formy deklarací typu Friend pro třídu:

```cpp
friend class F;
friend F;
```

První formulář zavádí novou třídu F, pokud v nejvnitřnějším oboru názvů nebyla nalezena žádná existující třída s tímto názvem. **C++ 11**: druhá forma nezavádí novou třídu; dá se použít, když už je třída deklarovaná, a musí se použít při deklaraci parametru typu šablony nebo typedef jako přítele.

Použijte `class friend F`, když odkazovaný typ ještě není deklarovaný:

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

V následujícím příkladu `friend F` odkazuje na `F` třídu, která je deklarována mimo obor NS.

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

Použijte `friend F` k deklaraci parametru šablony jako přítele:

```cpp
template <typename T>
class my_class
{
    friend T;
    //...
};
```

Použijte `friend F` k deklaraci typedef jako přítele:

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
>  Ačkoli celá druhá třída musí být přátelskou třídou první třídy, je možné vybrat, které funkce první třídy budou přáteli druhé třídy.

## <a name="friend-functions"></a>friend – funkce

Funkce **Friend** je funkce, která není členem třídy, ale má přístup k soukromým a chráněným členům třídy. Spřátelené funkce nejsou považovány za členy třídy. Jsou to normální externí funkce, kterým jsou přiřazena zvláštní přístupová oprávnění. Přátelé nejsou v oboru třídy a nejsou voláni pomocí operátorů výběru členů ( **.** a- **>** ), pokud nejsou členy jiné třídy. Funkce **Friend** je deklarována třídou, která uděluje přístup. Deklaraci **typu Friend** lze umístit kdekoli v deklaraci třídy. Není ovlivněna klíčovými slovy řízení přístupu.

Následující příklad ukazuje třídu `Point` a spřátelenou funkci `ChangePrivate`. Funkce **Friend** má přístup k soukromému datovému členu objektu `Point`, který přijímá jako parametr.

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

## <a name="class-members-as-friends"></a>Členy třídy jako přátelé

Členské funkce třídy mohou být v jiných třídách deklarovány jako přátelské funkce. Vezměte v úvahu v následujícím příkladu:

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

V předchozím příkladu je do třídy `A::Func1( B& )` udělen přátelský přístup pouze funkci `B`. Proto je přístup k privátnímu členu `_b` správný v `Func1` třídy `A`, ale ne v `Func2`.

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

Spravovaný typ (v C++/CLI) nemůže mít žádné funkce Friend, třídy Friend ani Friend.

Přátelství není zděděno, což znamená, že třídy odvozené z `YourOtherClass` nemohou získat přístup k soukromým členům `YourClass`. Přátelství není přenosné, takže třídy, které jsou přátelé `YourOtherClass`, nemohou získat přístup k soukromým členům `YourClass`.

Následující obrázek znázorňuje čtyři deklarace třídy: `Base`, `Derived`, `aFriend` a `anotherFriend`. Pouze třída `aFriend` má přímý přístup k soukromým členům `Base` (a ke všem členům, které byly zděděny `Base`).

![Důsledky typu Friend Relationship](../cpp/media/vc38v41.gif "Důsledky typu Friend Relationship") <br/>
Důsledky typu Friend Relationship

## <a name="inline-friend-definitions"></a>Vložené Friend – definice

V deklaracích třídy lze definovat funkce typu Friend (předané tělo funkce). Tyto funkce jsou vložené funkce a chovají se podobně jako vložené členské funkce, jako by byly definovány ihned po zjištění členů třídy, ale ještě před uzavřením oboru třídy (konec deklarace třídy). Funkce Friend definované uvnitř deklarací tříd jsou v oboru ohraničující třídy.

## <a name="see-also"></a>Viz také

[Klíčová slova](../cpp/keywords-cpp.md)
