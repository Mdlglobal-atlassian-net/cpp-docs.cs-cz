---
title: '&lt;Nástroj&gt; funkce | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- utility/std::exchange
- utility/std::forward
- utility/std::make_pair
- utility/std::move
- utility/std::swap
ms.assetid: b1df38cd-3a59-4098-9c81-83342eb719a4
helpviewer_keywords:
- std::exchange [C++]
- std::forward [C++]
- std::make_pair [C++]
- std::move [C++]
- std::swap [C++]
ms.openlocfilehash: a26a4a0cab0bdea8a7a642cc760da0f3fc79b471
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="ltutilitygt-functions"></a>&lt;Nástroj&gt; funkce

||||
|-|-|-|
|[exchange](#exchange)|[Předat dál](#forward)|[Get – funkce &lt;nástroj&gt;](#get)|
|[make_pair](#make_pair)|[Přesunutí](#move)|[Swap](#swap)|

## <a name="exchange"></a>  Exchange

**(C ++ 14)**  Přiřadí novou hodnotu do objektu a vrátí jeho původní hodnotu.

```cpp
template <class T, class Other = T>
T exchange(T& val, Other&& new_val)
```

### <a name="parameters"></a>Parametry

`val` Objekt, který se zobrazí hodnota new_val.

`new_val` Objekt, jehož hodnota je zkopírovat nebo přesunout do val.

### <a name="remarks"></a>Poznámky

Pro komplexní typy `exchange` zabraňuje kopírování původní hodnoty, když je dostupný konstruktor move a zabraňuje kopírování novou hodnotu, pokud je dočasný objekt nebo je přesunout a přijímá jakéhokoli typu jako nová hodnota, pomocí libovolné dostupné převodu operátor přiřazení. Funkce výměny se liší od [std::swap](../standard-library/algorithm-functions.md#swap) v, že levý argument není přesunout ani zkopírovat na pravý argument.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat `exchange`. V praxi `exchange` je velmi užitečné pomocí velkých objektů, které jsou nákladné zkopírovat:

```cpp
#include <utility>
#include <iostream>

using namespace std;

struct C
{
   int i;
   //...
};

int main()
{
   // Use brace initialization
   C c1{ 1 };
   C c2{ 2 };
   C result = exchange(c1, c2);
   cout << "The old value of c1 is: " << result.i << endl;
   cout << "The new value of c1 after exchange is: " << c1.i << endl;

   return 0;
}
```

```Output
The old value of c1 is: 1
The new value of c1 after exchange is: 2
```

## <a name="forward"></a>  Předat dál

Podmíněně přetypuje svůj argument na odkaz rvalue, pokud je argument hodnota rvalue nebo odkaz rvalue. Tím se období hodnota rvalue argumentu na funkci předání za účelem maximální podpory předávání.

```cpp
template <class Type>    // accepts lvalues
constexpr Type&& forward(typename remove_reference<Type>::type& Arg) noexcept

template <class Type>    // accepts everything else
constexpr Type&& forward(typename remove_reference<Type>::type&& Arg) noexcept
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`Type`|Typ hodnoty předané `Arg`, což může být jiná než typ `Arg`. Obvykle určeno argumentem šablony funkce předávání.|
|`Arg`|Argument, který chcete přetypovat.|

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na rvalue pro `Arg` Pokud předaná hodnota `Arg` byl původně rvalue nebo odkaz na rvalue; jinak vrátí `Arg` beze změny jeho typu.

### <a name="remarks"></a>Poznámky

Musíte zadat argument explicitní šablony volat `forward`.

`forward` Nepředávat dál jeho argumentem. Místo toho pomocí podmíněně přetypování její argument deklarátor odkazu, pokud byl původně rvalue nebo deklarátor odkazu `forward` umožňuje kompilátoru k rozlišení přetížení s znalostmi původní typ přesměrovaná argumentu. Může být jiná než jeho původní typ zřejmá typ argumentu funkce předávání – například když se používá jako argument pro funkci a je vázána na název parametru; rvalue s názvem umožňuje lvalue, bez ohledu na to, jestli hodnota skutečně existuje jako rvalue – `forward` obnoví rvalue – obchodní argumentu.

Chcete-li provést rozlišení přetížení obnovení rvalue – obchodní argument na původní hodnoty se označuje jako *ideální předávání*. Dokonalé předávání umožňuje funkci šablony přijmout argument některého typu odkazu a obnovit jeho vlastnost rvalue, když je nezbytná pro správné řešení přetížení. Pomocí dokonalého předávání můžete zachovat sémantiku přesunu pro hodnoty rvalue. Nebude tak nutné poskytovat přetížení pro funkce, které se liší pouze typem odkazu svých argumentů.

## <a name="get"></a>  GET

Získá element z `pair` objektu podle pozici indexu, nebo typu.

```cpp
// get reference to element at Index in pair Pr
template <size_t Index, class T1, class T2>
constexpr tuple_element_t<Index, pair<T1, T2>>&
get(pair<T1, T2>& Pr) noexcept;

// get reference to element T1 in pair Pr
template <class T1, class T2>
constexpr T1& get(pair<T1, T2>& Pr) noexcept;

// get reference to element T2 in pair Pr
template <class T2, class T1>
constexpr T2& get(pair<T1, T2>& Pr) noexcept;

// get const reference to element at Index in pair Pr
template <size_t Index, class T1, class T2>
constexpr const tuple_element_t<Index, pair<T1, T2>>&
get(const pair<T1, T2>& Pr) noexcept;

// get const reference to element T1 in pair Pr
template <class T1, class T2>
constexpr const T1& get(const pair<T1, T2>& Pr) noexcept;

// get const reference to element T2 in pair Pr
template <class T2, class T1>
constexpr const T2& get(const pair<T1, T2>& Pr) noexcept;

// get rvalue reference to element at Index in pair Pr
template <size_t Index, class T1, class T2>
constexpr tuple_element_t<Index, pair<T1, T2>>&&
get(pair<T1, T2>&& Pr) noexcept;

// get rvalue reference to element T1 in pair Pr
template <class T1, class T2>
constexpr T1&& get(pair<T1, T2>&& Pr) noexcept;

// get rvalue reference to element T2 in pair Pr
template <class T2, class T1>
constexpr T2&& get(pair<T1, T2>&& Pr) noexcept;
```

### <a name="parameters"></a>Parametry

`Index` Index založený na 0 určené elementu.

`T1` Typ první prvek pár.

`T2` Typ elementu druhý pár.

`pr` Pár lze vybírat.

### <a name="remarks"></a>Poznámky

Funkce šablony každý vrátíte odkaz na element jeho `pair` argument.

Pro indexované přetížení Pokud hodnota `Index` je 0, vrátí funkce `pr.first` a pokud hodnota `Index` 1, vrátí funkce `pr.second`. Typ `RI` je typ vrácený element.

Pro přetížení, které nemají parametrem Index je v argumentu typ odvodit elementu, který chcete vrátit. Volání metody `get<T>(Tuple)` způsobí chybu kompilátoru, pokud `pr` obsahuje více nebo méně než jeden element typu T.

### <a name="example"></a>Příklad

```cpp
#include <utility>
#include <iostream>
using namespace std;
int main()
{

    typedef pair<int, double> MyPair;

    MyPair c0(9, 3.14);

    // get elements by index
    cout << " " << get<0>(c0);
    cout << " " << get<1>(c0) << endl;

    // get elements by type (C++14)
    MyPair c1(1, 0.27);
    cout << " " << get<int>(c1);
    cout << " " << get<double>(c1) << endl;

    /*
    Output:
    9 3.14
    1 0.27
    */

}
```

## <a name="make_pair"></a>  make_pair –

Funkce šablony, který vám pomůže vytvořit objekty typu `pair`, kde typy součásti jsou automaticky vybrali, na základě typu dat, které se předávají jako parametry.

```cpp
template <class T, class U>
pair<T, U> make_pair(T& Val1, U& Val2);

template <class T, class U>
pair<T, U> make_pair(T& Val1, U&& Val2);

template <class T, class U>
pair<T, U> make_pair(T&& Val1, U& Val2);

template <class T, class U>
pair<T, U> make_pair(T&& Val1, U&& Val2);
```

### <a name="parameters"></a>Parametry

`Val1` Hodnota, která inicializuje první prvek `pair`.

`Val2` Hodnota, která inicializuje druhého prvku `pair`.

### <a name="return-value"></a>Návratová hodnota

Objekt dvojice, který je sestavený: `pair` <  `T`, `U`> ( `Val1`, `Val2`).

### <a name="remarks"></a>Poznámky

`make_pair` převádí objekt typu [reference_wrapper – třída](../standard-library/reference-wrapper-class.md) odkazové typy a převede Slábnoucí pole a funkce na ukazatele.

Ve vráceném `pair` objektu `T` je stanoven následujícím způsobem:

- Pokud typ vstupu `T` je `reference_wrapper<X>`, vrátil typ `T` je `X&`.

- Jinak typ vrácený `T` je `decay<T>::type`. Pokud [decay – třída](../standard-library/decay-class.md) není podporován typ vrácený `T` je stejný jako vstupní typ `T`.

Typ vrácený `U` Podobně se určí ze vstupní typ `U`.

Jednou z výhod `make_pair` je, že typy objektů, které ukládají automaticky určuje kompilátoru a není nutné explicitně určena. Nepoužívejte jako argumenty explicitní šablony `make_pair<int, int>(1, 2)` při použití `make_pair` protože je zbytečně podrobné a přidá komplexní deklarátor odkazu problémy, které může způsobit chyby kompilace. V tomto příkladu by být správná syntaxe `make_pair(1, 2)`

`make_pair` Pomocné funkce také umožňuje předat funkci, která vyžaduje pár jako vstupní parametr dvě hodnoty.

### <a name="example"></a>Příklad

Příklad o tom, jak používat pomocné funkce `make_pair` deklarace a inicializace pár najdete v tématu [pair – struktura](../standard-library/pair-structure.md).

## <a name="move"></a>  Přesunutí

Bezpodmínečně přetypuje svůj argument na odkaz hodnoty rvalue a značí, že ji lze přesunout, pokud je pro její typ přesunutí povoleno.

```cpp
template <class Type>
constexpr typename remove_reference<Type>::type&& move(Type&& Arg) noexcept;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`Type`|Typ odvodit z typu argument předaná `Arg`, společně s odkazem na sbalení pravidla.|
|`Arg`|Argument, který chcete přetypovat. I když typ `Arg` zdá být zadány jako deklarátor odkazu, `move` také přijímá argumenty lvalue, protože lvalue odkazy můžete vázat na odkazy rvalue.|

### <a name="return-value"></a>Návratová hodnota

`Arg` jako deklarátor odkazu zda jeho typ je odkazového typu.

### <a name="remarks"></a>Poznámky

Argument šablony `Type` neměla být explicitně uvedena, ale odvodit z typu předaná hodnota `Arg`. Typ `Type` další úpravě podle odkaz sbalení pravidla.

`move` nepřesouvá jeho argumentem. Místo toho pomocí bezpodmínečně přetypování její argument – což může být lvalue – k deklarátor odkazu, umožňuje kompilátoru následně přesunout, protože místo kopírování předaná hodnota `Arg` Pokud typ je povolen move. Pokud pro daný typ není povolen přesun, hodnota se zkopíruje.

Pokud je předaná hodnota `Arg` je lvalue –, má název, nebo můžete provést jeho adresy – je zrušena, když dojde k přesunutí. Neměly by konce odkazovat na hodnotu předaná `Arg` podle jeho názvu nebo adresy po byl přesunut.

## <a name="swap"></a>  Swap

Výměny dva elementy [pair – struktura](../standard-library/pair-structure.md) objekty.

```cpp
template <class T, class U>
void swap(pair<T, U>& left, pair<T, U>& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`left`|Objekt typu `pair`.|
|`right`|Objekt typu `pair`.|

### <a name="remarks"></a>Poznámky

Jednou z výhod `swap` je, že typy objektů, které ukládají automaticky určuje kompilátoru a není nutné explicitně určena. Nepoužívejte jako argumenty explicitní šablony `swap<int, int>(1, 2)` při použití `swap` protože je zbytečně podrobné a přidá komplexní deklarátor odkazu problémy, které může způsobit chyby kompilace.

## <a name="see-also"></a>Viz také

[\<nástroj >](../standard-library/utility.md)<br/>
