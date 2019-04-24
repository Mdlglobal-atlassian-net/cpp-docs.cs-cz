---
title: 'Deklarátor odkazu hodnoty r: &amp;&amp;'
ms.date: 11/04/2016
f1_keywords:
- '&&'
helpviewer_keywords:
- '&& rvalue reference declarator'
ms.assetid: eab0ce3a-c5a3-4992-aa70-6a8ab1f7491d
ms.openlocfilehash: 185c2de5dc21dd305a2792d4ee8e6baf69c35b28
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331087"
---
# <a name="rvalue-reference-declarator-ampamp"></a>Deklarátor odkazu hodnoty r: &amp;&amp;

Obsahuje odkaz na výraz rvalue.

## <a name="syntax"></a>Syntaxe

```
type-id && cast-expression
```

## <a name="remarks"></a>Poznámky

Odkazy rvalue umožňují odlišit lvalue od rvalue. Odkazy lvalue a odkazy rvalue jsou syntakticky a sémanticky podobné, ale řídí se poněkud odlišnými pravidly. Další informace o hodnotách lvalue a rvalue najdete v tématu [hodnoty lvalue a rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md). Další informace o odkazy lvalue, naleznete v tématu [deklarátor odkazu Lvalue: &](../cpp/lvalue-reference-declarator-amp.md).

Následující části popisují, jak odkazy rvalue podporují implementaci *sémantiky přesunutí* a *perfektní přesměrování*.

## <a name="move-semantics"></a>Přesunutí sémantiky

Odkazy rvalue podporují implementaci *sémantiky přesunutí*, která může výrazně zvýšit výkon vašich aplikací. Přesunutí sémantik umožňuje napsat kód, který převede prostředky (například dynamicky přidělené paměti) z jednoho objektu na jiný. Přesunutí sémantik funguje, protože umožňuje převedení z dočasných objektů, které nelze odkazovat kdekoli v programu prostředků.

K implementaci sémantiky přesunutí obvykle poskytujete *konstruktor přesunutí* a volitelně operátor přiřazení přesunutí (**operátoru =**), do vaší třídy. Operace kopírování a přiřazení, jejichž zdroje jsou hodnoty rvalues pak automaticky využijí sémantiky přesunutí. Na rozdíl od konstruktoru výchozí kopie kompilátor neposkytuje výchozí konstruktor pro přesunutí. Další informace o tom, jak zapsat konstruktor přesunutí a jak ji používat ve vaší aplikaci najdete v tématu [konstruktory přesunutí a operátory přiřazení přesunutí (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md).

Můžete také použít běžné funkce přetížení a operátory k využití výhod přesunutí sémantiky. Visual C++ 2010 představuje přesunutí sémantiky do standardní knihovny C++. Například `string` třída implementuje operace, které provádějí přesunutí sémantiky. Zvažte následující příklad, který zřetězí několik řetězců a vytiskne výsledek:

```cpp
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

Před Visual C++ 2010, každý volání **operátor +** přiděluje a vrací nový dočasný `string` objektu (rvalue). **Operator +** nedokáže připojit jeden řetězec k druhému, protože neví, zda jsou zdrojové řetězce lvalue nebo rvalue. Pokud jsou zdrojové řetězce obou hodnotami lvalues, mohou být odkazovány kdekoli v programu a nesmí být proto změněny. Pomocí odkazů rvalue **operátor +** můžete upravit tak, aby převzal rvalues, které nelze odkazovat kdekoli v programu. Proto **operátor +** může nyní přidat jeden řetězec do druhého. To může výrazně snížit počet přidělení dynamické paměti, která `string` třídy musí provádět. Další informace o `string` najdete v tématu [basic_string – třída](../standard-library/basic-string-class.md).

Přesunutí sémantik také pomáhá, když kompilátor nemůže vrátit hodnotu optimalizace (RVO) nebo s názvem vrátit hodnotu optimalizace (NRVO). V těchto případech kompilátor volá konstruktor přesunu, pokud jej definuje typ. Další informace o vrácení pojmenované optimalizace hodnot najdete v tématu [vrácení pojmenované optimalizace hodnot v aplikaci Visual C++ 2005](https://msdn.microsoft.com/library/ms364057.aspx).

Chcete-li lépe pochopili sémantiku přesunutí, zvažte příklad vložení elementu do `vector` objektu. Pokud kapacitu `vector` je překročena `vector` objektu musí znovu přidělit paměti její elementy a každý element zkopírovat do jiného umístění v paměti a uvolnila prostor pro vložený element. Když operace vložení zkopíruje element, vytvoří nový prvek, volá konstruktor ke kopírování dat z předchozí ho elementu do nového a potom zničí předchozí prvek. Přesunutí sémantik umožňuje přesunout objekty přímo bez nutnosti provádět náročné přidělení paměti a operace kopírování.

Chcete-li využít výhod sémantiky přesunutí v `vector` příkladu můžete zapsat konstruktor přesunutí přesun dat z jednoho objektu na jiný.

Další informace o úvodu sémantiky přesunutí do standardní knihovny C++ ve Visual C++ 2010 v tématu [standardní knihovny C++](../standard-library/cpp-standard-library-reference.md).

## <a name="perfect-forwarding"></a>Perfect Forwarding

Perfektní přesměrování snižuje potřebu přetížených funkcí a pomáhá vyhnout se problému s předáváním. *Problém s předáváním* může dojít při psaní obecné funkce, která přebírá odkazy jako svoje parametry a odesílá (nebo *předává*) tyto parametry jiné funkci. Například, pokud obecná funkce má parametr typu `const T&`, pak volaná funkce nemůže změnit hodnotu tohoto parametru. Pokud obecná funkce má parametr typu `T&`, pak funkci nelze volat pomocí rvalue (například dočasný objekt nebo literál celého čísla).

Obvykle pro vyřešení tohoto problému, je nutné zadat přetížené verze obecných funkcí, které využívají `T&` a `const T&` pro každý ze svých parametrů. V důsledku toho počet přetížených funkcí zvyšuje exponenciálně s počtem parametrů. Odkazy rvalue umožňují napsat jednu verzi funkce, která přijímá libovolný argument a předá je do jiné funkce jako kdyby byla jiná funkce přímo volána.

Podívejte se na následující příklad, který deklaruje čtyři typy `W`, `X`, `Y`, a `Z`. Konstruktor pro každý typ má jinou kombinaci **const** a jiných-**const** odkazy lvalue jako svoje parametry.

```cpp
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

Předpokládejme, že chcete napsat obecnou funkci, která vytváří objekty. Následující příklad ukazuje jeden ze způsobů jak napsat funkci:

```cpp
template <typename T, typename A1, typename A2>
T* factory(A1& a1, A2& a2)
{
   return new T(a1, a2);
}
```

Následující příklad ukazuje platné volání `factory` funkce:

```cpp
int a = 4, b = 5;
W* pw = factory<W>(a, b);
```

V následujícím příkladu však neobsahuje platné volání `factory` fungovat, protože `factory` bere odkazy lvalue, které lze měnit její parametry, ale je volána pomocí rvalues:

```cpp
Z* pz = factory<Z>(2, 2);
```

Obvykle pro vyřešení tohoto problému, je nutné vytvořit přetíženou verzi `factory` funkce pro každou kombinaci `A&` a `const A&` parametry. Odkazy rvalue umožňují také napsat jednu verzi `factory` fungovat, jak je znázorněno v následujícím příkladu:

```cpp
template <typename T, typename A1, typename A2>
T* factory(A1&& a1, A2&& a2)
{
   return new T(std::forward<A1>(a1), std::forward<A2>(a2));
}
```

Tento příklad používá odkazy rvalue jako parametry `factory` funkce. Účelem [std::forward](../standard-library/utility-functions.md#forward) je předat parametry tovární funkce konstruktoru třídy šablony.

Následující příklad ukazuje `main` funkci, která používá revidovanou `factory` funkce k vytvoření instance `W`, `X`, `Y`, a `Z` třídy. Revidovaná `factory` funkce předává své parametry (lvalue nebo rvalue) do odpovídajícího konstruktoru třídy.

```cpp
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

## <a name="additional-properties-of-rvalue-references"></a>Další vlastnosti odkazů Rvalue

**Můžete použít přetížení funkce k převzetí reference na lvalue a rvalue.**

Pomocí přetížení funkce k převzetí **const** odkaz lvalue nebo odkazu rvalue můžete napsat kód, který rozlišuje mezi neupravitelnými objekty (lvalues) a změnitelnými dočasnými hodnotami (rvalues). Objekt můžete předat funkci, která přebírá odkaz rvalue, pokud objekt je označen jako **const**. Následující příklad ukazuje funkci `f`, která je přetížena pro převzetí odkaz na lvalue a rvalue. `main` Volání funkce `f` s hodnotami lvalues i rvalue.

```cpp
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

```Output
In f(const MemoryBlock&). This version cannot modify the parameter.
In f(MemoryBlock&&). This version can modify the parameter.
```

V tomto příkladu první volání `f` předává místní proměnnou (lvalue) jako svůj argument. Druhé volání `f` předává jako argument dočasný objekt. Vzhledem k tomu, že dočasný objekt nelze odkazovat kdekoli v programu, volání vytvoří vazbu přetížené verze `f` , který bere odkaz rvalue, což je volné úpravy objektu.

**Kompilátor považuje pojmenované odkazy rvalue za hodnoty lvalue a nepojmenované odkazy rvalue za hodnoty rvalue.**

Při zápisu funkce, která přebírá odkaz rvalue jako svůj parametr, je tento parametr považován za lvalue v těle funkce. Kompilátor považuje pojmenované odkazy rvalue za hodnoty lvalue, protože na pojmenovaný objekt lze odkazovat pomocí několika částí programu; bylo by nebezpečné povolit více částem programu změnit nebo odebrat prostředky z tohoto objektu. Například pokud se více částí programu pokusí převést prostředky ze stejného objektu, jen jeho první část úspěšně převede prostředek.

Následující příklad ukazuje funkci `g`, která je přetížena pro převzetí odkaz na lvalue a rvalue. Funkce `f` bere odkaz rvalue jako svůj parametr (pojmenovaný odkaz rvalue) a vrátí odkaz rvalue (nepojmenovaný odkaz rvalue). Při volání funkce `g` z `f`, řešení přetížení vybere verzi `g` , která má odkaz na lvalue, protože tělo `f` zachází se svým parametrem jako s hodnotou lvalue. Při volání funkce `g` z `main`, řešení přetížení vybere verzi `g` , který bere odkaz rvalue, protože `f` vrátí odkaz rvalue.

```cpp
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
   return move(block);
}

int main()
{
   g(f(MemoryBlock()));
}
```

Tento příklad vytvoří následující výstup:

```cpp
In g(const MemoryBlock&).
In g(MemoryBlock&&).
```

V tomto příkladu `main` funkce předává rvalue do `f`. Tělo `f` zpracovává svým pojmenovaným parametrem jako s hodnotou lvalue. Volání z `f` k `g` váže parametr na odkaz lvalue (první přetížená verze `g`).

- **Můžete přetypovat lvalue na odkaz rvalue.**

Standardní knihovny C++ [std::move](../standard-library/utility-functions.md#move) funkce umožňuje převést objekt na odkaz rvalue na tento objekt. Alternativně můžete použít **static_cast** – klíčové slovo přetypovat lvalue na odkaz rvalue, jak je znázorněno v následujícím příkladu:

```cpp
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

```cpp
In g(const MemoryBlock&).
In g(MemoryBlock&&).
```

**Funkce šablony odvodit své typy argumentů šablon a potom použít pravidla pro sbalování odkazu.**

Je běžné vytvořit šablonu funkce, která předává (nebo *předává*) své parametry jiné funkci. Je důležité pochopit, jak funguje odpočet typu šablony pro šablony funkcí, které hodnota rvalue odkazuje.

Pokud je argumentem funkce rvalue, kompilátor odvodí, že argument bude odkaz rvalue. Například pokud předáte odkaz rvalue na objekt typu `X` do šablony funkce, které převezme typ `T&&` jako svůj parametr odvození argumentu šablony odvodí `T` bude `X`. Proto má parametr typ `X&&`. Pokud je argumentem funkce lvalue nebo **const** lvalue, kompilátor odvodí jeho typ jako reference na lvalue nebo **const** odkaz lvalue tohoto typu.

Následující příklad deklaruje jednu šablonu struktury a poté ji specializuje pro různé typy odkazů. `print_type_and_value` Funkce bere odkaz rvalue jako svůj parametr a předá jej do příslušné speciální verze `S::print` metody. `main` Funkce ukazuje různé způsoby volání `S::print` metody.

```cpp
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

```cpp
print<T&>: first
print<const T&>: second
print<T&&>: third
print<const T&&>: fourth
```

K vyřešení každého volání `print_type_and_value` funkce, kompilátor provádí nejprve odvození argumentu šablony. Kompilátor poté použije pravidla pro sbalování při nahrazení odvozených argumentů pro typy parametrů odkazu. Například předávání místní proměnné `s1` k `print_type_and_value` funkce způsobí, že kompilátor vytvoří následující podpis funkce:

```cpp
print_type_and_value<string&>(string& && t)
```

Kompilátor používá pravidla pro sbalování odkazu ke redukci podpisu následujícím:

```cpp
print_type_and_value<string&>(string& t)
```

Tato verze `print_type_and_value` funkce následně předá svůj parametr do správné specializované verze `S::print` metoda.

Následující tabulka shrnuje pravidla sbalení odkazu pro srážku typu argumentu šablony:

|||
|-|-|
|Rozšířený typ|Sbalený typ|
|`T& &`|`T&`|
|`T& &&`|`T&`|
|`T&& &`|`T&`|
|`T&& &&`|`T&&`|

Odvození argumentu šablony je důležitým prvkem provádění perfektního přesměrování. Oddíl dokonalé předávání, které jsou uvedeny dříve v tomto tématu, popisuje dokonalé předávání podrobněji.

## <a name="summary"></a>Souhrn

Odkazy rvalue rozlišují mezi hodnotami lvalue od rvalue. Mohou pomoci zvýšit výkon vašich aplikací, vyloučením potřeby zbytečného přidělení a operace kopírování. Umožňují také napsat jednu verzi funkce, která přijímá libovolný argument a předá je do jiné funkce jako kdyby byla jiná funkce přímo volána.

## <a name="see-also"></a>Viz také:

[Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)<br/>
[Deklarátor odkazu l-hodnoty: &](../cpp/lvalue-reference-declarator-amp.md)<br/>
[L-hodnoty a r-hodnoty](../cpp/lvalues-and-rvalues-visual-cpp.md)<br/>
[Konstruktory a operátory přiřazení pro přesunutí (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md)<br/>
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)
