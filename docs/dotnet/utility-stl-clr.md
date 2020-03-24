---
title: utility (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- <cliext/utility>
- cliext::pair
- cliext::pair::pair
- cliext::pair::first
- cliext::pair::first_type
- cliext::pair::second
- cliext::pair::second_type
- cliext::pair::swap
- cliext::make_pair
- cliext::pair::operator=
- cliext::pair::operator==
- cliext::pair::operator>=
- cliext::pair::operator>
- cliext::pair::operator!=
- cliext::pair::operator<=
- cliext::pair::operator<
helpviewer_keywords:
- <utility> header [STL/CLR]
- utility header [STL/CLR]
- <cliext/utility> header [STL/CLR]
- first member [STL/CLR]
- first_type member [STL/CLR]
- second member [STL/CLR]
- second_type member [STL/CLR]
- swap member [STL/CLR]
- make_pair function [STL/CLR]
- pair class [STL/CLR]
- pair member [STL/CLR]
- operator== member [STL/CLR]
- operator= member [STL/CLR]
- operator>= member [STL/CLR]
- operator> member [STL/CLR]
- operator!= member [STL/CLR]
- operator<= member [STL/CLR]
- operator< member [STL/CLR]
ms.assetid: fb48cb75-d5ef-47ce-b526-bf60dc86c552
ms.openlocfilehash: a841c41c8f640dcde2a3d98841f66f6c6dc04602
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208283"
---
# <a name="utility-stlclr"></a>utility (STL/CLR)

Zahrňte `<cliext/utility>` záhlaví STL/CLR pro definování `pair` třídy šablony a několika pomocných funkcí šablon.

## <a name="syntax"></a>Syntaxe

```cpp
#include <utility>
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<cliext –/utility >

**Obor názvů:** cliext –

## <a name="declarations"></a>Deklarace

|Třída|Popis|
|-----------|-----------------|
|[pair (STL/CLR)](#pair)|Zabalte dvojici prvků.|

|Operátor|Popis|
|--------------|-----------------|
|[operator== (pair) (STL/CLR)](#op_eq)|Párování rovnosti.|
|[operator!= (pair) (STL/CLR)](#op_neq)|Dvojice není shodná s porovnáním.|
|[operator< (pair) (STL/CLR)](#op_lt)|Dvojice je menší než porovnání.|
|[operator\<= (párové) – operátor (STL/CLR)](#op_lteq)|Dvojice je menší nebo rovna hodnotě porovnání.|
|[operator> (pair) (STL/CLR)](#op_gt)|Dvojice je větší než porovnání.|
|[operator>= (pair) (STL/CLR)](#op_gteq)|Dvojice, která je větší nebo rovna porovnání|

|Funkce|Popis|
|--------------|-----------------|
|[make_pair (STL/CLR)](#make_pair)|Vytvořte dvojici z páru hodnot.|

## <a name="members"></a>Členové

## <a name="pair-stlclr"></a><a name="pair"></a>párové (STL/CLR)
Třída šablony popisuje objekt, který zabalí dvojici hodnot.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    ref class pair;
```

#### <a name="parameters"></a>Parametry

*Hodnota1*<br/>
Typ první zabalené hodnoty.

*Argument*<br/>
Typ druhé zabalené hodnoty.

## <a name="members"></a>Členové

|Definice typu|Popis|
|---------------------|-----------------|
|[pair::first_type (STL/CLR)](#first_type)|Typ první zabalené hodnoty.|
|[pair::second_type (STL/CLR)](#second_type)|Typ druhé zabalené hodnoty.|

|Členský objekt|Popis|
|-------------------|-----------------|
|[pair::first (STL/CLR)](#first)|První uložená hodnota.|
|[pair::second (STL/CLR)](#second)|Druhá uložená hodnota.|

|Členská funkce|Popis|
|---------------------|-----------------|
|[pair::pair (STL/CLR)](#pair_pair)|Vytvoří dvojici objektu.|
|[pair::swap (STL/CLR)](#swap)|Zamění obsah dvou párů.|

|Operátor|Popis|
|--------------|-----------------|
|[pair::operator= (STL/CLR)](#op_as)|Nahradí uložený pár hodnot.|

## <a name="remarks"></a>Poznámky

Objekt ukládá dvojici hodnot. Tuto třídu šablony použijete ke kombinování dvou hodnot do jednoho objektu. Také `cliext::pair` objektu (popsané zde) ukládá pouze spravované typy; Chcete-li uložit dvojici nespravovaných typů, použijte `std::pair`deklarované v `<utility>`.

## <a name="pairfirst-stlclr"></a><a name="first"></a>párové:: First (STL/CLR)

První zabalená hodnota.

### <a name="syntax"></a>Syntaxe

```cpp
Value1 first;
```

### <a name="remarks"></a>Poznámky

Objekt ukládá první zabalenou hodnotu.

### <a name="example"></a>Příklad

```cpp
// cliext_pair_first.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    cliext::pair<wchar_t, int>::first_type first_val = c1.first;
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);
    return (0);
    }
```

```Output
[x, 3]
```

## <a name="pairfirst_type-stlclr"></a><a name="first_type"></a>párové:: first_type (STL/CLR)

Typ první zabalené hodnoty.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Value1 first_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony *hodnota1*.

### <a name="example"></a>Příklad

```cpp
// cliext_pair_first_type.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    cliext::pair<wchar_t, int>::first_type first_val = c1.first;
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);
    return (0);
    }
```

```Output
[x, 3]
```

## <a name="pairoperator-stlclr"></a><a name="op_as"></a>párové:: operator = (STL/CLR)

Nahradí uložený pár hodnot.

### <a name="syntax"></a>Syntaxe

```cpp
pair<Value1, Value2>% operator=(pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*Kliknutím*<br/>
Pár ke zkopírování.

### <a name="remarks"></a>Poznámky

Operátor členu kopíruje *přímo* na objekt a potom vrátí `*this`. Použijete ho k nahrazení uložené dvojice hodnot pomocí kopie uložené dvojice hodnot *vpravo*.

### <a name="example"></a>Příklad

```cpp
// cliext_pair_operator_as.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

// assign to a new pair
    cliext::pair<wchar_t, int> c2;
    c2 = c1;
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);
    return (0);
    }
```

```Output
[x, 3]
[x, 3]
```

## <a name="pairpair-stlclr"></a><a name="pair_pair"></a>párové::p Air (STL/CLR)

Vytvoří dvojici objektu.

### <a name="syntax"></a>Syntaxe

```cpp
pair();
pair(pair<Coll>% right);
pair(pair<Coll>^ right);
pair(Value1 val1, Value2 val2);
```

#### <a name="parameters"></a>Parametry

*Kliknutím*<br/>
Pár, který se má uložit

*Val1*<br/>
První hodnota, která se má uložit

*Val2*<br/>
Druhá hodnota, která se má uložit

### <a name="remarks"></a>Poznámky

Konstruktor:

`pair();`

Inicializuje uložený pár s výchozími konstruovanými hodnotami.

Konstruktor:

`pair(pair<Value1, Value2>% right);`

Inicializuje uložený pár pomocí `right.`[dvojice:: First (STL/CLR)](../dotnet/pair-first-stl-clr.md) a `right.`[dvojice:: Second (STL/CLR)](../dotnet/pair-second-stl-clr.md).

`pair(pair<Value1, Value2>^ right);`

Inicializuje uložený pár pomocí `right->`[dvojice:: First (STL/CLR)](../dotnet/pair-first-stl-clr.md) a `right>`[dvojice:: Second (STL/CLR)](../dotnet/pair-second-stl-clr.md).

Konstruktor:

`pair(Value1 val1, Value2 val2);`

Inicializuje uložený pár pomocí *Val1* a *Val2*.

### <a name="example"></a>Příklad

```cpp
// cliext_pair_construct.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
// construct an empty container
    cliext::pair<wchar_t, int> c1;
    System::Console::WriteLine("[{0}, {1}]",
        c1.first == L'\0' ? "\\0" : "??", c1.second);

// construct with a pair of values
    cliext::pair<wchar_t, int> c2(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

// construct by copying another pair
    cliext::pair<wchar_t, int> c3(c2);
    System::Console::WriteLine("[{0}, {1}]", c3.first, c3.second);

// construct by copying a pair handle
    cliext::pair<wchar_t, int> c4(%c3);
    System::Console::WriteLine("[{0}, {1}]", c4.first, c4.second);

    return (0);
    }
```

```Output
[\0, 0]
[x, 3]
[x, 3]
[x, 3]
```

## <a name="pairsecond-stlclr"></a><a name="second"></a>párové:: Second (STL/CLR)

Druhá zabalená hodnota.

### <a name="syntax"></a>Syntaxe

```cpp
Value2 second;
```

### <a name="remarks"></a>Poznámky

Objekt ukládá druhou zabalenou hodnotu.

### <a name="example"></a>Příklad

```cpp
// cliext_pair_second.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    cliext::pair<wchar_t, int>::first_type first_val = c1.first;
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);
    return (0);
    }
```

```Output
[x, 3]
```

## <a name="pairsecond_type-stlclr"></a><a name="second_type"></a>párové:: second_type (STL/CLR)

Typ druhé zabalené hodnoty.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Value2 second_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony *hodnota2*.

### <a name="example"></a>Příklad

```cpp
// cliext_pair_second_type.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    cliext::pair<wchar_t, int>::first_type first_val = c1.first;
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);
    return (0);
    }
```

```Output
[x, 3]
```

## <a name="pairswap-stlclr"></a><a name="swap"></a>párové:: swap (STL/CLR)

Zamění obsah dvou párů.

### <a name="syntax"></a>Syntaxe

```cpp
void swap(pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*Kliknutím*<br/>
Dvojici, pomocí které se má obsah prohodit.

### <a name="remarks"></a>Poznámky

Členská funkce přemění uloženou dvojici hodnot mezi `*this` a *Right*.

### <a name="example"></a>Příklad

```cpp
// cliext_pair_swap.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
    {
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct another container with repetition of values
    cliext::deque<wchar_t> d2(5, L'x');
    Mycoll c2(%d2);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// swap and redisplay
    c1.swap(c2);
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
x x x x x
x x x x x
a b c
```

## <a name="make_pair-stlclr"></a><a name="make_pair"></a>make_pair (STL/CLR)

Vytvoří `pair` z páru hodnot.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    pair<Value1, Value2> make_pair(Value1 first, Value2 second);
```

#### <a name="parameters"></a>Parametry

*Hodnota1*<br/>
Typ první zabalené hodnoty.

*Argument*<br/>
Typ druhé zabalené hodnoty.

*první*<br/>
První hodnota, která se má zabalit

*první*<br/>
Druhá hodnota, která se má zabalit

### <a name="remarks"></a>Poznámky

Funkce šablony vrací `pair<Value1, Value2>(first, second)`. Použijete ji k vytvoření objektu `pair<Value1, Value2>` z páru hodnot.

### <a name="example"></a>Příklad

```cpp
// cliext_make_pair.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    c1 = cliext::make_pair(L'y', 4);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    return (0);
    }
```

```Output
[x, 3]
[y, 4]
```

## <a name="operator-pair-stlclr"></a><a name="op_neq"></a>operator! = (Pair) – operátor (STL/CLR)

Dvojice není shodná s porovnáním.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    bool operator!=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*zbývá*<br/>
Levý pár k porovnání

*Kliknutím*<br/>
Pravý pár, který se má porovnat.

### <a name="remarks"></a>Poznámky

Funkce operátoru vrací `!(left == right)`. Použijete ho k otestování, jestli *vlevo* není seřazené stejně jako *právo* , pokud jsou tyto dva páry porovnány s elementy podle elementu.

### <a name="example"></a>Příklad

```cpp
// cliext_pair_operator_ne.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] != [x 3] is {0}",
        c1 != c1);
    System::Console::WriteLine("[x 3] != [x 4] is {0}",
        c1 != c2);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] != [x 3] is False
[x 3] != [x 4] is True
```

## <a name="operatorlt-pair-stlclr"></a><a name="op_lt"></a>operator&lt; (párové) – operátor (STL/CLR)

Dvojice je menší než porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    bool operator<(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*zbývá*<br/>
Levý pár k porovnání

*Kliknutím*<br/>
Pravý pár, který se má porovnat.

### <a name="remarks"></a>Poznámky

Funkce operator vrací `left.first <` `right.first || !(right.first <` `left.first &&` `left.second <` `right.second`. Použijete ji k otestování, zda je před porovnáním obou párů na základě prvku porovnáváno *levé* *straně.*

### <a name="example"></a>Příklad

```cpp
// cliext_pair_operator_lt.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] < [x 3] is {0}",
        c1 < c1);
    System::Console::WriteLine("[x 3] < [x 4] is {0}",
        c1 < c2);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] < [x 3] is False
[x 3] < [x 4] is True
```

## <a name="operatorlt-pair-stlclr"></a><a name="op_lteq"></a>operator&lt;= (párové) – operátor (STL/CLR)

Dvojice je menší nebo rovna hodnotě porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    bool operator<=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*zbývá*<br/>
Levý pár k porovnání

*Kliknutím*<br/>
Pravý pár, který se má porovnat.

### <a name="remarks"></a>Poznámky

Funkce operátoru vrací `!(right < left)`. Použijete ho k otestování, jestli není po *pravé straně* při porovnání obou párů na základě prvku k *stranu* seřazená.

### <a name="example"></a>Příklad

```cpp
// cliext_pair_operator_le.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] <= [x 3] is {0}",
        c1 <= c1);
    System::Console::WriteLine("[x 4] <= [x 3] is {0}",
        c2 <= c1);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] <= [x 3] is True
[x 4] <= [x 3] is False
```

## <a name="operator-pair-stlclr"></a><a name="op_eq"></a>operator = = (Pair) – operátor (STL/CLR)

Párování rovnosti.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    bool operator==(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*zbývá*<br/>
Levý pár k porovnání

*Kliknutím*<br/>
Pravý pár, který se má porovnat.

### <a name="remarks"></a>Poznámky

Funkce operator vrací `left.first ==` `right.first &&` `left.second ==` `right.second`. Použijete ji k otestování, zda je *levé* řazení stejné jako *pravé* , pokud jsou obě dvojice porovnány podle elementu.

### <a name="example"></a>Příklad

```cpp
// cliext_pair_operator_eq.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] == [x 3] is {0}",
        c1 == c1);
    System::Console::WriteLine("[x 3] == [x 4] is {0}",
        c1 == c2);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] == [x 3] is True
[x 3] == [x 4] is False
```

## <a name="operatorgt-pair-stlclr"></a><a name="op_gt"></a>operator&gt; (párové) – operátor (STL/CLR)

Dvojice je větší než porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    bool operator>(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*zbývá*<br/>
Levý pár k porovnání

*Kliknutím*<br/>
Pravý pár, který se má porovnat.

### <a name="remarks"></a>Poznámky

Funkce operator vrací `right` `<` `left`. Použijete ji k otestování, *zda je* po *pravé* době porovnávána dvojice dvou párů elementem.

### <a name="example"></a>Příklad

```cpp
// cliext_pair_operator_gt.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] > [x 3] is {0}",
        c1 > c1);
    System::Console::WriteLine("[x 4] > [x 3] is {0}",
        c2 > c1);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] > [x 3] is False
[x 4] > [x 3] is True
```

## <a name="operatorgt-pair-stlclr"></a><a name="op_gteq"></a>operator&gt;= (párové) – operátor (STL/CLR)

Dvojice, která je větší nebo rovna porovnání

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    bool operator>=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*zbývá*<br/>
Levý pár k porovnání

*Kliknutím*<br/>
Pravý pár, který se má porovnat.

### <a name="remarks"></a>Poznámky

Funkce operátoru vrací `!(left < right)`. Použijete ji k otestování, zda je *ponecháno* před *pravou* , pokud jsou obě dvojice porovnány elementem podle elementu.

### <a name="example"></a>Příklad

```cpp
// cliext_pair_operator_ge.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] >= [x 3] is {0}",
        c1 >= c1);
    System::Console::WriteLine("[x 3] >= [x 4] is {0}",
        c1 >= c2);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] >= [x 3] is True
[x 3] >= [x 4] is False
```
