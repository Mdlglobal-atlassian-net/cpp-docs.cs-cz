---
title: funkce &lt;&gt; nástrojů
ms.date: 11/04/2016
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
ms.openlocfilehash: 3e92d6dc9f6966efda0e26fb28cf14652be880c7
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075588"
---
# <a name="ltutilitygt-functions"></a>funkce &lt;&gt; nástrojů

## <a name="as_const"></a><a name="asconst"></a>as_const

```cpp
template <class T> constexpr add_const_t<T>& as_const(T& t) noexcept;
template <class T> void as_const(const T&&) = delete;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí *T*.

## <a name="declval"></a><a name="declval"></a>declval –

```cpp
template <class T> add_rvalue_reference_t<T> declval() noexcept;  // as unevaluated operand
```

## <a name="exchange"></a><a name="exchange"></a>výměn

**(C++ 14)** Přiřadí novou hodnotu objektu a vrátí jeho starou hodnotu.

```cpp
template <class T, class Other = T>
    T exchange(T& val, Other&& new_val)
```

### <a name="parameters"></a>Parametry

\ *Val*
Objekt, který získá hodnotu new_val.

*new_val*\
Objekt, jehož hodnota je zkopírována nebo přesunuta do hodnoty Val.

### <a name="remarks"></a>Poznámky

U komplexních typů `exchange` zabránit kopírování staré hodnoty, pokud je k dispozici konstruktor přesunutí, nekopíruje novou hodnotu, pokud se jedná o dočasný objekt nebo je přesunut, a přijímá libovolný typ jako novou hodnotu s použitím libovolného dostupného operátoru přiřazení převodu. Funkce Exchange je odlišná od [std:: swap](../standard-library/algorithm-functions.md#swap) v tom, že levý argument není přesunut nebo zkopírován do pravého argumentu.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít `exchange`. V reálném světě je `exchange` nejužitečnější s velkými objekty, které je náročné na kopírování:

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

## <a name="forward"></a><a name="forward"></a>Komisi

Podmíněně přetypuje svůj argument na odkaz rvalue, pokud je argument hodnota rvalue nebo odkaz rvalue. Tím se období hodnota rvalue argumentu na funkci předání za účelem maximální podpory předávání.

```cpp
template <class Type>    // accepts lvalues
    constexpr Type&& forward(typename remove_reference<Type>::type& Arg) noexcept

template <class Type>    // accepts everything else
    constexpr Type&& forward(typename remove_reference<Type>::type&& Arg) noexcept
```

### <a name="parameters"></a>Parametry

*Zadejte*\
Typ hodnoty předané v *arg*, který se může lišit od typu *arg*. Obvykle určeno argumentem šablony funkce předávání.

*Arg* –\
Argument, který chcete přetypovat.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz rvalue na *arg* , pokud hodnota předaná v *arg* byla původně rvalue nebo odkaz na rvalue; v opačném případě vrátí *arg* bez úprav jeho typu.

### <a name="remarks"></a>Poznámky

Je nutné zadat explicitní argument šablony pro volání `forward`.

`forward` nepředává argument. Namísto toho, aby při podmíněném přetypování svého argumentu na odkaz rvalue byl původně rvalue nebo rvalue, `forward` umožňuje kompilátoru provést řešení přetížení se znalostí původního typu předávaného argumentu. Zjevný typ argumentu funkce předávání může být jiný než původní typ – například při použití rvalue jako argumentu funkce a je svázána s názvem parametru; název má hodnotu lvalue, přičemž jakákoli hodnota skutečně existuje jako rvalue – `forward` obnoví rvalue-Ness argumentu.

Obnovení hodnoty rvalue-Ness původní hodnoty argumentu k provedení překladu přetížení se označuje jako *dokonalé přesměrování*. Dokonalé předávání umožňuje funkci šablony přijmout argument některého typu odkazu a obnovit jeho vlastnost rvalue, když je nezbytná pro správné řešení přetížení. Pomocí dokonalého předávání můžete zachovat sémantiku přesunu pro hodnoty rvalue. Nebude tak nutné poskytovat přetížení pro funkce, které se liší pouze typem odkazu svých argumentů.

## <a name="from_chars"></a><a name="from_chars"></a>from_chars

```cpp
from_chars_result from_chars(const char* first, const char* last, see below& value, int base = 10);

from_chars_result from_chars(const char* first, const char* last, float& value, chars_format fmt = chars_format::general);

from_chars_result from_chars(const char* first, const char* last, double& value, chars_format fmt = chars_format::general);

from_chars_result from_chars(const char* first, const char* last, long double& value, chars_format fmt = chars_format::general);
```

## <a name="get"></a><a name="get"></a>Čtěte

Získá prvek z objektu `pair` podle pozice indexu nebo podle typu.

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

*Index*\
Index vybraného elementu založený na nule.

\ *T1*
Typ prvního prvku dvojice.

*T2*\
Typ druhého prvku dvojice.

*\ žádosti* o přijetí změn
Pár, ze kterého se má vybírat

### <a name="remarks"></a>Poznámky

Jednotlivé funkce šablon vrátí odkaz na prvek jeho `pair` argument.

V případě indexovaných přetížení platí, že pokud je hodnota *indexu* 0, vrátí funkce `pr.first` a pokud je hodnota *indexu* 1, funkce vrátí `pr.second`. Typ `RI` je typ vráceného prvku.

Pro přetížení, která nemají parametr indexu, je element, který se má vrátit, odvozený pomocí argumentu typu. Volání `get<T>(Tuple)` vytvoří chybu kompilátoru, pokud *PR* obsahuje více nebo méně než jeden prvek typu t.

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
}
```

```Output
9 3.14
1 0.27
```

## <a name="index_sequence"></a><a name="index_sequence"></a>index_sequence

```cpp
template<size_t... I>
    using index_sequence = integer_sequence<size_t, I...>;
```

## <a name="index_sequence_for"></a><a name="index_sequence_for"></a>index_sequence_for

```cpp
template<class... T>
    using index_sequence_for = make_index_sequence<sizeof...(T)>;
```

## <a name="make_index_sequence"></a><a name="make_index_sequence"></a>make_index_sequence

```cpp
template<size_t N>
    using make_index_sequence = make_integer_sequence<size_t, N>;
```

## <a name="make_integer_sequence"></a><a name="make_integer_sequence"></a>make_integer_sequence

```cpp
template<class T, T N>
    using make_integer_sequence = integer_sequence<T, see below >;
```

## <a name="make_pair"></a><a name="make_pair"></a>make_pair

Funkce šablony, kterou lze použít k vytvoření objektů typu `pair`, kde se typy komponent automaticky volí na základě datových typů, které jsou předány jako parametry.

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

*Val1*\
Hodnota, která inicializuje první prvek `pair`.

*Val2*\
Hodnota, která inicializuje druhý prvek `pair`.

### <a name="return-value"></a>Návratová hodnota

Objekt dvojice, který je vytvořen: `pair`<`T``U`> (`Val1`, `Val2`).

### <a name="remarks"></a>Poznámky

`make_pair` převede objekt typu [Reference_wrapper třídy](../standard-library/reference-wrapper-class.md) na odkazové typy a převede pole a funkce selhání na ukazatele.

V vráceném objektu `pair` `T` je určena následujícím způsobem:

- Pokud je typ vstupu `T` `reference_wrapper<X>`, vrácený typ `T` je `X&`.

- V opačném případě je vrácený typ `T` `decay<T>::type`. Pokud [Třída Decay](../standard-library/decay-class.md) není podporována, vrácený typ `T` je stejný jako vstupní typ `T`.

Vrácený typ `U` je podobně určen z `U`typu vstupu.

Jednou z výhod `make_pair` je, že typy objektů, které jsou uložené, jsou určeny automaticky kompilátorem a není nutné je explicitně zadat. Nepoužívejte explicitní argumenty šablony, jako je například `make_pair<int, int>(1, 2)` při použití `make_pair`, protože je podrobná a přidává složité problémy s odkazem rvalue, které by mohly způsobit selhání kompilace. V tomto příkladu by byla `make_pair(1, 2)` Správná syntaxe.

Pomocná funkce `make_pair` také umožňuje předat dvě hodnoty funkci, která vyžaduje dvojici jako vstupní parametr.

### <a name="example"></a>Příklad

Příklad použití pomocné funkce `make_pair` k deklaraci a inicializaci páru naleznete v tématu [Struktura páru](../standard-library/pair-structure.md).

## <a name="move"></a><a name="move"></a>Pøesunout

Bezpodmínečně přetypuje svůj argument na odkaz hodnoty rvalue a značí, že ji lze přesunout, pokud je pro její typ přesunutí povoleno.

```cpp
template <class Type>
    constexpr typename remove_reference<Type>::type&& move(Type&& Arg) noexcept;
```

### <a name="parameters"></a>Parametry

*Zadejte*\
Typ odvozený z typu argumentu předaného do *arg*spolu s pravidly sbalení odkazu.

*Arg* –\
Argument, který chcete přetypovat. I když se typ *arg* zdá být určen jako odkaz rvalue, `move` také přijímá argumenty lvalue, protože odkazy lvalue mohou vytvořit vazby na odkazy rvalue.

### <a name="return-value"></a>Návratová hodnota

`Arg` jako odkaz rvalue bez ohledu na to, zda je jeho typ odkazový typ.

### <a name="remarks"></a>Poznámky

*Typ* argumentu šablony není určen k explicitnímu zadání, ale bude odvozen od typu hodnoty předané v *arg*. Typ *typu* je dále upravován podle pravidel pro sbalení odkazů.

`move` nepřesouvá argument. Namísto toho nepodmíněně přetypování svého argumentu (což může být l-hodnota) na odkaz rvalue umožňuje kompilátoru následně přesunout místo kopírování hodnotu předanou v *arg* , pokud je jeho typ zapnutý k přesunutí. Pokud se jeho typ nepovoluje přesunout, je místo toho zkopírován.

Pokud hodnota předaná v *arg* je lvalue – to znamená, že má název nebo adresu, která může být provedena, je při přesunu zrušena její platnost. Po přesunutí neodkazujte na hodnotu předanou v *arg* pomocí jejího názvu nebo adresy.

## <a name="move_if_noexcept"></a><a name="moveif"></a>move_if_noexcept

```cpp
template <class T> constexpr conditional_t< !is_nothrow_move_constructible_v<T> && is_copy_constructible_v<T>, const T&, T&&> move_if_noexcept(T& x) noexcept;
```

## <a name="swap"></a><a name="swap"></a>adresu

Vyměňuje prvky dvou typů nebo objektů [struktury páru](../standard-library/pair-structure.md) .

```cpp
template <class T>
    void swap(T& left, T& right) noexcept(see below );
template <class T, size_t N>
    void swap(T (&left)[N], T (&right)[N]) noexcept(is_nothrow_swappable_v<T>);
template <class T, class U>
    void swap(pair<T, U>& left, pair<T, U>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu nebo typu `pair`.

*pravé*\
Objekt typu nebo typu `pair`.

### <a name="remarks"></a>Poznámky

Jednou z výhod `swap` je, že typy objektů, které jsou uložené, jsou určeny automaticky kompilátorem a není nutné je explicitně zadat. Nepoužívejte explicitní argumenty šablony, jako je například `swap<int, int>(1, 2)` při použití `swap`, protože je podrobná a přidává složité problémy s odkazem rvalue, které by mohly způsobit selhání kompilace.

## <a name="to_chars"></a><a name="to_chars"></a>to_chars

```cpp
to_chars_result to_chars(char* first, char* last, see below value, int base = 10);
to_chars_result to_chars(char* first, char* last, float value);
to_chars_result to_chars(char* first, char* last, double value);
to_chars_result to_chars(char* first, char* last, long double value);
to_chars_result to_chars(char* first, char* last, float value, chars_format fmt);
to_chars_result to_chars(char* first, char* last, double value, chars_format fmt);
to_chars_result to_chars(char* first, char* last, long double value, chars_format fmt);
to_chars_result to_chars(char* first, char* last, float value, chars_format fmt, int precision);
to_chars_result to_chars(char* first, char* last, double value, chars_format fmt, int precision);
to_chars_result to_chars(char* first, char* last, long double value, chars_format fmt, int precision);
```

### <a name="remarks"></a>Poznámky

Převede hodnotu na řetězec znaků vyplněním `[first, last)`rozsahu, kde `[first, last)` musí být platný rozsah.
