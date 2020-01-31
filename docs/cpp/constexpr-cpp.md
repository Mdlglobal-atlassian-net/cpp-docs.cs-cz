---
title: constexpr (C++)
description: Průvodce C++ jazykovým constexprovým klíčovým slovem
ms.date: 01/28/2020
f1_keywords:
- constexpr_cpp
ms.assetid: c6458ccb-51c6-4a16-aa61-f69e6f4e04f7
no-loc:
- constexpr
- const
- inline
- goto
- try
- if
- switch
- for
- while
ms.openlocfilehash: 4f34eef3217377ab50a2d80d42b5bea4b054c5be
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821776"
---
# <a name="opno-locconstexpr-c"></a>constexpr (C++)

Klíčové slovo **constexpr** bylo zavedeno v jazyce c++ 11 a v jazyce c++ 14 bylo vylepšeno. To znamená *konstantní výraz*. Stejně jako **const** lze použít na proměnné: Chyba kompilátoru je vyvolána, když se jakýkoliv kód pokusí změnit hodnotu. Na rozdíl od **const** lze **constexpr** také použít na funkce a konstruktory tříd. **constexpr** označuje, že hodnota nebo návratová hodnota je konstantní a pokud je to možné, vypočítává se v době kompilace.

**constexpr** celočíselnou hodnotu lze použít všude, kde je požadováno const celé číslo, například v argumentech šablony a deklaracích polí. A pokud je hodnota vypočítána v době kompilace namísto běhu, pomáhá programu běžet rychleji a používat méně paměti.

Pro omezení složitosti konstantních výpočtů v době kompilace a jejich možných dopadů na čas kompilace vyžaduje Standard C++ 14 typy v konstantních výrazech, aby byly [literální typy](trivial-standard-layout-and-pod-types.md#literal_types).

## <a name="syntax"></a>Syntaxe

> **constexpr** identifikátor *typu literálu* **=** *konstantní výraz* **;** \
> **constexpr** identifikátor *typu literálu* **{** *constant-expression* **}** **;** \
> **constexpr** identifikátor *typu literálu* **(** *params* **)** **;** \
> **constexpr** *ctor* **(** *params* **)** **;**

## <a name="parameters"></a>Parametry

\ *parametrů*
Jeden nebo více parametrů, z nichž každý musí být literálový typ a musí se jednat o konstantní výraz.

## <a name="return-value"></a>Návratová hodnota

**constexprová** proměnná nebo funkce musí vracet [typ literálu](trivial-standard-layout-and-pod-types.md#literal_types).

## <a name="opno-locconstexpr-variables"></a>proměnné constexpr

Hlavním rozdílem mezi **const** a **constexpr** proměnných je, že inicializace proměnné **const** může být odložena až do doby běhu. Proměnná **constexpr** musí být inicializována v době kompilace.  Všechny proměnné **constexpr** jsou **const** .

- Proměnnou lze deklarovat s **constexpr** , pokud má typ literálu a je inicializován. Pokud je inicializace provedena konstruktorem, musí být konstruktor deklarován jako **constexpr** .

- Odkaz může být deklarován jako **constexpr** , pokud jsou splněny obě tyto podmínky: odkazovaný objekt je inicializován konstantním výrazem a všechny implicitní převody vyvolané během inicializace jsou také konstantními výrazy.

- Všechny deklarace **constexpr** proměnné nebo funkce musí mít specifikátor **constexpr** .

```cpp
constexpr float x = 42.0;
constexpr float y{108};
constexpr float z = exp(5, 3);
constexpr int i; // Error! Not initialized
int j = 0;
constexpr int k = j + 1; //Error! j not a constant expression
```

## <a name="constexpr_functions"></a>funkce constexpr

Funkce **constexpr** je taková, jejíž návratová hodnota je COMPUTE v době kompilace, která vyžaduje použití kódu. Použití kódu vyžaduje vrácenou hodnotu v čase kompilace pro inicializaci **constexpr** proměnné nebo poskytnutí netypového argumentu šablony. Pokud jsou argumenty **constexpr** hodnoty, funkce **constexpr** vytvoří konstantu v čase kompilace. Při volání s **neconstexprmi** argumenty nebo když její hodnota není potřebná v době kompilace, vytvoří hodnotu v době běhu jako běžná funkce. (Toto duální chování šetří, abyste museli psát **constexpr** a **neconstexpr** verze stejné funkce.)

**constexpr** funkce nebo konstruktor je implicitně **inline** .

Následující pravidla se vztahují na funkce constexpr:

- Funkce **constexpr** musí přijmout a vracet pouze [typy literálů](trivial-standard-layout-and-pod-types.md#literal_types).

- Funkce **constexpr** může být rekurzivní.

- Nemůže být [virtuální](../cpp/virtual-cpp.md). Konstruktor nejde definovat jako **constexpr** , pokud má ohraničující třída nějaké virtuální základní třídy.

- Tělo lze definovat jako `= default` nebo `= delete`.

- Tělo nesmí obsahovat žádné příkazy **goto** ani bloky **try** .

- Explicitní specializace šablony bez **constexpr** se dá deklarovat jako **constexpr** :

- Explicitní specializace šablony **constexpr** nemusí být také **constexpr** :

Následující pravidla se vztahují na funkce **constexpr** v aplikaci Visual Studio 2017 a novější:

- Může obsahovat příkazy **if** a **switch** a všechny příkazy smyček, včetně **for** , **for** , **while** a **dowhile** na základě rozsahu.

- Může obsahovat deklarace místních proměnných, ale proměnná musí být inicializována. Musí se jednat o typ literálu a nemůže být **statický** nebo musí být místní vláknem. Místně deklarovaná proměnná není nutná **const** a může to být vhodné.

- Nestatickou členskou funkci **constexpr** není nutné implicitně **const** .

```cpp
constexpr float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
};
```

> [!TIP]
> V ladicím programu sady Visual Studio, při ladění neoptimalizovaného sestavení ladění, můžete určit, zda je funkce **constexpr** vyhodnocována v době kompilace vložením zarážky dovnitř. Pokud se zarážka zavolá, funkce byla volána v době běhu.  V takovém případě je funkce volána v době kompilace.

## <a name="extern-opno-locconstexpr"></a>externí constexpr

Možnost kompilátoru [/Zc: externConstexpr](../build/reference/zc-externconstexpr.md) způsobí, že kompilátor použije [vnější propojení](../c-language/external-linkage.md) na proměnné deklarované pomocí **extern constexpr** . V dřívějších verzích sady Visual Studio, buď ve výchozím nastavení, nebo je-li zadán parametr **/Zc: externConstexpr-** , aplikace Visual Studio použije vnitřní propojení na **constexpr** proměnné i v případě, že je použito klíčové slovo **extern** . Možnost **/Zc: externConstexpr** je k dispozici počínaje verzí Visual Studio 2017 Update 15,6 a je ve výchozím nastavení vypnutá. Možnost [/Permissive-](../build/reference/permissive-standards-conformance.md) nepovoluje **/Zc: externConstexpr**.

## <a name="example"></a>Příklad

Následující příklad ukazuje **constexpr** proměnných, funkcí a uživatelsky definovaného typu. V posledním příkazu v `main()`je členská funkce **constexpr** `GetValue()` volání za běhu, protože hodnota se nemusí v době kompilace znát.

```cpp
// constexpr.cpp
// Compile with: cl /EHsc /W4 constexpr.cpp
#include <iostream>

using namespace std;

// Pass by value
constexpr float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
};

// Pass by reference
constexpr float exp2(const float& x, const int& n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp2(x * x, n / 2) :
        exp2(x * x, (n - 1) / 2) * x;
};

// Compile-time computation of array length
template<typename T, int N>
constexpr int length(const T(&)[N])
{
    return N;
}

// Recursive constexpr function
constexpr int fac(int n)
{
    return n == 1 ? 1 : n * fac(n - 1);
}

// User-defined type
class Foo
{
public:
    constexpr explicit Foo(int i) : _i(i) {}
    constexpr int GetValue() const
    {
        return _i;
    }
private:
    int _i;
};

int main()
{
    // foo is const:
    constexpr Foo foo(5);
    // foo = Foo(6); //Error!

    // Compile time:
    constexpr float x = exp(5, 3);
    constexpr float y { exp(2, 5) };
    constexpr int val = foo.GetValue();
    constexpr int f5 = fac(5);
    const int nums[] { 1, 2, 3, 4 };
    const int nums2[length(nums) * 2] { 1, 2, 3, 4, 5, 6, 7, 8 };

    // Run time:
    cout << "The value of foo is " << foo.GetValue() << endl;
}
```

## <a name="requirements"></a>Požadavky

Visual Studio 2015 nebo novější.

## <a name="see-also"></a>Viz také:

[Deklarace a definice](../cpp/declarations-and-definitions-cpp.md)\
[const](../cpp/const-cpp.md)
