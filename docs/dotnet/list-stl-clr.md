---
title: seznam (STL/CLR) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::list
- cliext::list::assign
- cliext::list::assign
- cliext::list::back
- cliext::list::back_item
- cliext::list::begin
- cliext::list::clear
- cliext::list::const_iterator
- cliext::list::const_reference
- cliext::list::const_reverse_iterator
- cliext::list::difference_type
- cliext::list::empty
- cliext::list::end
- cliext::list::erase
- cliext::list::front
- cliext::list::front_item
- cliext::list::generic_container
- cliext::list::generic_iterator
- cliext::list::generic_reverse_iterator
- cliext::list::generic_value
- cliext::list::insert
- cliext::list::iterator
- cliext::list::list
- cliext::list::merge
- cliext::list::operator=
- cliext::list::pop_back
- cliext::list::pop_front
- cliext::list::push_back
- cliext::list::push_front
- cliext::list::rbegin
- cliext::list::reference
- cliext::list::remove
- cliext::list::remove_if
- cliext::list::rend
- cliext::list::resize
- cliext::list::reverse
- cliext::list::reverse_iterator
- cliext::list::size
- cliext::list::size_type
- cliext::list::sort
- cliext::list::splice
- cliext::list::swap
- cliext::list::to_array
- cliext::list::unique
- cliext::list::value_type
- cliext::operator!=(list)
- cliext::operator<(list)
- cliext::operator<=(list)
- cliext::operator==(list)
- cliext::operator>(list)
- cliext::operator>=(list)
dev_langs:
- C++
helpviewer_keywords:
- <cliext/list> header [STL/CLR]
- list class [STL/CLR]
- <list> header [STL/CLR]
- assign member [STL/CLR]
- assign member [STL/CLR]
- back member [STL/CLR]
- back_item member [STL/CLR]
- begin member [STL/CLR]
- clear member [STL/CLR]
- const_iterator member [STL/CLR]
- const_reference member [STL/CLR]
- const_reverse_iterator member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- end member [STL/CLR]
- erase member [STL/CLR]
- front member [STL/CLR]
- front_item member [STL/CLR]
- generic_container member [STL/CLR]
- generic_iterator member [STL/CLR]
- generic_reverse_iterator member [STL/CLR]
- generic_value member [STL/CLR]
- insert member [STL/CLR]
- iterator member [STL/CLR]
- list member [STL/CLR]
- merge member [STL/CLR]
- operator= member [STL/CLR]
- pop_back member [STL/CLR]
- pop_front member [STL/CLR]
- push_back member [STL/CLR]
- push_front member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- remove member [STL/CLR]
- remove_if member [STL/CLR]
- rend member [STL/CLR]
- resize member [STL/CLR]
- reverse member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- sort member [STL/CLR]
- splice member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- unique member [STL/CLR]
- value_type member [STL/CLR]
- operator!=(list) member [STL/CLR]
- operator<(list) member [STL/CLR]
- operator<=(list) member [STL/CLR]
- operator==(list) member [STL/CLR]
- operator>(list) member [STL/CLR]
- operator>=(list) member [STL/CLR]
ms.assetid: a70c45c8-a257-4f6b-8434-b27ff6685bac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4e6ae13efabd34c6c685b07691789634ca0aed9c
ms.sourcegitcommit: 301bb19056e5bae84ff50f7d1df1e546efe225ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/21/2018
ms.locfileid: "36305914"
---
# <a name="list-stlclr"></a>list (STL/CLR)
Šablony třídy popisuje objekt, který řídí různých délka pořadí elementů, která má obousměrný přístup. Použít metodu kontejneru `list` spravovat pořadí elementů jako obousměrný odkazovaného seznamu uzlů, ukládání jeden element.  
  
 V popisu níže `GValue` je stejný jako `Value` Pokud k tomu je typu ref, v takovém případě je `Value^`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value>  
    ref class list  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        Microsoft::VisualC::StlClr::IList<GValue>  
    { ..... };  
```  
  
#### <a name="parameters"></a>Parametry  
 Hodnota  
 Typ elementu v řízené sekvenci  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – nebo jejich výpisu >  
  
 **Namespace:** cliext – 

## <a name="members"></a>Členové  
  
|Definice typu|Popis|  
|---------------------|-----------------|  
|[list::const_iterator (STL/CLR)](#const_iterator)|Typ konstantního iterátoru řízené sekvence|  
|[list::const_reference (STL/CLR)](#const_reference)|Typ konstantního odkazu na prvek|  
|[list::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|Typ konstantní zpětné iterator pro řízené sekvenci.|  
|[list::difference_type (STL/CLR)](#difference_type)|Typ vzdálenosti se znaménkem mezi dvěma prvky|  
|[list::generic_container (STL/CLR)](#generic_container)|Typ generické rozhraní pro kontejner.|  
|[list::generic_iterator (STL/CLR)](#generic_iterator)|Typ iterace pro obecné rozhraní kontejneru.|  
|[list::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|Typ zpětné iterator pro obecné rozhraní kontejneru.|  
|[list::generic_value (STL/CLR)](#generic_value)|Typ elementu pro obecné rozhraní kontejneru.|  
|[list::iterator (STL/CLR)](#iterator)|Typ iterátoru řízené sekvence|  
|[list::reference (STL/CLR)](#reference)|Typ odkazu na prvek|  
|[list::reverse_iterator (STL/CLR)](#reverse_iterator)|Typ zpětné iterator pro řízené sekvenci.|  
|[list::size_type (STL/CLR)](#size_type)|Typ vzdálenosti se znaménkem mezi dvěma prvky|  
|[list::value_type (STL/CLR)](#value_type)|Typ prvku|  
  
|Členská funkce|Popis|  
|---------------------|-----------------|  
|[list::assign (STL/CLR)](#assign)|Nahradí všechny elementy.|  
|[list::back (STL/CLR)](#back)|Přístup k posledním elementem.|  
|[list::begin (STL/CLR)](#begin)|Určuje začátek řízené sekvence.|  
|[list::clear (STL/CLR)](#clear)|Odebere všechny prvky.|  
|[list::empty (STL/CLR)](#empty)|Zkouší, zda nejsou přítomny žádné prvky.|  
|[list::end (STL/CLR)](#end)|Určuje konec řízené sekvence.|  
|[list::erase (STL/CLR)](#erase)|Odebere prvky v určených pozicích.|  
|[list::front (STL/CLR)](#front)|Přístup k první prvek.|  
|[list::insert (STL/CLR)](#insert)|Přidá elementy na zadané pozici.|  
|[list::list (STL/CLR)](#list)|Sestaví objekt kontejneru.|  
|[list::merge (STL/CLR)](#merge)|Sloučí dvě řízené pořadí řazení.|  
|[list::pop_back (STL/CLR)](#pop_back)|Odebere poslední element.|  
|[list::pop_front (STL/CLR)](#pop_front)|Odebere první prvek.|  
|[list::push_back (STL/CLR)](#push_back)|Přidá nový posledním elementem.|  
|[list::push_front (STL/CLR)](#push_front)|Přidá nový první prvek.|  
|[list::rbegin (STL/CLR)](#rbegin)|Označuje začátek odstínech řízené sekvenci.|  
|[list::remove (STL/CLR)](#remove)|Odebere element se zadanou hodnotou.|  
|[list::remove_if (STL/CLR)](#remove_if)|Odebere prvky, které předávají testu zadaný.|  
|[list::rend (STL/CLR)](#rend)|Označuje konec odstínech řízené sekvenci.|  
|[list::resize (STL/CLR)](#resize)|Změní počet elementů.|  
|[list::reverse (STL/CLR)](#reverse)|Obrátí řízené sekvenci.|  
|[list::size (STL/CLR)](#size)|Spočítá počet prvků.|  
|[list::sort (STL/CLR)](#sort)|Řadí řízené sekvenci.|  
|[list::splice (STL/CLR)](#splice)|Restitches propojení mezi uzly.|  
|[list::swap (STL/CLR)](#swap)|Zamění obsah dvou kontejnerů.|  
|[list::to_array (STL/CLR)](#to_array)|Zkopíruje řízené sekvenci do nové pole.|  
|[list::unique (STL/CLR)](#unique)|Odebere přiléhající prvky, které předávají testu zadaný.|  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|[list::back_item (STL/CLR)](#back_item)|Přístup k posledním elementem.|  
|[list::front_item (STL/CLR)](#front_item)|Přístup k první prvek.|  
  
|Operátor|Popis|  
|--------------|-----------------|  
|[list::operator= (STL/CLR)](#op_as)|Nahradí řízené sekvenci.|  
|[operator!= (list) (STL/CLR)](#op_neq)|Určuje, zda `list` objekt není rovno jiné `list` objektu.|  
|[operator< (list) (STL/CLR)](#op_lt)|Určuje, zda `list` objektu je menší než jiná `list` objektu.|  
|[operator<= (list) (STL/CLR)](#op_lteq)|Určuje, zda `list` objektu je menší než nebo rovna do jiného `list` objektu.|  
|[operator== (list) (STL/CLR)](#op_eq)|Určuje, zda `list` objekt rovná jiné `list` objektu.|  
|[operator> (list) (STL/CLR)](#op_gt)|Určuje, zda `list` je větší než druhý objekt `list` objektu.|  
|[operator>= (list) (STL/CLR)](#op_gteq)|Určuje, zda `list` objekt je větší než nebo rovna hodnotě jiného `list` objektu.|  
  
## <a name="interfaces"></a>Rozhraní  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Duplicitní objekt.|  
|<xref:System.Collections.IEnumerable>|Pořadí pomocí elementů.|  
|<xref:System.Collections.ICollection>|Údržba skupiny elementů.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Pořadí prostřednictvím typové elementy.|  
|<xref:System.Collections.Generic.ICollection%601>|Údržba skupiny typové elementů.|  
|IList\<hodnota >|Udržujte obecné kontejneru.|  
  
## <a name="remarks"></a>Poznámky  
 Objekt přiděluje a uvolní úložiště pro pořadí, které ovládá jako jednotlivé uzly v seznamu obousměrného odkaz. Elementy ho Přeuspořádá změnou propojení mezi uzly, nikdy zkopírováním obsah jednoho uzlu do jiného. To znamená, že můžete vložit a odeberte elementy volně bez narušení zbývající elementy. Proto je seznam vhodným kandidátem pro základní kontejner pro třídu šablony [fronty (STL/CLR)](../dotnet/queue-stl-clr.md) nebo třída šablony [zásobníku (STL/CLR)](../dotnet/stack-stl-clr.md).  
  
 A `list` objekt podporuje obousměrné iterátory, což znamená, že můžete tak, aby přiléhající elementy zadané iterátor, který označuje elementu v řízené sekvenci. Speciální hlavního uzlu odpovídá iterator vrácený [list::end (STL/CLR)](../dotnet/list-end-stl-clr.md)`()`. Tato iterator k dosažení poslední elementu v řízené sekvenci, můžete snížení, pokud je k dispozici. Můžete zvýšit iterator seznamu k dosažení hlavního uzlu a bude potom porovnejte rovna `end()`. Ale nemůže dereference iterator vrácený `end()`.  
  
 Všimněte si, že nemůže odkazovat na prvek seznamu přímo zadané pořadí umístění – vyžadující iterator náhodný přístup. Tak, aby seznam `not` použít jako základní kontejner pro třídu šablony [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md).  
  
 Iterator seznamu uloží popisovač do uzlu přidružený seznam, který je pak uloží popisovač pro jeho přidružené kontejneru. Iterátory lze použít pouze jejich přidružené kontejnerové objekty. Iterator seznamu zůstane platný tak dlouho, dokud jeho přidružený seznam uzlu je přidružen některé seznamu. Kromě toho je platný iterator dereferencable – slouží k přístupu k nebo alter hodnota elementu se označí – tak dlouho, dokud není rovno `end()`.  
  
 Mazání nebo odebrání element volání destruktoru pro jeho uložené hodnoty. Zničení kontejneru vymaže všechny elementy. Proto kontejner, jehož typ elementu je třída ref zajistí, že žádné elementy outlive kontejneru. Upozorňujeme však, že nemá kontejner popisovače `not` zrušení jeho elementy.  
  
## <a name="assign"></a> list::Assign (STL/CLR)
Nahradí všechny elementy.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void assign(size_type count, value_type val);  
template<typename InIt>  
    void assign(InIt first, InIt last);  
void assign(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>Parametry  
 count  
 Počet elementů k vložení.  
  
 první  
 Začátek rozsahu k vložení.  
  
 poslední  
 Konec rozsahu k vložení.  
  
 vpravo  
 Výčet k vložení.  
  
 Val  
 Hodnota elementu, který chcete vložit.  
  
### <a name="remarks"></a>Poznámky  
 První člen funkce nahradí řízené sekvenci opakování `count` elementy hodnoty `val`. Použijete jej vyplníte kontejneru elementů všechny má stejnou hodnotu.  
  
 Pokud `InIt` je celočíselného typu, druhý členská funkce se chová stejně jako `assign((size_type)first, (value_type)last)`. Jinak nahradí řízené sekvenci s pořadím [`first`, `last`). Použijete jej aby řízené pořadí kopii jiného pořadí.  
  
 Třetí členská funkce nahradí řízené sekvenci pořadí určených enumerátor `right`. Můžete použít k vytvoření kopie pořadí popsaného enumerátor řízené sekvenci.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_assign.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// assign a repetition of values   
    cliext::list<wchar_t> c2;   
    c2.assign(6, L'x');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign an iterator range   
    cliext::list<wchar_t>::iterator it = c1.end();   
    c2.assign(c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign an enumeration   
    c2.assign(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
x x x x x x  
a b  
a b c  
```  
 
## <a name="back"></a> list::back (STL/CLR)
Přístup k posledním elementem.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
reference back();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí odkaz na poslední elementu řízené sekvenci, která musí být neprázdný. Použít pro přístup k posledním elementem, když víte, že existuje.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_back.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("back() = {0}", c1.back());   
  
// alter last item and reinspect   
    c1.back() = L'x';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
back() = c  
 a b x  
```  

## <a name="back_item"></a> list::back_item (STL/CLR)
Přístup k posledním elementem.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
property value_type back_item;  
```  
  
### <a name="remarks"></a>Poznámky  
 Vlastnost přistupuje ke poslední elementu řízené sekvenci, která musí být neprázdný. Použijete jej číst nebo zapisovat posledním elementem, když víte, že existuje.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_back_item.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("back_item = {0}", c1.back_item);   
  
// alter last item and reinspect   
    c1.back_item = L'x';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
back_item = c  
 a b x  
```  

## <a name="begin"></a> list::begin (STL/CLR)
Určuje začátek řízené sekvence.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
iterator begin();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí iterator náhodný přístup, který určuje první elementu v řízené sekvenci nebo právě přesahuje za konec prázdnou sekvencí. Můžete ji použít k získání iterátor, který označuje `current` začátku řízené sekvenci, ale jeho stav můžete změnit, pokud se změní délka řízené sekvenci.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_begin.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    cliext::list<wchar_t>::iterator it = c1.begin();   
    System::Console::WriteLine("*begin() = {0}", *it);   
    System::Console::WriteLine("*++begin() = {0}", *++it);   
  
// alter first two items and reinspect   
    *--it = L'x';   
    *++it = L'y';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*begin() = a  
*++begin() = b  
 x y c  
```  

## <a name="clear"></a> list::clear (STL/CLR)
Odebere všechny prvky.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void clear();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce efektivně volá [list::erase (STL/CLR)](../dotnet/list-erase-stl-clr.md) `(` [list::begin (STL/CLR)](../dotnet/list-begin-stl-clr.md) `(),` [list::end (STL/CLR)](../dotnet/list-end-stl-clr.md) `())`. Použijte k zajištění, že řízené sekvenci je prázdný.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_clear.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// add elements and clear again   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
  
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
size() = 0  
 a b  
size() = 0  
```  

## <a name="const_iterator"></a> list::const_iterator (STL/CLR)
Typ konstantního iterátoru řízené sekvence  
  
### <a name="syntax"></a>Syntaxe  
  
```  
typedef T2 const_iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Popisuje typ objekt neurčeného typu `T2` , může sloužit jako konstantní iterator náhodný přístup pro řízené sekvenci.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_const_iterator.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    cliext::list<wchar_t>::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        System::Console::Write(" {0}", *cit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="const_reference"></a> list::const_reference (STL/CLR)
Typ konstantního odkazu na prvek  
  
### <a name="syntax"></a>Syntaxe  
  
```  
typedef value_type% const_reference;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ popisuje konstantní odkaz na element.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_const_reference.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    cliext::list<wchar_t>::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        {   // get a const reference to an element   
        cliext::list<wchar_t>::const_reference cref = *cit;   
        System::Console::Write(" {0}", cref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="const_reverse_iterator"></a> list::const_reverse_iterator (STL/CLR)
Typ konstantní zpětné iterator pro řízené sekvenci...  
  
### <a name="syntax"></a>Syntaxe  
  
```  
typedef T4 const_reverse_iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Popisuje typ objekt neurčeného typu `T4` , může sloužit jako konstantní zpětné iterator pro řízené sekvenci.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_const_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" reversed   
    cliext::list<wchar_t>::const_reverse_iterator crit = c1.rbegin();   
    cliext::list<wchar_t>::const_reverse_iterator crend = c1.rend();   
    for (; crit != crend; ++crit)   
        System::Console::Write(" {0}", *crit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c b a  
```  

## <a name="difference_type"></a> list::difference_type (STL/CLR)
Typy podepsaný vzdálenost mezi dvěma prvky.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
typedef int difference_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ popisuje počet podepsaný elementu.  
  
### <a name="example"></a>Příklad  
  
```cpp 
// cliext_list_difference_type.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    cliext::list<wchar_t>::difference_type diff = 0;   
    for (cliext::list<wchar_t>::iterator it = c1.begin();   
        it != c1.end(); ++it) ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
  
// compute negative difference   
    diff = 0;   
    for (cliext::list<wchar_t>::iterator it = c1.end();   
        it != c1.begin(); --it) --diff;   
    System::Console::WriteLine("begin()-end() = {0}", diff);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
end()-begin() = 3  
begin()-end() = -3  
```  

## <a name="empty"></a> list::Empty (STL/CLR)
Zkouší, zda nejsou přítomny žádné prvky.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
bool empty();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí hodnotu true pro prázdný řízené sekvenci. Ta je ekvivalentní [list::size (STL/CLR)](../dotnet/list-size-stl-clr.md)`() == 0`. Můžete použít k ověření, zda seznam je prázdný.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_empty.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    System::Console::WriteLine("empty() = {0}", c1.empty());   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    System::Console::WriteLine("empty() = {0}", c1.empty());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
size() = 3  
empty() = False  
size() = 0  
empty() = True  
```  

## <a name="end"></a> list::end (STL/CLR)
Určuje konec řízené sekvence.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
iterator end();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí iterator náhodný přístup tohoto body právě přesahuje za konec řízené sekvenci. Můžete ji použít k získání iterátor, který označuje konec řízené sekvenci; jeho stav nemá není změnit, pokud se změní délka řízené sekvenci.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_end.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last two items   
    cliext::list<wchar_t>::iterator it = c1.end();   
    --it;   
    System::Console::WriteLine("*-- --end() = {0}", *--it);   
    System::Console::WriteLine("*--end() = {0}", *++it);   
  
// alter first two items and reinspect   
    *--it = L'x';   
    *++it = L'y';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*-- --end() = b  
*--end() = c  
 a x y  
```  

## <a name="erase"></a> list::Erase (STL/CLR)
Odebere prvky v určených pozicích.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
```  
  
#### <a name="parameters"></a>Parametry  
 první  
 Začátek rozsahu vymazat.  
  
 poslední  
 Konec rozsahu vymazat.  
  
 kde  
 Element vymazat.  
  
### <a name="remarks"></a>Poznámky  
 Odebere první členská funkce elementu řízené sekvenci, na kterou odkazuje `where`. Použijte k odebrání jediným elementem.  
  
 Druhý členská funkce odebere elementy řízené sekvenci v rozsahu [`first`, `last`). Použijte k odebrání nula nebo více souvislý prvků.  
  
 Obě členské funkce vrátí iterátor, který označí první prvek zbývající nad rámec všechny elementy odebrán, nebo [list::end (STL/CLR)](../dotnet/list-end-stl-clr.md) `()` Pokud neexistuje žádný takový prvek.  
  
 Při mazání elementy, je počet kopií element lineární v počet elementů mezi koncem vymazání a blíž k uživateli konci pořadí. (Pokud mazání jeden či více elementů na libovolném konci sekvenci, žádné element kopie dojít k.)  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_erase.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase an element and reinspect   
    System::Console::WriteLine("erase(begin()) = {0}",   
        *c1.erase(c1.begin()));   
  
// add elements and display " b c d e"   
    c1.push_back(L'd');   
    c1.push_back(L'e');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase all but end   
    cliext::list<wchar_t>::iterator it = c1.end();   
    System::Console::WriteLine("erase(begin(), end()-1) = {0}",   
        *c1.erase(c1.begin(), --it));   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
erase(begin()) = b  
 b c d e  
erase(begin(), end()-1) = e  
size() = 1  
```  

## <a name="front"></a> list::front (STL/CLR)
Přístup k první prvek.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
reference front();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí odkaz na první prvek řízené sekvenci, která musí být neprázdný. Použijete jej číst nebo zapisovat první prvek, když víte, že existuje.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_front.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first item   
    System::Console::WriteLine("front() = {0}", c1.front());   
  
// alter first item and reinspect   
    c1.front() = L'x';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
front() = a  
 x b c  
```  

## <a name="front_item"></a> list::front_item (STL/CLR)
Přístup k první prvek.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
property value_type front_item;  
```  
  
### <a name="remarks"></a>Poznámky  
 Vlastnost přistupuje k první prvek řízené sekvenci, která musí být neprázdný. Použijete jej číst nebo zapisovat první prvek, když víte, že existuje.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_front_item.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first item   
    System::Console::WriteLine("front_item = {0}", c1.front_item);   
  
// alter first item and reinspect   
    c1.front_item = L'x';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
front_item = a  
 x b c  
```  

## <a name="generic_container"></a> list::generic_container (STL/CLR)
Typ generické rozhraní pro kontejner.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
typedef Microsoft::VisualC::StlClr::  
    IList<generic_value>  
    generic_container;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ popisuje obecné rozhraní pro tuto třídu kontejneru šablony.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_generic_container.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    gc1->insert(gc1->end(), L'd');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify original and display generic   
    c1.push_back(L'e');   
  
    System::Collections::IEnumerator^ enum1 =   
        gc1->GetEnumerator();   
    while (enum1->MoveNext())   
        System::Console::Write(" {0}", enum1->Current);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a b c d  
a b c d e  
```  

## <a name="generic_iterator"></a> list::generic_iterator (STL/CLR)
Typ iterace pro použití s generické rozhraní pro kontejner.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
typedef Microsoft::VisualC::StlClr::Generic::  
    ContainerBidirectionalIterator<generic_value>  
    generic_iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ popisuje obecný iterator, který lze použít s obecné rozhraní pro tuto třídu kontejneru šablony.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_generic_iterator.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    cliext::list<wchar_t>::generic_iterator gcit = gc1->begin();   
    cliext::list<wchar_t>::generic_value gcval = *gcit;   
    *++gcit = gcval;   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a a c  
```  

## <a name="generic_reverse_iterator"></a> list::generic_reverse_iterator (STL/CLR)
Typ zpětné iterator pro použití s generické rozhraní pro kontejner.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
typedef Microsoft::VisualC::StlClr::Generic::  
    ReverseBidirectionalIterator<generic_value> generic_reverse_iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ popisuje obecný zpětné iterator, který lze použít s obecné rozhraní pro tuto třídu kontejneru šablony.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_generic_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    cliext::list<wchar_t>::generic_reverse_iterator gcit = gc1->rbegin();   
    cliext::list<wchar_t>::generic_value gcval = *gcit;   
    *++gcit = gcval;   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a c c  
```  

## <a name="generic_value"></a> list::generic_value (STL/CLR)
Typ elementu pro použití s generické rozhraní pro kontejner.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
typedef GValue generic_value;  
```  
  
### <a name="remarks"></a>Poznámky  
 Popisuje typ objektu typu `GValue` , který popisuje element uložené hodnoty pro použití s obecné rozhraní pro tuto třídu kontejneru šablony.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_generic_value.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    cliext::list<wchar_t>::generic_iterator gcit = gc1->begin();   
    cliext::list<wchar_t>::generic_value gcval = *gcit;   
    *++gcit = gcval;   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a a c  
```  

## <a name="insert"></a> list::Insert (STL/CLR)
Přidá elementy na zadané pozici.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
iterator insert(iterator where, value_type val);  
void insert(iterator where, size_type count, value_type val);  
template<typename InIt>  
    void insert(iterator where, InIt first, InIt last);  
void insert(iterator where,  
    System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>Parametry  
 count  
 Počet elementů k vložení.  
  
 první  
 Začátek rozsahu k vložení.  
  
 poslední  
 Konec rozsahu k vložení.  
  
 vpravo  
 Výčet k vložení.  
  
 Val  
 Hodnota elementu, který chcete vložit.  
  
 kde  
 Kde v kontejneru vložit před.  
  
### <a name="remarks"></a>Poznámky  
 Každý člen funkce vložení před element, na kterou odkazuje `where` v řízené sekvenci sekvenci určeného zbývající operandy.  
  
 První člen funkce vloží element s hodnotou `val` a vrátí iterátor, který označuje nově vloženou elementu. Použijete jej vložit jeden prvek před místo určené, které iterace.  
  
 Druhý členská funkce vloží opakování `count` elementy hodnoty `val`. Použijte k vložení nula nebo více souvislý prvků, které jsou všechny kopie stejnou hodnotu.  
  
 Pokud `InIt` je typ integer třetí členská funkce se chová stejně jako `insert(where, (size_type)first, (value_type)last)`. Jinak, vloží sekvenci [`first`, `last`). Použijte k vložení nula nebo více souvislý prvků zkopírovaných z jiného pořadí.  
  
 Čtvrtý – členská funkce vloží pořadí určené, které `right`. Použijte k vložení sekvenci popsaného enumerátor.  
  
 Při vkládání jeden prvek, je počet kopií element lineární v počet elementů mezi kurzor a blíž k uživateli koncem pořadí. (Při vkládání jeden či více elementů na libovolném konci sekvenci, žádné element kopie dojít.) Pokud `InIt` je iterátor vstupní třetí členská funkce efektivně provádí jeden vložení pro každý prvek v pořadí. Jinak, při vkládání `N` elementy, je lineární v počtu kopií element `N` plus počet elementů mezi kurzor a blíž k uživateli koncem pořadí.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_insert.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value using iterator   
    cliext::list<wchar_t>::iterator it = c1.begin();   
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",   
        *c1.insert(++it, L'x'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a repetition of values   
    cliext::list<wchar_t> c2;   
    c2.insert(c2.begin(), 2, L'y');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    it = c1.end();   
    c2.insert(c2.end(), c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    c2.insert(c2.begin(),   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value using index   
    it = c2.begin();   
    ++it, ++it, ++it;   
    c2.insert(it, L'z');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
insert(begin()+1, L'x') = x  
 a x b c  
 y y  
 y y a x b  
 a x b c y y a x b  
```  

## <a name="iterator"></a> list::iterator (STL/CLR)
Typ iterátoru řízené sekvence  
  
### <a name="syntax"></a>Syntaxe  
  
```  
typedef T1 iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Popisuje typ objekt neurčeného typu `T1` , může sloužit jako iterator náhodný přístup pro řízené sekvenci.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_iterator.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    cliext::list<wchar_t>::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
  
// alter first element and redisplay   
    it = c1.begin();   
    *it = L'x';   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
x b c  
```  

## <a name="list"></a> list::list (STL/CLR)
Sestaví objekt kontejneru.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
list();  
list(list<Value>% right);  
list(list<Value>^ right);  
explicit list(size_type count);  
list(size_type count, value_type val);  
template<typename InIt>  
    list(InIt first, InIt last);  
list(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>Parametry  
 `count`  
 Počet elementů k vložení.  
  
 `first`  
 Začátek rozsahu k vložení.  
  
 `last`  
 Konec rozsahu k vložení.  
  
 `right`  
 Objekt, nebo rozsah k vložení.  
  
 `val`  
 Hodnota elementu, který chcete vložit.  
  
### <a name="remarks"></a>Poznámky  
  
 Konstruktor:  
  
 `list();`  
  
 Inicializuje řízené sekvenci s žádné elementy. Se používá k určení prázdný počáteční řízené sekvenci.  
  
 Konstruktor:  
  
 `list(list<Value>% right);`  
  
 Inicializuje řízené sekvenci s pořadím [`right.begin()`, `right.end()`). Se používá k určení počáteční řízené sekvenci, který je kopií pořadí ovládaná objektem seznamu `right`.  
  
 Konstruktor:  
  
 `list(list<Value>^ right);`  
  
 Inicializuje řízené sekvenci s pořadím [`right->begin()`, `right->end()`). Se používá k určení počáteční řízené sekvenci, který je kopií pořadí řízené list objekt, jehož popisovač `right`.  
  
 Konstruktor:  
  
 `explicit list(size_type count);`  
  
 Inicializuje řízené sekvenci s `count` elementy s hodnotou `value_type()`. Použijete jej vyplníte kontejneru elementů všechny má výchozí hodnotu.  
  
 Konstruktor:  
  
 `list(size_type count, value_type val);`  
  
 Inicializuje řízené sekvenci s `count` elementy s hodnotou `val`. Použijete jej vyplníte kontejneru elementů všechny má stejnou hodnotu.  
  
 Konstruktor:  
  
 `template<typename InIt>`  
  
 `list(InIt first, InIt last);`  
  
 Inicializuje řízené sekvenci s pořadím [`first`, `last`). Použít k vytvoření kopie jiné pořadí řízené sekvenci.  
  
 Konstruktor:  
  
 `list(System::Collections::Generic::IEnumerable<Value>^ right);`  
  
 Inicializuje řízené sekvenci s pořadím určené, které enumerátor `right`. Použít k vytvoření kopie jiné pořadí popsaného enumerátor řízené sekvenci.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_construct.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
// construct an empty container   
    cliext::list<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct with a repetition of default values   
    cliext::list<wchar_t> c2(3);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// construct with a repetition of values   
    cliext::list<wchar_t> c3(6, L'x');   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    cliext::list<wchar_t>::iterator it = c3.end();   
    cliext::list<wchar_t> c4(c3.begin(), --it);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    cliext::list<wchar_t> c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    cliext::list<wchar_t> c7(c3);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    cliext::list<wchar_t> c8(%c3);   
    for each (wchar_t elem in c8)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 0 0 0  
 x x x x x x  
 x x x x x  
 x x x x x x  
 x x x x x x  
 x x x x x x  
```  

## <a name="merge"></a> list::merge (STL/CLR)
Sloučí dvě řízené pořadí řazení.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void merge(list<Value>% right);  
template<typename Pred2>  
    void merge(list<Value>% right, Pred2 pred);  
```  
  
#### <a name="parameters"></a>Parametry  
 Před  
 Porovnávače pro dvojice elementu.  
  
 vpravo  
 Kontejner sloučit v.  
  
### <a name="remarks"></a>Poznámky  
 První člen funkce odebere všechny elementy z pořadí řízené `right` a vložte je v řízené sekvenci. Obě pořadí musí být dříve seřazené podle `operator<` – elementy nesmí snížení hodnoty v průběhu buď pořadí. Výsledné pořadí je také seřazené podle `operator<`. Sloučit dva pořadí, které se zvyšují v hodnotě do sekvence, které se také zvyšuje hodnotu použijete tuto funkci člen.  
  
 Druhý členská funkce se chová stejně jako první, s tím rozdílem, že pořadí jsou seřazené podle `pred`  --  `pred(X, Y)` musí mít hodnotu false pro libovolný element `X` element, který následuje `Y` v pořadí. Použít sloučit dva pořadí řazení podle funkce predikátu nebo delegáta, který zadáte.  
  
 Jak funkce provést stabilní sloučení – žádné pár elementů v některém z původní řízené pořadí je obrácený v výsledné řízené sekvenci. Navíc pokud pár elementů `X` a `Y` v řízené sekvenci výsledné má ekvivalentní řazení – `!(X < Y) && !(X < Y)` – element z původní řízené sekvenci se zobrazuje před element z pořadí řízené `right`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_merge.cpp   
// compile with: /clr   
#include <cliext/list>   
  
typedef cliext::list<wchar_t> Mylist;   
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'c');   
    c1.push_back(L'e');   
  
// display initial contents " a c e"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    cliext::list<wchar_t> c2;   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
    c2.push_back(L'f');   
  
// display initial contents " b d f"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// merge and display   
    cliext::list<wchar_t> c3(c1);   
    c3.merge(c2);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("c2.size() = {0}", c2.size());   
  
// sort descending, merge descending, and redisplay   
    c1.sort(cliext::greater<wchar_t>());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    c3.sort(cliext::greater<wchar_t>());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    c3.merge(c1, cliext::greater<wchar_t>());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("c1.size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a c e  
 b d f  
 a b c d e f  
c2.size() = 0  
 e c a  
 f e d c b a  
 f e e d c c b a a  
c1.size() = 0  
```  

## <a name="op_as"></a> list::Operator = (STL/CLR)
Nahradí řízené sekvenci.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
list<Value>% operator=(list<Value>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 vpravo  
 Kontejner pro kopírování.  
  
### <a name="remarks"></a>Poznámky  
 Kopie operátor člen `right` k objektu, vrátí `*this`. Můžete použít k nahrazení řízené sekvenci kopii v řízené sekvenci `right`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_operator_as.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::list<wchar_t> c2;   
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

## <a name="pop_back"></a> list::pop_back (STL/CLR)
Odebere poslední element.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void pop_back();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce odebere poslední elementu řízené sekvenci, která musí být neprázdný. Použijete jej tak, aby zkrátil seznamu podle jednoho prvku na pozadí.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_pop_back.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// pop an element and redisplay   
    c1.pop_back();   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b  
```  

## <a name="pop_front"></a> list::pop_front (STL/CLR)
Odebere první prvek.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void pop_front();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce Odebere první prvek řízené sekvenci, která musí být neprázdný. Použijete jej tak, aby zkrátil seznamu jednoho elementu vpředu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_pop_front.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// pop an element and redisplay   
    c1.pop_front();   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
b c  
```  

## <a name="push_back"></a> list::push_back (STL/CLR)
Přidá nový posledním elementem.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void push_back(value_type val);  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vloží element s hodnotou `val` na konci řízené sekvenci. Použít pro připojení jiný element do seznamu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_push_back.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  
  
## <a name="push_front"></a> list::push_front (STL/CLR)
Přidá nový první prvek.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void push_front(value_type val);  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vloží element s hodnotou `val` na začátku řízené sekvenci. Použít pro předřazení jiný element do seznamu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_push_front.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_front(L'a');   
    c1.push_front(L'b');   
    c1.push_front(L'c');   
  
// display contents " c b a"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c b a  
```  

## <a name="rbegin"></a> list::rbegin (STL/CLR)
Označuje začátek odstínech řízené sekvenci.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
reverse_iterator rbegin();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí zpětné iterator, který určuje poslední elementu v řízené sekvenci nebo právě nad rámec začátku prázdnou sekvencí. Proto označí `beginning` zpětné pořadí. Můžete ji použít k získání iterátor, který označuje `current` začátku řízené sekvenci vidět v obráceném pořadí, ale jeho stav můžete změnit, pokud se změní délka řízené sekvenci.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_rbegin.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items in reversed sequence   
    cliext::list<wchar_t>::reverse_iterator rit = c1.rbegin();   
    System::Console::WriteLine("*rbegin() = {0}", *rit);   
    System::Console::WriteLine("*++rbegin() = {0}", *++rit);   
  
// alter first two items and reinspect   
    *--rit = L'x';   
    *++rit = L'y';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*rbegin() = c  
*++rbegin() = b  
 a y x  
```  

## <a name="reference"></a> list::Reference (STL/CLR)
Typ odkazu na prvek  
  
### <a name="syntax"></a>Syntaxe  
  
```  
typedef value_type% reference;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ popisuje odkaz na element.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_reference.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    cliext::list<wchar_t>::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        {   // get a reference to an element   
        cliext::list<wchar_t>::reference ref = *it;   
        System::Console::Write(" {0}", ref);   
        }   
    System::Console::WriteLine();   
  
// modify contents " a b c"   
    for (it = c1.begin(); it != c1.end(); ++it)   
        {   // get a reference to an element   
        cliext::list<wchar_t>::reference ref = *it;   
  
        ref += (wchar_t)(L'A' - L'a');   
        System::Console::Write(" {0}", ref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
A B C  
```  

## <a name="remove"></a> list::Remove (STL/CLR)
Odebere element se zadanou hodnotou.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void remove(value_type val);  
```  
  
#### <a name="parameters"></a>Parametry  
 Val  
 Hodnota elementu, který chcete odebrat.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce odebere elementu v řízené sekvenci pro kterou `((System::Object^)val)->Equals((System::Object^)x)` hodnotu true (pokud existuje). Použijete jej vymazat libovolně zvolený element se zadanou hodnotou.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_remove.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// fail to remove and redisplay   
    c1.remove(L'A');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();  
  
// remove and redisplay   
    c1.remove(L'b');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a c  
```  

## <a name="remove_if"></a> list::remove_if (STL/CLR)
Odebere prvky, které předávají testu zadaný.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Pred1>  
    void remove_if(Pred1 pred);  
```  
  
#### <a name="parameters"></a>Parametry  
 Před  
 Testování pro elementy odebrat.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce se odebere z řízené sekvenci (vymazáním) každý element `X` pro kterou `pred(X)` hodnotu true. Použijte k odebrání všech prvků, které splňují podmínku, které že zadáte jako funkce nebo delegáta.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_remove_if.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'b');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b b b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// fail to remove and redisplay   
    c1.remove_if(cliext::binder2nd<cliext::equal_to<wchar_t> >(   
        cliext::equal_to<wchar_t>(), L'd'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// remove and redisplay   
    c1.remove_if(cliext::binder2nd<cliext::not_equal_to<wchar_t> >(   
        cliext::not_equal_to<wchar_t>(), L'b'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b b b c  
a b b b c  
b b b  
``` 

## <a name="rend"></a> list::rend (STL/CLR)
Označuje konec odstínech řízené sekvenci.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
reverse_iterator rend();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí zpětné iterator této body právě nad rámec začátku řízené sekvenci. Proto označí `end` zpětné pořadí. Můžete ji použít k získání iterátor, který označuje `current` konec řízené sekvenci vidět v obráceném pořadí, ale jeho stav můžete změnit, pokud se změní délka řízené sekvenci.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_rend.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    cliext::list<wchar_t>::reverse_iterator rit = c1.rend();   
    --rit;   
    System::Console::WriteLine("*-- --rend() = {0}", *--rit);   
    System::Console::WriteLine("*--rend() = {0}", *++rit);   
  
// alter first two items and reinspect   
    *--rit = L'x';   
    *++rit = L'y';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*-- --rend() = b  
*--rend() = a  
 y x c  
```  

## <a name="resize"></a> list::Resize (STL/CLR)
Změní počet elementů.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void resize(size_type new_size);  
void resize(size_type new_size, value_type val);  
```  
  
#### <a name="parameters"></a>Parametry  
 new_size  
 Nová velikost řízené sekvenci.  
  
 Val  
 Hodnota odsazení elementu.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce obou Ujistěte se, že [list::size (STL/CLR)](../dotnet/list-size-stl-clr.md) `()` od nynějška vrátí `new_size`. Pokud je třeba provést řízené sekvenci déle, první členská funkce připojí elementy s hodnotou `value_type()`, zatímco druhý členská funkce připojí elementy s hodnotou `val`. Chcete-li řízené sekvenci kratší, oba členské funkce efektivně vymazat posledním elementem [list::size (STL/CLR)](../dotnet/list-size-stl-clr.md) `() -` `new_size` časy. Můžete použít k zajištění, že řízené sekvenci má velikost `new_size`, ořezávání nebo odsazení aktuální řízené sekvenci.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_resize.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
// construct an empty container and pad with default values   
    cliext::list<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
    c1.resize(4);   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// resize to empty   
    c1.resize(0);   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// resize and pad   
    c1.resize(5, L'x');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 0 0 0 0  
size() = 0  
 x x x x x  
```  

## <a name="reverse"></a> list::reverse (STL/CLR)
Obrátí řízené sekvenci.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void reverse();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce obrátí pořadí všechny elementy v řízené sekvenci. Použijete jej tak, aby odrážela seznam prvků.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_reverse.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// reverse and redisplay   
    c1.reverse();   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
c b a  
```  

## <a name="reverse_iterator"></a> list::reverse_iterator (STL/CLR)
Typ zpětné iterator pro řízené sekvenci.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
typedef T3 reverse_iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Popisuje typ objekt neurčeného typu `T3` , může sloužit jako reverzní iterator pro řízené sekvenci.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" reversed   
    cliext::list<wchar_t>::reverse_iterator rit = c1.rbegin();   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" {0}", *rit);   
    System::Console::WriteLine();   
  
// alter first element and redisplay   
    rit = c1.rbegin();   
    *rit = L'x';   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" {0}", *rit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c b a  
x b a  
```  
  
## <a name="size"></a> list::size (STL/CLR)
Spočítá počet prvků.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
size_type size();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí délku řízené sekvenci. Použijte k určení počtu elementy aktuálně v řízené sekvenci. Pokud všechny se zajímáte o tom, jestli má pořadí nenulové hodnoty velikosti, najdete v části [list::empty (STL/CLR)](../dotnet/list-empty-stl-clr.md)`()`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_size.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0} after clearing", c1.size());   
  
// add elements and clear again   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
size() = 3 starting with 3  
size() = 0 after clearing  
size() = 2 after adding 2  
```  

## <a name="size_type"></a> list::size_type (STL/CLR)
Typ podepsaný vzdálenost mezi dvěma elementu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
typedef int size_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ popisuje element záporný počet.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_size_type.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    cliext::list<wchar_t>::size_type diff = 0;   
    for (cliext::list<wchar_t>::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
end()-begin() = 3  
```

## <a name="sort"></a> list::sort (STL/CLR)
Řadí řízené sekvenci.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void sort();  
template<typename Pred2>  
    void sort(Pred2 pred);  
```  
  
#### <a name="parameters"></a>Parametry  
 Před  
 Porovnávače pro dvojice elementu.  
  
### <a name="remarks"></a>Poznámky  
 První člen funkce pořadí prvků v řízené sekvenci tak, že jsou seřazené podle `operator<` – elementy nesnižujte v hodnotě v průběhu sekvenci. Používáte tuto funkci člen seřadit pořadí ve vzestupném pořadí.  
  
 Druhý členská funkce se chová stejně jako první, s tím rozdílem, že je pořadí řazení podle `pred`  --  `pred(X, Y)` je hodnota false pro libovolný element `X` element, který následuje `Y` v výsledné pořadí. Použít k seřazení pořadí, v pořadí, které zadáte funkce predikátu nebo delegáta.  
  
 Jak funkce provést stabilní řazení – žádné pár elementů v původní řízené sekvenci je obrácený v výsledné řízené sekvenci.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_sort.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// sort descending and redisplay   
    c1.sort(cliext::greater<wchar_t>());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// sort ascending and redisplay   
    c1.sort();   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
c b a  
a b c  
``` 

## <a name="splice"></a> list::splice (STL/CLR)
Restitch propojení mezi uzly.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void splice(iterator where, list<Value>% right);  
void splice(iterator where, list<Value>% right,  
    iterator first);  
void splice(iterator where, list<Value>% right,  
    iterator first, iterator last);  
```  
  
#### <a name="parameters"></a>Parametry  
 první  
 Začátek rozsahu do splice.  
  
 poslední  
 Konec rozsahu do splice.  
  
 vpravo  
 Kontejner pro splice z.  
  
 kde  
 Kde v kontejneru na splice před.  
  
### <a name="remarks"></a>Poznámky  
 První člen funkce vloží pořadí řízené `right` před elementu v řízené sekvenci, na kterou odkazuje `where`. Také odebere všechny elementy z `right`. (`%right` nesmí být stejný jako `this`.) Použít na všechny jeden seznam splice do jiné.  
  
 Druhý členská funkce odebere element na kterou odkazuje `first` v řízené sekvenci `right` a vloží ho před elementu v řízené sekvenci na kterou odkazuje `where`. (Pokud `where` `==` `first` `||` `where` `== ++first`, žádná změna.) Použijete ho k splice jeden element jeden seznam do jiné.  
  
 Třetí členská funkce vloží Podoblast sady určené, které [`first`, `last`) z pořadí řízené `right` před elementu v řízené sekvenci, na kterou odkazuje `where`. Odebere také původní Podoblast sady z pořadí řízené `right`. (Pokud `right` `==` `this`, rozsah [`first`, `last`) nesmí obsahovat elementu, na kterou odkazuje `where`.) Použijete ho k splice dalším počtu nula či více elementů z jednoho seznamu do jiné.  
  
### <a name="example"></a>Příklad  
  
```cpp
// cliext_list_splice.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// splice to a new list   
    cliext::list<wchar_t> c2;   
    c2.splice(c2.begin(), c1);   
    System::Console::WriteLine("c1.size() = {0}", c1.size());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// return one element   
    c1.splice(c1.end(), c2, c2.begin());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// return remaining elements   
    c1.splice(c1.begin(), c2, c2.begin(), c2.end());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("c2.size() = {0}", c2.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
c1.size() = 0  
 a b c  
 a  
 b c  
 b c a  
c2.size() = 0  
```    

## <a name="swap"></a> list::swap (STL/CLR)
Zamění obsah dvou kontejnerů.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void swap(list<Value>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 vpravo  
 Kontejner se Prohodit obsah s.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce prohození řízené pořadí mezi `*this` a `right`. Dělá to tak včas konstantní a vyvolá žádné výjimky. Můžete ho použít jako rychlý způsob, jak exchange obsah dva kontejnery.  
  
### <a name="example"></a>Příklad  
  
```cpp 
// cliext_list_swap.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct another container with repetition of values   
    cliext::list<wchar_t> c2(5, L'x');   
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

## <a name="to_array"></a> list::to_array (STL/CLR)
Zkopíruje řízené sekvenci do nové pole.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
cli::array<Value>^ to_array();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí pole obsahující řízené sekvenci. Můžete ji použít k získání kopii řízené sekvenci v pole formuláře.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_to_array.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// copy the container and modify it   
    cli::array<wchar_t>^ a1 = c1.to_array();   
  
    c1.push_back(L'd');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display the earlier array copy   
    for each (wchar_t elem in a1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c d  
a b c  
```  

## <a name="unique"></a> list::Unique (STL/CLR)
Odebere přiléhající prvky, které předávají testu zadaný.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void unique();  
template<typename Pred2>  
    void unique(Pred2 pred);  
```  
  
#### <a name="parameters"></a>Parametry  
 Před  
 Porovnávače pro dvojice elementu.  
  
### <a name="remarks"></a>Poznámky  
 První člen funkce se odebere z řízené sekvenci (vymazáním) každý element, který porovnává rovno jeho předchozí element – Pokud element `X` předchází element `Y` a `X == Y`, odebere – členská funkce `Y`. Použijete jej odebrat všechny kromě jednoho kopii každé dalším přiléhající elementů tohoto porovnání rovnosti. Všimněte si, že pokud řízené sekvenci je seřadit, například jako voláním [list::sort (STL/CLR)](../dotnet/list-sort-stl-clr.md)`()`, – členská funkce ponechá pouze elementy s jedinečné hodnoty. (Proto název).  
  
 Druhý členská funkce se chová stejně jako první, s tím rozdílem, že jej odebere každý prvek `Y` následující element `X` pro kterou `pred(X, Y)`. Použijete jej odebrat všechny kromě jednoho kopii každé dalším přiléhající elementů, které vyhovují funkce predikátu nebo delegáta, který zadáte. Všimněte si, že pokud řízené sekvenci je seřadit, například jako voláním `sort(pred)`, – členská funkce ponechá pouze elementy, které nemají ekvivalentní řazení s jinými prvky.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_unique.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display contents after unique   
    cliext::list<wchar_t> c2(c1);   
    c2.unique();   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display contents after unique(not_equal_to)   
    c2 = c1;   
    c2.unique(cliext::not_equal_to<wchar_t>());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a a b c  
a b c  
a a  
```  

## <a name="value_type"></a> list::value_type (STL/CLR)
Typ prvku  
  
### <a name="syntax"></a>Syntaxe  
  
```  
typedef Value value_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro parametr šablony `Value`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_value_type.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" using value_type   
    for (cliext::list<wchar_t>::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        {   // store element in value_type object   
        cliext::list<wchar_t>::value_type val = *it;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
``` 

## <a name="op_neq"></a> Operator! = (list) (STL/CLR)
Zobrazí seznam není rovno porovnání.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value>  
    bool operator!=(list<Value>% left,  
        list<Value>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 left  
 Levé kontejner k porovnání.  
  
 vpravo  
 Správném kontejneru k porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Operátor funkce vrátí hodnotu `!(left == right)`. Můžete použít k testování zda `left` není stejný jako seřazené `right` při dva seznamy jsou porovná s prvkem elementu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_operator_ne.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::list<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] != [a b c] is {0}",   
        c1 != c1);   
    System::Console::WriteLine("[a b c] != [a b d] is {0}",   
        c1 != c2);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] != [a b c] is False  
[a b c] != [a b d] is True  
```  

## <a name="op_lt"></a> operátor&lt; (list) (STL/CLR)
Seznam menší než porovnání.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value>  
    bool operator<(list<Value>% left,  
        list<Value>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 left  
 Levé kontejner k porovnání.  
  
 vpravo  
 Správném kontejneru k porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Operátor funkce vrátí hodnotu true, pokud, pro nejnižší pozici `i` pro kterou `!(right[i] < left[i])` je také hodnotu true, `left[i] < right[i]`. Funkce `left->size() < right->size()` použijete k testování zda `left` je seřadí před `right` při dva seznamy jsou porovná s prvkem elementu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_operator_lt.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::list<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] < [a b c] is {0}",   
        c1 < c1);   
    System::Console::WriteLine("[a b c] < [a b d] is {0}",   
        c1 < c2);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] < [a b c] is False  
[a b c] < [a b d] is True  
```  

## <a name="op_lteq"></a> operátor&lt;= (list) (STL/CLR)
Seznam menší než nebo rovna porovnání.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value>  
    bool operator<=(list<Value>% left,  
        list<Value>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 left  
 Levé kontejner k porovnání.  
  
 vpravo  
 Správném kontejneru k porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Operátor funkce vrátí hodnotu `!(right < left)`. Můžete použít k testování zda `left` není objednaný po `right` při dva seznamy jsou porovná s prvkem elementu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_operator_le.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::list<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] <= [a b c] is {0}",   
        c1 <= c1);   
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",   
        c2 <= c1);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] <= [a b c] is True  
[a b d] <= [a b c] is False  
```  

## <a name="op_eq"></a> Operator == (list) (STL/CLR)
Zobrazí seznam rovna porovnání.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value>  
    bool operator==(list<Value>% left,  
        list<Value>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 left  
 Levé kontejner k porovnání.  
  
 vpravo  
 Správném kontejneru k porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Operátor funkce vrátí hodnotu true pouze v případě, že daná pořadí řízené `left` a `right` mít stejnou délku a pro každou pozici `i`, `left[i] ==` `right[i]`. Můžete použít k testování zda `left` je stejný jako seřazené `right` při dva seznamy jsou porovná s prvkem elementu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_operator_eq.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::list<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] == [a b c] is {0}",   
        c1 == c1);   
    System::Console::WriteLine("[a b c] == [a b d] is {0}",   
        c1 == c2);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] == [a b c] is True  
[a b c] == [a b d] is False  
```  

## <a name="op_gt"></a> operátor&gt; (list) (STL/CLR)
Seznam je větší než porovnání.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value>  
    bool operator>(list<Value>% left,  
        list<Value>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 left  
 Levé kontejner k porovnání.  
  
 vpravo  
 Správném kontejneru k porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Operátor funkce vrátí hodnotu `right` `<` `left`. Můžete použít k testování zda `left` je objednaný po `right` při dva seznamy jsou porovná s prvkem elementu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_operator_gt.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::list<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] > [a b c] is {0}",   
        c1 > c1);   
    System::Console::WriteLine("[a b d] > [a b c] is {0}",   
        c2 > c1);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] > [a b c] is False  
[a b d] > [a b c] is True  
```  

## <a name="op_gteq"></a> operátor&gt;= (list) (STL/CLR)
Seznam větší než nebo rovna porovnání.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value>  
    bool operator>=(list<Value>% left,  
        list<Value>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 left  
 Levé kontejner k porovnání.  
  
 vpravo  
 Správném kontejneru k porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Operátor funkce vrátí hodnotu `!(left` `<` `right)`. Můžete použít k testování zda `left` není seřadí před `right` při dva seznamy jsou porovná s prvkem elementu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_operator_ge.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::list<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] >= [a b c] is {0}",   
        c1 >= c1);   
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",   
        c1 >= c2);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] >= [a b c] is True  
[a b c] >= [a b d] is False  
```  
