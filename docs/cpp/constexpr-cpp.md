---
title: constexpr (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 04/06/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- constexpr_cpp
dev_langs:
- C++
ms.assetid: c6458ccb-51c6-4a16-aa61-f69e6f4e04f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 150179fc0fd97450ba805d6957f5282bfaf8345c
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50071255"
---
# <a name="constexpr-c"></a>constexpr (C++)

Klíčové slovo **constexpr** byla zavedena v C ++ 11 a vylepšení v C ++ 14. To znamená, že *konstantní výraz*. Stejně jako **const**, ho můžete použít u proměnné tak, že pokud se žádný kód se pokusí změnit hodnotu, bude vyvolána chyba kompilátoru. Na rozdíl od **const**, **constexpr** můžete také použít pro funkce a třídy konstruktory. **constexpr** označuje, že hodnota nebo návratová hodnota je konstantní a, pokud je to možné, budou mít vypočítána v době kompilace.

A **constexpr** celočíselnou hodnotu je možné, bez ohledu na to se nevyžadují, jako například argumenty šablony a deklarace pole konstantní celé číslo. A pokud hodnotu nelze vypočítat v době kompilace místo běhu, pomáhají aplikace rychleji a použít méně paměti.

Pokud chcete omezit složitost výpočetní konstanty z doby kompilace a jejich potenciální dopad čas kompilace, C ++ 14 standard vyžaduje, aby typech účastnících konstantní výrazy s omezeným přístupem k [typy literálu](trivial-standard-layout-and-pod-types.md#literal_types).

## <a name="syntax"></a>Syntaxe

```
constexpr  literal-type  identifier = constant-expression;
constexpr  literal-type  identifier { constant-expression };
constexpr literal-type identifier(params );
constexpr ctor (params);
```

## <a name="parameters"></a>Parametry

*params*<br/>
Jeden nebo více parametrů, které musí být typu literálu a samotné musí být konstantní výraz.

## <a name="return-value"></a>Návratová hodnota

Proměnná constexpr nebo funkce musí vracet [typ literálu](trivial-standard-layout-and-pod-types.md#literal_types).

## <a name="constexpr-variables"></a>proměnné constexpr

Hlavní rozdíl mezi const a proměnné constexpr je inicializace konstantní proměnné může být odložena až do doby běhu, zatímco proměnné constexpr musí inicializovat v době kompilace.  Všechny proměnné constexpr jsou const.

- Proměnné mohou být deklarovány s **constexpr**, pokud má typ literálu a je inicializován. Pokud se inicializace provádí pomocí konstruktoru, konstruktor musí být deklarována jako **constexpr**.

- Odkaz mohou být deklarovány jako constexpr, pokud byl inicializován objekt, který odkazuje na výraz konstanty a všechny implicitní převody, které jsou vyvolány během inicializace jsou také výrazy konstant.

- Všechny deklarace **constexpr** proměnné nebo funkce musí mít **constexpr** specifikátor.

```cpp
constexpr float x = 42.0;
constexpr float y{108};
constexpr float z = exp(5, 3);
constexpr int i; // Error! Not initialized
int j = 0;
constexpr int k = j + 1; //Error! j not a constant expression
```

## <a name="constexpr_functions"></a> Funkce constexpr.

A **constexpr** funkce je taková, jejíž návratovou hodnotu nelze vypočítat při kompilaci při využívání kód vyžaduje.  Pokud argumenty jsou **constexpr** hodnoty a časově náročný kód vyžaduje hodnotu vrácenou v době kompilace, třeba když chcete inicializovat **constexpr** proměnné nebo zadat argument šablony bez typu, je Vytvoří konstantu kompilace. Při volání s jinou hodnotu než**constexpr** argumenty, nebo když jeho hodnota není vyžadována v době kompilace, vytvoří hodnotu v době běhu jako normální funkce.  (Toto chování duální vám ušetří od nutnosti psát **constexpr** a jiných-**constexpr** verze stejné funkce.)

A **constexpr** funkce nebo konstruktoru je implicitně **vložené**.

Funkce constexpr platí následující pravidla:

- A **constexpr** musí funkce přijímají a vrací pouze [typy literálu](trivial-standard-layout-and-pod-types.md#literal_types).

- A **constexpr** funkce mohou být rekurzivní.

- Nemůže být [virtuální](../cpp/virtual-cpp.md). A konstruktor nelze definovat jako constexpr, pokud má všechny virtuální základní třídy nadřazené třídy.

- Text může být definován jako `= default` nebo `= delete`.

- Text můžete neobsahuje žádné **goto** příkazy nebo bloky try.

- Explicitní specializace šablony, která není constexpr mohou být deklarovány jako **constexpr**:

- Explicitní specializace **constexpr** šablona nemá být také **constexpr**:

Následující pravidla platí pro **constexpr** funkce v sadě Visual Studio 2017 a novější:

- Může obsahovat **Pokud** a **přepnout** příkazů a všechny opakování příkazů, včetně **pro**, na základě rozsahu, **při**a **proveďte – zatímco**.

- Může obsahovat místní deklarace proměnných, ale proměnná musí být inicializován, musí být typu literálu a nemůže být statická nebo místního vlákna. Místně deklarované proměnné nemusí být konstantní a může změnit.

- Nestatická členská funkce constexpr není musí být implicitně const.

```cpp
constexpr float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
};
```

> [!TIP]
> Poznámka: V ladicím programu sady Visual Studio při ladění jiných úsporné laděné sestavení, můžete zjistit, jestli **constexpr** vyhodnocení funkce v době kompilace vložením zarážky dovnitř. Pokud je zarážka dosažena, byla volána funkce v době běhu.  Pokud ne, pak byla volána funkce v době kompilace.

## <a name="extern-constexpr"></a>extern constexpr

[/Zc: externconstexpr](../build/reference/zc-externconstexpr.md) – možnost kompilátoru způsobí, že kompilátor použije [vnější propojení]() k proměnné deklarované s použitím **extern constexpr**. V dřívějších verzích sady Visual Studio a ve výchozím nastavení nebo pokud **/Zc:externConstexpr-** není zadána, Visual Studio použije vnitřní propojení k **constexpr** i pokud proměnné **extern** klíčové slovo se používá. **/Zc: externconstexpr** možnost je k dispozici od verze Visual Studio 2017 Update 15.6. a je vypnuto ve výchozím nastavení. /Permissive-option/Zc: externconstexpr nepovolí.

## <a name="example"></a>Příklad

Následující příklad ukazuje **constexpr** proměnné, funkce a uživatelem definovaného typu. Všimněte si, že se v poslední příkaz v main(), **constexpr** členská funkce GetValue() je volání za běhu, protože hodnota nemusí být v době kompilace znám.

```cpp
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

// Compile time computation of array length
template<typename T, int N>
constexpr int length(const T(&ary)[N])
{
    return N;
}

// Recursive constexpr function
constexpr int fac(int n)
{
    return n == 1 ? 1 : n*fac(n - 1);
}

// User-defined type
class Foo
{
public:
    constexpr explicit Foo(int i) : _i(i) {}
    constexpr int GetValue()
    {
        return _i;
    }
private:
    int _i;
};

int main()
{
    //foo is const:
    constexpr Foo foo(5);
    // foo = Foo(6); //Error!

    //Compile time:
    constexpr float x = exp(5, 3);
    constexpr float y { exp(2, 5) };
    constexpr int val = foo.GetValue();
    constexpr int f5 = fac(5);
    const int nums[] { 1, 2, 3, 4 };
    const int nums2[length(nums) * 2] { 1, 2, 3, 4, 5, 6, 7, 8 };

    //Run time:
    cout << "The value of foo is " << foo.GetValue() << endl;

}
```

## <a name="requirements"></a>Požadavky

Visual Studio 2015

## <a name="see-also"></a>Viz také:

[Deklarace a definice](../cpp/declarations-and-definitions-cpp.md)<br/>
[const](../cpp/const-cpp.md)
