---
title: Automatické (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
f1_keywords:
- auto_CPP
- auto
helpviewer_keywords:
- auto keyword [C++]
ms.assetid: e9d495d7-601c-4547-b897-998389a311f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e832dfa694e5d2977e6b6a4d659d373f726c0cd6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059030"
---
# <a name="auto-c"></a>Automatické (C++)

Odvodí typ proměnné deklarované z jeho výrazu inicializace.

## <a name="syntax"></a>Syntaxe

```
auto declarator initializer;
```

```
[](auto param1, auto param2) {};
```

## <a name="remarks"></a>Poznámky

**Automaticky** – klíčové slovo instruuje kompilátor odvodit typ pomocí výrazu inicializace deklarovaná proměnná nebo parametr výrazu lambda.

Doporučujeme použít **automaticky** – klíčové slovo pro většinu situací – Pokud Opravdu chcete převod – protože tato funkce nabízí tyto výhody:

- **Odolnost:** při změně typu výrazu – jedná se o návratový typ funkce se při změně – prostě to funguje.

- **Výkon:** je zaručeno, že bude žádný převod.

- **Použitelnost:** nemusíte starat o typ název pravopisu potíže a překlepy.

- **Efektivita:** psaní kódu může být efektivnější.

Převod případy, ve kterých není vhodné používat **automaticky**:

- Když chcete určitého typu a nic jiného provede.

- Výraz šablona pomocné rutiny typů – například `(valarray+valarray)`.

Použít **automaticky** – klíčové slovo, použijte místo typu k deklaraci proměnné a zadejte výraz inicializace. Kromě toho můžete upravit **automaticky** – klíčové slovo pomocí kombinace specifikátorů a deklarátorů jako **const**, **volatile**, ukazatel (`*`), odkaz (`&`) a odkaz rvalue (`&&`). Kompilátor vyhodnotí výraz inicializace a tuto informaci následně používá k odvození typu proměnné.

Inicializační výraz může být přiřazením (syntaxe znaménka rovnosti), přímou inicializací (syntaxe stylu funkce), [operátor new](new-operator-cpp.md) může být výraz nebo výraz inicializace  *deklarace pro rozsah* parametr [Range-based for Statement (C++)](../cpp/range-based-for-statement-cpp.md) příkazu. Další informace najdete v tématu [inicializátory](../cpp/initializers.md) a příklady kódu dále v tomto dokumentu.

**Automaticky** – klíčové slovo je zástupný symbol pro typ, ale není samotného typu. Proto **automaticky** – klíčové slovo nelze použít v přetypování nebo operátorů, jako [sizeof](../cpp/sizeof-operator.md) a [typeid](../windows/typeid-cpp-component-extensions.md).

## <a name="usefulness"></a>Užitečnost

**Automaticky** – klíčové slovo je jednoduchý způsob, jak deklarovat proměnné, která má typ složité. Například můžete použít **automaticky** k deklaraci proměnné, kde výraz inicializace zahrnuje šablony, ukazatele na funkce a ukazatelů na členy.

Můžete také použít **automaticky** deklarovat a inicializovat proměnnou tak, výraz lambda. Typ proměnné nelze deklarovat sami vzhledem k tomu, že je pouze pro kompilátor známým typ výrazu lambda. Další informace najdete v tématu [Examples of Lambda Expressions](../cpp/examples-of-lambda-expressions.md).

## <a name="trailing-return-types"></a>Koncové návratové typy

Můžete použít **automaticky**společně s **decltype** specifikátor, abychom vytvářejí knihovny šablon typu. Použití **automaticky** a **decltype** k deklarování šablony funkce, jejíž návratový typ závisí na typech šablony argumentů. Nebo použijte **automaticky** a **decltype** k deklarování šablony funkce, která zabalí volání další funkce a potom vrátí cokoli, co je návratový typ této funkce. Další informace najdete v tématu [decltype](../cpp/decltype-cpp.md).

## <a name="references-and-cv-qualifiers"></a>Odkazy a kvalifikátory cv

Všimněte si, že při použití **automaticky** zahodí odkazy, kvalifikátory const a volatile kvalifikátory. Vezměte v úvahu v následujícím příkladu:

```cpp
// cl.exe /analyze /EHsc /W4
#include <iostream>

using namespace std;

int main( )
{
    int count = 10;
    int& countRef = count;
    auto myAuto = countRef;

    countRef = 11;
    cout << count << " ";

    myAuto = 12;
    cout << count << endl;
}

```

V předchozím příkladu myAuto je int, není odkaz na int, takže výstup je `11 11`, nikoli `11 12` jako by tomu bylo-li referenční kvalifikátor Loader vyřazen **automaticky**.

## <a name="type-deduction-with-braced-initializers-c14"></a>Odvození typu s inicializátory závorkách (C ++ 14)

Exmample následující kód ukazuje, jak inicializovat proměnnou automaticky pomocí závorek. Všimněte si rozdílu mezi B a C a mezi objekt a E.

```cpp
#include <initializer_list>

int main()
{
    // std::initializer_list<int>
    auto A = { 1, 2 };

    // std::initializer_list<int>
    auto B = { 3 };

    // int
    auto C{ 4 };

    // C3535: cannot deduce type for 'auto' from initializer list'
    auto D = { 5, 6.7 };

    // C3518 in a direct-list-initialization context the type for 'auto'
    // can only be deduced from a single initializer expression
    auto E{ 8, 9 };

    return 0;
}
```

## <a name="restrictions-and-error-messages"></a>Omezení a chybové zprávy

Následující tabulka uvádí omezení týkající se použití **automaticky** – klíčové slovo a odpovídající diagnostických chybovou zprávu, která generuje kompilátor.

|Číslo chyby|Popis|
|------------------|-----------------|
|[C3530](../error-messages/compiler-errors-2/compiler-error-c3530.md)|**Automaticky** – klíčové slovo se nedá kombinovat s jakékoli jiným specifikátorem typu.|
|[C3531](../error-messages/compiler-errors-2/compiler-error-c3531.md)|Symbol, který je deklarován s **automaticky** – klíčové slovo musí mít inicializátor.|
|[C3532](../error-messages/compiler-errors-2/compiler-error-c3532.md)|Nesprávně použitý **automaticky** – klíčové slovo pro deklaraci typu. Například deklarovaný návratový typ metody nebo pole.|
|[C3533](../error-messages/compiler-errors-2/compiler-error-c3533.md), [C3539](../error-messages/compiler-errors-2/compiler-error-c3539.md)|Argument parametru nebo šablony se nedá deklarovat pomocí **automaticky** – klíčové slovo.|
|[C3535](../error-messages/compiler-errors-2/compiler-error-c3535.md)|Parametr metody nebo šablony se nedá deklarovat pomocí **automaticky** – klíčové slovo.|
|[C3536](../error-messages/compiler-errors-2/compiler-error-c3536.md)|Symbol nelze použít před inicializací. V praxi to znamená, že proměnné nelze inicializovat.|
|[C3537](../error-messages/compiler-errors-2/compiler-error-c3537.md)|Nelze přetypovat na typ, který je deklarován s **automaticky** – klíčové slovo.|
|[C3538](../error-messages/compiler-errors-2/compiler-error-c3538.md)|Všechny symboly, která je deklarována pomocí deklarátoru seznam **automaticky** – klíčové slovo musí překládat stejného typu. Další informace najdete v tématu [deklarace a definice](declarations-and-definitions-cpp.md).|
|[C3540](../error-messages/compiler-errors-2/compiler-error-c3540.md), [C3541](../error-messages/compiler-errors-2/compiler-error-c3541.md)|[Sizeof](../cpp/sizeof-operator.md) a [typeid](../windows/typeid-cpp-component-extensions.md) operátory nejde použít u symbolu, který je deklarován s **automaticky** – klíčové slovo.|

## <a name="examples"></a>Příklady

Tyto fragmenty kódu ukazují některé ze způsobů, ve kterém **automaticky** – klíčové slovo lze použít.

Následující deklarace jsou ekvivalentní. V prvním příkazu proměnné `j` je deklarován jako typ **int**. V druhém příkazu proměnné `k` je rozpoznán jako typ **int** vzhledem k tomu, že výraz inicializace (0) je celé číslo.

```cpp
int j = 0;  // Variable j is explicitly type int.
auto k = 0; // Variable k is implicitly type int because 0 is an integer.
```

Následující deklarace jsou ekvivalentní, ale druhý deklarace je jednodušší než první. Jeden z nejpůsobivějších důvody pro použití **automaticky** – klíčové slovo je jednoduché.

```cpp
map<int,list<string>>::iterator i = m.begin();
auto i = m.begin();
```

Následující fragment kódu deklaruje typ proměnné `iter` a `elem` při **pro** a rozsah **pro** smyčky start.

```cpp
// cl /EHsc /nologo /W4
#include <deque>
using namespace std;

int main()
{
    deque<double> dqDoubleData(10, 0.1);

    for (auto iter = dqDoubleData.begin(); iter != dqDoubleData.end(); ++iter)
    { /* ... */ }

    // prefer range-for loops with the following information in mind
    // (this applies to any range-for with auto, not just deque)

    for (auto elem : dqDoubleData) // COPIES elements, not much better than the previous examples
    { /* ... */ }

    for (auto& elem : dqDoubleData) // observes and/or modifies elements IN-PLACE
    { /* ... */ }

    for (const auto& elem : dqDoubleData) // observes elements IN-PLACE
    { /* ... */ }
}
```

Následující fragment kódu používá **nové** operátor a ukazatel deklarace deklarovat ukazatele.

```cpp
double x = 12.34;
auto *y = new auto(x), **z = new auto(&x);
```

Další fragment kódu deklaruje několik symboly v každém výroku deklarace. Všimněte si, že všechny symboly v každém výroku vyřešit stejného typu.

```cpp
auto x = 1, *y = &x, **z = &y; // Resolves to int.
auto a(2.01), *b (&a);         // Resolves to double.
auto c = 'a', *d(&c);          // Resolves to char.
auto m = 1, &n = m;            // Resolves to int.
```

Tento fragment kódu používá podmíněný operátor (`?:`) Chcete-li deklarovat proměnnou `x` jako celé číslo, které má hodnotu 200:

```cpp
int v1 = 100, v2 = 200;
auto x = v1 > v2 ? v1 : v2;
```

Následující fragment kódu inicializuje proměnnou `x` na typ **int**variabilní `y` na odkaz na typ **const int**a proměnnou `fp` na ukazatel na funkci který vrátí typ **int**.

```cpp
int f(int x) { return x; }
int main()
{
    auto x = f(0);
    const auto & y = f(1);
    int (*p)(int x);
    p = f;
    auto fp = p;
    //...
}
```

## <a name="see-also"></a>Viz také:

[Auto – klíčové slovo](../cpp/auto-keyword.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[/Zc:auto (odvození typu proměnné)](../build/reference/zc-auto-deduce-variable-type.md)<br/>
[sizeof – operátor](../cpp/sizeof-operator.md)<br/>
[identifikátor TypeId.](../windows/typeid-cpp-component-extensions.md)<br/>
[new – operátor](new-operator-cpp.md)<br/>
[Deklarace a definice](declarations-and-definitions-cpp.md)<br/>
[Příklady výrazů lambda](../cpp/examples-of-lambda-expressions.md)<br/>
[Inicializátory](../cpp/initializers.md)<br/>
[decltype](../cpp/decltype-cpp.md)