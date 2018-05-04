---
title: Obory názvů (C++) | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2017
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- namespace_CPP
- using_CPP
dev_langs:
- C++
helpviewer_keywords:
- namespaces [C++], C++
- namespaces [C++]
- namespaces [C++], global
- global namespace
- Visual C++, namespaces
ms.assetid: d1a5a9ab-1cad-47e6-a82d-385bb77f4188
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aac72a23e50ca3bc6d5b737d533bd11a40ed9da3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="namespaces-c"></a>Obory názvů (C++)
Obor názvů je deklarativní oblasti, která poskytuje obor na identifikátory (názvy typů, funkce, proměnné atd) uvnitř ho. Obory názvů se používají k uspořádání kódu do logických skupin a aby se zabránilo kolize názvů, které můžou nastat, zejména v případě, že vaše základu kódu obsahuje více knihoven. Všechny identifikátory v oboru názvů jsou viditelné na sebe navzájem bez kvalifikace. Identifikátory mimo obor názvů přístup pomocí plně kvalifikovaný název pro každý identifikátor, například členové `std::vector<std::string> vec;`, nebo pomocí [pomocí deklarace](../cpp/using-declaration.md) pro jediný identifikátor (`using std::string`), nebo [using – direktiva](../cpp/namespaces-cpp.md#using_directives) pro všechny identifikátory v oboru názvů (`using namespace std;`). Kód v hlavičkových souborů měli vždycky používat obor názvů plně kvalifikovaný název.  
  
 Následující příklad ukazuje deklaraci oboru názvů a tři způsoby, které code mimo obor názvů můžete přistupuje k jejich členové.  
  
```cpp  
namespace ContosoData  
{      
    class ObjectManager   
    {  
    public:  
        void DoSomething() {}  
    };  
    void Func(ObjectManager) {}  
}  
```  
  
 Použijte plně kvalifikovaný název:  
  
```cpp  
ContosoData::ObjectManager mgr;  
mgr.DoSomething();  
ContosoData::Func(mgr);  
```  
  
 Použít, pomocí deklarace tím jeden identifikátor do rozsahu:  
  
```cpp  
using ContosoData::ObjectManager;  
ObjectManager mgr;  
mgr.DoSomething();  
  
```  
  
 Direktivu using – direktiva tím všechno, co v oboru názvů do oboru:  
  
```cpp  
using namespace ContosoData;
  
ObjectManager mgr;  
mgr.DoSomething();  
Func(mgr);  
  
```  
  
## <a id="using_directives"></a> Pomocí direktiv  
 `using` – Direktiva umožňuje všechny názvy v **obor názvů** bez *název oboru názvů* jako explicitní kvalifikátor. Použít, pomocí direktiv souboru implementace (tj. *.cpp), pokud používáte několik různých identifikátory v oboru názvů; Pokud používáte pouze jeden nebo dva identifikátory, pak zvažte použití deklarace jenom tím tyto identifikátory do oboru a ne všechny identifikátory v oboru názvů. Pokud má lokální proměnná stejný název jako proměnná oboru názvů, je proměnná oboru názvů skryta. Jedná se o chybu, pokud má proměnná oboru názvů stejný název jako globální proměnná.  
  
> [!NOTE]
>  Using – direktiva mohou být umístěny v horní části souboru sada (v oboru soubor), nebo v definici třídy nebo funkce.  
>   
>  V nepoužívejte pomocí direktiv v záhlaví soubory (* .h) vzhledem k tomu, že všechny soubory, které zahrnuje této hlavičky bude přenést všechno, co v oboru názvů do oboru, který může způsobit skrytí název a názvů kolizí problémy, které jsou velmi obtížné ladění. Vždy používejte plně kvalifikované názvy v záhlaví souboru. Pokud tyto názvy příliš dlouho, můžete tak, aby zkrátil je alias oboru názvů. (Viz níže).  
  
## <a name="declaring-namespaces-and-namespace-members"></a>Deklarace oborů názvů a obor názvů členy  
 Obvykle je deklarovat obor názvů v záhlaví souboru. Pokud vaše implementace funkce v samostatném souboru, potom kvalifikaci názvy funkcí, jako v následujícím příkladu.  
  
```cpp  
//contosoData.h   
#pragma once  
namespace ContosoDataServer  
{  
    void Foo();  
    int Bar();  
  
}  
```  
  
 Implementace funkce v contosodata.cpp měli použít plně kvalifikovaný název, i v případě, že umístíte `using` direktivy v horní části souboru:  
  
```cpp  
#include "contosodata.h"  
using namespace ContosoDataServer;   
  
void ContosoDataServer::Foo() // use fully-qualified name here  
{  
   // no qualification needed for Bar()  
   Bar();   
}  
  
int ContosoDataServer::Bar(){return 0;}  
```  
  
 Obor názvů lze deklarovat ve více bloků v jednom souboru a ve více souborech. Kompilátor připojí části společně při předběžném zpracování a výsledný obor názvů obsahuje všechny členy deklarován ve všech částech. Příkladem je obor názvů – std, který je deklarován v každé z hlavičky souborů ve standardní knihovně.  
  
 Mimo obor názvů, ve které jsou deklarovány pomocí explicitní kvalifikace názvu definovaný lze definovat členy s názvem oboru názvů. Definice však musí být uvedena za bod deklarace v oboru názvů, která obklopuje deklaraci oboru názvů. Příklad:  
  
```cpp  
// defining_namespace_members.cpp  
// C2039 expected  
namespace V {  
        void f();  
    }  
  
    void V::f() { }        // ok  
    void V::g() { }        // C2039, g() is not yet a member of V  
  
    namespace V {  
        void g();  
    }  
}  
```  
  
 Této chybě může dojít, když členů oboru názvů, které jsou deklarovány napříč více hlavičkových souborů a tyto hlavičky nebyly zahrnuty ve správném pořadí.  
  
## <a name="the-global-namespace"></a>Globální obor názvů  
 Pokud identifikátor není deklarován v explicitní oboru názvů, je součástí implicitní globální obor názvů. Obecně platí, pokuste se vyhnout provádění deklarace v globálním oboru, pokud je to možné, s výjimkou vstupní bod [hlavní funkce](../c-language/main-function-and-program-execution.md), které musí být v globálním oboru názvů. Chcete-li explicitně kvalifikaci globální identifikátor, použijte operátor řešení rozsahu bez názvu, jako v `::SomeFunction(x);`. To bude rozlišit identifikátor z ničeho se stejným názvem v jiné oboru názvů, a také vám pomůže snadněji kódu ostatním uživatelům pochopit.  
  
## <a name="the-std-namespace"></a>Obor názvů std  
 Všechny typy standardní knihovny C++ a funkce, které jsou deklarované v `std` obor názvů nebo obory názvů vnořit `std`.  
  
## <a name="nested-namespaces"></a>Vnořené obory názvů  
 Může být vnořené obory názvů. Obyčejnou vnořené obor názvů obsahuje neúplné přístup k nadřazené členy, ale nadřazené členy nemají nekvalifikované přístup k oboru názvů vnořené (Pokud byl deklarován jako vložené), jak je znázorněno v následujícím příkladu:  
  
```cpp  
namespace ContosoDataServer  
{  
    void Foo();   
  
    namespace Details  
    {  
        int CountImpl;  
        void Ban() { return Foo(); }  
    }  
  
    int Bar(){...};  
    int Baz(int i) { return Details::CountImpl; }      
  
}  
```  
  
 Obyčejnou vnořené obory názvů umožňuje zapouzdření podrobnosti interní implementace, které nejsou součástí veřejné rozhraní nadřazeného oboru názvů.  
  
## <a name="inline-namespaces-c-11"></a>Vnořené obory názvů (C++ 11)  
 Na rozdíl od běžných názvů vnořené jsou považovány členů oboru názvů vložené jako členové nadřazené oboru názvů. Tato vlastnost umožňuje argument závislé vyhledávání týkající se přetížených funkcí pro práci na funkce, které mají přetížení v nadřazené a vnořené vložené názvů. Také umožňuje deklarovat specializace v nadřazené oboru názvů pro šablonu, která je deklarován v oboru názvů vložené. Následující příklad ukazuje, jak externí kód váže k oboru názvů vložené ve výchozím nastavení:  
  
```cpp  
//Header.h  
#include <string>  
  
namespace Test  
{  
    namespace old_ns  
    {  
        std::string Func() { return std::string("Hello from old"); }  
    }  
  
    inline namespace new_ns  
    {  
        std::string Func() { return std::string("Hello from new"); }  
    }  
}  
  
#include "header.h"  
#include <string>  
#include <iostream>  
  
int main()  
{  
    using namespace Test;  
    using namespace std;  
  
    string s = Func();  
    std::cout << s << std::endl; // "Hello from new"  
    return 0;  
}  
```  
  
 Následující příklad ukazuje, jak můžou deklarovat specializace v nadřazené šablony, kterou je deklarován v oboru názvů vložené:  
  
```cpp  
namespace Parent  
{  
    inline namespace new_ns  
    {  
         template <typename T>  
         struct C  
         {  
             T member;  
         };  
    }  
     template<>  
     class C<int> {};  
}  
  
```  
  
 Obory názvů vložené jako vhodný mechanismus Správa verzí slouží ke správě změny veřejné rozhraní knihovny. Můžete například vytvořit obor názvů jedné nadřazené a zapouzdřují každou verzi rozhraní v vlastní obor názvů vnořit do nadřazené. Obor názvů, který obsahuje verzi nejnovějšího nebo upřednostňované je kvalifikovaný jako vložené a je proto viditelné, jako by šlo přímým členem nadřazené obor názvů. Kód klienta, která volá Parent::Class automaticky vytvoří vazbu nový kód. Klienti, kteří dávají přednost používání starší verzi stále k němu přístup pomocí plně kvalifikovaná cesta k vnořené obor názvů, který má tento kód.  
  
 Inline – klíčové slovo musí být použita pro první deklaraci oboru názvů v jednotce kompilace.  
  
 Následující příklad ukazuje dvě verze rozhraní, každou v vnořené oboru názvů. `v_20` Má některé změny z oboru názvů `v_10` rozhraní a je označen jako vložené. Kód klienta, který používá novou knihovnu a volání `Contoso::Funcs::Add` bude vyvolání v_20 verze. Kód, který se pokusí zavolat `Contoso::Funcs::Divide` , teď získají chybu v době kompilace. Pokud skutečně potřebují této funkce, stále přístupem `v_10` verze explicitně voláním `Contoso::v_10::Funcs::Divide`.  
  
```cpp  
namespace Contoso  
{  
    namespace v_10  
    {  
        template <typename T>  
        class Funcs  
        {  
        public:  
            Funcs(void);  
            T Add(T a, T b);  
            T Subtract(T a, T b);  
            T Multiply(T a, T b);  
            T Divide(T a, T b);  
        };  
    }  
  
    inline namespace v_20  
    {  
        template <typename T>  
        class Funcs  
        {  
        public:  
            Funcs(void);  
            T Add(T a, T b);  
            T Subtract(T a, T b);  
            T Multiply(T a, T b);  
            std::vector<double> Log(double);  
            T Accumulate(std::vector<T> nums);  
      };  
    }  
}  
  
```  
  
## <a id="namespace_aliases"></a> Namespace aliasy  
 Namespace názvy musí být jedinečné, což znamená, že často nemělo by být moc krátké. Pokud délka názvu je obtížné číst, kódu nebo je zdlouhavé k zadání v záhlaví souboru, kde pomocí direktiv nelze použít, a potom můžete provést alias oboru názvů, který slouží jako zkratkou pro skutečný název. Příklad:  
  
```cpp  
namespace a_very_long_namespace_name { class Foo {}; }  
namespace AVLNN = a_very_long_namespace_name;  
void Bar(AVLNN::Foo foo){ }  
  
```  
  
## <a name="anonymous-or-unnamed-namespaces"></a>anonymní nebo nepojmenované obory názvů  
 Můžete vytvořit explicitní obor názvů, ale není pojmenujte ho:  
  
```cpp  
namespace  
{  
    int MyFunc(){}  
}  
```  
  
 To se označuje jako na obor názvů nepojmenovaný nebo anonymní a je užitečné, pokud chcete nastavit neviditelné kódu deklarace proměnných v další soubory (tj. jim poskytnout vnitřní propojení) bez nutnosti vytvoření s názvem oboru názvů. Všechny kódu ve stejném souboru můžete zobrazit identifikátory v nepojmenované oboru názvů, ale identifikátory, společně s oboru názvů samostatně, nejsou viditelné mimo tento soubor – nebo přesněji mimo překlad jednotku.  
  
## <a name="see-also"></a>Viz také  
 [Deklarace a definice](declarations-and-definitions-cpp.md)
