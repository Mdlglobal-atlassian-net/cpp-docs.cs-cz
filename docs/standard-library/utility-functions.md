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
ms.openlocfilehash: 7a061ede19c5c4c181b5fea912b9c6212c583267
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362364"
---
# <a name="ltutilitygt-functions"></a>&lt;Nástroj&gt; funkce

||||
|-|-|-|
|[exchange](#exchange)|[Vpřed](#forward)|[Funkce Get &lt;nástroje&gt;](#get)|
|[make_pair](#make_pair)|[move](#move)|[swap](#swap)|

## <a name="exchange"></a>  Exchange

**(C ++ 14)**  Objektu přiřadí novou hodnotu a vrátí jeho starou hodnotu.

```cpp
template <class T, class Other = T>
T exchange(T& val, Other&& new_val)
```

### <a name="parameters"></a>Parametry

*Val*<br/>
Objekt, který se zobrazí hodnota new_val.

*new_val*<br/>
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

## <a name="forward"></a>  Vpřed

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
|*Typ*|Typ hodnoty předané v *Arg*, který může být jiný než typ *Arg*. Obvykle určeno argumentem šablony funkce předávání.|
|*arg*|Argument, který chcete přetypovat.|

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz rvalue na *Arg* Pokud hodnota předaná v *Arg* byla původně rvalue nebo odkaz na rvalue; v opačném případě vrátí *Arg* beze změny jeho typu.

### <a name="remarks"></a>Poznámky

Je nutné zadat explicitní argument šablony pro volání `forward`.

`forward` nepředává svůj argument. Místo toho podle podmíněně přetypuje svůj argument na odkaz rvalue, pokud byla původně rvalue nebo odkaz rvalue, `forward` umožňuje kompilátoru provést řešení přetížení se znalostí původního typu předaného argumentu. Viditelný typ argumentu pro funkci předání může být jiný než jeho původní typ, například když se používá jako argument pro funkci a je vázán na název parametru; r-hodnoty. s názvem umožňuje l-hodnotou, bez ohledu na to, zda daná hodnota skutečně existuje jako hodnota rvalue – `forward` obnoví deklarovanou rvalue argumentu.

Obnovení deklarovanou rvalue původní hodnoty argumentu, aby bylo možné provést řešení přetížení se označuje jako *perfektní přesměrování*. Dokonalé předávání umožňuje funkci šablony přijmout argument některého typu odkazu a obnovit jeho vlastnost rvalue, když je nezbytná pro správné řešení přetížení. Pomocí dokonalého předávání můžete zachovat sémantiku přesunu pro hodnoty rvalue. Nebude tak nutné poskytovat přetížení pro funkce, které se liší pouze typem odkazu svých argumentů.

## <a name="get"></a>  získat

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

*Index*<br/>
Index elementu určené založený na 0.

*T1*<br/>
Typ první prvek dvojice.

*T2*<br/>
Typ elementu druhý pár.

*pr*<br/>
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

    /*
    Output:
    9 3.14
    1 0.27
    */

}
```

## <a name="make_pair"></a>  make_pair

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

*Val1*<br/>
Hodnota, která inicializuje první prvek `pair`.

*Val2*<br/>
Hodnota, která inicializuje druhý prvek `pair`.

### <a name="return-value"></a>Návratová hodnota

Vytvořený objekt dvojice: `pair` <  `T`, `U`> ( `Val1`, `Val2`).

### <a name="remarks"></a>Poznámky

`make_pair` Převede objekt typu [reference_wrapper – třída](../standard-library/reference-wrapper-class.md) na referenční typy a převede Slábnoucí pole a funkce na ukazatele.

Ve vráceném `pair` objektu, `T` je stanoven následujícím způsobem:

- Pokud vstupní typ `T` je `reference_wrapper<X>`, vrátil typ `T` je `X&`.

- V opačném případě vrácený typ `T` je `decay<T>::type`. Pokud [decay – třída](../standard-library/decay-class.md) není podporováno, vrácený typ `T` je stejný jako vstupní typ `T`.

Vrácený typ `U` je podobně určen na základě vstupního typu `U`.

Jednou z výhod `make_pair` je, že typy ukládaných objektů jsou určeny automaticky kompilátorem a není nutné explicitně zadat. Nepoužívejte explicitní argumenty šablony, jako `make_pair<int, int>(1, 2)` při použití `make_pair` protože je zbytečně podrobný a přidá komplexní rvalue reference problémy, které mohou způsobit selhání kompilace. V tomto příkladu by správná syntaxe byla `make_pair(1, 2)`

`make_pair` Pomocná funkce také umožňuje předat dvě hodnoty funkci, která vyžaduje dvojici jako vstupní parametr.

### <a name="example"></a>Příklad

Příklad použití funkce pomocné rutiny `make_pair` deklaraci a inicializaci dvojice naleznete v tématu [pair – struktura](../standard-library/pair-structure.md).

## <a name="move"></a>  Přesunutí

Bezpodmínečně přetypuje svůj argument na odkaz hodnoty rvalue a značí, že ji lze přesunout, pokud je pro její typ přesunutí povoleno.

```cpp
template <class Type>
constexpr typename remove_reference<Type>::type&& move(Type&& Arg) noexcept;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Typ*|Typ odvozený od typu argumentu předaného *Arg*společně s pravidly pro sbalení odkazu.|
|*arg*|Argument, který chcete přetypovat. I když typ *Arg* jeví jako zadaný jako odkaz hodnoty rvalue, `move` také přijímá argumenty hodnoty lvalue, protože odkazy lvalue lze vázat na odkazy rvalue.|

### <a name="return-value"></a>Návratová hodnota

`Arg` jako odkaz hodnoty rvalue zda její typ je typ odkazu.

### <a name="remarks"></a>Poznámky

Argument šablony *typ* není určen k explicitnímu určení, ale k odvození od typu hodnoty předané v *Arg*. Typ *typ* je dále upraven podle pravidel sbalení odkazů.

`move` nepřesune svůj argument. Místo toho podle bezpodmínečným přetypováním svého argumentu, který může být l-hodnota – na odkaz rvalue, povolí kompilátorovi následně přesunout, spíše než kopírování, hodnota předaná v *Arg* li její typ přesunutí povoleno. Pokud pro daný typ není povolen přesun, hodnota se zkopíruje.

Pokud hodnota předaná v *Arg* l-hodnotou, tedy má název nebo adresu je možné provést – zneplatněna po provedení přesunutí. Neodkazují na hodnotu předanou v *Arg* podle názvu nebo adresy až po přesunutí neodkazujte.

## <a name="swap"></a>  Prohození

Vymění prvky dvou [pair – struktura](../standard-library/pair-structure.md) objekty.

```cpp
template <class T, class U>
void swap(pair<T, U>& left, pair<T, U>& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*doleva*|Objekt typu `pair`.|
|*doprava*|Objekt typu `pair`.|

### <a name="remarks"></a>Poznámky

Jednou z výhod `swap` je, že typy ukládaných objektů jsou určeny automaticky kompilátorem a není nutné explicitně zadat. Nepoužívejte explicitní argumenty šablony, jako `swap<int, int>(1, 2)` při použití `swap` protože je zbytečně podrobný a přidá komplexní rvalue reference problémy, které mohou způsobit selhání kompilace.

## <a name="see-also"></a>Viz také:

[\<Nástroje >](../standard-library/utility.md)<br/>
