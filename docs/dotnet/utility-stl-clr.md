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
ms.openlocfilehash: 6d025230abcff42e367a231e616a13f0f8c684f0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320295"
---
# <a name="utility-stlclr"></a>utility (STL/CLR)

Zahrňte hlavičku `<cliext/utility>` STL/CLR `pair` a definujte třídu šablony a několik podpůrných funkcí šablony.

## <a name="syntax"></a>Syntaxe

```cpp
#include <utility>
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<cliext/utility>

**Obor názvů:** cliext

## <a name="declarations"></a>Deklarace

|Třída|Popis|
|-----------|-----------------|
|[pair (STL/CLR)](#pair)|Zabalte pár prvků.|

|Operátor|Popis|
|--------------|-----------------|
|[operator== (pair) (STL/CLR)](#op_eq)|Pár rovná porovnání.|
|[operátor!= (pár) (STL/CLR)](#op_neq)|Dvojice není rovna porovnání.|
|[operátor< (pár) (STL/CLR)](#op_lt)|Spárovat méně než porovnání.|
|[operátor\<= (pár) (STL/CLR)](#op_lteq)|Spárovat porovnání menší než nebo rovno porovnání.|
|[operátor> (pár) (STL/CLR)](#op_gt)|Pár větší než porovnání.|
|[operátor>= (pár) (STL/CLR)](#op_gteq)|Spárovat porovnání větší než nebo rovno porovnání.|

|Funkce|Popis|
|--------------|-----------------|
|[make_pair (STL/CLR)](#make_pair)|Vytvořte pár z dvojice hodnot.|

## <a name="members"></a>Členové

## <a name="pair-stlclr"></a><a name="pair"></a>pár (STL/CLR)

Třída šablony popisuje objekt, který obtéká dvojici hodnot.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    ref class pair;
```

#### <a name="parameters"></a>Parametry

*Hodnota1*<br/>
Typ první zabalené hodnoty.

*Hodnota2*<br/>
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
|[pair::pair (STL/CLR)](#pair_pair)|Vytvoří objekt dvojice.|
|[pair::swap (STL/CLR)](#swap)|Zamění obsah dvou párů.|

|Operátor|Popis|
|--------------|-----------------|
|[pair::operator= (STL/CLR)](#op_as)|Nahradí uloženou dvojici hodnot.|

## <a name="remarks"></a>Poznámky

Objekt ukládá dvojici hodnot. Tato třída šablony slouží ke sloučení dvou hodnot do jednoho objektu. Objekt `cliext::pair` (popsaný zde) také ukládá pouze spravované typy; chcete-li uložit dvojici `std::pair`nespravovaných typů použití , deklarované v `<utility>`.

## <a name="pairfirst-stlclr"></a><a name="first"></a>pár::první (STL/CLR)

První zabalené hodnoty.

### <a name="syntax"></a>Syntaxe

```cpp
Value1 first;
```

### <a name="remarks"></a>Poznámky

Objekt ukládá první zalomenou hodnotu.

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

## <a name="pairfirst_type-stlclr"></a><a name="first_type"></a>dvojice::first_type (STL/CLR)

Typ první zabalené hodnoty.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Value1 first_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro parametr šablony *Value1*.

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

## <a name="pairoperator-stlclr"></a><a name="op_as"></a>pár::operátor= (STL/CLR)

Nahradí uloženou dvojici hodnot.

### <a name="syntax"></a>Syntaxe

```cpp
pair<Value1, Value2>% operator=(pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*Právo*<br/>
Spárujte ke kopírování.

### <a name="remarks"></a>Poznámky

Operátor člena zkopíruje *právo* na `*this`objekt a pak vrátí . Slouží k nahrazení uložené dvojice hodnot kopií uložené dvojice hodnot v *pravé .*

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

## <a name="pairpair-stlclr"></a><a name="pair_pair"></a>pár::pair (STL/CLR)

Vytvoří objekt dvojice.

### <a name="syntax"></a>Syntaxe

```cpp
pair();
pair(pair<Coll>% right);
pair(pair<Coll>^ right);
pair(Value1 val1, Value2 val2);
```

#### <a name="parameters"></a>Parametry

*Právo*<br/>
Spárujte do uložení.

*val1*<br/>
První hodnota k uložení.

*val2*<br/>
Druhá hodnota pro uložení.

### <a name="remarks"></a>Poznámky

Konstruktor:

`pair();`

inicializuje uloženou dvojici s výchozími vytvořenými hodnotami.

Konstruktor:

`pair(pair<Value1, Value2>% right);`

inicializuje uloženou `right.`dvojici s [pair::first (STL/CLR)](../dotnet/pair-first-stl-clr.md) a `right.` [pair::second (STL/CLR).](../dotnet/pair-second-stl-clr.md)

`pair(pair<Value1, Value2>^ right);`

inicializuje uloženou `right->`dvojici s [pair::first (STL/CLR)](../dotnet/pair-first-stl-clr.md) a `right>` [pair::second (STL/CLR).](../dotnet/pair-second-stl-clr.md)

Konstruktor:

`pair(Value1 val1, Value2 val2);`

inicializuje uloženou dvojici s *val1* a *val2*.

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

## <a name="pairsecond-stlclr"></a><a name="second"></a>pár::sekunda (STL/CLR)

Druhá zalomená hodnota.

### <a name="syntax"></a>Syntaxe

```cpp
Value2 second;
```

### <a name="remarks"></a>Poznámky

Objekt ukládá druhou zalomenou hodnotu.

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

## <a name="pairsecond_type-stlclr"></a><a name="second_type"></a>dvojice::second_type (STL/CLR)

Typ druhé zabalené hodnoty.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Value2 second_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro parametr šablony *Value2*.

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

## <a name="pairswap-stlclr"></a><a name="swap"></a>pár::swap (STL/CLR)

Zamění obsah dvou párů.

### <a name="syntax"></a>Syntaxe

```cpp
void swap(pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*Právo*<br/>
Spárujte obsah a vyměňte si obsah.

### <a name="remarks"></a>Poznámky

Členská funkce zamění uloženou `*this` dvojici hodnot mezi a *vpravo*.

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

Vytvořte `pair` z dvojice hodnot.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    pair<Value1, Value2> make_pair(Value1 first, Value2 second);
```

#### <a name="parameters"></a>Parametry

*Hodnota1*<br/>
Typ první zabalené hodnoty.

*Hodnota2*<br/>
Typ druhé zabalené hodnoty.

*První*<br/>
První hodnota zalomit.

*Druhé*<br/>
Druhá hodnota zalomit.

### <a name="remarks"></a>Poznámky

Funkce šablony `pair<Value1, Value2>(first, second)`vrátí . Slouží k vytvoření `pair<Value1, Value2>` objektu z dvojice hodnot.

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

## <a name="operator-pair-stlclr"></a><a name="op_neq"></a>operátor!= (pár) (STL/CLR)

Dvojice není rovna porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    bool operator!=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*Vlevo*<br/>
Levý pár k porovnání.

*Právo*<br/>
Správný pár k porovnání.

### <a name="remarks"></a>Poznámky

Funkce operátoru `!(left == right)`vrátí . Můžete použít k testování zda *left* není objednané stejné jako *right* při porovnání element po elementu dva páry.

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

## <a name="operatorlt-pair-stlclr"></a><a name="op_lt"></a>operátor&lt; (pár) (STL/CLR)

Spárovat méně než porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    bool operator<(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*Vlevo*<br/>
Levý pár k porovnání.

*Právo*<br/>
Správný pár k porovnání.

### <a name="remarks"></a>Poznámky

Funkce operátoru `left.first <` `right.first || !(right.first <` `left.first &&` `left.second <` `right.second`vrátí . Můžete použít k testování zda *left* je objednané před *right* při porovnání element po elementu dva páry.

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

## <a name="operatorlt-pair-stlclr"></a><a name="op_lteq"></a>operátor&lt;= (pár) (STL/CLR)

Spárovat porovnání menší než nebo rovno porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    bool operator<=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*Vlevo*<br/>
Levý pár k porovnání.

*Právo*<br/>
Správný pár k porovnání.

### <a name="remarks"></a>Poznámky

Funkce operátoru `!(right < left)`vrátí . Můžete použít k testování zda *left* není objednané po *right* při porovnání element po elementu dva páry.

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

## <a name="operator-pair-stlclr"></a><a name="op_eq"></a>operátor== (pár) (STL/CLR)

Pár rovná porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    bool operator==(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*Vlevo*<br/>
Levý pár k porovnání.

*Právo*<br/>
Správný pár k porovnání.

### <a name="remarks"></a>Poznámky

Funkce operátoru `left.first ==` `right.first &&` `left.second ==` `right.second`vrátí . Můžete použít k testování zda *left* je objednané stejné jako *right* při porovnání element po elementu dva páry.

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

## <a name="operatorgt-pair-stlclr"></a><a name="op_gt"></a>operátor&gt; (pár) (STL/CLR)

Pár větší než porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    bool operator>(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*Vlevo*<br/>
Levý pár k porovnání.

*Právo*<br/>
Správný pár k porovnání.

### <a name="remarks"></a>Poznámky

Funkce operátoru `right` `<` `left`vrátí . Můžete použít k testování zda *left* je objednáno po *right* při porovnání element po elementu dva páry.

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

## <a name="operatorgt-pair-stlclr"></a><a name="op_gteq"></a>operátor&gt;= (pár) (STL/CLR)

Spárovat porovnání větší než nebo rovno porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    bool operator>=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*Vlevo*<br/>
Levý pár k porovnání.

*Právo*<br/>
Správný pár k porovnání.

### <a name="remarks"></a>Poznámky

Funkce operátoru `!(left < right)`vrátí . Můžete použít k testování zda *left* není objednané před *right* při porovnání element po elementu dva páry.

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
