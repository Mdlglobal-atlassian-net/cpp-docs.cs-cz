---
title: Obory názvů (C++) | Dokumentace Microsoftu
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
ms.openlocfilehash: 5a68a0a67748e79fe4379cb5f820cca0c845f392
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39405480"
---
# <a name="namespaces-c"></a>Obory názvů (C++)
Obor názvů je deklarativní oblast, která nabízí obor na identifikátory (názvy typů, funkce, proměnné atd) uvnitř. Obory názvů slouží k uspořádání kódu do logických skupin a zabránit kolize názvů, které mohou nastat, zejména v případě, že vašeho základu kódu obsahuje více knihoven. Všechny identifikátory v oboru názvů jsou navzájem viditelné bez kvalifikace. Identifikátory mimo obor názvů, můžete přistupovat ke členům pomocí plně kvalifikovaný název pro jednotlivé identifikátory, třeba `std::vector<std::string> vec;`, nebo podle [using – deklarace](../cpp/using-declaration.md) pro jednoho identifikátoru (`using std::string`), nebo [direktiva using](../cpp/namespaces-cpp.md#using_directives) pro všechny identifikátory v oboru názvů (`using namespace std;`). Kód v souborech hlaviček vždy používejte plně kvalifikovaný obor názvů.  
  
 Následující příklad ukazuje deklaraci oboru názvů a tři způsoby, tento kód mimo obor názvů, můžete přistupuje k jejich členy.  
  
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
  
 Použít, a s použitím deklarace převeďte do rozsahu jednoho identifikátoru:  
  
```cpp  
using ContosoData::ObjectManager;  
ObjectManager mgr;  
mgr.DoSomething();  
```  
  
 Použít using – direktiva všechno, co vám v oboru názvů do oboru:  
  
```cpp  
using namespace ContosoData;
  
ObjectManager mgr;  
mgr.DoSomething();  
Func(mgr);  
```  
  
## <a id="using_directives"></a> direktivy using  
 **Pomocí** – direktiva umožňuje použití všech názvů v **obor názvů** bez *název oboru názvů* jako explicitního kvalifikátoru. Použijte sadu pomocí direktivy v souboru implementace (tj. *.cpp), pokud používáte několik různých identifikátorů v oboru názvů; Pokud používáte pouze jeden nebo dva identifikátory, zvažte using deklarace pouze přenést tyto identifikátory do oboru a ne všechny identifikátory v oboru názvů. Pokud má lokální proměnná stejný název jako proměnná oboru názvů, je proměnná oboru názvů skryta. Jedná se o chybu, pokud má proměnná oboru názvů stejný název jako globální proměnná.  
  
> [!NOTE]
>  Using – direktiva mohou být umístěny v horní části souboru s příponou .cpp (v oboru souboru), nebo uvnitř definice třídy nebo funkce.  
>   
>  Obecně platí, vyhněte se vložení pomocí direktivy v hlavičkových souborech (* .h) vzhledem k tomu, že každý soubor, který obsahuje tuto hlavičku přinese všechno, co v oboru názvů do oboru, které můžou způsobovat skrývání názvů a názvů kolizí problémy, které jsou velmi obtížné ladit. Vždy používejte plně kvalifikované názvy v záhlaví souboru. Pokud se zobrazí názvy příliš dlouhý, můžete zkrátit je alias oboru názvů. (Viz níže).  
  
## <a name="declaring-namespaces-and-namespace-members"></a>Deklarace oborů názvů a názvů členů  
 Obvykle deklarujte obor názvů v souboru hlaviček. Pokud vaše implementace funkce jsou v samostatném souboru, pak kvalifikovat názvy funkcí, jako v následujícím příkladu.  
  
```cpp  
//contosoData.h   
#pragma once  
namespace ContosoDataServer  
{  
    void Foo();  
    int Bar();  
}  
```  
  
 Implementace funkce v contosodata.cpp by měl použít plně kvalifikovaný název, i v případě, že umístíte **pomocí** direktiv v horní části souboru:  
  
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
  
 Obor názvů lze deklarovat ve více blocích v jednom souboru a ve více souborech. Kompilátor připojí části společně během předběžného zpracování a výsledný obor názvů obsahuje všechny členy deklarované ve všech částech. Příkladem je obor názvů std, který je deklarován v každém ze souborů záhlaví ve standardní knihovně.  
  
 Členy pojmenovaného oboru názvů lze definovat mimo obor názvů, ve kterém jsou deklarovány pomocí explicitní kvalifikace definovaného názvu. Definice však musí vyskytovat za deklarací v oboru názvů, který obklopuje obor názvů deklarace. Příklad:  
  
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
  
 Této chybě může dojít, pokud obor názvů členů jsou deklarovány napříč více souborů záhlaví a nezahrnuli jste těchto záhlaví ve správném pořadí.  
  
## <a name="the-global-namespace"></a>Globální obor názvů  
 Pokud není identifikátor deklarovaný v explicitní obor názvů, je součástí implicitní globální obor názvů. Obecně platí, snažte se vyhnout prohlášení v globálním oboru, pokud je to možné, s výjimkou vstupní bod [hlavní funkci](../c-language/main-function-and-program-execution.md), které musí být v globálním oboru názvů. Pro explicitní kvalifikaci globálního identifikátoru, použijte operátor rozlišení rozsahu bez názvu jako v `::SomeFunction(x);`. To bude rozlišovat identifikátor z ničeho se stejným názvem v jiné oboru názvů a vám také pomůže snadněji ostatním uživatelům pochopit, aby váš kód.  
  
## <a name="the-std-namespace"></a>Obor názvů std  
 Všechny typy standardní knihovny C++ a funkce jsou deklarovány v `std` oboru názvů nebo obory názvů vnořit do `std`.  
  
## <a name="nested-namespaces"></a>Vnořené obory názvů  
 Mohou být vnořené obory názvů. Je běžné vnořené obory názvů nekvalifikované přístup k členům svého nadřazeného objektu, ale členové nadřazené nemají nekvalifikované přístup k vnořené oboru názvů (Pokud je deklarovaná jako inline), jak je znázorněno v následujícím příkladu:  
  
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
  
 Běžné vnořené obory názvů lze použít k zapouzdření podrobnosti interní implementace, které nejsou součástí veřejného rozhraní nadřazený obor názvů.  
  
## <a name="inline-namespaces-c-11"></a>Pomocí vložených oborů názvů (C++ 11)  
 Na rozdíl od běžných vnořené oboru jsou členy oboru názvů vloženého považovány za členy nadřazený obor názvů. Tato vlastnost umožňuje vyhledávání závislé argument týkající se přetížených funkcí pro práci na funkcích, které mají přetížení v nadřazený a vnořený vložené oboru názvů. Také umožňuje deklarovat v oboru nadřazené šablony, která je deklarována v oboru názvů vložené specializace. Následující příklad ukazuje, jak externí kód váže k oboru názvů vloženého ve výchozím nastavení:  
  
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
  
 Následující příklad ukazuje, jak je možné deklarovat jako specializaci té v nadřazené šablony, která je deklarována v oboru názvů vloženého:  
  
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
  
 Pomocí vložených oborů názvů jako mechanismus správy verzí můžete spravovat změny veřejné rozhraní knihovny. Můžete například vytvořit jeden nadřazený obor názvů a zapouzdřují jednotlivé verze rozhraní v svůj vlastní obor názvů, vnořené uvnitř nadřazeného objektu. Obor názvů, který obsahuje verzi nejnovějšího nebo upřednostňované je kvalifikován jako vložený a proto je vystavena jako by šlo přímým členem nadřazený obor názvů. Klientský kód, který vyvolá Parent::Class bude automaticky svázán s novým kódem. Klienti, kteří dávají přednost používání starší verze k němu přístup pomocí plně kvalifikovanou cestu k vnořené oboru názvů, který má tento kód.  
  
 Klíčové slovo inline se musí použít pro první deklaraci oboru názvů v jednotce kompilace.  
  
 Následující příklad ukazuje dvě verze rozhraní, každá do vnořené oboru názvů. `v_20` Má některé změny z oboru názvů `v_10` rozhraní a je označen jako vložené. Klientský kód, který používá novou knihovnu a volání `Contoso::Funcs::Add` vyvolá v_20 verze. Kód, který se pokusí volat `Contoso::Funcs::Divide` teď získají chybu v době kompilace. Pokud je opravdu nutné tuto funkci, můžete stále přistupují `v_10` verze explicitně voláním `Contoso::v_10::Funcs::Divide`.  
  
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
  
## <a id="namespace_aliases"></a> Aliasy Namespace  
 Názvy Namespace musí být jedinečný, což znamená, že často neměly by být moc krátký. Pokud délka názvu je kód obtížné číst, nebo je únavné na typ v hlavičkovém souboru, kde direktiv using nelze použít, pak můžete provádět aliasem oboru názvů, která slouží jako zkratka pro skutečný název. Příklad:  
  
```cpp  
namespace a_very_long_namespace_name { class Foo {}; }  
namespace AVLNN = a_very_long_namespace_name;  
void Bar(AVLNN::Foo foo){ }  
```  
  
## <a name="anonymous-or-unnamed-namespaces"></a>anonymní nebo nepojmenované obory názvů  
 Můžete vytvořit explicitní obor názvů, ale ne pojmenujte ho:  
  
```cpp  
namespace  
{  
    int MyFunc(){}  
}  
```  
  
 To se označuje jako obor názvů služby Nepojmenovaná nebo anonymní, a to je užitečné, když chcete skrytí deklarace proměnných kódu v jiných souborech (tedy můžete svým uživatelům umožnit vnitřní propojení) bez nutnosti vytvářet pojmenovaného oboru názvů. Veškerý kód ve stejném souboru můžete zobrazit identifikátory v nepojmenovaného oboru názvů ale identifikátory, spolu s oboru názvů, nejsou viditelné mimo tento soubor, nebo přesněji mimo jednotky překladu.  
  
## <a name="see-also"></a>Viz také:  
 [Deklarace a definice](declarations-and-definitions-cpp.md)