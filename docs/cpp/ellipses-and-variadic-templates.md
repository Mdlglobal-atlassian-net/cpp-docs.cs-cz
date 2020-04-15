---
title: Tři tečky a variadické šablony
ms.date: 11/04/2016
ms.assetid: f20967d9-c967-4fd2-b902-2bb1d5ed87e3
ms.openlocfilehash: 358cdeeaf6f3e8c7f7841bbc796eca6557ccd145
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366342"
---
# <a name="ellipses-and-variadic-templates"></a>Tři tečky a variadické šablony

Tento článek ukazuje, jak používat`...`tři tečky ( ) s variadické šablony Jazyka C++. Tři tečky má mnoho použití v Jazyce C a C++. Patří mezi ně seznamy proměnných argumentů pro funkce. Funkce `printf()` z knihovny C Runtime je jedním z nejznámějších příkladů.

*Variadická šablona* je šablona třídy nebo funkce, která podporuje libovolný počet argumentů. Tento mechanismus je zvláště užitečné pro vývojáře knihovny C++, protože jej můžete použít na šablony tříd y šablony funkcí a šablony funkcí a tím poskytují širokou škálu typu bezpečné a netriviální funkce a flexibilitu.

## <a name="syntax"></a>Syntaxe

Tři tečky se používají dvěma způsoby variadické šablony. Vlevo od názvu parametru označuje *balíček parametrů*a vpravo od názvu parametru rozšiřuje balíčky parametrů do samostatných názvů.

Zde je základní příklad syntaxe definice *třídy variadic šablony:*

```cpp
template<typename... Arguments> class classname;
```

Pro balíčky parametrů i rozšíření můžete přidat mezery kolem tří setu na základě vašich preferencí, jak je znázorněno v těchto příkladech:

```cpp
template<typename ...Arguments> class classname;
```

Nebo toto:

```cpp
template<typename ... Arguments> class classname;
```

Všimněte si, že tento článek používá konvenci, která je `typename`uvedena v prvním příkladu (tři tečky jsou připojeny k ).

V předchozích příkladech *Arguments* je balíček parametrů. Třída `classname` může přijmout proměnný počet argumentů, jako v těchto příkladech:

```cpp
template<typename... Arguments> class vtclass;

vtclass< > vtinstance1;
vtclass<int> vtinstance2;
vtclass<float, bool> vtinstance3;
vtclass<long, std::vector<int>, std::string> vtinstance4;
```

Pomocí definice třídy variadické šablony můžete také vyžadovat alespoň jeden parametr:

```cpp
template <typename First, typename... Rest> class classname;
```

Zde je základní příklad *syntaxe funkce variadic šablony:*

```cpp
template <typename... Arguments> returntype functionname(Arguments... args);
```

Balíček parametrů *Arguments* je pak rozbalen pro použití, jak je znázorněno v další části **Principy variadických šablon**.

Jiné formy syntaxe funkce variadické šablony jsou možné – mimo jiné včetně těchto příkladů:

```cpp
template <typename... Arguments> returntype functionname(Arguments&... args);
template <typename... Arguments> returntype functionname(Arguments&&... args);
template <typename... Arguments> returntype functionname(Arguments*... args);
```

Specifikátory jako **const** jsou také povoleny:

```cpp
template <typename... Arguments> returntype functionname(const Arguments&... args);
```

Stejně jako u definic tříd variadických šablon můžete vytvářet funkce, které vyžadují alespoň jeden parametr:

```cpp
template <typename First, typename... Rest> returntype functionname(const First& first, const Rest&... args);
```

Variadické šablony `sizeof...()` používají operátor (nesouvisející `sizeof()` se starším operátorem):

```cpp
template<typename... Arguments>
void tfunc(const Arguments&... args)
{
    constexpr auto numargs{ sizeof...(Arguments) };

    X xobj[numargs]; // array of some previously defined type X

    helper_func(xobj, args...);
}
```

## <a name="more-about-ellipsis-placement"></a>Více o umístění tři tečky

Dříve tento článek popsal umístění třísek, které definuje balíčky parametrů a rozšíření jako "nalevo od názvu parametru, znamená balíček parametrů a vpravo od názvu parametru rozšiřuje balíčky parametrů do samostatných názvů". To je technicky pravda, ale může být matoucí v překladu do kódu. Rozmyslete si:

- V seznamu parametrů šablony`template <parameter-list>`( `typename...` ) zavádí balíček parametrů šablony.

- V klauzuli parametr-declaration`func(parameter-list)`- ) "nejvyšší úroveň" tři tečky zavádí balíček parametrů funkce a umístění se třemi tečkami je důležité:

    ```cpp
    // v1 is NOT a function parameter pack:
    template <typename... Types> void func1(std::vector<Types...> v1);

    // v2 IS a function parameter pack:
    template <typename... Types> void func2(std::vector<Types>... v2);
    ```

- Kde se tři tečky zobrazí bezprostředně za názvem parametru, máte rozšíření balíčku parametrů.

## <a name="example"></a>Příklad

Dobrým způsobem, jak ilustrovat mechanismus funkce variadické šablony, je použít jej `printf`při přepsání některých funkcí :

```cpp
#include <iostream>

using namespace std;

void print() {
    cout << endl;
}

template <typename T> void print(const T& t) {
    cout << t << endl;
}

template <typename First, typename... Rest> void print(const First& first, const Rest&... rest) {
    cout << first << ", ";
    print(rest...); // recursive call using pack expansion syntax
}

int main()
{
    print(); // calls first overload, outputting only a newline
    print(1); // calls second overload

    // these call the third overload, the variadic template,
    // which uses recursion as needed.
    print(10, 20);
    print(100, 200, 300);
    print("first", 2, "third", 3.14159);
}
```

## <a name="output"></a>Výstup

```Output
1
10, 20
100, 200, 300
first, 2, third, 3.14159
```

> [!NOTE]
> Většina implementací, které obsahují funkce variadické šablony, používá rekurzi určité hospo-  Tradiční rekurze zahrnuje funkci volá sám pomocí stejného podpisu. (Může být přetížený nebo šablonovaný, ale pokaždé je vybrán stejný podpis.) Variadická rekurze zahrnuje volání šablony variadické funkce pomocí různých (téměř vždy klesajících) čísel argumentů, a tím pokaždé potlačení jiného podpisu. "Základní případ" je stále nutné, ale povaha rekurze je odlišná.
