---
title: constexpr (C++)
ms.date: 08/05/2019
f1_keywords:
- constexpr_cpp
ms.assetid: c6458ccb-51c6-4a16-aa61-f69e6f4e04f7
ms.openlocfilehash: 5c98436f537b34b1c9050e057971938d48792db1
ms.sourcegitcommit: c3bf94210bdb73be80527166264d49e33784152c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2019
ms.locfileid: "68821096"
---
# <a name="constexpr-c"></a>constexpr (C++)

Klíčové slovo **constexpr** bylo představeno v jazyce c++ 11 a vylepšeno v jazyce c++ 14. To znamená *konstantní výraz*. Podobnějako const, lze použít na proměnné, aby byla vyvolána chyba kompilátoru, pokud se jakýkoliv kód pokusí změnit hodnotu. Na rozdílod const lze použít **constexpr** také na funkce a konstruktory tříd. **constexpr** označuje, že hodnota nebo návratová hodnota je konstantní a pokud je to možné, vypočítává se v době kompilace.

Celočíselnou hodnotu **constexpr** lze použít všude, kde je vyžadováno konstantní celé číslo, například v argumentech šablony a deklaracích polí. A pokud je možné hodnotu vypočítat v době kompilace namísto běhu, může vám program rychleji běžet a používat méně paměti.

Pro omezení složitosti konstantních výpočtů v době kompilace a jejich možných dopadů na čas kompilace vyžaduje Standard C++ 14 typy v konstantních výrazech, aby byly [literální typy](trivial-standard-layout-and-pod-types.md#literal_types).

## <a name="syntax"></a>Syntaxe

> **constexpr** *typem literálu* *identifikátor* **=** *konstantní výraz* **;** 
>  **constexpr** *typem literálu* *identifikátor* **{** *konstantního výrazu.* **}** **;** 
>  **constexpr** *typem literálu* *identifikátor* **(** *params* **)** **;** 
>  **constexpr** *ctor* **(** *params* **)** **;**

## <a name="parameters"></a>Parametry

*params*<br/>
Jeden nebo více parametrů, z nichž každý musí být literálový typ a musí se jednat o konstantní výraz.

## <a name="return-value"></a>Návratová hodnota

Proměnná nebo funkce constexpr musí vracet [typ literálu](trivial-standard-layout-and-pod-types.md#literal_types).

## <a name="constexpr-variables"></a>proměnné constexpr

Hlavním rozdílem mezi konstantami const a constexpr je, že inicializace proměnné const může být odložena až do doby běhu. V době kompilace musí být inicializována proměnná constexpr.  Všechny proměnné constexpr jsou const.

- Proměnnou lze deklarovat pomocí **constexpr**, pokud má typ literálu a je inicializován. Pokud je inicializace provedena konstruktorem, musí být konstruktor deklarován jako **constexpr**.

- Odkaz může být deklarován jako constexpr, pokud objekt, na který odkazuje, byl inicializován konstantním výrazem a všechny implicitní převody, které jsou vyvolány během inicializace, jsou také konstantními výrazy.

- Všechny deklarace proměnné nebo funkce **constexpr** musí mít specifikátor **constexpr** .

```cpp
constexpr float x = 42.0;
constexpr float y{108};
constexpr float z = exp(5, 3);
constexpr int i; // Error! Not initialized
int j = 0;
constexpr int k = j + 1; //Error! j not a constant expression
```

## <a name="constexpr_functions"></a>funkce constexpr

Funkce **constexpr** je taková, jejíž návratová hodnota může být počítána v době kompilace, pokud vyžaduje použití kódu. Používání kódu vyžaduje vrácenou hodnotu v době kompilace, například pro inicializaci proměnné **constexpr** nebo poskytnutí netypového argumentu šablony. Pokud jsou argumenty hodnoty **constexpr** , funkce **constexpr** vytvoří konstantu v čase kompilace. Při volání s jinými argumenty než**constexpr** nebo když její hodnota není potřebná v době kompilace, vytvoří hodnotu v době běhu, jako je obvyklá funkce. (Toto duální chování šetří, abyste museli psát **Modifikátor constexpr** a jiné verze než**constexpr** .)

Funkce **constexpr** nebo konstruktor je implicitně **vložená**.

Následující pravidla platí pro funkce constexpr:

- Funkce **constexpr** musí přijmout a vracet jenom [typy literálů](trivial-standard-layout-and-pod-types.md#literal_types).

- Funkce **constexpr** může být rekurzivní.

- Nemůže být [virtuální](../cpp/virtual-cpp.md). Konstruktor nemůže být definován jako constexpr, pokud má ohraničující třída nějaké virtuální základní třídy.

- Tělo lze definovat jako `= default` nebo. `= delete`

- Tělo nemůže obsahovat příkazy **goto** ani bloky try.

- Explicitní specializace šablony jiného typu než constexpr může být deklarovaná jako **constexpr**:

- Explicitní specializace šablony **constexpr** nemusí být zároveň **constexpr**:

Následující pravidla platí pro funkce **constexpr** v aplikaci Visual Studio 2017 a novější:

- Může obsahovat příkazy **if** a **Switch** a všechny příkazy smyček, včetně **pro**, v rozsahu založeném na rozsahu, **while**av.

- Může obsahovat deklarace místních proměnných, ale proměnná musí být inicializována, musí být typu literál a nemůže být statická nebo místní vlákna. Místně deklarovaná proměnná není vyžadována jako const a může být povinná.

- Nestatická členská funkce constexpr není nutná implicitně const.

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

## <a name="extern-constexpr"></a>externí constexpr

Možnost kompilátoru [/Zc: externConstexpr](../build/reference/zc-externconstexpr.md) způsobí, že kompilátor použije [vnější propojení](../c-language/external-linkage.md) na proměnné deklarované pomocí **extern constexpr**. V dřívějších verzích sady Visual Studio a ve výchozím nastavení, nebo pokud je zadán parametr **/Zc: externConstexpr-** , aplikace Visual Studio aplikuje vnitřní propojení na proměnné **constexpr** , i když je použito klíčové slovo **extern** . Možnost **/Zc: externConstexpr** je k dispozici počínaje verzí Visual Studio 2017 Update 15,6 a je ve výchozím nastavení vypnutá. Možnost/Permissive-nepovoluje **/Zc: externConstexpr**.

## <a name="example"></a>Příklad

Následující příklad ukazuje proměnné **constexpr** , funkce a uživatelsky definovaný typ. V posledním příkazu v Main () je členská funkce **constexpr** GetValue () volána za běhu, protože hodnotu není nutné znát v době kompilace.

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
