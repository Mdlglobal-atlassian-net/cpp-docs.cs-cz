---
title: decltype (C++)
ms.date: 11/04/2016
f1_keywords:
- decltype_cpp
helpviewer_keywords:
- operators [C++], decltype
- decltype operator
- operators [C++], type of an expression
- operators [C++], deduce expression type
ms.assetid: 6dcf8888-8196-4f13-af50-51e3797255d4
ms.openlocfilehash: 1ed07b8987df7b621ea2809409069cc1121fa24f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180209"
---
# <a name="decltype--c"></a>decltype (C++)

Specifikátor typu **decltype** vrací typ zadaného výrazu. Specifikátor typu **decltype** spolu s [klíčovým slovem auto](../cpp/auto-cpp.md)je užitečný hlavně pro vývojáře, kteří vytvářejí knihovny šablon. Použijte **auto** a **decltype** k deklarování šablony funkce, jejíž návratový typ závisí na typech svých argumentů šablony. Nebo použijte **auto** a **decltype** k deklaraci funkce šablony, která zabalí volání jiné funkce a vrátí návratový typ zabalené funkce.

## <a name="syntax"></a>Syntaxe

```
decltype( expression )
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*vyjádření*|Výraz. Další informace najdete v tématu [výrazy](../cpp/expressions-cpp.md).|

## <a name="return-value"></a>Návratová hodnota

Typ parametru *výrazu*

## <a name="remarks"></a>Poznámky

Specifikátor typu **decltype** je podporován v aplikaci Visual Studio 2010 nebo novějších verzích a lze jej použít s nativním nebo spravovaným kódem. `decltype(auto)` (C++ 14) je podporován v aplikaci Visual Studio 2015 a novější.

Kompilátor používá následující pravidla pro určení typu parametru *výrazu* .

- Pokud je parametr *výrazu* identifikátor nebo [přístup ke členu třídy](../cpp/member-access-operators-dot-and.md), `decltype(expression)` je typ entity s názvem *Expression*. Pokud žádná taková entita nebo parametr *výrazu* nejmenuje sadu přetížených funkcí, kompilátor vrátí chybovou zprávu.

- Pokud je parametr *výrazu* volání funkce nebo funkce přetíženého operátoru, `decltype(expression)` je návratový typ funkce. Závorky kolem přetíženého operátoru jsou ignorovány.

- Pokud je parametr *výrazu* [rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md), `decltype(expression)` je typ *výrazu*. Pokud je parametr *výrazu* [l](../cpp/lvalues-and-rvalues-visual-cpp.md)-hodnota, `decltype(expression)` je [odkaz lvalue](../cpp/lvalue-reference-declarator-amp.md) na typ *výrazu*.

Následující příklad kódu ukazuje některá použití specifikátoru typu **decltype** . Nejprve předpokládejme, že jste nakódovali následující příkazy.

```cpp
int var;
const int&& fx();
struct A { double x; }
const A* a = new A();
```

Dále prověřte typy, které jsou vráceny čtyřmi příkazy **decltype** v následující tabulce.

|Výpis|Typ|Poznámky:|
|---------------|----------|-----------|
|`decltype(fx());`|`const int&&`|[Odkaz rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) na **const int**.|
|`decltype(var);`|**int**|Typ proměnné `var`.|
|`decltype(a->x);`|**double**|Typ přístupu členu.|
|`decltype((a->x));`|`const double&`|Vnitřní závorky způsobí, že je příkaz vyhodnocen jako výraz namísto přístupu ke členu. A vzhledem k tomu, že `a` je deklarován jako `const` ukazatel, je typ odkaz na hodnotu **const Double**.|

## <a name="decltype-and-auto"></a>Klíčová slova Decltype a Auto

V jazyce C++ 14 můžete použít `decltype(auto)` bez ukončovacího návratového typu k deklaraci funkce šablony, jejíž návratový typ závisí na typech svých argumentů šablony.

V jazyce C++ 11 můžete použít specifikátor typu **decltype** na konci návratového typu společně s klíčovým slovem **auto** k deklaraci funkce šablony, jejíž návratový typ závisí na typech svých argumentů šablony. Zvažte například následující příklad kódu, ve kterém návratový typ šablony funkce závisí na typech šablony argumentů. V příkladu kódu *Neznámý* zástupný symbol označuje, že nelze zadat návratový typ.

```cpp
template<typename T, typename U>
UNKNOWN func(T&& t, U&& u){ return t + u; };
```

Zavedení specifikátoru typu **decltype** umožňuje vývojářům získat typ výrazu, který vrací funkce šablony. Použijte *alternativní syntaxi deklarace funkce* , která se zobrazí později, klíčové **slovo auto** a specifikátor typu **decltype** k deklaraci *zpožděně určeného* návratového typu. Pozdně určený návratový typ je určen při kompilaci deklarace, nikoli když je kódován.

Následující prototyp znázorňuje syntaxi alternativní deklarace funkce. Všimněte si, že kvalifikátory **const** a **volatile** a [specifikace výjimky](../cpp/exception-specifications-throw-cpp.md) **throw** jsou volitelné. Zástupný symbol *function_body* představuje složený příkaz, který určuje, co funkce dělá. Jako osvědčený postup pro psaní kódu by měl zástupné znaky *výrazu* v příkazu **decltype** odpovídat výrazu určenému příkazem **return** , pokud existuje, v *function_body*.

**auto** *function_name* **(** *parameters*<sub>opt</sub> -parametry **)** **const**<sub>opt opt</sub> **opt**<sub>opt</sub> **->** **decltype (** *výraz* **)** **throw**<sub>opt</sub> **{** *function_body* **};**

V následujícím příkladu kódu je pozdně zadaný návratový typ šablony funkce `myFunc` určen pomocí typů `t` a `u` šablony argumentů. V rámci osvědčeného postupu kódování používá příklad kódu také odkazy rvalue a šablonu funkce `forward`, která podporuje *dokonalé přesměrování*. Další informace naleznete v tématu [rvalue reference deklarátor: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

```cpp
//C++11
template<typename T, typename U>
auto myFunc(T&& t, U&& u) -> decltype (forward<T>(t) + forward<U>(u))
        { return forward<T>(t) + forward<U>(u); };

//C++14
template<typename T, typename U>
decltype(auto) myFunc(T&& t, U&& u)
        { return forward<T>(t) + forward<U>(u); };
```

## <a name="decltype-and-forwarding-functions-c11"></a>Funkce decltype a předávání (C++ 11)

Funkce předávání zaobalují volání dalších funkcí. Zvažte šablonu funkce, která předává své argumenty nebo výsledky výrazu, který zahrnuje tyto argumenty, jiné funkci. Kromě toho funkce předávání vrátí výsledek volání další funkce. V tomto scénáři by měl návratový typ funkce předávání být stejný jako návratový typ zabalené funkce.

V tomto scénáři nelze zapsat odpovídající výraz typu bez specifikátoru typu **decltype** . Specifikátor typu **decltype** umožňuje funkce obecného předávání, protože neztratí požadované informace o tom, zda funkce vrací typ odkazu. Příklad kódu funkce předávání naleznete v předchozím příkladu šablony funkce `myFunc`.

## <a name="example"></a>Příklad

Následující příklad kódu deklaruje pozdně zadaný návratový typ šablony funkce `Plus()`. Funkce `Plus` zpracovává své dva operandy **operátorem +** Overload. V důsledku toho interpretace operátoru plus (+) a návratový typ funkce `Plus` závisí na typech argumentů funkce.

```cpp
// decltype_1.cpp
// compile with: cl /EHsc decltype_1.cpp

#include <iostream>
#include <string>
#include <utility>
#include <iomanip>

using namespace std;

template<typename T1, typename T2>
auto Plus(T1&& t1, T2&& t2) ->
   decltype(forward<T1>(t1) + forward<T2>(t2))
{
   return forward<T1>(t1) + forward<T2>(t2);
}

class X
{
   friend X operator+(const X& x1, const X& x2)
   {
      return X(x1.m_data + x2.m_data);
   }

public:
   X(int data) : m_data(data) {}
   int Dump() const { return m_data;}
private:
   int m_data;
};

int main()
{
   // Integer
   int i = 4;
   cout <<
      "Plus(i, 9) = " <<
      Plus(i, 9) << endl;

   // Floating point
   float dx = 4.0;
   float dy = 9.5;
   cout <<
      setprecision(3) <<
      "Plus(dx, dy) = " <<
      Plus(dx, dy) << endl;

   // String
   string hello = "Hello, ";
   string world = "world!";
   cout << Plus(hello, world) << endl;

   // Custom type
   X x1(20);
   X x2(22);
   X x3 = Plus(x1, x2);
   cout <<
      "x3.Dump() = " <<
      x3.Dump() << endl;
}
```

```Output
Plus(i, 9) = 13
Plus(dx, dy) = 13.5
Hello, world!
x3.Dump() = 42
```

## <a name="example"></a>Příklad

**Visual Studio 2017 a novější:** Kompilátor analyzuje argumenty decltype při deklaraci šablony namísto vytvoření instance. V důsledku toho, pokud je v argumentu decltype Nalezeno nezávislá specializace, nebude odložena k vytvoření instance a bude zpracována okamžitě a všechny výsledné chyby budou v tomto čase diagnostikovány.

Následující příklad ukazuje chybu kompilátoru, která je vyvolána v bodě deklarace:

```cpp
#include <utility>
template <class T, class ReturnT, class... ArgsT> class IsCallable
{
public:
   struct BadType {};
   template <class U>
   static decltype(std::declval<T>()(std::declval<ArgsT>()...)) Test(int); //C2064. Should be declval<U>
   template <class U>
   static BadType Test(...);
   static constexpr bool value = std::is_convertible<decltype(Test<T>(0)), ReturnT>::value;
};

constexpr bool test1 = IsCallable<int(), int>::value;
static_assert(test1, "PASS1");
constexpr bool test2 = !IsCallable<int*, int>::value;
static_assert(test2, "PASS2");
```

## <a name="requirements"></a>Požadavky

Visual Studio 2010 nebo novější verze.

`decltype(auto)` vyžaduje Visual Studio 2015 nebo novější.
