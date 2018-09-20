---
title: nástroje (STL/CLR) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 307d3c2f95d006ae36ff39cf3c16ff3fd65a4c34
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46374233"
---
# <a name="utility-stlclr"></a>utility (STL/CLR)

Zahrnout záhlaví STL/CLR `<cliext/utility>` definice třídy šablony `pair` a několik podpůrných šablon funkcí.

## <a name="syntax"></a>Syntaxe

```cpp
#include <utility>
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<cliext – / nástroje >

**Namespace:** cliext –

## <a name="declarations"></a>Deklarace

|Třída|Popis|
|-----------|-----------------|
|[pair (STL/CLR)](#pair)|Zabalení dvojici prvků.|

|Operátor|Popis|
|--------------|-----------------|
|[operator== (pair) (STL/CLR)](#op_eq)|Porovnání rovna pár.|
|[operator!= (pair) (STL/CLR)](#op_neq)|Spárujte nerovná porovnání.|
|[operator< (pair) (STL/CLR)](#op_lt)|Dvojice menší než porovnání.|
|[operátor\<= (pair) (STL/CLR)](#op_lteq)|Pair – menší nebo rovna porovnání.|
|[operator> (pair) (STL/CLR)](#op_gt)|Dvojice větší než porovnání.|
|[operator>= (pair) (STL/CLR)](#op_gteq)|Pár větší než nebo rovna porovnání.|

|Funkce|Popis|
|--------------|-----------------|
|[make_pair (STL/CLR)](#make_pair)|Proveďte pár z dvojice hodnot.|

## <a name="members"></a>Členové

##<a name="pair"></a> pár (STL/CLR)
Třída šablony popisuje objekt, který obtéká dvojici hodnot.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    ref class pair;
```

#### <a name="parameters"></a>Parametry

*Hodnota1*<br/>
Typ první zabalená hodnota.

*Hodnota2*<br/>
Typ druhého zabalená hodnota.

## <a name="members"></a>Členové

|Definice typu|Popis|
|---------------------|-----------------|
|[pair::first_type (STL/CLR)](#first_type)|Typ první zabalená hodnota.|
|[pair::second_type (STL/CLR)](#second_type)|Typ druhého zabalená hodnota.|

|Člen objektu|Popis|
|-------------------|-----------------|
|[pair::first (STL/CLR)](#first)|První uloženou hodnotu.|
|[pair::second (STL/CLR)](#second)|Druhý uloženou hodnotu.|

|Členská funkce|Popis|
|---------------------|-----------------|
|[pair::pair (STL/CLR)](#pair_pair)|Vytvoří objekt dvojice.|
|[pair::swap (STL/CLR)](#swap)|Zamění obsah dvou dvojice.|

|Operátor|Popis|
|--------------|-----------------|
|[pair::operator= (STL/CLR)](#op_as)|Nahradí uloženou dvojice hodnot.|

## <a name="remarks"></a>Poznámky

Objekt ukládají dvojice hodnot. Pomocí této třídy šablony kombinovat dvě hodnoty do jediného objektu. Kromě toho objekt `cliext::pair` (zde popsané) ukládá pouze spravované typy; k uložení pár nespravovaného typy používají `std::pair`, které jsou deklarovány v `<utility>`.

## <a name="first"></a> Pair::First (STL/CLR)

První zabalená hodnota.

### <a name="syntax"></a>Syntaxe

```cpp
Value1 first;
```

### <a name="remarks"></a>Poznámky

Objekt ukládá první zabalená hodnota.

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

## <a name="first_type"></a> Pair::first_type (STL/CLR)

Typ první zabalená hodnota.

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

## <a name="op_as"></a> Pair::Operator = (STL/CLR)

Nahradí uloženou dvojice hodnot.

### <a name="syntax"></a>Syntaxe

```cpp
pair<Value1, Value2>% operator=(pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*doprava*<br/>
Dvojice ke kopírování.

### <a name="remarks"></a>Poznámky

Kopie členský operátor *správné* na objekt, vrátí `*this`. Můžete použít k nahrazení uložené dvojice hodnot kopie uložené dvojice hodnot v *správné*.

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

## <a name="pair_pair"></a> Pair::Pair (STL/CLR)

Vytvoří objekt dvojice.

### <a name="syntax"></a>Syntaxe

```cpp
pair();
pair(pair<Coll>% right);
pair(pair<Coll>^ right);
pair(Value1 val1, Value2 val2);
```

#### <a name="parameters"></a>Parametry

*doprava*<br/>
Dvojice k uložení.

*Val1*<br/>
První hodnota pro uložení.

*Val2*<br/>
Druhá hodnota pro uložení.

### <a name="remarks"></a>Poznámky

Konstruktor:

`pair();`

Inicializuje uložený pár vytvořen výchozí hodnoty.

Konstruktor:

`pair(pair<Value1, Value2>% right);`

Inicializuje uložený pár s `right.` [pair::first (STL/CLR)](../dotnet/pair-first-stl-clr.md) a `right.` [pair::second (STL/CLR)](../dotnet/pair-second-stl-clr.md).

`pair(pair<Value1, Value2>^ right);`

Inicializuje uložený pár s `right->` [pair::first (STL/CLR)](../dotnet/pair-first-stl-clr.md) a `right>` [pair::second (STL/CLR)](../dotnet/pair-second-stl-clr.md).

Konstruktor:

`pair(Value1 val1, Value2 val2);`

Inicializuje uložený pár s *val1* a *val2*.

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

## <a name="second"></a> Pair::Second (STL/CLR)

Druhá zabalená hodnota.

### <a name="syntax"></a>Syntaxe

```cpp
Value2 second;
```

### <a name="remarks"></a>Poznámky

Objekt uchovává druhá zabalená hodnota.

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

## <a name="second_type"></a> Pair::second_type (STL/CLR)

Typ druhého zabalená hodnota.

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

## <a name="swap"></a> Pair::swap (STL/CLR)

Zamění obsah dvou dvojice.

### <a name="syntax"></a>Syntaxe

```cpp
void swap(pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*doprava*<br/>
Dvojice k výměně obsahu s.

### <a name="remarks"></a>Poznámky

Členská funkce Zamění uložené dvojice hodnot mezi `*this` a *správné*.

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

## <a name="make_pair"></a> make_pair (STL/CLR)

Ujistěte se, `pair` z dvojice hodnot.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    pair<Value1, Value2> make_pair(Value1 first, Value2 second);
```

#### <a name="parameters"></a>Parametry

*Hodnota1*<br/>
Typ první zabalená hodnota.

*Hodnota2*<br/>
Typ druhého zabalená hodnota.

*první*<br/>
První hodnota zabalit.

*Sekundy*<br/>
Druhá hodnota zabalit.

### <a name="remarks"></a>Poznámky

Šablona funkce vrátí `pair<Value1, Value2>(first, second)`. Lze použít k sestavení `pair<Value1, Value2>` objekt z dvojice hodnot.

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

## <a name="op_neq"></a> Operator! = (pair) (STL/CLR)

Spárujte nerovná porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    bool operator!=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*doleva*<br/>
Levé pár k porovnání.

*doprava*<br/>
Správné pár k porovnání.

### <a name="remarks"></a>Poznámky

Vrátí funkci operátoru `!(left == right)`. Pomocí něho můžete testovat, zda *levé* není stejný jako seřazené *správné* když jsou dvě dvojice porovnání elementu pomocí elementu.

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

## <a name="op_lt"></a> operátor&lt; (pair) (STL/CLR)

Dvojice menší než porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    bool operator<(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*doleva*<br/>
Levé pár k porovnání.

*doprava*<br/>
Správné pár k porovnání.

### <a name="remarks"></a>Poznámky

Vrátí funkci operátoru `left.first <` `right.first || !(right.first <` `left.first &&` `left.second <` `right.second`. Pomocí něho můžete testovat, zda *levé* je seřazen před *správné* když jsou dvě dvojice porovnání elementu pomocí elementu.

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

## <a name="op_lteq"></a> operátor&lt;= (pair) (STL/CLR)

Pair – menší nebo rovna porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    bool operator<=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*doleva*<br/>
Levé pár k porovnání.

*doprava*<br/>
Správné pár k porovnání.

### <a name="remarks"></a>Poznámky

Vrátí funkci operátoru `!(right < left)`. Pomocí něho můžete testovat, zda *levé* není seřazené po *správné* když jsou dvě dvojice porovnání elementu pomocí elementu.

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

## <a name="op_eq"></a> Operator == (pair) (STL/CLR)

Porovnání rovna pár.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    bool operator==(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*doleva*<br/>
Levé pár k porovnání.

*doprava*<br/>
Správné pár k porovnání.

### <a name="remarks"></a>Poznámky

Vrátí funkci operátoru `left.first ==` `right.first &&` `left.second ==` `right.second`. Pomocí něho můžete testovat, zda *levé* je stejný jako seřazené *správné* když jsou dvě dvojice porovnání elementu pomocí elementu.

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

## <a name="op_gt"></a> operátor&gt; (pair) (STL/CLR)

Dvojice větší než porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    bool operator>(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*doleva*<br/>
Levé pár k porovnání.

*doprava*<br/>
Správné pár k porovnání.

### <a name="remarks"></a>Poznámky

Vrátí funkci operátoru `right` `<` `left`. Pomocí něho můžete testovat, zda *levé* seřazené po *správné* když jsou dvě dvojice porovnání elementu pomocí elementu.

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

## <a name="op_gteq"></a> operátor&gt;= (pair) (STL/CLR)

Pár větší než nebo rovna porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value1,
    typename Value2>
    bool operator>=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parametry

*doleva*<br/>
Levé pár k porovnání.

*doprava*<br/>
Správné pár k porovnání.

### <a name="remarks"></a>Poznámky

Vrátí funkci operátoru `!(left < right)`. Pomocí něho můžete testovat, zda *levé* není řazen před *správné* když jsou dvě dvojice porovnání elementu pomocí elementu.

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