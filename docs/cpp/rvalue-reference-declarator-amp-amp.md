---
title: Deklarátor odkazu na rvalu:&amp;&amp;
ms.date: 11/04/2016
f1_keywords:
- '&&'
helpviewer_keywords:
- '&& rvalue reference declarator'
ms.assetid: eab0ce3a-c5a3-4992-aa70-6a8ab1f7491d
ms.openlocfilehash: 53729cca7c259bc2d3b792ddc3509d5fc3bd255a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749824"
---
# <a name="rvalue-reference-declarator-ampamp"></a>Deklarátor odkazu na rvalu:&amp;&amp;

Obsahuje odkaz na výraz rvalue.

## <a name="syntax"></a>Syntaxe

```
type-id && cast-expression
```

## <a name="remarks"></a>Poznámky

Odkazy rvalue umožňují odlišit lvalue od rvalue. Lvalue odkazy a rvalue odkazy jsou syntakticky a sémanticky podobné, ale postupujte podle poněkud odlišných pravidel. Další informace o lvalues a rvalues naleznete v [tématu Lvalues a Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md). Další informace o odkazech na lvalue naleznete v [tématu Deklarátor odkazů lvalue: &](../cpp/lvalue-reference-declarator-amp.md).

Následující části popisují, jak odkazy na rvalue podporují implementaci *sémantiky přesunutí* a *dokonalého předávání*.

## <a name="move-semantics"></a>Přesunout sémantiku

Rvalue odkazy podporují implementaci *přesunout sémantiku*, což může výrazně zvýšit výkon vašich aplikací. Přesunout sémantiku umožňuje psát kód, který přenáší prostředky (například dynamicky přidělené paměti) z jednoho objektu do druhého. Přesunout sémantiku funguje, protože umožňuje prostředky, které mají být převedeny z dočasných objektů, které nelze odkazovat jinde v programu.

Chcete-li implementovat přesunout sémantiku, obvykle poskytují *move konstruktor* a volitelně operátor přiřazení přesunutí (**operátor =**), do vaší třídy. Operace kopírování a přiřazení, jejichž zdroje jsou rvalues, pak automaticky využívají sémantiku přesunutí. Na rozdíl od výchozího konstruktoru kopie kompilátor neposkytuje výchozí konstruktor move. Další informace o tom, jak napsat konstruktor přesunutí a jak jej používat ve vaší aplikaci, naleznete v [tématu Přesunutí konstruktorů a přesunutí operátorů přiřazení (C++).](../cpp/move-constructors-and-move-assignment-operators-cpp.md)

Můžete také přetížení běžné funkce a operátory využít přesunout sémantiku. Visual Studio 2010 zavádí přesunout sémantiku do standardní knihovny C++. Například třída `string` implementuje operace, které provádějí sémantiku přesunutí. Vezměme si následující příklad, který zřetězí několik řetězců a vytiskne výsledek:

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

Před Visual Studio 2010 každé volání **operátor+** přiděluje a vrací nový dočasný `string` objekt (rvalue). **operátor+** nemůže připojit jeden řetězec k druhému, protože neví, zda jsou zdrojové řetězce lvalues nebo rvalues. Pokud jsou zdrojové řetězce obě lvalues, mohou být odkazovány jinde v programu a proto nesmí být změněny. Pomocí rvalue odkazy, **operátor+** lze upravit tak, aby rvalues, které nelze odkazovat jinde v programu. Proto **operátor+** nyní můžete připojit jeden řetězec do druhého. To může výrazně snížit počet přidělení dynamické `string` paměti, které musí třída provést. Další informace o `string` třídě naleznete v [tématu basic_string Class](../standard-library/basic-string-class.md).

Přesunout sémantiku také pomáhá, když kompilátor nemůže použít optimalizaci návratové hodnoty (RVO) nebo pojmenovanou optimalizaci návratové hodnoty (NRVO). V těchto případech kompilátor volá konstruktor move, pokud jej definuje typ.

Chcete-li lépe porozumět sémantiku přesunutí, zvažte `vector` příklad vložení prvku do objektu. Pokud je překročena kapacita objektu, `vector` `vector` musí objekt znovu přidělit paměť pro jeho prvky a potom zkopírovat každý prvek do jiného umístění paměti, aby se uvolnilo místo pro vložený prvek. Když operace vložení zkopíruje prvek, vytvoří nový prvek, volá konstruktor kopie zkopírovat data z předchozího prvku do nového prvku a pak zničí předchozí prvek. Přesunout sémantiku umožňuje přesunout objekty přímo bez nutnosti provádět nákladné přidělení paměti a kopírování operací.

Chcete-li využít přesunout sémantiku v příkladu, `vector` můžete napsat move konstruktor přesunout data z jednoho objektu do druhého.

Další informace o zavedení přesunout sémantiku do standardní knihovny Jazyka C++ v sadě Visual Studio 2010 naleznete v [tématu C++ Standard Library](../standard-library/cpp-standard-library-reference.md).

## <a name="perfect-forwarding"></a>Dokonalé přeposílání

Dokonalé předávání snižuje potřebu přetížených funkcí a pomáhá vyhnout se problému s předáváním. *Problém předávání* může dojít při zápisu obecné funkce, která přebírá odkazy jako jeho parametry a předá (nebo *předává*) tyto parametry do jiné funkce. Pokud například obecná funkce přebírá parametr `const T&`typu , nemůže volaná funkce změnit hodnotu tohoto parametru. Pokud obecná funkce přebírá parametr `T&`typu , pak funkci nelze volat pomocí rvalue (například dočasný objekt nebo literál celého čísla).

Obvykle k vyřešení tohoto problému je nutné zadat přetížené verze obecné `T&` `const T&` funkce, které trvat oba a pro každý z jeho parametrů. V důsledku toho se počet přetížených funkcí exponenciálně zvyšuje s počtem parametrů. Rvalue odkazy umožňují napsat jednu verzi funkce, která přijímá libovolné argumenty a předává je do jiné funkce, jako kdyby druhá funkce byla volána přímo.

Zvažte následující příklad, který `W`deklaruje čtyři typy , `X`, `Y`a `Z`. Konstruktor pro každý typ má jinou kombinaci **const** a**non-const** lvalue odkazy jako jeho parametry.

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

Předpokládejme, že chcete napsat obecnou funkci, která generuje objekty. Následující příklad ukazuje jeden způsob, jak napsat tuto funkci:

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

Následující příklad však neobsahuje platné volání `factory` funkce, protože `factory` přebírá odkazy lvalue, které jsou upravitelné jako jeho parametry, ale je volána pomocí rvalues:

```cpp
Z* pz = factory<Z>(2, 2);
```

Obvykle k vyřešení tohoto problému je nutné vytvořit přetíženou verzi `factory` funkce `A&` `const A&` pro každou kombinaci a parametry. Odkazy na rvalue umožňují napsat jednu `factory` verzi funkce, jak je znázorněno v následujícím příkladu:

```cpp
template <typename T, typename A1, typename A2>
T* factory(A1&& a1, A2&& a2)
{
   return new T(std::forward<A1>(a1), std::forward<A2>(a2));
}
```

Tento příklad používá odkazy rvalue jako `factory` parametry funkce. Účelem funkce [std::forward](../standard-library/utility-functions.md#forward) je předat parametry funkce factory konstruktoru třídy šablony.

Následující příklad ukazuje `main` funkci, která `factory` používá revidovanou funkci `W`k `X` `Y`vytvoření `Z` instancí tříd , , a tříd. Revidovaná `factory` funkce předá své parametry (buď lvalues nebo rvalues) příslušnému konstruktoru třídy.

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

## <a name="additional-properties-of-rvalue-references"></a>Další vlastnosti odkazů rvalue

**Můžete přetížení funkce, aby se odkaz lvalue a rvalue odkaz.**

Přetížením funkce tak, aby byla přijata referenční hodnota **const** lvalue nebo odkaz rvalue, můžete napsat kód, který rozlišuje mezi neupravitelnými objekty (lvalues) a modifikovatelnými dočasnými hodnotami (rvalues). Objekt můžete předat funkci, která přebírá odkaz na rvalue, pokud není objekt označen jako **const**. Následující příklad ukazuje `f`funkci , která je přetížena, aby přijala odkaz lvalue a odkaz rvalue. Funkce `main` volá `f` s ilvalues a rvalue.

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

Tento příklad vytváří následující výstup:

```Output
In f(const MemoryBlock&). This version cannot modify the parameter.
In f(MemoryBlock&&). This version can modify the parameter.
```

V tomto příkladu první `f` volání předá místní proměnné (lvalue) jako jeho argument. Druhé volání `f` předá dočasný objekt jako jeho argument. Vzhledem k tomu, že dočasný objekt nelze odkazovat jinde v `f` programu, volání váže přetížené verze, která má rvalue odkaz, který je volně měnit objekt.

**Kompilátor považuje pojmenovanou hodnotu rvalue za lvalue a nepojmenovanou hodnotu jako rvalue.**

Při zápisu funkce, která má rvalue odkaz jako jeho parametr, tento parametr je považován za lvalue v těle funkce. Kompilátor považuje pojmenovanou hodnotu rvalue za lvalue, protože pojmenovaný objekt může odkazovat několik částí programu; bylo by nebezpečné povolit více částí programu upravit nebo odebrat prostředky z tohoto objektu. Pokud se například více částí programu pokusí přenést prostředky ze stejného objektu, pouze první část úspěšně převede prostředek.

Následující příklad ukazuje `g`funkci , která je přetížena, aby přijala odkaz lvalue a odkaz rvalue. Funkce `f` přebírá jako svůj parametr odkaz rvalue (pojmenovaný odkaz rvalue) a vrací odkaz rvalue (nepojmenovaný odkaz rvalue). Volání do `g` from `f`, rozlišení přetížení vybere `g` verzi, která má odkaz `f` lvalue, protože tělo zachází s jeho parametr jako lvalue. Při volání `g` do `main`from , rozlišení přetížení `g` vybere verzi, která `f` má rvalue odkaz, protože vrátí odkaz rvalue.

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

Tento příklad vytváří následující výstup:

```cpp
In g(const MemoryBlock&).
In g(MemoryBlock&&).
```

V tomto příkladu `main` funkce předá `f`rvalue . Tělo považuje `f` jeho pojmenovaný parametr jako lvalue. Volání z `f` `g` to váže parametr na odkaz lvalue (první `g`přetížená verze).

- **Lvalue můžete přetypovat na odkaz rvalue.**

Funkce [std::move](../standard-library/utility-functions.md#move) standardní knihovny jazyka C++umožňuje převést objekt na odkaz rvalue na tento objekt. Alternativně můžete použít **static_cast** klíčové slovo k přetypování lvalue na odkaz rvalue, jak je znázorněno v následujícím příkladu:

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

Tento příklad vytváří následující výstup:

```cpp
In g(const MemoryBlock&).
In g(MemoryBlock&&).
```

**Šablony funkcí odvodí jejich typy argumentů šablony a poté použijí pravidla sbalení odkazů.**

Je běžné napsat šablonu funkce, která předává (nebo *předává*) své parametry jiné funkci. Je důležité pochopit, jak funguje odpočet typu šablony pro šablony funkcí, které berou odkazy na rvalue.

Pokud je argument funkce rvalue, kompilátor odvodí argument jako odkaz na rvalue. Pokud například předáte odkaz na rvalue `X` na objekt typu funkci `T&&` šablony, která bere typ jako `T` jeho `X`parametr, odpočet odpočtu argumentu šablony se odvede . Proto má parametr `X&&`typ . Pokud je argumentem funkce lvalue nebo **const** lvalue, kompilátor odvodí svůj typ jako odkaz lvalue nebo odkaz **const** lvalue tohoto typu.

Následující příklad deklaruje jednu šablonu struktury a pak ji specializuje na různé typy odkazů. Funkce `print_type_and_value` přebírá odkaz rvalue jako jeho parametr a předá jej `S::print` příslušné specializované verzi metody. Funkce `main` ukazuje různé způsoby volání `S::print` metody.

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

Tento příklad vytváří následující výstup:

```cpp
print<T&>: first
print<const T&>: second
print<T&&>: third
print<const T&&>: fourth
```

Chcete-li vyřešit `print_type_and_value` každé volání funkce, kompilátor nejprve provede odpočet argumentů šablony. Kompilátor pak použije pravidla sbalení odkazu, když nahradí odvozené argumenty šablony pro typy parametrů. Například předání místní `s1` proměnné `print_type_and_value` funkci způsobí, že kompilátor vytvoří následující podpis funkce:

```cpp
print_type_and_value<string&>(string& && t)
```

Kompilátor používá pravidla sbalení odkazu ke snížení podpisu na následující:

```cpp
print_type_and_value<string&>(string& t)
```

Tato verze `print_type_and_value` funkce pak předá svůj parametr správné specializované `S::print` verzi metody.

Následující tabulka shrnuje pravidla sbalení odkazu pro odpočet typu argumentu šablony:

|||
|-|-|
|Rozšířený typ|Sbalený typ|
|`T& &`|`T&`|
|`T& &&`|`T&`|
|`T&& &`|`T&`|
|`T&& &&`|`T&&`|

Odpočet argumentů šablony je důležitým prvkem implementace dokonalého předávání. Sekce Dokonalé předávání, která je uvedena dříve v tomto tématu, popisuje dokonalé předávání podrobněji.

## <a name="summary"></a>Souhrn

Odkazy rvalue rozlišují hodnoty lvalues od hodnot rvalues. Mohou vám pomoci zlepšit výkon aplikací tím, že eliminují potřebu zbytečného přidělení paměti a operací kopírování. Umožňují také napsat jednu verzi funkce, která přijímá libovolné argumenty a předává je do jiné funkce, jako by druhá funkce byla volána přímo.

## <a name="see-also"></a>Viz také

[Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)<br/>
[Deklarátor odkazu l-hodnoty: &](../cpp/lvalue-reference-declarator-amp.md)<br/>
[Lhodnoty a Hodnoty R](../cpp/lvalues-and-rvalues-visual-cpp.md)<br/>
[Konstruktory a operátory přiřazení pro přesunutí (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md)<br/>
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)
