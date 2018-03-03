---
title: Friend (C++) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- friend_cpp
dev_langs:
- C++
helpviewer_keywords:
- member access, from friend functions
- friend classes [C++]
- friend keyword [C++]
ms.assetid: 8fe9ee55-d56f-40cd-9075-d9fb1375aff4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 46caba9230676e30cde02e31cc231d606f446767
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="friend-c"></a>friend (C++)
V některých případech je pohodlnější k udělení přístupu na úrovni člena na funkce, které nejsou členy třídy, nebo pro všechny členy v samostatné třídy. Pouze implementátor třída můžou deklarovat kdo jsou jeho přáteli. Funkce nebo třída nelze samotné deklarovat jako přítele libovolné třídy. V definici třídy, použijte `friend` – klíčové slovo a název třetí funkce nebo jiná třída jí udělit přístup k privátním a chráněné členy vaší třídy.         V definici šablony může být parametr typu deklarované jako přítele.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class friend F  
friend F;  
```  
  
## <a name="friend-declarations"></a>Friend – deklarace  
 Je-li deklarována přátelská funkce, která předtím deklarována nebyla, je tato funkce exportována do ohraničujícího netřídního oboru.  
  
 Funkce deklarované v rámci přátelské deklarace jsou brány, jako kdyby byly deklarovány klíčovým slovem `extern`. (Další informace o `extern`, najdete v části [statické specifikátory třídy úložiště](http://msdn.microsoft.com/en-us/3ba9289a-a412-4a17-b319-ceb2c087df48).)  
  
 Přestože lze funkce s globálním rozsahem deklarovat jako přátelské s předností před jejich prototypy, nelze členské funkce deklarovat jako přátelské před objevením deklarace jejich úplné třídy. Následující kód ukazuje důvod selhání:  
  
```cpp  
class ForwardDeclared;   // Class name is known.  
class HasFriends  
{  
    friend int ForwardDeclared::IsAFriend();   // C2039 error expected  
};  
```  
  
 Předchozí příklad zadá do rozsahu název třídy `ForwardDeclared`, ale úplná deklarace – konkrétně část deklarující funkci `IsAFriend` – není známa. Proto deklarace `friend` ve třídě `HasFriends` vygeneruje chybu.  
  
 Počínaje C ++ 11, existují dvě formy friend – deklarace pro třídu:  
  
```cpp  
friend class F;  
friend F;  
```  
  
 První formulář zavádí novou třídu F, pokud neexistuje žádná existující třída tímto názvem byla nalezena v oboru názvů nejvnitřnější.  **C ++ 11**: druhý formulář nezavádí nové třídy; lze použít, pokud třída již byl deklarován a při deklarující typ parametru šablony nebo typedef jako přítele musí použít.  
  
 Použití `class friend F` při nebyla odkazovaného typu ještě deklarována:  
  
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
  
 V následujícím příkladu `friend F` odkazuje `F` třídu, která je mimo rozsah NS deklarován.  
  
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
  
 Použití `friend F` deklarovat jako přítele parametru šablony:  
  
```cpp  
template <typename T>  
class my_class  
{  
    friend T;  
    //...  
};  
```  
  
 Použití `friend F` deklarovat typedef jako friend:  
  
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
 Funkce `friend` je funkce, která není členem třídy, ale má přístup k soukromým a chráněným členům třídy. Spřátelené funkce nejsou považovány za členy třídy. Jsou to normální externí funkce, kterým jsou přiřazena zvláštní přístupová oprávnění. Přátel nejsou v oboru třídy a jejich nejsou volat pomocí operátory výběru členů (**.** a -**>**) Pokud jsou členy jiné třídy. Funkce `friend` je deklarována pomocí třídy, která uděluje přístup. Deklarace `friend` může být umístěna kdekoli v deklaraci třídy. Není ovlivněna klíčovými slovy řízení přístupu.  
  
 Následující příklad ukazuje třídu `Point` a spřátelenou funkci `ChangePrivate`. Funkce `friend` má přístup ke členu soukromých dat objektu `Point`, který přijímá jako parametr.  
  
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
  
## <a name="class-members-as-friends"></a>Členy třídy jako friends  
 Členské funkce třídy mohou být v jiných třídách deklarovány jako přátelské funkce. Podívejte se na následující příklad:  
  
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
  
 V předchozím příkladu je do třídy `A::Func1( B& )` udělen přátelský přístup pouze funkci `B`. Proto přístup privátního člena `_b` správné v `Func1` třídy `A` , ale ne v `Func2`.  
  
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
  
 Spravovaný typ nemůže mít jakékoli přátelské funkce, přátelské třídy nebo přátelská rozhraní.  
  
 Přátelství není zděděno, což znamená, že třídy odvozené z `YourOtherClass` nemohou získat přístup k soukromým členům `YourClass`. Přátelství není přenosné, takže třídy, které jsou přátelé `YourOtherClass`, nemohou získat přístup k soukromým členům `YourClass`.  
  
 Následující obrázek znázorňuje čtyři deklarace třídy: `Base`, `Derived`, `aFriend` a `anotherFriend`. Pouze třída `aFriend` má přímý přístup k soukromým členům `Base` (a ke všem členům, které byly zděděny `Base`).  
  
 ![Důsledky friend vztah](../cpp/media/vc38v41.gif "vc38V41")  
Důsledky přátelské relace  
  
## <a name="inline-friend-definitions"></a>Definice vloženého friend  
 Spřátelené funkce lze definovat uvnitř deklarací tříd. Tyto funkce jsou vložené funkce a chovají se podobně jako vložené členské funkce, jako by byly definovány ihned po zjištění členů třídy, ale ještě před uzavřením oboru třídy (konec deklarace třídy).  
  
 Spřátelené funkce definované uvnitř deklarací třídy nejsou v rozsahu považovány za nadřazené třídy. Jsou v rozsahu souboru.  
  
## <a name="see-also"></a>Viz také  
 [Klíčová slova](../cpp/keywords-cpp.md)