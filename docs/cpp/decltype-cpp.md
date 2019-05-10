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
ms.openlocfilehash: 0a4e9eb015df056dfe2a35da18cfa50875ced432
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222455"
---
# <a name="decltype--c"></a>decltype (C++)

**Decltype** specifikátor typu vrací typ zadaného výrazu. **Decltype** specifikátor, spolu s typu [auto – klíčové slovo](../cpp/auto-cpp.md), je užitečný především pro vývojáře, kteří vytvářejí knihovny šablon. Použití **automaticky** a **decltype** k deklarování šablony funkce, jejíž návratový typ závisí na typech šablony argumentů. Nebo použijte **automaticky** a **decltype** k deklarování šablony funkce, která zabalí volání další funkce a potom vrátí návratový typ zabalené funkce.

## <a name="syntax"></a>Syntaxe

```
decltype( expression )
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Výraz*|Výraz. Další informace najdete v tématu [výrazy](../cpp/expressions-cpp.md).|

## <a name="return-value"></a>Návratová hodnota

Typ *výraz* parametru.

## <a name="remarks"></a>Poznámky

**Decltype** specifikátor typu je podporováno v sadě Visual Studio 2010 nebo novější verze a jde použít s nativním nebo spravovaným kódem. `decltype(auto)` (C ++ 14) je podporováno v sadě Visual Studio 2015 a novější.

Kompilátor používá následující pravidla pro určení typu *výraz* parametru.

- Pokud *výraz* parametr je identifikátor nebo [přístup ke členům třídy](../cpp/member-access-operators-dot-and.md), `decltype(expression)` je typ entity s názvem *výraz*. Pokud není žádná taková entita nebo *výraz* názvy parametrů sadu přetížených funkcí, vrátí kompilátor chybovou zprávu.

- Pokud *výraz* volání funkce nebo funkce přetíženého operátoru, je parametr `decltype(expression)` je návratový typ funkce. Závorky kolem přetíženého operátoru jsou ignorovány.

- Pokud *výraz* parametr je [rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md), `decltype(expression)` je typ *výraz*. Pokud *výraz* parametr je [l-hodnoty](../cpp/lvalues-and-rvalues-visual-cpp.md), `decltype(expression)` je [odkaz lvalue](../cpp/lvalue-reference-declarator-amp.md) typu *výraz*.

Následující příklad kódu ukazuje některá použití **decltype** specifikátoru typu. Nejprve předpokládejme, že jste nakódovali následující příkazy.

```cpp
int var;
const int&& fx();
struct A { double x; }
const A* a = new A();
```

Dále zkontrolujte typy, které jsou vráceny pomocí čtyř **decltype** příkazy v následující tabulce.

|Příkaz|Type|Poznámky|
|---------------|----------|-----------|
|`decltype(fx());`|`const int&&`|[Odkaz rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) k **const int**.|
|`decltype(var);`|**int**|Typ proměnné `var`.|
|`decltype(a->x);`|**double**|Typ přístupu členu.|
|`decltype((a->x));`|`const double&`|Vnitřní závorky způsobí, že je příkaz vyhodnocen jako výraz namísto přístupu ke členu. A protože `a` je deklarován jako `const` ukazatele, typ je odkaz na **const double**.|

## <a name="decltype-and-auto"></a>Klíčová slova Decltype a Auto

V C ++ 14, můžete použít `decltype(auto)` bez koncové návratového typu k deklarování šablony funkce, jejíž návratový typ závisí na typech šablony argumentů.

V C ++ 11, můžete použít **decltype** specifikátor na koncovým návratovým typem, spolu s typu **automaticky** – klíčové slovo k deklarování šablony funkce, jejíž návratový typ závisí na typech šablony argumenty. Zvažte například následující příklad kódu, ve kterém návratový typ šablony funkce závisí na typech šablony argumentů. V příkladu kódu *neznámý* zástupný text označuje, že návratový typ nelze zadat.

```cpp
template<typename T, typename U>
UNKNOWN func(T&& t, U&& u){ return t + u; };
```

Po zavedení služby **decltype** specifikátor typu umožňuje vývojáři získat typ výrazu, který šablona funkce vrátí. Použití *alternativní syntaxi deklarace funkce* , která je uvedena dále, **automaticky** – klíčové slovo a **decltype** specifikátor pro deklaraci typu  *pozdně zadaný* návratového typu. Pozdně určený návratový typ je určen při kompilaci deklarace, nikoli když je kódován.

Následující prototyp znázorňuje syntaxi alternativní deklarace funkce. Všimněte si, že **const** a **volatile** kvalifikátory a **throw** [specifikace výjimky](../cpp/exception-specifications-throw-cpp.md) jsou volitelné. *Function_body* zástupný text představuje složený příkaz, který určuje, co funkce dělá. Osvědčeným postupem je *výraz* zástupný symbol v **decltype** příkazu by měl odpovídat výrazu určeném příkazem **vrátit** příkazu, pokud existují v *function_body*.

**Automatické** *Název_funkce* **(** *parametry*<sub>optimalizované</sub> **)**  **Const**<sub>optimalizované</sub> **volatile**<sub>optimalizované</sub> **->** **decltype (** *výraz* **)** **throw**<sub>optimalizované</sub> **{** *function_body* **};**

V následujícím příkladu kódu je pozdně zadaný návratový typ šablony funkce `myFunc` určen pomocí typů `t` a `u` šablony argumentů. Osvědčeným postupem, příklad kódu používá také odkazy na r-hodnoty a `forward` šablony funkce, které podporují *perfektní přesměrování*. Další informace najdete v tématu [Rvalue Reference Declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

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

## <a name="decltype-and-forwarding-functions-c11"></a>Klíčové slovo decltype a přesměrování funkce (C ++ 11)

Funkce předávání zaobalují volání dalších funkcí. Zvažte šablonu funkce, která předává své argumenty nebo výsledky výrazu, který zahrnuje tyto argumenty, jiné funkci. Kromě toho funkce předávání vrátí výsledek volání další funkce. V tomto scénáři by měl návratový typ funkce předávání být stejný jako návratový typ zabalené funkce.

V tomto scénáři nelze odpovídající typ výrazu bez zapisovat **decltype** specifikátoru typu. **Decltype** specifikátor typu umožňuje obecné funkce předávání, protože neztratí požadované informace o tom, zda funkce vrací typ reference. Příklad kódu funkce předávání naleznete v předchozím příkladu šablony funkce `myFunc`.

## <a name="example"></a>Příklad

Následující příklad kódu deklaruje pozdně zadaný návratový typ šablony funkce `Plus()`. `Plus` Funkce zpracuje své dva operandy s **operátor +** přetížení. V důsledku toho interpretace operátoru plus (+) a návratový typ funkce `Plus` závisí na typech argumentů funkce.

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

**Visual Studio 2017 a novější:** Kompilátor analyzuje decltype argumenty při šablony jsou deklarovány, nikoli vytvořena instance. V důsledku toho pokud nezávislé specializace je nalezena v argument pro decltype, nesmí být odložena na čas vytvoření instance a bude potřeba zpracovat okamžitě a všechny případné chyby se zjistit, v daném čase.

Následující příklad ukazuje takový chybu kompilátoru, která je vyvolána v okamžiku deklarace:

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