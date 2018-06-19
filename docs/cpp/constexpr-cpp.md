---
title: constexpr (C++) | Microsoft Docs
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
ms.openlocfilehash: 1f95f6c98138ff1eb52750c1b8593795ca28c784
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32417994"
---
# <a name="constexpr-c"></a>constexpr (C++)

Klíčové slovo **constexpr** byla zavedená v C ++ 11 a vylepšené v C ++ 14. Znamená to, *konstantní výraz*. Jako **const**, může platit pro proměnné tak, že pokud se kód, se pokusí změnit hodnotu, bude vyvolána chyba kompilátoru. Na rozdíl od **const**, **constexpr** lze použít také k funkcím a třídy konstruktory. **constexpr** označuje, že hodnota nebo vrací hodnotu, je konstantní a, pokud je to možné, se automaticky spočítá v době kompilace.

A **constexpr** celočíselné hodnoty lze použít, kdykoli je to požadováno, například v šabloně argumentů a deklarace pole const celé číslo. A pokud v době kompilace místo běhu můžete vypočítat hodnotu, může pomoci váš program spouštět rychleji a používat méně paměti.

Pokud chcete omezit složitosti výpočetní konstanty doba kompilace a jejich potenciální ovlivňuje dobu kompilace, C ++ 14 standardní vyžaduje, aby účastnící se konstantní výrazy typy omezen na [typy literálu](trivial-standard-layout-and-pod-types.md#literal_types).

## <a name="syntax"></a>Syntaxe

```
constexpr  literal-type  identifier = constant-expression;
constexpr  literal-type  identifier { constant-expression };
constexpr literal-type identifier(params );
constexpr ctor (params);
```

## <a name="parameters"></a>Parametry

 *params*  
Jeden nebo více parametrů, které musí být typu literálu a sám sebe musí být konstantní výraz.

## <a name="return-value"></a>Návratová hodnota


 Constexpr proměnné nebo funkce musí vracet [typu literálu](trivial-standard-layout-and-pod-types.md#literal_types).

## <a name="constexpr-variables"></a>constexpr proměnné

 Hlavní rozdíl mezi const a constexpr proměnné je inicializace const proměnné může být odložen až při spuštění, zatímco v době kompilace se musí inicializovat proměnnou constexpr.  Const jsou všechny proměnné constexpr.

- Proměnné lze deklarovat s **constexpr**, pokud se typ literálu a je inicializován. Pokud se inicializace provádí pomocí konstruktoru, konstruktor musí být deklarována jako **constexpr**.

- Odkaz může být deklarován jako constexpr, pokud objekt, který odkazuje na byl inicializován nástrojem konstantní výraz a všechny implicitní převody, které jsou vyvolány během inicializace jsou také konstantní výrazy.

- Všechny deklarace **constexpr** proměnné nebo funkce musí mít **constexpr** specifikátor.

```cpp
constexpr float x = 42.0;
constexpr float y{108};
constexpr float z = exp(5, 3);
constexpr int i; // Error! Not initialized
int j = 0;
constexpr int k = j + 1; //Error! j not a constant expression
```

## <a name="constexpr_functions"></a> Funkce constexpr

A **constexpr** funkce je taková, jejíž návratovou hodnotu můžete vypočítat v kompilaci při použití kódu vyžaduje.  Při jeho argumenty jsou **constexpr** hodnoty a využívání kódu vyžaduje návratovou hodnotu při kompilaci, např. k chybě při inicializaci **constexpr** proměnné nebo zadejte jiný typ šablony argument, je Vytvoří kompilaci konstanta. Při volání s jinou hodnotu než**constexpr** argumenty, nebo když její hodnota není požadovaná při kompilaci, vytvoří hodnotu v době běhu jako normální funkce.  (Toto chování duální odběratelské zápis **constexpr** a jiných-**constexpr** verze stejné funkce.)

A **constexpr** funkce nebo konstruktor je implicitně **vložené**.

Následující pravidla platí při constexpr funkce:

- A **constexpr** funkce musíte přijmout a vrátit pouze [typy literálu](trivial-standard-layout-and-pod-types.md#literal_types).

- A **constexpr** funkce může být rekurzivní.

- Nemůže být [virtuální](../cpp/virtual-cpp.md). A konstruktor nelze definovat jako constexpr, pokud nadřazených třída nemá žádné virtuální základní třídy.

- Text může být definováno jako **= výchozí** nebo **= odstranění**.

- Text může obsahovat žádné **goto** příkazy nebo bloky try.

- Explicitní specializace šablony bez constexpr lze deklarovat jako **constexpr**:

- Explicitní specializace **constexpr** šablona nemá být také **constexpr**:

Následující pravidla platí při **constexpr** funkce Visual Studio 2017 a novější:

- Může obsahovat **Pokud** a **přepínač** příkazy a všechny příkazy smyček včetně **pro**, na základě rozsahu, **při**a **udělat-při**.
 
- Může obsahovat místní deklarace proměnných, ale proměnná musí být inicializován, musí být typu literálu a nemůže být statické nebo místní. Proměnná lokálně deklarovaný nemusí být const a může změnit.

- Nestatické členské funkce constexpr nemusí být implicitně const.


```cpp
constexpr float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
};
```

> [!TIP]
> Poznámka: V ladicím programu sady Visual Studio, ladění jiných optimalizované ladění sestavení, můžete zjistit, jestli **constexpr** funkce je vyhodnocovaný v době kompilace umístěním zarážku uvnitř ho. Pokud je průchodu zarážkou, funkce byla volána při spuštění.  Pokud ne, pak byla zavolána funkce v době kompilace.

## <a name="extern-constexpr"></a>extern constexpr

[/Zc:externConstexpr](../build/reference/zc-externconstexpr.md) – možnost kompilátoru způsobí, že kompilátor použít [externí propojení]() do proměnných deklarovaných pomocí **extern constexpr**. V dřívějších verzích sady Visual Studio a ve výchozím nastavení nebo, pokud **/Zc:externConstexpr-** není zadaný, Visual Studio použije vnitřní propojení na **constexpr** proměnné, i když **extern** – klíčové slovo se používá. **/Zc:externConstexpr** možnost je k dispozici od 15,6 operací aktualizace 2017 Visual Studio. a ve výchozím nastavení. /Permissive-option neumožňuje /Zc:externConstexpr.

## <a name="example"></a>Příklad

 Následující příklad ukazuje **constexpr** proměnné, funkce a uživatelsky definovaný typ. Všimněte si, že se v poslední příkaz v main(), **constexpr** – členská funkce GetValue() je volání spuštění, protože hodnota nemusí být známé v době kompilace.

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

## <a name="see-also"></a>Viz také

- [Deklarace a definice](../cpp/declarations-and-definitions-cpp.md)
- [const](../cpp/const-cpp.md)
