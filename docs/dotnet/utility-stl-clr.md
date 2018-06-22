---
title: Nástroj (STL/CLR) | Microsoft Docs
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
ms.openlocfilehash: fcc97e5037898b3a9c39a6c72ed21b2c19a4c777
ms.sourcegitcommit: 301bb19056e5bae84ff50f7d1df1e546efe225ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/21/2018
ms.locfileid: "36306018"
---
# <a name="utility-stlclr"></a>utility (STL/CLR)
Zahrnout hlavičku STL/CLR `<cliext/utility>` definovat šablony třídy `pair` a několik podpůrné funkce šablony.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#include <utility>  
```

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / nástroj >  
  
 **Namespace:** cliext –  
  
## <a name="declarations"></a>Deklarace  
  
|Třída|Popis|  
|-----------|-----------------|  
|[pair (STL/CLR)](#pair)|Zabalení pár elementů.|  
  
|Operátor|Popis|  
|--------------|-----------------|  
|[operator== (pair) (STL/CLR)](#op_eq)|Pár rovnat porovnání.|  
|[operator!= (pair) (STL/CLR)](#op_neq)|Pár nerovná porovnání.|  
|[operator< (pair) (STL/CLR)](#op_lt)|Pár menší než porovnání.|  
|[operátor\<= (pair) (STL/CLR)](#op_lteq)|Spárujte menší než nebo rovna porovnání.|  
|[operator> (pair) (STL/CLR)](#op_gt)|Pár větší než porovnání.|  
|[operator>= (pair) (STL/CLR)](#op_gteq)|Pár větší než nebo rovna porovnání.|  
  
|Funkce|Popis|  
|--------------|-----------------|  
|[make_pair (STL/CLR)](#make_pair)|Aby dvojice z dvojici hodnot.|  

## <a name="members"></a>Členové

##<a name="pair"></a> pár (STL/CLR)
Šablony třídy popisuje objekt, který zabalí dvojici hodnot.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value1,  
    typename Value2>  
    ref class pair;  
```  
  
#### <a name="parameters"></a>Parametry  
 value1  
 Typ první zabalená hodnota.  
  
 Value2  
 Typ druhého zabalená hodnota.  
  
## <a name="members"></a>Členové  
  
|Definice typu|Popis|  
|---------------------|-----------------|  
|[pair::first_type (STL/CLR)](#first_type)|Typ první zabalená hodnota.|  
|[pair::second_type (STL/CLR)](#second_type)|Typ druhého zabalená hodnota.|  
  
|Člen objektu|Popis|  
|-------------------|-----------------|  
|[pair::first (STL/CLR)](#first)|První uložené hodnotu.|  
|[pair::second (STL/CLR)](#second)|Druhá hodnota uložené.|  
  
|Členská funkce|Popis|  
|---------------------|-----------------|  
|[pair::pair (STL/CLR)](#pair_pair)|Vytvoří objekt dvojice.|  
|[pair::swap (STL/CLR)](#swap)|Zamění obsah dvě dvojice.|  
  
|Operátor|Popis|  
|--------------|-----------------|  
|[pair::operator= (STL/CLR)](#op_as)|Nahradí uložené dvojice hodnot.|  
  
## <a name="remarks"></a>Poznámky  
 Objekt ukládá dvojici hodnot. Tato třída šablony slouží ke kombinování dvou hodnot do jednoho objektu. Navíc objekt `cliext::pair` (zde popsané) ukládá pouze spravované typy; k uložení pár nespravované typy využívají `std::pair`, deklarované v `<utility>`.  


## <a name="first"></a> Pair::First (STL/CLR)
První zabalená hodnota.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
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
  
```  
typedef Value1 first_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro parametr šablony `Value1`.  
  
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
Nahradí uložené dvojice hodnot.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
pair<Value1, Value2>% operator=(pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 vpravo  
 Pár ke kopírování.  
  
### <a name="remarks"></a>Poznámky  
 Kopie operátor člen `right` k objektu, vrátí `*this`. Můžete použít k nahrazení uložené dvojice hodnot s kopie uložené dvojice hodnot v `right`.  
  
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
  
```  
pair();  
pair(pair<Coll>% right);  
pair(pair<Coll>^ right);  
pair(Value1 val1, Value2 val2);  
```  
  
#### <a name="parameters"></a>Parametry  
 vpravo  
 Pár k uložení.  
  
 Hodnota1  
 První hodnota k uložení.  
  
 hodnota2  
 Druhá hodnota, která k ukládání.  
  
### <a name="remarks"></a>Poznámky  
 Konstruktor:  
  
 `pair();`  
  
 Inicializuje uložené pár s sestavený výchozí hodnoty.  
  
 Konstruktor:  
  
 `pair(pair<Value1, Value2>% right);`  
  
 Inicializuje uložené pár s `right.` [pair::first (STL/CLR)](../dotnet/pair-first-stl-clr.md) a `right.` [pair::second (STL/CLR)](../dotnet/pair-second-stl-clr.md).  
  
 `pair(pair<Value1, Value2>^ right);`  
  
 Inicializuje uložené pár s `right->` [pair::first (STL/CLR)](../dotnet/pair-first-stl-clr.md) a `right>` [pair::second (STL/CLR)](../dotnet/pair-second-stl-clr.md).  
  
 Konstruktor:  
  
 `pair(Value1 val1, Value2 val2);`  
  
 Inicializuje uložené pár s s `val1` a `val2`.  
  
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
Druhý zabalená hodnota.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
Value2 second;  
```  
  
### <a name="remarks"></a>Poznámky  
 Objekt ukládá druhý zabalená hodnota.  
  
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
  
```  
typedef Value2 second_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro parametr šablony `Value2`.  
  
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
Zamění obsah dvě dvojice.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void swap(pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 vpravo  
 Pár k výměně obsahu s.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce prohození uložené dvojice hodnot mezi `*this` a `right`.  
  
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
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct another container with repetition of values   
    cliext::deque<wchar_t> d2(5, L'x');   
    Mycoll c2(%d2);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// swap and redisplay   
    c1.swap(c2);   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
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

## <a name="make_pair"></a> make_pair – (STL/CLR)
Ujistěte se, `pair` z dvojici hodnot.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value1,  
    typename Value2>  
    pair<Value1, Value2> make_pair(Value1 first, Value2 second);  
```  
  
#### <a name="parameters"></a>Parametry  
 `Value1`  
 Typ první zabalená hodnota.  
  
 `Value2`  
 Typ druhého zabalená hodnota.  
  
 `first`  
 První hodnota zabalit.  
  
 `second`  
 Druhá hodnota zabalit.  
  
### <a name="remarks"></a>Poznámky  
 Funkce šablony vrátí `pair<Value1, Value2>(first, second)`. Lze použít k sestavení `pair<Value1, Value2>` objekt z dvojici hodnot.  
  
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
Pár nerovná porovnání.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value1,  
    typename Value2>  
    bool operator!=(pair<Value1, Value2>% left,  
        pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 left  
 Levé pár k porovnání.  
  
 vpravo  
 Pravé pár k porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Operátor funkce vrátí hodnotu `!(left == right)`. Můžete použít k testování zda `left` není stejný jako seřazené `right` když jsou dvě dvojice porovná s prvkem elementu.  
  
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
Pár menší než porovnání.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value1,  
    typename Value2>  
    bool operator<(pair<Value1, Value2>% left,  
        pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 left  
 Levé pár k porovnání.  
  
 vpravo  
 Pravé pár k porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Operátor funkce vrátí hodnotu `left.first <` `right.first || !(right.first <` `left.first &&` `left.second <` `right.second`. Můžete použít k testování zda `left` je seřazené před `right` když jsou dvě dvojice porovná s prvkem elementu.  
  
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
Spárujte menší než nebo rovna porovnání.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value1,  
    typename Value2>  
    bool operator<=(pair<Value1, Value2>% left,  
        pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 left  
 Levé pár k porovnání.  
  
 vpravo  
 Pravé pár k porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Operátor funkce vrátí hodnotu `!(right < left)`. Můžete použít k testování zda `left` není objednaný po `right` když jsou dvě dvojice porovná s prvkem elementu.  
  
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
Pár rovnat porovnání.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value1,  
    typename Value2>  
    bool operator==(pair<Value1, Value2>% left,  
        pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 left  
 Levé pár k porovnání.  
  
 vpravo  
 Pravé pár k porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Operátor funkce vrátí hodnotu `left.first ==` `right.first &&` `left.second ==` `right.second`. Můžete použít k testování zda `left` je stejný jako seřazené `right` když jsou dvě dvojice porovná s prvkem elementu.  
  
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
Pár větší než porovnání.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value1,  
    typename Value2>  
    bool operator>(pair<Value1, Value2>% left,  
        pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 left  
 Levé pár k porovnání.  
  
 vpravo  
 Pravé pár k porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Operátor funkce vrátí hodnotu `right` `<` `left`. Můžete použít k testování zda `left` je objednaný po `right` když jsou dvě dvojice porovná s prvkem elementu.  
  
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
  
```  
template<typename Value1,  
    typename Value2>  
    bool operator>=(pair<Value1, Value2>% left,  
        pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 left  
 Levé pár k porovnání.  
  
 vpravo  
 Pravé pár k porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Operátor funkce vrátí hodnotu `!(left < right)`. Můžete použít k testování zda `left` není seřadí před `right` když jsou dvě dvojice porovná s prvkem elementu.  
  
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
