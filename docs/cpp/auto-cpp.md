---
title: auto (C++)
ms.date: 12/10/2019
f1_keywords:
- auto_CPP
- auto
helpviewer_keywords:
- auto keyword [C++]
ms.assetid: e9d495d7-601c-4547-b897-998389a311f4
ms.openlocfilehash: 0991c836d1ade663be3e1b734ec4745796b91abd
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301649"
---
# <a name="auto-c"></a>auto (C++)

Odvodit typ deklarované proměnné z inicializačního výrazu.

> [!NOTE]
> C++ Standard definuje původní a přepracovaný význam tohoto klíčového slova. Před Visual Studio 2010, klíčové slovo **auto** deklaruje proměnnou v *Automatické* třídě úložiště; To znamená, že proměnná, která má místní životnost. Počínaje sadou Visual Studio 2010, klíčové slovo **auto** deklaruje proměnnou, jejíž typ je odvozen z inicializačního výrazu ve své deklaraci. Možnost [/Zc: auto&#91;-&#93; ](../build/reference/zc-auto-deduce-variable-type.md) Compiler řídí význam klíčového slova **auto** .

## <a name="syntax"></a>Syntaxe

```
auto declarator initializer;
```

```
[](auto param1, auto param2) {};
```

## <a name="remarks"></a>Poznámky

Klíčové slovo **auto** přesměruje kompilátor na použití inicializačního výrazu deklarované proměnné nebo parametru výrazu lambda pro odvození jeho typu.

Doporučujeme, abyste pro většinu situací použili klíčové slovo **auto** – Pokud to opravdu nechcete, protože poskytuje tyto výhody:

- **Odolnost:** Pokud se změní typ výrazu, zahrnuje to, kdy se změní návratový typ funkce, ale funguje.

- **Výkon:** Zaručujeme, že nebude k dispozici žádný převod.

- **Použitelnost:** Nemusíte se starat o problémy se pravopisem typu a překlepy.

- **Efektivita:** Vaše kódování může být efektivnější.

Případy převodu, ve kterých pravděpodobně nechcete používat **auto**:

- Pokud budete chtít konkrétní typ a nic jiného.

- Typy pomocných šablon výrazů – například `(valarray+valarray)`.

Chcete-li použít klíčové slovo **auto** , použijte jej místo typu k deklaraci proměnné a určení inicializačního výrazu. Kromě toho můžete změnit klíčové slovo **auto** pomocí specifikátorů a deklarátory, jako je **const**, **volatile**, ukazatel (`*`), Reference (`&`) a odkaz rvalue (`&&`). Kompilátor vyhodnocuje inicializační výraz a poté používá tyto informace k odvození typu proměnné.

Inicializační výraz může být přiřazením (se znaménkem rovnosti), přímou inicializací (syntaxí Function-Style), [operátorem New](new-operator-cpp.md) nebo výrazem inicializace může být parametr *for-range-declaration* v [rozsahu příkazu pro příkaz (C++) založený na rozsahu](../cpp/range-based-for-statement-cpp.md) . Další informace naleznete v části [Inicializátory](../cpp/initializers.md) a příklady kódu dále v tomto dokumentu.

Klíčové slovo **auto** je zástupný symbol pro typ, ale nejedná se o typ. Proto klíčové slovo **auto** nelze použít v přetypováních nebo operátorech, jako je [sizeof](../cpp/sizeof-operator.md) a ( C++pro/CLI) [typeid](../extensions/typeid-cpp-component-extensions.md).

## <a name="usefulness"></a>Užitečnost

Klíčové slovo **auto** je jednoduchý způsob, jak deklarovat proměnnou, která má složitý typ. Můžete například použít **auto** k deklaraci proměnné, kde výraz inicializace zahrnuje šablony, ukazatele na funkce nebo ukazatele na členy.

Můžete také použít **auto** k deklaraci a inicializaci proměnné pro lambda výraz. Typ proměnné nelze deklarovat sami, protože typ výrazu lambda je známý pouze pro kompilátor. Další informace naleznete v tématu [Příklady výrazů lambda](../cpp/examples-of-lambda-expressions.md).

## <a name="trailing-return-types"></a>Koncové návratové typy

Můžete použít **auto**společně se specifikátorem typu **decltype** pro psaní knihoven šablon. Použijte **auto** a **decltype** k deklarování šablony funkce, jejíž návratový typ závisí na typech svých argumentů šablony. Nebo použijte **auto** a **decltype** k deklaraci funkce šablony, která zabalí volání jiné funkce, a potom vrátí jakýkoli typ návratové hodnoty této jiné funkce. Další informace naleznete v tématu [decltype](../cpp/decltype-cpp.md).

## <a name="references-and-cv-qualifiers"></a>Odkazy a kvalifikátory cv

Všimněte si, že používáte **Automatické** přehození odkazů, kvalifikátory const a kvalifikátory volatile. Vezměte v úvahu v následujícím příkladu:

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

V předchozím příkladu je myAuto int, nikoli odkaz int, takže výstup je `11 11`, nikoli `11 12` jako by byl případ, pokud kvalifikátor odkazu nebyl **automaticky**vyřazen.

## <a name="type-deduction-with-braced-initializers-c14"></a>Srážky typu u inicializátorů v závorkách (C++ 14)

Následující příklad kódu ukazuje, jak inicializovat auto proměnnou pomocí složených závorek. Všimněte si rozdílu mezi B a C a mezi a a E.

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

V následující tabulce jsou uvedena omezení použití klíčového slova **auto** a odpovídající diagnostická chybová zpráva, kterou kompilátor generuje.

|Číslo chyby|Popis|
|------------------|-----------------|
|[C3530](../error-messages/compiler-errors-2/compiler-error-c3530.md)|Klíčové slovo **auto** nelze kombinovat s žádným jiným specifikátorem typu.|
|[C3531](../error-messages/compiler-errors-2/compiler-error-c3531.md)|Symbol deklarovaný s klíčovým slovem **auto** musí mít inicializátor.|
|[C3532](../error-messages/compiler-errors-2/compiler-error-c3532.md)|Nesprávně jste použili klíčové slovo **auto** k deklaraci typu. Například jste deklarovali návratový typ metody nebo pole.|
|[C3533](../error-messages/compiler-errors-2/compiler-error-c3533.md), [C3539](../error-messages/compiler-errors-2/compiler-error-c3539.md)|Parametr nebo argument šablony nelze deklarovat pomocí klíčového slova **auto** .|
|[C3535](../error-messages/compiler-errors-2/compiler-error-c3535.md)|Metodu nebo parametr šablony nelze deklarovat pomocí klíčového slova **auto** .|
|[C3536](../error-messages/compiler-errors-2/compiler-error-c3536.md)|Symbol nelze použít před inicializací. V praxi to znamená, že proměnnou nelze použít k inicializaci samotného.|
|[C3537](../error-messages/compiler-errors-2/compiler-error-c3537.md)|Nemůžete přetypovat na typ, který je deklarovaný pomocí klíčového slova **auto** .|
|[C3538](../error-messages/compiler-errors-2/compiler-error-c3538.md)|Všechny symboly v seznamu deklarátor deklarované s klíčovým slovem **auto** se musí přeložit na stejný typ. Další informace najdete v tématu [deklarace a definice](declarations-and-definitions-cpp.md).|
|[C3540](../error-messages/compiler-errors-2/compiler-error-c3540.md), [C3541](../error-messages/compiler-errors-2/compiler-error-c3541.md)|Operátory [sizeof](../cpp/sizeof-operator.md) a [typeid](../extensions/typeid-cpp-component-extensions.md) nelze použít pro symbol deklarovaný pomocí klíčového slova **auto** .|

## <a name="examples"></a>Příklady

Tyto fragmenty kódu ilustrují některé způsoby, jak lze použít klíčové slovo **auto** .

Následující deklarace jsou ekvivalentní. V prvním příkazu je proměnná `j` deklarována jako typ **int**. V druhém příkazu je proměnná `k` odvozena na typ **int** , protože inicializační výraz (0) je celé číslo.

```cpp
int j = 0;  // Variable j is explicitly type int.
auto k = 0; // Variable k is implicitly type int because 0 is an integer.
```

Následující deklarace jsou ekvivalentní, ale druhá deklarace je jednodušší než první. Jedním z nejvýraznějších důvodů použití klíčového slova **auto** je jednoduchost.

```cpp
map<int,list<string>>::iterator i = m.begin();
auto i = m.begin();
```

Následující fragment kódu deklaruje typ proměnných `iter` a `elem` při zahájení cyklu **for** a rozsah **pro** smyčky.

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

Následující fragment kódu používá deklaraci **New** operátor a ukazatel na deklaraci ukazatelů.

```cpp
double x = 12.34;
auto *y = new auto(x), **z = new auto(&x);
```

Další fragment kódu deklaruje více symbolů v každém příkazu deklarace. Všimněte si, že všechny symboly v každém příkazu jsou přeloženy na stejný typ.

```cpp
auto x = 1, *y = &x, **z = &y; // Resolves to int.
auto a(2.01), *b (&a);         // Resolves to double.
auto c = 'a', *d(&c);          // Resolves to char.
auto m = 1, &n = m;            // Resolves to int.
```

Tento fragment kódu používá podmíněný operátor (`?:`) k deklaraci proměnné `x` jako celé číslo, které má hodnotu 200:

```cpp
int v1 = 100, v2 = 200;
auto x = v1 > v2 ? v1 : v2;
```

Následující fragment kódu inicializuje proměnnou `x` pro typ **int**, proměnná `y` na odkaz pro typ **const int**a proměnnou `fp` na ukazatel na funkci vracející typ **int**.

```cpp
int f(int x) { return x; }
int main()
{
    auto x = f(0);
    const auto& y = f(1);
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
[typeid](../extensions/typeid-cpp-component-extensions.md)<br/>
[New – operátor](new-operator-cpp.md)<br/>
[Deklarace a definice](declarations-and-definitions-cpp.md)<br/>
[Příklady výrazů lambda](../cpp/examples-of-lambda-expressions.md)<br/>
[Inicializátory](../cpp/initializers.md)<br/>
[decltype](../cpp/decltype-cpp.md)
