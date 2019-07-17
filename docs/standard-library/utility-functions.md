---
title: '&lt;Nástroj&gt; funkce'
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
ms.openlocfilehash: 723b077500b9b741445efcd8574fb26cd53e5fc7
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246301"
---
# <a name="ltutilitygt-functions"></a>&lt;Nástroj&gt; funkce

## <a name="asconst"></a> as_const

```cpp
template <class T> constexpr add_const_t<T>& as_const(T& t) noexcept;
template <class T> void as_const(const T&&) = delete;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí *T*.

## <a name="declval"></a> declval –

```cpp
template <class T> add_rvalue_reference_t<T> declval() noexcept;  // as unevaluated operand
```

## <a name="exchange"></a> Exchange

**(C ++ 14)**  Objektu přiřadí novou hodnotu a vrátí jeho starou hodnotu.

```cpp
template <class T, class Other = T>
    T exchange(T& val, Other&& new_val)
```

### <a name="parameters"></a>Parametry

*Val*\
Objekt, který se zobrazí hodnota new_val.

*new_val*\
Objekt, jehož hodnota je zkopírovaný ani přesunutý do val.

### <a name="remarks"></a>Poznámky

U komplexních typů `exchange` nekopíruje starou hodnotu, pokud je dostupný konstruktor přesunutí, nekopíruje novou hodnotu, pokud je dočasný objekt nebo je přesunout a přijímá jako novou hodnotu pomocí všechny dostupné převodního operátoru přiřazení libovolný typ. Funkce systému exchange se liší od [std::swap](../standard-library/algorithm-functions.md#swap) , levý argument není přenesou nebo zkopírují na pravý argument.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat `exchange`. V praxi `exchange` je nejužitečnější s velké objekty, které je vždycky kopírovat:

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

## <a name="forward"></a> Vpřed

Podmíněně přetypuje svůj argument na odkaz rvalue, pokud je argument hodnota rvalue nebo odkaz rvalue. Tím se období hodnota rvalue argumentu na funkci předání za účelem maximální podpory předávání.

```cpp
template <class Type>    // accepts lvalues
    constexpr Type&& forward(typename remove_reference<Type>::type& Arg) noexcept

template <class Type>    // accepts everything else
    constexpr Type&& forward(typename remove_reference<Type>::type&& Arg) noexcept
```

### <a name="parameters"></a>Parametry

*Typ*\
Typ hodnoty předané v *Arg*, který může být jiný než typ *Arg*. Obvykle určeno argumentem šablony funkce předávání.

*arg*\
Argument, který chcete přetypovat.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz rvalue na *Arg* Pokud hodnota předaná v *Arg* byla původně rvalue nebo odkaz na rvalue; v opačném případě vrátí *Arg* beze změny jeho typu.

### <a name="remarks"></a>Poznámky

Je nutné zadat explicitní argument šablony pro volání `forward`.

`forward` není přeposlat svého argumentu. Místo toho podle podmíněně přetypuje svůj argument na odkaz rvalue, pokud byla původně rvalue nebo odkaz rvalue, `forward` umožňuje kompilátoru provést řešení přetížení se znalostí původního typu předaného argumentu. Viditelný typ argumentu pro funkci předání může být jiný než jeho původní typ, například když se používá jako argument pro funkci a je vázán na název parametru; r-hodnoty. s názvem umožňuje l-hodnotou, s kterou hodnota skutečně existuje jako hodnota rvalue – `forward` obnoví deklarovanou rvalue argumentu.

Obnovení deklarovanou rvalue původní hodnoty argumentu do řešení přetížení se označuje jako *perfektní přesměrování*. Dokonalé předávání umožňuje funkci šablony přijmout argument některého typu odkazu a obnovit jeho vlastnost rvalue, když je nezbytná pro správné řešení přetížení. Pomocí dokonalého předávání můžete zachovat sémantiku přesunu pro hodnoty rvalue. Nebude tak nutné poskytovat přetížení pro funkce, které se liší pouze typem odkazu svých argumentů.

## <a name="from_chars"></a> from_chars

```cpp
from_chars_result from_chars(const char* first, const char* last, see below& value, int base = 10);

from_chars_result from_chars(const char* first, const char* last, float& value, chars_format fmt = chars_format::general); 

from_chars_result from_chars(const char* first, const char* last, double& value, chars_format fmt = chars_format::general); 

from_chars_result from_chars(const char* first, const char* last, long double& value, chars_format fmt = chars_format::general);
```

## <a name="get"></a> získat

Získá prvek z `pair` index pozice, nebo podle typu objektu.

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
Index zvolené elementu založený na 0.

*T1*\
Typ první prvek dvojice.

*T2.* \
Typ elementu druhý pár.

*žádost o přijetí změn*\
Dvojice lze vybírat.

### <a name="remarks"></a>Poznámky

Vrátí odkaz na element šablony funkce každého jeho `pair` argument.

Pro indexované přetížení Pokud hodnota *Index* je 0, vrátí funkce `pr.first` a, pokud hodnota *Index* 1, funkce vrátí `pr.second`. Typ `RI` je typ vrácený element.

Pro přetížení, které nemají v parametru indexu je argumentem typ odvozený elementu, který chcete vrátit. Volání `get<T>(Tuple)` způsobí chybu kompilátoru, pokud *žádosti o přijetí změn* obsahuje více nebo méně než jeden element typu T.

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

## <a name="index_sequence"></a> index_sequence

```cpp
template<size_t... I>
    using index_sequence = integer_sequence<size_t, I...>;
```

## <a name="index_sequence_for"></a> index_sequence_for

```cpp
template<class... T>
    using index_sequence_for = make_index_sequence<sizeof...(T)>;
```

## <a name="make_index_sequence"></a> make_index_sequence

```cpp
template<size_t N>
    using make_index_sequence = make_integer_sequence<size_t, N>;
```

## <a name="make_integer_sequence"></a> make_integer_sequence

```cpp
template<class T, T N>
    using make_integer_sequence = integer_sequence<T, see below >;
```

## <a name="make_pair"></a> make_pair

Funkce šablony, můžete použít k vytvoření objektů typu `pair`, kde typy komponenty je automaticky kliknuto, na základě typu dat, které jsou předány jako parametry.

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

Vytvořený objekt dvojice: `pair` < `T`,`U`> (`Val1`, `Val2`).

### <a name="remarks"></a>Poznámky

`make_pair` Převede objekt typu [reference_wrapper – třída](../standard-library/reference-wrapper-class.md) na referenční typy a převede Slábnoucí pole a funkce na ukazatele.

Ve vráceném `pair` objektu, `T` je stanoven následujícím způsobem:

- Pokud vstupní typ `T` je `reference_wrapper<X>`, vrátil typ `T` je `X&`.

- V opačném případě vrácený typ `T` je `decay<T>::type`. Pokud [decay – třída](../standard-library/decay-class.md) není podporováno, vrácený typ `T` je stejný jako vstupní typ `T`.

Vrácený typ `U` je podobně určen na základě vstupního typu `U`.

Jednou z výhod `make_pair` je, že typy ukládaných objektů jsou určeny automaticky kompilátorem a není potřeba explicitně zadat. Nepoužívejte explicitní argumenty šablony, jako `make_pair<int, int>(1, 2)` při použití `make_pair` protože je verbose a přidá komplexní rvalue reference problémy, které mohou způsobit selhání kompilace. V tomto příkladu by správná syntaxe byla `make_pair(1, 2)`

`make_pair` Pomocná funkce také umožňuje předat dvě hodnoty funkci, která vyžaduje dvojici jako vstupní parametr.

### <a name="example"></a>Příklad

Příklad použití funkce pomocné rutiny `make_pair` deklaraci a inicializaci dvojice naleznete v tématu [pair – struktura](../standard-library/pair-structure.md).

## <a name="move"></a> Přesunutí

Bezpodmínečně přetypuje svůj argument na odkaz hodnoty rvalue a značí, že ji lze přesunout, pokud je pro její typ přesunutí povoleno.

```cpp
template <class Type>
    constexpr typename remove_reference<Type>::type&& move(Type&& Arg) noexcept;
```

### <a name="parameters"></a>Parametry

*Typ*\
Typ odvozený od typu argumentu předaného *Arg*společně s pravidly pro sbalení odkazu.

*arg*\
Argument, který chcete přetypovat. I když typ *Arg* jeví jako zadaný jako odkaz hodnoty rvalue, `move` také přijímá argumenty hodnoty lvalue, protože odkazy lvalue lze vázat na odkazy rvalue.

### <a name="return-value"></a>Návratová hodnota

`Arg` jako odkaz hodnoty rvalue zda její typ je typ odkazu.

### <a name="remarks"></a>Poznámky

Argument šablony *typ* není určen k explicitnímu určení, ale k odvození od typu hodnoty předané v *Arg*. Typ *typ* je dále upraven podle pravidel sbalení odkazů.

`move` čárka nepohybuje svého argumentu. Místo toho podle bezpodmínečným přetypováním svého argumentu, který může být l-hodnota – na odkaz rvalue, povolí kompilátorovi následně přesunout, spíše než kopírování, hodnota předaná v *Arg* li její typ přesunutí povoleno. Není-li její typ přesunutí povoleno, zkopíruje se místo toho.

Pokud hodnota předaná v *Arg* l-hodnotou, tedy má název nebo adresu je možné provést – zneplatněna po provedení přesunutí. Není odkazovat na hodnotu předanou v *Arg* podle názvu nebo adresy až po přesunutí neodkazujte.

## <a name="moveif"></a> move_if_noexcept

```cpp
template <class T> constexpr conditional_t< !is_nothrow_move_constructible_v<T> && is_copy_constructible_v<T>, const T&, T&&> move_if_noexcept(T& x) noexcept;
```

## <a name="swap"></a> Prohození

Vymění prvky dvou typů nebo [pair – struktura](../standard-library/pair-structure.md) objekty.

```cpp
template <class T>
    void swap(T& left, T& right) noexcept(see below );
template <class T, size_t N>
    void swap(T (&left)[N], T (&right)[N]) noexcept(is_nothrow_swappable_v<T>);
template <class T, class U>
    void swap(pair<T, U>& left, pair<T, U>& right);
```

### <a name="parameters"></a>Parametry

*doleva*\
Objekt typu nebo typu `pair`.

*doprava*\
Objekt typu nebo typu `pair`.

### <a name="remarks"></a>Poznámky

Jednou z výhod `swap` je, že typy ukládaných objektů jsou určeny automaticky kompilátorem a není potřeba explicitně zadat. Nepoužívejte explicitní argumenty šablony, jako `swap<int, int>(1, 2)` při použití `swap` protože je verbose a přidá komplexní rvalue reference problémy, které mohou způsobit selhání kompilace.

## <a name="to_chars"></a> to_chars

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

Převede hodnotu na řetězec znaků zadáním rozsahu `[first, last)`, kde `[first, last)` musí být platný rozsah.
