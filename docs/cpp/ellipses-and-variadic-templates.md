---
title: Tři tečky a variadické šablony
ms.date: 11/04/2016
ms.assetid: f20967d9-c967-4fd2-b902-2bb1d5ed87e3
ms.openlocfilehash: 9c9294089b9f0a144946b7f6b81da2a71ca710bc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189257"
---
# <a name="ellipses-and-variadic-templates"></a>Tři tečky a variadické šablony

Tento článek ukazuje, jak používat tři tečky (`...`) C++ s šablonami variadické. Tři tečky mají mnoho použití v C a C++. Mezi ně patří seznamy argumentů proměnných pro funkce. `printf()` funkce z běhové knihovny jazyka C je jedním z nejznámých příkladů.

*Šablona variadické* je šablona třídy nebo funkce, která podporuje libovolný počet argumentů. Tento mechanismus je zvláště užitečný pro C++ vývojáře knihoven, protože ho můžete použít jak pro šablony třídy, tak pro šablony funkcí a poskytujeme tak široké spektrum netriviálních funkcí a flexibility.

## <a name="syntax"></a>Syntaxe

Tři způsoby používají tři tečky pro variadické šablony. Vlevo od názvu parametru znamená *balíček parametrů*a napravo od názvu parametru rozšiřuje balíčky parametrů na samostatné názvy.

Tady je základní příklad syntaxe definice *třídy variadické šablony* :

```cpp
template<typename... Arguments> class classname;
```

Pro balíčky parametrů i rozšíření můžete přidat prázdné znaky kolem tří teček na základě předvolby, jak je znázorněno v těchto příkladech:

```cpp
template<typename ...Arguments> class classname;
```

Nebo:

```cpp
template<typename ... Arguments> class classname;
```

Všimněte si, že tento článek používá konvenci, která je zobrazená v prvním příkladu (tři tečky jsou připojené k `typename`).

V předchozích příkladech jsou *argumenty* sadou parametrů. Třída `classname` může přijmout proměnlivý počet argumentů, jako v těchto příkladech:

```cpp
template<typename... Arguments> class vtclass;

vtclass< > vtinstance1;
vtclass<int> vtinstance2;
vtclass<float, bool> vtinstance3;
vtclass<long, std::vector<int>, std::string> vtinstance4;
```

Pomocí definice třídy šablony variadické můžete také vyžadovat alespoň jeden parametr:

```cpp
template <typename First, typename... Rest> class classname;
```

Zde je základní příklad syntaxe *funkce variadické Template* :

```cpp
template <typename... Arguments> returntype functionname(Arguments... args);
```

Sada parametrů *arguments* se pak rozbalí pro použití, jak je znázorněno v další části **Principy šablon variadické**.

Je možné použít i jiné formy syntaxe variadické šablony funkce – včetně, ale ne omezení na, tyto příklady:

```cpp
template <typename... Arguments> returntype functionname(Arguments&... args);
template <typename... Arguments> returntype functionname(Arguments&&... args);
template <typename... Arguments> returntype functionname(Arguments*... args);
```

Jsou povolené taky specifikátory, jako je **const** :

```cpp
template <typename... Arguments> returntype functionname(const Arguments&... args);
```

Stejně jako u definicí třídy šablon variadické můžete vytvořit funkce, které vyžadují aspoň jeden parametr:

```cpp
template <typename First, typename... Rest> returntype functionname(const First& first, const Rest&... args);
```

Šablony variadické používají operátor `sizeof...()` (nesouvisí se starším operátorem `sizeof()`):

```cpp
template<typename... Arguments>
void tfunc(const Arguments&... args)
{
    constexpr auto numargs{ sizeof...(Arguments) };

    X xobj[numargs]; // array of some previously defined type X

    helper_func(xobj, args...);
}
```

## <a name="more-about-ellipsis-placement"></a>Další informace o umístění tří teček

Dříve Tento článek popisuje umístění se třemi tečkami, které definuje balíčky parametrů a rozšíření jako nalevo od názvu parametru, označuje balíček parametrů a napravo od názvu parametru rozšiřuje balíčky parametrů na samostatné názvy. Jedná se o technicky true, ale může být matoucí v překladu na kód. Rozmyslete si:

- V seznamu Template-Parameter-list (`template <parameter-list>`) `typename...` zavádí balíček parametrů šablony.

- V klauzuli Parameter-Declaration-klauzule (`func(parameter-list)`) zavádí tři tečky na nejvyšší úrovni balíček parametrů funkce a umístění tří teček je důležité:

    ```cpp
    // v1 is NOT a function parameter pack:
    template <typename... Types> void func1(std::vector<Types...> v1);

    // v2 IS a function parameter pack:
    template <typename... Types> void func2(std::vector<Types>... v2);
    ```

- Kde se tři tečky zobrazují hned za názvem parametru, máte rozšíření sady parametrů.

## <a name="example"></a>Příklad

Dobrým způsobem, jak znázornit mechanizmus variadické funkce, je použít ho v novém zápisu některých funkcí `printf`:

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
>  Většina implementací, které obsahují funkce šablon variadické, používá rekurzi nějakého formuláře, ale je mírně odlišná od tradiční rekurze.  Tradiční rekurze zahrnuje funkci, která volá sebe sama pomocí stejného podpisu. (Může být přetížený nebo v šabloně, ale stejný podpis se vybere pokaždé, když.) Rekurze variadické zahrnuje volání šablony funkce variadické pomocí odlišného (téměř vždy klesajícího) počtu argumentů a tím pokaždé, když se pokaždé označí za jiný podpis. Základní případ je stále vyžadován, ale povaha rekurze je odlišná.
