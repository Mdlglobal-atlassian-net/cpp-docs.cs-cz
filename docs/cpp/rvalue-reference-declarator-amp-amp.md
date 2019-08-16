---
title: Deklarátor odkazu rvalue:&amp;&amp;
ms.date: 11/04/2016
f1_keywords:
- '&&'
helpviewer_keywords:
- '&& rvalue reference declarator'
ms.assetid: eab0ce3a-c5a3-4992-aa70-6a8ab1f7491d
ms.openlocfilehash: d6aa6aa9caed77f92b3b183cc49c63aaaa6c724f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498567"
---
# <a name="rvalue-reference-declarator-ampamp"></a>Deklarátor odkazu rvalue:&amp;&amp;

Obsahuje odkaz na výraz rvalue.

## <a name="syntax"></a>Syntaxe

```
type-id && cast-expression
```

## <a name="remarks"></a>Poznámky

Odkazy rvalue umožňují odlišit lvalue od rvalue. Odkazy lvalue a odkazy rvalue jsou syntakticky a sémanticky podobné, ale následují trochu odlišná pravidla. Další informace o hodnoty lvalue a rvalue najdete v tématu [hodnoty lvalue a rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md). Další informace o odkazech na hodnotu lvalue naleznete v tématu [referenční hodnota deklarátor: &](../cpp/lvalue-reference-declarator-amp.md).

Následující části popisují, jak odkazy rvalue podporují implementaci sémantiky *přesunutí* a dokonalého *předávání*.

## <a name="move-semantics"></a>Přesunout sémantiky

Odkazy rvalue podporují implementaci sémantiky *přesunutí*, což může významně zvýšit výkon vašich aplikací. Přesunutí sémantiky umožňuje napsat kód, který přenáší prostředky (například dynamicky přidělené paměti) z jednoho objektu na jiný. Přesunutí sémantiky funguje, protože umožňuje přenos prostředků z dočasných objektů, na které nelze odkazovat jinde v programu.

Pro implementaci sémantiky přesunutí obvykle poskytnete *konstruktor Move* a volitelně operátor přiřazení přesunu (**Operator =** ) do vaší třídy. Operace kopírování a přiřazení, jejichž zdroje jsou rvalue, pak automaticky využijí sémantiky přesunutí. Na rozdíl od výchozího kopírovacího konstruktoru kompilátor neposkytuje výchozí konstruktor Move. Další informace o tom, jak napsat konstruktor přesunu a jak ho použít v aplikaci, naleznete v tématu [Move konstruktors and Move Assignment OperatorsC++()](../cpp/move-constructors-and-move-assignment-operators-cpp.md).

Můžete také přetížit běžné funkce a operátory a využít přitom sémantiku přesunutí. Visual Studio 2010 zavádí sémantiku přesunutí do C++ standardní knihovny. `string` Třída například implementuje operace, které provádějí sémantiku přesunutí. Vezměte v úvahu následující příklad, který zřetězí několik řetězců a vytiskne výsledek:

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

Před Visual Studio 2010 se každé volání **operátoru +** přidělí a vrátí nový dočasný `string` objekt (rvalue). **Operator +** nemůže připojit jeden řetězec k druhému, protože neví, zda jsou zdrojové řetězce hodnoty lvalue nebo rvalue. Pokud jsou zdrojové řetězce hodnoty lvalue, mohou být odkazovány jinde v programu a proto nesmí být upraveny. Pomocí odkazů rvalue lze **operátor +** upravit tak, aby převzal rvalue, na který nelze odkazovat jinde v programu. Proto **operátor +** může nyní připojit jeden řetězec k druhému. To může významně snížit počet přidělených dynamických paměti, které `string` třída musí provádět. Další informace o `string` třídě naleznete v tématu [Třída basic_string](../standard-library/basic-string-class.md).

Přesunutí sémantiky také pomáhá, když kompilátor nemůže použít optimalizaci návratových hodnot (RVO) nebo pojmenovanou optimalizaci návratové hodnoty (NRVO). V těchto případech vyvolá kompilátor přesunutí konstruktoru, pokud jej definuje typ. Další informace o optimalizaci pojmenovaných vrácených hodnot naleznete [v tématu Optimalizace pojmenované návratové hodnoty v aplikaci Visual Studio 2005](/previous-versions/ms364057(v=vs.80)).

Chcete-li lépe pochopit sémantiku přesunutí, zvažte příklad vložení elementu do `vector` objektu. Pokud je překročena kapacita `vector` objektu `vector` , objekt musí znovu přidělit paměť pro své prvky a pak zkopírovat každý element do jiného umístění v paměti, aby uvolnil prostor pro vložený element. Když operace vložení zkopíruje prvek, vytvoří nový prvek, zavolá kopírovací konstruktor pro zkopírování dat z předchozího prvku do nového prvku a poté zničí předchozí prvek. Přesunutí sémantik umožňuje přesun objektů přímo bez nutnosti provádět náročné přidělování paměti a operace kopírování.

Chcete-li využít výhod sémantiky přesunutí v `vector` příkladu, můžete napsat konstruktor Move pro přesun dat z jednoho objektu na jiný.

Další informace o zavedení sémantiky přesunutí do C++ standardní knihovny v aplikaci Visual Studio 2010 naleznete v tématu [ C++ standardní knihovna](../standard-library/cpp-standard-library-reference.md).

## <a name="perfect-forwarding"></a>Dokonalé přesměrování

Dokonalé přesměrování snižuje potřebu přetížených funkcí a pomáhá vyhnout se problému s předáváním. K tomuto *problému* může dojít při psaní obecné funkce, která jako své parametry přijímá odkazy, a předá (nebo *předává*) tyto parametry jiné funkci. Například pokud obecná funkce přebírá parametr typu `const T&`, volaná funkce nemůže změnit hodnotu tohoto parametru. Pokud Obecná funkce přebírá parametr typu `T&`, nemůže být funkce volána pomocí rvalue (například dočasného objektu nebo celočíselného literálu).

Obvykle pro vyřešení tohoto problému je nutné poskytnout přetížené verze generické funkce, která přijímá obojí `T&` a `const T&` pro každý z jeho parametrů. V důsledku toho se počet přetížených funkcí zvyšuje exponenciálně s počtem parametrů. Odkazy rvalue umožňují napsat jednu verzi funkce, která přijímá libovolný argument, a předá je do jiné funkce, jako kdyby byla jiná funkce přímo volána.

Vezměte v úvahu následující příklad, který deklaruje čtyři typy `W`, `X`, `Y`, a `Z`. Konstruktor pro každý typ používá jinou kombinaci odkazů const a non-**const** jako svůj parametr.

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

Předpokládejme, že chcete napsat obecnou funkci, která generuje objekty. Následující příklad ukazuje jeden ze způsobů, jak zapsat tuto funkci:

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

Následující příklad však neobsahuje platné volání `factory` funkce, protože `factory` bere odkazy lvalue, které lze upravit jako své parametry, ale je volána pomocí rvalue:

```cpp
Z* pz = factory<Z>(2, 2);
```

Obvykle pro vyřešení tohoto problému je nutné vytvořit přetíženou verzi `factory` funkce pro každou `A&` kombinaci parametrů a `const A&` . Odkazy rvalue umožňují napsat jednu verzi `factory` funkce, jak je znázorněno v následujícím příkladu:

```cpp
template <typename T, typename A1, typename A2>
T* factory(A1&& a1, A2&& a2)
{
   return new T(std::forward<A1>(a1), std::forward<A2>(a2));
}
```

Tento příklad používá odkazy rvalue jako parametry `factory` funkce. Účelem funkce [std::](../standard-library/utility-functions.md#forward) dopředné je přeposlání parametrů funkce Factory do konstruktoru třídy šablony.

Následující `main` příklad ukazuje funkci, která používá revidovanou `factory` funkci `W`k vytvoření instancí tříd, `X`, `Y`a `Z` . Revidovaná `factory` funkce přepošle své parametry (buď hodnoty lvalue nebo rvalue) do příslušného konstruktoru třídy.

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

**Můžete přetížit funkci, aby převzala odkaz lvalue a odkaz rvalue.**

Přetížením funkce, aby převzala odkaz **const** lvalue nebo odkaz rvalue, můžete napsat kód, který rozlišuje mezi neupravitelnými objekty (hodnoty lvalue) a upravitelnými dočasnými hodnotami (rvalue). Objektu můžete předat funkci, která převezme odkaz rvalue, pokud objekt není označený jako const. Následující příklad ukazuje funkci `f`, která je přetížena pro převzetí odkazu lvalue a odkazu rvalue. `main` Funkce volá`f` obě hodnoty lvalue i rvalue.

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

V tomto příkladu první volání `f` předává místní proměnnou (l-hodnotu) jako argument. Druhé volání `f` předává dočasný objekt jako argument. Vzhledem k tomu, že na dočasný objekt nelze odkazovat jinde v programu, volání se váže k přetížené verzi `f` , která přebírá odkaz rvalue, což je zdarma upravovat objekt.

**Kompilátor považuje pojmenovaný odkaz rvalue za lvalue a nepojmenované odkazy rvalue jako rvalue.**

Při psaní funkce, která jako svůj parametr přebírá odkaz rvalue, je tento parametr považován za lvalue v těle funkce. Kompilátor považuje pojmenovaný odkaz rvalue za hodnotu lvalue, protože na pojmenovaný objekt může odkazovat několik částí programu; mohlo by to být nebezpečné, aby bylo možné upravovat nebo odebírat prostředky z tohoto objektu více částmi programu. Například pokud se více částí programu pokusí přenést prostředky ze stejného objektu, pouze první část úspěšně převede prostředek.

Následující příklad ukazuje funkci `g`, která je přetížena pro převzetí odkazu lvalue a odkazu rvalue. Funkce `f` přebírá odkaz rvalue jako svůj parametr (pojmenovaný odkaz rvalue) a vrací odkaz rvalue (nepojmenovaný odkaz rvalue). Při volání `g` `f` z `f` ,`g` řešení přetížení vybere verzi, která přebírá odkaz lvalue, protože tělo považuje svůj parametr za lvalue. Při volání `g` `f` z `main` ,`g` řešení přetížení vybere verzi, která přebírá odkaz rvalue, protože vrací odkaz rvalue.

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

V tomto příkladu `main` funkce předává rvalue do `f`. Tělo `f` zpracovává jeho pojmenovaný parametr jako lvalue. Volání `f` `g`metody váže parametr na odkaz lvalue (první přetížená verze). `g`

- **L-hodnotu můžete přetypovat na odkaz rvalue.**

C++ Standardní knihovna funkce [std:: Move](../standard-library/utility-functions.md#move) umožňuje převést objekt na odkaz rvalue na tento objekt. Alternativně můžete použít klíčové slovo **static_cast** k přetypování hodnoty lvalue na odkaz rvalue, jak je znázorněno v následujícím příkladu:

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

**Šablony funkcí odvodit své typy argumentů šablony a pak používají pravidla sbalení odkazů.**

Je běžné napsat šablonu funkce, která předává (nebo *předává*) své parametry jiné funkci. Je důležité porozumět tomu, jak odvození typu šablony funguje pro šablony funkcí, které přijímají odkazy rvalue.

Pokud je argumentem funkce rvalue, kompilátor odvodit argument jako odkaz rvalue. Například Pokud předáte odkaz rvalue objektu `X` typu na funkci šablony, která jako svůj parametr přebírá typ `T&&` , `X`odpočty `T` argumentů šablony se odvodit. Proto má parametr typ `X&&`. Pokud je argumentem funkce l-hodnota nebo const lvalue, kompilátor odvodí svůj typ tak, aby byl odkaz lvalue nebo **const** odkaz na lvalue tohoto typu.

Následující příklad deklaruje jednu šablonu struktury a potom ji specializuje pro různé typy odkazů. Funkce jako svůj parametr převezme odkaz rvalue a předá ho příslušné specializované verzi `S::print` metody. `print_type_and_value` Funkce ukazuje různé způsoby `S::print` volání metody. `main`

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

Chcete-li vyřešit každé volání `print_type_and_value` funkce, kompilátor nejprve provede odvození argumentu šablony. Kompilátor potom použije pravidla sbalení odkazu, když nahradí odvozené argumenty šablony pro typy parametrů. Například předání místní proměnné `s1` `print_type_and_value` funkci způsobí, že kompilátor vygeneruje následující signaturu funkce:

```cpp
print_type_and_value<string&>(string& && t)
```

Kompilátor používá pravidla sbalení odkazů ke snížení signatury na následující:

```cpp
print_type_and_value<string&>(string& t)
```

Tato verze `print_type_and_value` funkce pak předá svůj parametr správné specializované verzi `S::print` metody.

Následující tabulka shrnuje pravidla sbalení odkazu pro odvození typu argumentu šablony:

|||
|-|-|
|Rozbalený typ|Sbalený typ|
|`T& &`|`T&`|
|`T& &&`|`T&`|
|`T&& &`|`T&`|
|`T&& &&`|`T&&`|

Odvození argumentu šablony je důležitým prvkem implementace dokonalého předávání. Oddíl Perfect forwarding uvedený výše v tomto tématu popisuje dokonalé přesměrování podrobněji.

## <a name="summary"></a>Souhrn

Odkazy rvalue odlišují hodnoty lvalue od rvalue. Mohou pomoci zlepšit výkon aplikací tím, že eliminují nutnost zbytečného přidělení paměti a operací kopírování. Umožňují také napsat jednu verzi funkce, která přijímá libovolný argument, a předá je do jiné funkce, jako kdyby byla jiná funkce přímo volána.

## <a name="see-also"></a>Viz také:

[Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)<br/>
[Deklarátor odkazu l-hodnoty: &](../cpp/lvalue-reference-declarator-amp.md)<br/>
[L-hodnoty a r-hodnoty](../cpp/lvalues-and-rvalues-visual-cpp.md)<br/>
[Konstruktory a operátory přiřazení pro přesunutí (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md)<br/>
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)
