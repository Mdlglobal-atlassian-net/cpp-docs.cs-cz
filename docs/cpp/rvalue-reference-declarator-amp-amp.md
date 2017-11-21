---
title: "Deklarátor odkazu rvalue: &amp; &amp; | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '&&'
dev_langs: C++
helpviewer_keywords: '&& rvalue reference declarator'
ms.assetid: eab0ce3a-c5a3-4992-aa70-6a8ab1f7491d
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8d0595078c9515c5c705a1cbfb1ed6b5e55db788
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="rvalue-reference-declarator-ampamp"></a>Deklarátor odkazu hodnoty R:&amp;&amp;
Obsahuje odkaz na rvalue výrazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
type-id && cast-expression  
```  
  
## <a name="remarks"></a>Poznámky  
 Odkazy rvalue umožňují rozlišit lvalue z rvalue. Odkazy lvalue a rvalue odkazy jsou syntakticky a sémanticky podobné, ale jejich postupujte podle poněkud odlišná pravidla. Další informace o hodnoty lvalue a rvalue najdete v tématu [hodnoty lvalue a rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md). Další informace o lvalue odkazů najdete v tématu [deklarátor odkazu Lvalue: &](../cpp/lvalue-reference-declarator-amp.md).  
  
 Následující části popisují, jak odkazy rvalue podporují implementace *přesunout sémantiku* a *ideální předávání*.  
  
## <a name="move-semantics"></a>Přesunutí sémantiky  
 Odkazy rvalue podporu implementace *přesunout sémantiku*, což může značně zvýšit výkon aplikací. Přesun sémantiku umožňuje psát kód, který přenese prostředky (například dynamicky přidělené paměti) z jednoho objektu na jiný. Přesun sémantiku funguje, protože umožňuje prostředky, které se mají přenést z dočasné objekty, které nelze odkazovat na jiném místě v programu.  
  
 Chcete-li implementovat sémantiku přesunutí, je obvykle zadat *přesunout konstruktoru,* a volitelně operátor přiřazení move (`operator=`), ke třídě. Operace kopírování a přiřazení, jejichž zdroje jsou rvalue pak automaticky využít přesunout sémantiku. Na rozdíl od výchozí konstruktor copy kompilátor neposkytuje výchozí konstruktor move. Další informace o tom, jak psát konstruktor move a způsobu jeho použití v aplikaci najdete v tématu [přesunout konstruktory a operátory přesunout přiřazení (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md).  
  
 Můžete také přetížení obyčejnou funkcí a operátory využívat výhod přesunout sémantiku. Visual C++ 2010 zavádí sémantiku přesunout do standardní knihovny C++. Například `string` třída implementuje operace, které provádět sémantiku move. Podívejte se na následující příklad, který zřetězí několik řetězec a vytiskne výsledek:  
  
```  
// string_concatenation.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <string>  
using namespace std;  
  
int main()  
{  
   string s = string("h") + "e" + "ll" + "o";  
   cout << s << endl;  
}  
```  
  
 Před Visual C++ 2010 každé volání do `operator+` přiděluje a vrátí nové dočasného `string` objektu (rvalue). `operator+`jeden řetězec na druhý nelze připojit, protože nemůže určit, zda jsou hodnoty lvalue a rvalue řetězce zdrojů. Pokud obě hodnoty lvalue řetězce zdrojů se může odkazovat v programu a proto nesmí změnit. Pomocí odkazů rvalue `operator+` můžete upravit tak, aby trvat rvalue, který nelze odkazovat na jiném místě v programu. Proto `operator+` můžete nyní připojit jeden řetězec na jiný. To může výrazně snížit počet přidělených dynamickou paměť, `string` třída musí provést. Další informace o `string` třídy najdete v tématu [basic_string – třída](../standard-library/basic-string-class.md).  
  
 Přesunutí sémantiku také pomáhá při kompilátor nelze použít optimalizaci vrátit hodnotu (RVO) nebo s názvem vrátit hodnotu optimalizace (NRVO). V těchto případech kompilátor volá konstruktor move, pokud ji definuje typ. Další informace o optimalizaci vrátit hodnotu s názvem najdete v tématu [s názvem vrátit hodnotu optimalizace v nástroji Visual C++ 2005](http://go.microsoft.com/fwlink/?LinkId=131571).  
  
 Abyste lépe pochopili sémantiku přesunutí, podívejte se na příklad vložení prvku do `vector` objektu. Pokud kapacitu `vector` překročení objektu `vector` objekt musí znovu přidělte paměti pro jeho elementy a zkopírujte do jiného umístění paměti, aby uvolnil prostor pro vložené element každý prvek. Při operaci vložení kopie elementu, vytvoří nového elementu, volá konstruktor copy zkopírovat data z předchozí prvku do nového elementu a pak zničí předchozí elementu. Přesunutí sémantiku umožňuje přesun objektů přímo bez nutnosti provádět přidělení paměti nákladné a operace kopírování.  
  
 Chcete využít výhod přesunutí sémantiku v `vector` příkladu může zapisovat konstruktor move pro přesun dat z jednoho objektu do jiné.  
  
 Další informace o zavedení sémantiku přesunout do standardní knihovny C++ v sadě Visual C++ 2010 najdete v tématu [standardní knihovna C++](../standard-library/cpp-standard-library-reference.md).  
  
## <a name="perfect-forwarding"></a>Perfect Forwarding  
 Ideální předávání snižuje potřebu přetížených funkcí a pomáhá zabránit potížím předávání. *Předávání problém* může dojít, když napíšete obecné funkce, která přebírá odkazy jako jeho parametry a předává (nebo *předává*) tyto parametry jiné funkci. Například, pokud obecné funkce přebírá parametr typu `const T&`, pak volaná funkce nelze změnit hodnotu tohoto parametru. Pokud obecné funkce přebírá parametr typu `T&`, pak funkci nelze volat pomocí rvalue (například dočasný objekt nebo celé číslo literálu).  
  
 Normálně, pokud chcete tento problém vyřešit, musíte zadat přetížené verze obecné funkce, které zpracovat oba současně `T&` a `const T&` pro všechny její parametry. V důsledku toho zvyšuje počet přetížených funkcí exponenciálnímu s počtem parametrů. Odkazy rvalue umožňují zápisu jednu verzi funkci, která přijímá libovolný argumenty a předává je jiné funkci, jako kdyby jiné funkce přímo zavolal.  
  
 Podívejte se na následující příklad, který deklaruje čtyři typy `W`, `X`, `Y`, a `Z`. V konstruktoru pro každý typ trvá různé kombinace `const` a jiných-`const` lvalue odkazy jako jeho parametry.  
  
```  
struct W  
{  
   W(int&, int&) {}  
};  
  
struct X  
{  
   X(const int&, int&) {}  
};  
  
struct Y  
{  
   Y(int&, const int&) {}  
};  
  
struct Z  
{  
   Z(const int&, const int&) {}  
};  
```  
  
 Předpokládejme, že chcete vytvořit obecné funkci, která generuje objekty. Následující příklad ukazuje jeden ze způsobů zápisu této funkce:  
  
```  
template <typename T, typename A1, typename A2>  
T* factory(A1& a1, A2& a2)  
{  
   return new T(a1, a2);  
}  
```  
  
 Následující příklad ukazuje platný volání `factory` funkce:  
  
```  
int a = 4, b = 5;  
W* pw = factory<W>(a, b);  
```  
  
 V následujícím příkladu však neobsahuje platný volání `factory` fungovat, protože `factory` trvá lvalue odkazy, které lze měnit jako jeho parametry, ale je volána pomocí rvalue:  
  
```  
Z* pz = factory<Z>(2, 2);  
```  
  
 Normálně, chcete-li tento problém vyřešit, musíte vytvořit přetížené verzi `factory` funkce pro každou kombinaci `A&` a `const A&` parametry. Odkazy rvalue umožňují zápisu jednu verzi `factory` fungovat, jak je znázorněno v následujícím příkladu:  
  
```  
template <typename T, typename A1, typename A2>  
T* factory(A1&& a1, A2&& a2)  
{  
   return new T(std::forward<A1>(a1), std::forward<A2>(a2));  
}  
```  
  
 Tento příklad používá odkazy rvalue jako parametry, které chcete `factory` funkce. Účelem [std::forward](../standard-library/utility-functions.md#forward) funkce je k předávání parametry funkce vytváření konstruktoru třídy šablony.  
  
 Následující příklad ukazuje `main` funkce, která se používá revidované `factory` funkce vytváření instancí `W`, `X`, `Y`, a `Z` třídy. Revidované `factory` funkce předává jeho parametry (hodnoty lvalue a rvalue) do konstruktoru příslušné třídy.  
  
```  
int main()  
{  
   int a = 4, b = 5;  
   W* pw = factory<W>(a, b);  
   X* px = factory<X>(2, b);  
   Y* py = factory<Y>(a, 2);  
   Z* pz = factory<Z>(2, 2);  
  
   delete pw;  
   delete px;  
   delete py;  
   delete pz;  
}  
```  
  
## <a name="additional-properties-of-rvalue-references"></a>Další vlastnosti odkazy Rvalue  
 **Můžete použít přetížení funkce, která se odkazu lvalue a rvalue odkaz.**  
  
 Pomocí přetížení funkce, která se provést `const` nebo odkaz na deklarátor odkazu lvalue, můžete napsat kód, který slouží k rozlišení mezi neměnitelný objekty (hodnoty lvalue) a upravitelnými dočasných hodnoty (rvalue). Objekt můžete předat funkci, která přebírá deklarátor odkazu objekt není označena jako `const`. Následující příklad ukazuje funkce `f`, což je přetížena odkazu lvalue a rvalue odkaz. `main` Volání funkce `f` s hodnoty lvalue a rvalue.  
  
```  
// reference-overload.cpp  
// Compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
// A class that contains a memory resource.  
class MemoryBlock  
{  
   // TODO: Add resources for the class here.  
};  
  
void f(const MemoryBlock&)  
{  
   cout << "In f(const MemoryBlock&). This version cannot modify the parameter." << endl;  
}  
  
void f(MemoryBlock&&)  
{  
   cout << "In f(MemoryBlock&&). This version can modify the parameter." << endl;  
}  
  
int main()  
{  
   MemoryBlock block;  
   f(block);  
   f(MemoryBlock());  
}  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```  
In f(const MemoryBlock&). This version cannot modify the parameter.  
In f(MemoryBlock&&). This version can modify the parameter.  
```  
  
 V tomto příkladu, první volání `f` předá místní proměnné (lvalue) jako její argument. Druhé volání `f` předá dočasný objekt jako její argument. Protože dočasný objekt nelze na něj odkazovat jinde v programu, volání váže na přetížené verzi `f` deklarátor odkazu, který je bez k úpravě objektu, která má.  
  
 **Kompilátor považuje za rvalue pojmenované deklarátor odkazu jako lvalue a nepojmenované deklarátor odkazu.**  
  
 Když píšete funkce, která přebírá odkaz rvalue jako jeho parametr, tento parametr je považována za lvalue v těle funkce. Pojmenované deklarátor odkazu kompilátor považuje za lvalue, protože objekt s názvem může odkazovat několik částí programu; je nebezpečné povolit více částí programu změnit nebo odebrat prostředky z tohoto objektu. Například pokud více částí programu se pokuste přenést prostředky ze stejného objektu, pouze první část úspěšně přenese prostředku.  
  
 Následující příklad ukazuje funkce `g`, což je přetížena odkazu lvalue a rvalue odkaz. Funkce `f` přebere deklarátor odkazu jako jeho parametr (s názvem rvalue odkaz) a vrátí odkaz rvalue (referenční dokumentace nepojmenované rvalue). Ve volání `g` z `f`, rozlišení přetížení vybere verzi `g` , která má odkazu lvalue protože text `f` považuje za lvalue její parametr. Ve volání `g` z `main`, rozlišení přetížení vybere verzi `g` , která má deklarátor odkazu protože `f` vrátí deklarátor odkazu.  
  
```  
// named-reference.cpp  
// Compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
// A class that contains a memory resource.  
class MemoryBlock  
{  
   // TODO: Add resources for the class here.  
};  
  
void g(const MemoryBlock&)   
{  
   cout << "In g(const MemoryBlock&)." << endl;  
}  
  
void g(MemoryBlock&&)   
{  
   cout << "In g(MemoryBlock&&)." << endl;  
}  
  
MemoryBlock&& f(MemoryBlock&& block)  
{  
   g(block);  
   return block;  
}  
  
int main()  
{  
   g(f(MemoryBlock()));  
}  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```  
In g(const MemoryBlock&).  
In g(MemoryBlock&&).  
```  
  
 V tomto příkladu `main` funkce předá rvalue k `f`. Tělo `f` považuje za lvalue jeho uvedený parametr. Volání z `f` k `g` sváže parametr odkazu lvalue (první přetížené verzi `g`).  
  
-   **Může odevzdat lvalue k deklarátor odkazu.**  
  
 Standardní knihovna C++ [std::move](../standard-library/utility-functions.md#move) funkce umožňuje převedení objektu na rvalue odkaz na tento objekt. Alternativně můžete použít `static_cast` – klíčové slovo přetypovat lvalue k deklarátor odkazu, jak je znázorněno v následujícím příkladu:  
  
```  
// cast-reference.cpp  
// Compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
// A class that contains a memory resource.  
class MemoryBlock  
{  
   // TODO: Add resources for the class here.  
};  
  
void g(const MemoryBlock&)   
{  
   cout << "In g(const MemoryBlock&)." << endl;  
}  
  
void g(MemoryBlock&&)   
{  
   cout << "In g(MemoryBlock&&)." << endl;  
}  
  
int main()  
{  
   MemoryBlock block;  
   g(block);  
   g(static_cast<MemoryBlock&&>(block));  
}  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```  
In g(const MemoryBlock&).  
In g(MemoryBlock&&).  
```  
  
 **Funkce šablony odvodit jejich typy argumentů šablony a potom odkaz sbalení pravidla používat.**  
  
 Je běžné pro zápis funkce šablonu, která předá (nebo *předává*) jeho parametry pro jinou funkci. Je důležité pochopit, jak funguje odvození typu šablony pro šablony funkce, které provést odkazy rvalue.  
  
 Pokud je argumentem funkce rvalue, kompilátor deduces argumentem být deklarátor odkazu. Například pokud předáte rvalue odkaz na objekt typu `X` funkce šablony, která přebírá typ `T&&` jako jeho parametr odvození argumentu šablony deduces `T` být `X`. Proto parametr má typ `X&&`. Pokud jako argument funkce je lvalue nebo `const` lvalue, kompilátor deduces typ jako odkaz na lvalue nebo `const` odkazu lvalue daného typu.  
  
 Následující příklad deklaruje jednu šablonu struktura a pak se specializuje pro různé typy odkazů. `print_type_and_value` Funkce použije deklarátor odkazu hodnoty jako jeho parametr a předává k příslušné verzi specializované `S::print` metoda. `main` Funkce ukazuje různé způsoby, jak volat `S::print` metoda.  
  
```  
// template-type-deduction.cpp  
// Compile with: /EHsc  
#include <iostream>  
#include <string>  
using namespace std;  
  
template<typename T> struct S;  
  
// The following structures specialize S by   
// lvalue reference (T&), const lvalue reference (const T&),   
// rvalue reference (T&&), and const rvalue reference (const T&&).  
// Each structure provides a print method that prints the type of   
// the structure and its parameter.  
  
template<typename T> struct S<T&> {  
   static void print(T& t)  
   {  
      cout << "print<T&>: " << t << endl;  
   }  
};  
  
template<typename T> struct S<const T&> {  
   static void print(const T& t)  
   {  
      cout << "print<const T&>: " << t << endl;  
   }  
};  
  
template<typename T> struct S<T&&> {  
   static void print(T&& t)  
   {  
      cout << "print<T&&>: " << t << endl;  
   }  
};  
  
template<typename T> struct S<const T&&> {  
   static void print(const T&& t)  
   {  
      cout << "print<const T&&>: " << t << endl;  
   }  
};  
  
// This function forwards its parameter to a specialized  
// version of the S type.  
template <typename T> void print_type_and_value(T&& t)   
{  
   S<T&&>::print(std::forward<T>(t));  
}  
  
// This function returns the constant string "fourth".  
const string fourth() { return string("fourth"); }  
  
int main()  
{  
   // The following call resolves to:  
   // print_type_and_value<string&>(string& && t)  
   // Which collapses to:  
   // print_type_and_value<string&>(string& t)  
   string s1("first");  
   print_type_and_value(s1);   
  
   // The following call resolves to:  
   // print_type_and_value<const string&>(const string& && t)  
   // Which collapses to:  
   // print_type_and_value<const string&>(const string& t)  
   const string s2("second");  
   print_type_and_value(s2);  
  
   // The following call resolves to:  
   // print_type_and_value<string&&>(string&& t)  
   print_type_and_value(string("third"));  
  
   // The following call resolves to:  
   // print_type_and_value<const string&&>(const string&& t)  
   print_type_and_value(fourth());  
}  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```  
print<T&>: first  
print<const T&>: second  
print<T&&>: third  
print<const T&&>: fourth  
```  
  
 Chcete-li vyřešit každé volání `print_type_and_value` funkce kompilátoru nejprve provádí odvození argumentu šablony. Kompilátor poté použije odkaz sbalení pravidla, pokud ji nahradí odvodit šablony argumenty pro typy parametrů. Například předávání místní proměnné `s1` k `print_type_and_value` funkce způsobí, že kompilátor vytvořit podpis následující funkce:  
  
```  
print_type_and_value<string&>(string& && t)  
```  
  
 Kompilátor používá ke snížení podpis na následující odkaz sbalení pravidla:  
  
```  
print_type_and_value<string&>(string& t)  
```  
  
 Tato verze `print_type_and_value` funkce poté předává její parametr správnou verzi specializované `S::print` metoda.  
  
 Následující tabulka shrnuje odkaz sbalení pravidla pro typ odvození argumentu šablony:  
  
|||  
|-|-|  
|Rozšířené typu|Sbalené typu|  
|`T& &`|`T&`|  
|`T& &&`|`T&`|  
|`T&& &`|`T&`|  
|`T&& &&`|`T&&`|  
  
 Odvození argumentu šablony představuje důležitý prvek implementace ideální předávání. V části Perfect Forwarding, které je uvedené výše v tomto tématu, popisuje ideální předávání podrobněji.  
  
## <a name="summary"></a>Souhrn  
 Odkazy rvalue odlišit od rvalue hodnoty lvalue. Můžou pomoct zlepšit výkon aplikací odstraněním potřeby pro přidělení nepotřebné paměti a operace kopírování. Umožňují také k zápisu jednu verzi funkci, která přijímá libovolný argumenty a předává je jiné funkci, jako kdyby jiné funkce přímo zavolal.  
  
## <a name="see-also"></a>Viz také  
 [Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)   
 [Deklarátor odkazu lvalue: &](../cpp/lvalue-reference-declarator-amp.md)   
 [Hodnoty lvalue a rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md)   
 [Konstruktory a operátory přiřazení pro přesunutí (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md)   
 [Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)   
