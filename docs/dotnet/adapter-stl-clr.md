---
title: adaptér (STL/CLR) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 06/15/2018
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- <cliext/adapter>
- cliext::collection_adapter
- cliext::collection_adapter::base
- cliext::collection_adapter::begin
- cliext::collection_adapter
- cliext::collection_adapter::collection_adapter
- cliext::collection_adapter::difference_type
- cliext::collection_adapter::end
- cliext::collection_adapter::iterator
- cliext::collection_adapter::key_type
- cliext::collection_adapter::mapped_type
- cliext::collection_adapter::operator=
- cliext::collection_adapter::reference
- cliext::collection_adapter::size
- cliext::collection_adapter::size_type
- cliext::collection_adapter::swap
- cliext::collection_adapter::value_type
- cliext::make_collection
- cliext::range_adapter
- cliext::operator=
- cliext::range_adapter::operator=
- cliext::range_adapter::range_adapter
dev_langs:
- C++
helpviewer_keywords:
- <adapter> header [STL/CLR]
- adapter [STL/CLR]
- <cliext/adapter> header [STL/CLR]
- collection_adapter class [STL/CLR]
- base member [STL/CLR]
- begin member [STL/CLR]
- collection_adapter member [STL/CLR]
- difference_type member [STL/CLR]
- end member [STL/CLR]
- iterator member [STL/CLR]
- key_type member [STL/CLR]
- mapped_type member [STL/CLR]
- operator= member [STL/CLR]
- reference member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- value_type member [STL/CLR]
- make_collection function [STL/CLR]
- range_adapter class [STL/CLR]
- operator= member [STL/CLR]
- range_adapter member [STL/CLR]
ms.assetid: 71ce7e51-42b6-4f70-9595-303791a97677
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f87ea6791144b7ce40f4e2d71a2ca7f031adbedf
ms.sourcegitcommit: bad2441d1930275ff506d44759d283d94cccd1c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/31/2018
ms.locfileid: "39376105"
---
# <a name="adapter-stlclr"></a>adapter (STL/CLR)
Záhlaví STL/CLR `<cliext/adapter>` určuje dvě šablony třídy (`collection_adapter` a `range_adapter`) a funkce šablon `make_collection`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
#include <cliext/adapter>  
```  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<adaptéru cliext – >  
  
 **Namespace:** cliext – 
  
## <a name="declarations"></a>Deklarace  
  
|Třída|Popis|  
|-----------|-----------------|  
|[collection_adapter (STL/CLR)](#collection_adapter)|Zabalí základní třídy knihovny (BCL) kolekce jako rozsah.|  
|[range_adapter (STL/CLR)](#range_adapter)|Zabalí rozsahu jako kolekci BCL.|  

|Funkce|Popis|  
|--------------|-----------------|  
|[make_collection (STL/CLR)](#make_collection)|Vytvoří rozsah adaptér pomocí páru iterátoru.|   
  
## <a name="members"></a>Členové

## <a name="collection_adapter"></a> collection_adapter – (STL/CLR)
Zabalí kolekci .NET pro použití jako kontejner STL/CLR. A `collection_adapter` je třída šablony popisující objekt jednoduchý kontejner STL/CLR. Zabalí rozhraní knihovny třídy Base (BCL) a vrátí páru iterátoru, který používáte k manipulaci s řízené sekvence.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Coll>  
    ref class collection_adapter;  
  
template<>  
    ref class collection_adapter<  
        System::Collections::ICollection>;  
template<>  
    ref class collection_adapter<  
        System::Collections::IEnumerable>;  
template<>  
    ref class collection_adapter<  
        System::Collections::IList>;  
template<>  
    ref class collection_adapter<  
        System::Collections::IDictionary>;  
template<typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::ICollection<Value>>;  
template<typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::IEnumerable<Value>>;  
template<typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::IList<Value>>;  
template<typename Key,  
    typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::IDictionary<Key, Value>>;  
```  
  
#### <a name="parameters"></a>Parametry  
 *Coll*  
 Typ kolekce.  
  
### <a name="specializations"></a>Specializace  
  
|Specializace|Popis|  
|--------------------|-----------------|  
|IEnumerable|Pořadí mezi prvky.|  
|Rozhraní ICollection|Spravuje skupiny prvků.|  
|IList|Udržuje seřazený skupiny prvků.|  
|IDictionary|Zachovat sadu {klíč, hodnota} dvojice.|  
|IEnumerable\<hodnotu >|Pořadí pomocí zadané elementy.|  
|Rozhraní ICollection\<hodnotu >|Udržuje typy prvků.|  
|IList\<hodnotu >|Udržuje uspořádanou skupinu zadané elementy.|  
|IDictionary\<hodnotu >|Udržuje sadu typu {klíč, hodnota} dvojice.|  
  
### <a name="members"></a>Členové  
  
|Definice typu|Popis|  
|---------------------|-----------------|  
|[collection_adapter::difference_type (STL/CLR)](#difference_type)|Typ vzdálenosti se znaménkem mezi dvěma prvky|  
|[collection_adapter::iterator (STL/CLR)](#iterator)|Typ iterátoru řízené sekvence|  
|[collection_adapter::key_type (STL/CLR)](#key_type)|Typ klíče slovníku.|  
|[collection_adapter::mapped_type (STL/CLR)](#mapped_type)|Typ hodnoty slovníku.|  
|[collection_adapter::reference (STL/CLR)](#reference)|Typ odkazu na prvek|  
|[collection_adapter::size_type (STL/CLR)](#size_type)|Typ vzdálenosti se znaménkem mezi dvěma prvky|  
|[collection_adapter::value_type (STL/CLR)](#value_type)|Typ prvku|  
  
|Členská funkce|Popis|  
|---------------------|-----------------|  
|[collection_adapter::base (STL/CLR)](#base)|Označí rozhraní zabalené BCL.|  
|[collection_adapter::begin (STL/CLR)](#begin)|Určuje začátek řízené sekvence.|  
|[collection_adapter::collection_adapter (STL/CLR)](#collection_adapter_collection_adapter)|Vytvoří objekt adaptér.|  
|[collection_adapter::end (STL/CLR)](#end)|Určuje konec řízené sekvence.|  
|[collection_adapter::size (STL/CLR)](#size)|Spočítá počet prvků.|  
|[collection_adapter::swap (STL/CLR)](#swap)|Zamění obsah dvou kontejnerů.|  
  
|Operátor|Popis|  
|--------------|-----------------|  
|[collection_adapter::operator= (STL/CLR)](#op_eq)|Nahradí uloženou BCL popisovač.|  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této třídy šablony pro manipulaci s BCL kontejneru jako kontejner STL/CLR. `collection_adapter` Uloží popisovač BCL rozhraní, které zase určuje pořadí prvků. A `collection_adapter` objekt `X` vrátí pár iterátorů vstupní `X.begin()` a `X.end()` můžete navštívit prvky v pořadí. Některé z odborností, které jsou také umožňují napsat `X.size()` má být určena délka řízené sekvence.  

## <a name="base"></a> collection_adapter::Base (STL/CLR)
Označí rozhraní zabalené BCL.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
Coll^ base();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí uložený rozhraní popisovač BCL.  
  
### <a name="example"></a>Příklad  
  
```cpp
// cliext_collection_adapter_base.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d6x(6, L'x');   
    Mycoll c1(%d6x);   
  
// display initial contents " x x x x x x"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("base() same = {0}", c1.base() == %c1);   
    return (0);   
    }  
```  
  
```Output  
 x x x x x x  
base() same = True  
```  

## <a name="begin"></a> collection_adapter::begin (STL/CLR)
Určuje začátek řízené sekvence.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
iterator begin();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí vstupní iterátor, který určuje první prvek řízenou sekvenci nebo přesně za konec k prázdné sekvenci.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_collection_adapter_begin.cpp   
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
  
// inspect first two items   
    Mycoll::iterator it = c1.begin();   
    System::Console::WriteLine("*begin() = {0}", *it);   
    System::Console::WriteLine("*++begin() = {0}", *++it);   
    return (0);   
    }  
```  
  
```Output  
 a b c  
*begin() = a  
*++begin() = b  
```  

## <a name="collection_adapter_collection_adapter"></a> collection_adapter::collection_adapter (STL/CLR)
Vytvoří objekt adaptér.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
collection_adapter();  
collection_adapter(collection_adapter<Coll>% right);  
collection_adapter(collection_adapter<Coll>^ right);  
collection_adapter(Coll^ collection);  
```  
  
#### <a name="parameters"></a>Parametry  
 *Kolekce*  
 Obslužná rutina BCL Zabalit.  
  
 *doprava*  
 Kopírovaný objekt.  
  
### <a name="remarks"></a>Poznámky  
 Konstruktor:  
  
 `collection_adapter();`  
  
 Inicializuje uložený popisovač s `nullptr`.  
  
 Konstruktor:  
  
 `collection_adapter(collection_adapter<Coll>% right);`  
  
 Inicializuje uložený popisovač s `right.` [collection_adapter::base (STL/CLR)](../dotnet/collection-adapter-base-stl-clr.md)`()`.  
  
 Konstruktor:  
  
 `collection_adapter(collection_adapter<Coll>^ right);`  
  
 Inicializuje uložený popisovač s `right->` [collection_adapter::base (STL/CLR)](../dotnet/collection-adapter-base-stl-clr.md)`()`.  
  
 Konstruktor:  
  
 `collection_adapter(Coll^ collection);`  
  
 Inicializuje uložený popisovač s s `collection`.  
  
### <a name="example"></a>Příklad  
  
```cpp 
// cliext_collection_adapter_construct.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d6x(6, L'x');   
  
// construct an empty container   
    Mycoll c1;   
    System::Console::WriteLine("base() null = {0}", c1.base() == nullptr);   
  
// construct with a handle   
    Mycoll c2(%d6x);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mycoll c3(c2);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    Mycoll c4(%c3);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
```  
  
```Output  
base() null = True  
 x x x x x x  
 x x x x x x  
 x x x x x x  
```  

## <a name="difference_type"></a> collection_adapter::difference_type (STL/CLR)
Typ vzdálenosti se znaménkem mezi dvěma prvky.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef int difference_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ, který popisuje počet podepsaný prvků.  
  
### <a name="example"></a>Příklad  
  
```cpp 
// cliext_collection_adapter_difference_type.cpp   
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
  
// compute positive difference   
    Mycoll::difference_type diff = 0;   
    Mycoll::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
end()-begin() = 3  
```  

## <a name="end"></a> collection_adapter::end (STL/CLR)
Určuje konec řízené sekvence.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
iterator end();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí vstupní iterátor, který ukazuje za konec řízené sekvence.  
  
### <a name="example"></a>Příklad  
  
```cpp 
// cliext_collection_adapter_end.cpp   
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
    Mycoll::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="iterator"></a> collection_adapter::iterator (STL/CLR)
Typ iterátoru řízené sekvence  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef T1 iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ popisuje objekt neurčeného typu `T1` , který může sloužit jako ke vstupnímu iterátoru řízené sekvence.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_collection_adapter_iterator.cpp   
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
    Mycoll::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
```  

## <a name="key_type"></a> collection_adapter::key_type (STL/CLR)
Typ klíče slovníku.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro parametr šablony `Key`, ve specializaci pro `IDictionary` nebo `IDictionary<Value>`; v opačném případě není definován.  
  
### <a name="example"></a>Příklad  
  
```cpp
// cliext_collection_adapter_key_type.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
typedef cliext::collection_adapter<   
    System::Collections::Generic::IDictionary<wchar_t, int>> Mycoll;   
typedef System::Collections::Generic::KeyValuePair<wchar_t,int> Mypair;   
int main()   
    {   
    Mymap d1;   
    d1.insert(Mymap::make_value(L'a', 1));   
    d1.insert(Mymap::make_value(L'b', 2));   
    d1.insert(Mymap::make_value(L'c', 3));   
    Mycoll c1(%d1);   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mypair elem in c1)   
        {   
        Mycoll::key_type key = elem.Key;   
        Mycoll::mapped_type value = elem.Value;   
        System::Console::Write(" [{0} {1}]", key, value);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```  

## <a name="mapped_type"></a> collection_adapter::mapped_type (STL/CLR)
Typ hodnoty slovníku.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef Value mapped_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro parametr šablony `Value`, ve specializaci pro `IDictionary` nebo `IDictionary<Value>`; v opačném případě není definován.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_collection_adapter_mapped_type.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
typedef cliext::collection_adapter<   
    System::Collections::Generic::IDictionary<wchar_t, int>> Mycoll;   
typedef System::Collections::Generic::KeyValuePair<wchar_t,int> Mypair;   
int main()   
    {   
    Mymap d1;   
    d1.insert(Mymap::make_value(L'a', 1));   
    d1.insert(Mymap::make_value(L'b', 2));   
    d1.insert(Mymap::make_value(L'c', 3));   
    Mycoll c1(%d1);   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mypair elem in c1)   
        {   
        Mycoll::key_type key = elem.Key;   
        Mycoll::mapped_type value = elem.Value;   
        System::Console::Write(" [{0} {1}]", key, value);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```  

## <a name="op_eq"></a> collection_adapter::Operator = (STL/CLR)
Nahradí uloženou BCL popisovač.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
collection_adapter<Coll>% operator=(collection_adapter<Coll>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *doprava*  
 Adaptér pro kopírování.  
  
### <a name="remarks"></a>Poznámky  
 Kopie členský operátor *správné* na objekt, vrátí `*this`. Můžete použít k nahrazení uložené popisovač BCL kopie uložené BCL úchytu v *správné*.  
  
### <a name="example"></a>Příklad  
  
```cpp 
// cliext_collection_adapter_operator_as.cpp   
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
  
// assign to a new container   
    Mycoll c2;   
    c2 = c1;   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
a b c  
```  

## <a name="reference"></a> collection_adapter::Reference (STL/CLR)
Typ odkazu na prvek  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef value_type% reference;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ, který popisuje odkaz na element.  
  
### <a name="example"></a>Příklad  
  
```cpp 
// cliext_collection_adapter_reference.cpp   
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
    Mycoll::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        {   // get a reference to an element   
        Mycoll::reference ref = *it;   
        System::Console::Write(" {0}", ref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
```  

## <a name="size"></a> collection_adapter::size (STL/CLR)
Spočítá počet prvků.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
size_type size();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí délku objektu řízené sekvence. Není definovaný ve specializaci pro `IEnumerable` nebo `IEnumerable<Value>`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_collection_adapter_size.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d6x(6, L'x');   
    Mycoll c1(%d6x);   
  
// display initial contents " x x x x x x"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
```  
  
```Output  
 x x x x x x  
size() = 6  
```  

## <a name="size_type"></a> collection_adapter::size_type (STL/CLR)
Typ vzdálenosti se znaménkem mezi dvěma elementu.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef int size_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ, který popisuje počet prvků záporná.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_collection_adapter_size_type.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d6x(6, L'x');   
    Mycoll c1(%d6x);   
  
// display initial contents " x x x x x x"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    Mycoll::size_type size = c1.size();   
    System::Console::WriteLine("size() = {0}", size);   
    return (0);   
    }  
```  
  
```Output  
 x x x x x x  
size() = 6  
```  

## <a name="swap"></a> collection_adapter::swap (STL/CLR)
Zamění obsah dvou kontejnerů.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
void swap(collection_adapter<Coll>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *doprava*  
 Kontejner pro obsah s.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce Zamění uložené popisovače BCL mezi `*this` a *správné*.  
  
### <a name="example"></a>Příklad  
  
```cpp
// cliext_collection_adapter_swap.cpp   
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

## <a name="value_type"></a> collection_adapter::value_type (STL/CLR)
Typ prvku  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef Value value_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro parametr šablony *hodnotu*, pokud jsou k dispozici ve specializaci; v opačném případě je synonymum pro `System::Object^`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_collection_adapter_value_type.cpp   
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
  
// display contents " a b c" using value_type   
    for (Mycoll::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        {   // store element in value_type object   
        Mycoll::value_type val = *it;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
```  

## <a name="make_collection"></a> make_collection – (STL/CLR)
Ujistěte se, `range_adapter` z páru iterátoru.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Iter>  
    range_adapter<Iter> make_collection(Iter first, Iter last);  
```  
  
#### <a name="parameters"></a>Parametry  
 *ITER*  
 Typ zabalené iterátory.  
  
 *první*  
 První iterátor, který chcete zabalit.  
  
 *poslední*  
 Druhý iterátor zabalit.  
  
### <a name="remarks"></a>Poznámky  
 Šablona funkce vrátí `gcnew range_adapter<Iter>(first, last)`. Lze použít k sestavení `range_adapter<Iter>` objekt z pár iterátorů.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_make_collection.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::deque<wchar_t> Mycont;   
typedef cliext::range_adapter<Mycont::iterator> Myrange;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in d1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Collections::ICollection^ p1 =   
        cliext::make_collection(d1.begin(), d1.end());   
    System::Console::WriteLine("Count = {0}", p1->Count);   
    System::Console::WriteLine("IsSynchronized = {0}",   
        p1->IsSynchronized);   
    System::Console::WriteLine("SyncRoot not nullptr = {0}",   
        p1->SyncRoot != nullptr);   
  
// copy the sequence   
    cli::array<System::Object^>^ a1 = gcnew cli::array<System::Object^>(5);   
  
    a1[0] = L'|';   
    p1->CopyTo(a1, 1);   
    a1[4] = L'|';   
    for each (wchar_t elem in a1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
```  
  
```Output  
 a b c  
Count = 3  
IsSynchronized = False  
SyncRoot not nullptr = True  
 | a b c |  
```  

## <a name="range_adapter"></a> range_adapter – (STL/CLR)
Třída šablony, která obaluje pár iterátorů, které se používají k implementaci několika rozhraní knihovny třídy Base (BCL). Použít range_adapter – k manipulaci s rozsahem STL/CLR, jako by šlo BCL kolekce.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Iter>  
    ref class range_adapter  
        :   public  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<Value>,  
        System::Collections::Generic::ICollection<Value>  
    { ..... };  
```  
  
#### <a name="parameters"></a>Parametry  
 *ITER*  
 Typ přidružený k zabalené iterátory.  
  
### <a name="members"></a>Členové  
  
|Členská funkce|Popis|  
|---------------------|-----------------|  
|[range_adapter::range_adapter (STL/CLR)](#range_adapter_range_adapter)|Vytvoří objekt adaptér.|  
  
|Operátor|Popis|  
|--------------|-----------------|  
|[range_adapter::operator= (STL/CLR)](#range_adapter_op_eq)|Nahradí pár uložený iterátor.|  
  
### <a name="interfaces"></a>Rozhraní  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|<xref:System.Collections.IEnumerable>|Provede iteraci prvků v kolekci.|  
|<xref:System.Collections.ICollection>|Spravuje skupiny prvků.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Iteruje zadaný elementů v kolekci...|  
|<xref:System.Collections.Generic.ICollection%601>|Udržuje typy prvků.|  
  
### <a name="remarks"></a>Poznámky  
 Range_adapter – ukládá pár iterátorů, které zase vymezují sekvenci prvků. Daný objekt implementuje čtyři BCL rozhraní, které umožňují iteraci v rámci elementů v pořadí. Pomocí této třídy šablony pro manipulaci s rozsahy STL/CLR podobně jako kontejnery BCL.  

## <a name="range_adapter_op_eq"></a> range_adapter::Operator = (STL/CLR)
Nahradí pár uložený iterátor.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
range_adapter<Iter>% operator=(range_adapter<Iter>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *doprava*  
 Adaptér pro kopírování.  
  
### <a name="remarks"></a>Poznámky  
 Kopie členský operátor *správné* na objekt, vrátí `*this`. Můžete použít k nahrazení uloženého iterátoru dvojice kopii uloženého iterátoru dvojice v *správné*.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_range_adapter_operator_as.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::deque<wchar_t> Mycont;   
typedef cliext::range_adapter<Mycont::iterator> Myrange;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
    Myrange c1(d1.begin(), d1.end());   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myrange c2;   
    c2 = c1;   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
a b c  
```  

## <a name="range_adapter_range_adapter"></a> range_adapter::range_adapter (STL/CLR)
Vytvoří objekt adaptér.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
range_adapter();  
range_adapter(range_adapter<Iter>% right);  
range_adapter(range_adapter<Iter>^ right);  
range_adapter(Iter first, Iter last);  
```  
  
#### <a name="parameters"></a>Parametry  
 *první*  
 První iterátor, který chcete zabalit.  
  
 *poslední*  
 Druhý iterátor zabalit.  
  
 *doprava*  
 Kopírovaný objekt.  
  
### <a name="remarks"></a>Poznámky  
 Konstruktor:  
  
 `range_adapter();`  
  
 Inicializuje uloženého iterátoru dvojice s výchozí vyrobený iterátory.  
  
 Konstruktor:  
  
 `range_adapter(range_adapter<Iter>% right);`  
  
 Inicializuje uloženého iterátoru dvojice zkopírováním uložený v pár *správné*.  
  
 Konstruktor:  
  
 `range_adapter(range_adapter<Iter>^ right);`  
  
 Inicializuje uloženého iterátoru dvojice zkopírováním uložený v pár `*right`.  
  
 Konstruktor:  
  
 `range_adapter(Iter^ first, last);`  
  
 Inicializuje uloženého iterátoru dvojice s *první* a *poslední*.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_range_adapter_construct.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::deque<wchar_t> Mycont;   
typedef cliext::range_adapter<Mycont::iterator> Myrange;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
  
// construct an empty adapter   
    Myrange c1;   
  
// construct with an iterator pair   
    Myrange c2(d1.begin(), d1.end());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another adapter   
    Myrange c3(c2);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying an adapter handle   
    Myrange c4(%c3);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
```  
  
```Output  
a b c  
a b c  
a b c  
```  