---
title: Nastavte (STL/CLR) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::set
- cliext::operator!=
- cliext::operator<
- cliext::operator<=
- cliext::operator==
- cliext::operator>
- cliext::operator>=
- cliext::set::begin
- cliext::set::clear
- cliext::set::const_iterator
- cliext::set::const_reference
- cliext::set::const_reverse_iterator
- cliext::set::count
- cliext::set::difference_type
- cliext::set::empty
- cliext::set::end
- cliext::set::equal_range
- cliext::set::erase
- cliext::set::find
- cliext::set::generic_container
- cliext::set::generic_iterator
- cliext::set::generic_reverse_iterator
- cliext::set::generic_value
- cliext::set::insert
- cliext::set::iterator
- cliext::set::key_comp
- cliext::set::key_compare
- cliext::set::key_type
- cliext::set::lower_bound
- cliext::set::make_value
- cliext::set::operator=
- cliext::set::rbegin
- cliext::set::reference
- cliext::set::rend
- cliext::set::reverse_iterator
- cliext::set::set
- cliext::set::size
- cliext::set::size_type
- cliext::set::swap
- cliext::set::to_array
- cliext::set::upper_bound
- cliext::set::value_comp
- cliext::set::value_compare
- cliext::set::value_type
dev_langs:
- C++
helpviewer_keywords:
- <cliext/set> header [STL/CLR]
- <set> header [STL/CLR]
- set class [STL/CLR]
- operator!= (set) member [STL/CLR]
- operator< (set) member [STL/CLR]
- operator<= (set) member [STL/CLR]
- operator== (set) member [STL/CLR]
- operator> (set) member [STL/CLR]
- operator>= (set) member [STL/CLR]
- begin member [STL/CLR]
- clear member [STL/CLR]
- const_iterator member [STL/CLR]
- const_reference member [STL/CLR]
- const_reverse_iterator member [STL/CLR]
- count member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- end member [STL/CLR]
- equal_range member [STL/CLR]
- erase member [STL/CLR]
- find member [STL/CLR]
- generic_container member [STL/CLR]
- generic_iterator member [STL/CLR]
- generic_reverse_iterator member [STL/CLR]
- generic_value member [STL/CLR]
- insert member [STL/CLR]
- iterator member [STL/CLR]
- key_comp member [STL/CLR]
- key_compare member [STL/CLR]
- key_type member [STL/CLR]
- lower_bound member [STL/CLR]
- make_value member [STL/CLR]
- operator= member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rend member [STL/CLR]
- reverse_iterator member [STL/CLR]
- set member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- upper_bound member [STL/CLR]
- value_comp member [STL/CLR]
- value_compare member [STL/CLR]
- value_type member [STL/CLR]
ms.assetid: 27d3628c-741a-43a7-bef1-5085536f679e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e12314be2711eb45487ed7430ebd4b998ab0e373
ms.sourcegitcommit: bad2441d1930275ff506d44759d283d94cccd1c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/31/2018
ms.locfileid: "39376245"
---
# <a name="set-stlclr"></a>set (STL/CLR)
Třída šablony popisuje objekt, který řídí různé délky sekvence elementů, která má obousměrný přístup. Použití kontejneru `set` , spravovat řadu prvků, jako větve (téměř) s vyrovnáváním seřazených uzlů, každý ukládání jeden element.  
  
 V popisu níže `GValue` je stejný jako `GKey`, který je stejný jako *klíč* Pokud je typ odkazu, v takovém případě je `Key^`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Key>  
    ref class set  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        Microsoft::VisualC::StlClr::ITree<Gkey, GValue>  
    { ..... };  
```  
  
### <a name="parameters"></a>Parametry  
 *Key*  
 Typ klíčovou komponentou elementu v řízené sekvenci.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / set >  
  
 **Namespace:** cliext –  

## <a name="declarations"></a>Deklarace  
  
|Definice typu|Popis|  
|---------------------|-----------------|  
|[set::const_iterator (STL/CLR)](#const_iterator)|Typ konstantního iterátoru řízené sekvence|  
|[set::const_reference (STL/CLR)](#const_reference)|Typ konstantního odkazu na prvek|  
|[set::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|Typ konstantního zpětného iterátoru řízené sekvence.|  
|[set::difference_type (STL/CLR)](#difference_type)|Typ (může být podepsaná) vzdálenosti mezi dvěma prvky.|  
|[set::generic_container (STL/CLR)](#generic_container)|Typ obecné rozhraní pro kontejner.|  
|[set::generic_iterator (STL/CLR)](#generic_iterator)|Typ iterátoru pro obecné rozhraní pro kontejner.|  
|[set::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|Typ "reverse iterator" pro obecné rozhraní pro kontejner.|  
|[set::generic_value (STL/CLR)](#generic_value)|Typ elementu pro obecné rozhraní pro kontejner.|  
|[set::iterator (STL/CLR)](#iterator)|Typ iterátoru řízené sekvence|  
|[set::key_compare (STL/CLR)](#key_compare)|Pořadí delegáta pro dva klíče.|  
|[set::key_type (STL/CLR)](#key_type)|Typ klíče řazení|  
|[set::reference (STL/CLR)](#reference)|Typ odkazu na prvek|  
|[set::reverse_iterator (STL/CLR)](#reverse_iterator)|Typ "reverse iterator" pro řízenou sekvenci.|  
|[set::size_type (STL/CLR)](#size_type)|Typ vzdálenosti (nezáporné) mezi dvěma prvky.|  
|[set::value_compare (STL/CLR)](#value_compare)|Pořadí delegáta pro dvě hodnoty prvků.|  
|[set::value_type (STL/CLR)](#value_type)|Typ prvku|  
  
|Členská funkce|Popis|  
|---------------------|-----------------|  
|[set::begin (STL/CLR)](#begin)|Určuje začátek řízené sekvence.|  
|[set::clear (STL/CLR)](#clear)|Odebere všechny prvky.|  
|[set::count (STL/CLR)](#count)|Vrátí počet prvků odpovídající zadanému klíči.|  
|[set::empty (STL/CLR)](#empty)|Zkouší, zda nejsou přítomny žádné prvky.|  
|[set::end (STL/CLR)](#end)|Určuje konec řízené sekvence.|  
|[set::equal_range (STL/CLR)](#equal_range)|Najde rozsah, který odpovídá zadanému klíči.|  
|[set::erase (STL/CLR)](#erase)|Odebere prvky v určených pozicích.|  
|[set::find (STL/CLR)](#find)|Vyhledá prvek, který odpovídá zadanému klíči.|  
|[set::insert (STL/CLR)](#insert)|Přidá prvky.|  
|[set::key_comp (STL/CLR)](#key_comp)|Zkopíruje pořadí delegáta pro dva klíče.|  
|[set::lower_bound (STL/CLR)](#lower_bound)|Vyhledá počátek rozsahu, který odpovídá zadanému klíči.|  
|[set::make_value (STL/CLR)](#make_value)|Vytvoří objekt hodnoty.|  
|[set::rbegin (STL/CLR)](#rbegin)|Určuje začátek řízené obrácené sekvenci.|  
|[set::rend (STL/CLR)](#rend)|Určuje konec řízené obrácené sekvenci.|  
|[set::set (STL/CLR)](#set)|Sestaví objekt kontejneru.|  
|[set::size (STL/CLR)](#size)|Spočítá počet prvků.|  
|[set::swap (STL/CLR)](#swap)|Zamění obsah dvou kontejnerů.|  
|[set::to_array (STL/CLR)](#to_array)|Zkopíruje do nového pole řízené sekvence.|  
|[set::upper_bound (STL/CLR)](#upper_bound)|Najde konec rozsahu, který odpovídá zadanému klíči.|  
|[set::value_comp (STL/CLR)](#value_comp)|Zkopíruje pořadí delegáta pro dvě hodnoty prvků.|  
  
|Operátor|Popis|  
|--------------|-----------------|  
|[set::operator= (STL/CLR)](#op_as)|Nahradí řízené sekvence.|  
|[operator!= (set) (STL/CLR)](#op_neq)|Určuje, zda `set` není roven jinému objektu `set` objektu.|  
|[operator< (set) (STL/CLR)](#op_lt)|Určuje, zda `set` je menší než jiný objekt `set` objektu.|  
|[operator<= (set) (STL/CLR)](#op_lteq)|Určuje, zda `set` objekt je menší nebo rovna jiné `set` objektu.|  
|[operator== (set) (STL/CLR)](#op_eq)|Určuje, zda `set` je roven jinému objektu `set` objektu.|  
|[operator> (set) (STL/CLR)](#op_gt)|Určuje, zda `set` je větší než jiný objekt `set` objektu.|  
|[operator>= (set) (STL/CLR)](#op_gteq)|Určuje, zda `set` objekt je větší než nebo roven jinému `set` objektu.|  
  
## <a name="interfaces"></a>Rozhraní  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Duplicitní objektu.|  
|<xref:System.Collections.IEnumerable>|Pořadí mezi prvky.|  
|<xref:System.Collections.ICollection>|Údržba skupiny prvků.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Pořadí pomocí zadané elementy.|  
|<xref:System.Collections.Generic.ICollection%601>|Údržba skupiny zadané elementy.|  
|ITree\<klíč, hodnota >|Udržujte obecný kontejneru.|  
  
## <a name="remarks"></a>Poznámky  
 Objekt přiděluje a uvolňuje úložiště pro sekvenci, ovládací prvky jako jednotlivé uzly. Vloží prvky do (téměř) s vyrovnáváním strom, který udržuje seřazený tím, že změna vazby mezi uzly, nikdy zkopírováním obsah jednoho uzlu do jiného. To znamená, že můžete vložit a odebrat elementy volně bez narušení zbývající prvky.  
  
 Objekt seřadí sekvence pomocí volání uloženého delegáta objekt typu [set::key_compare (STL/CLR)](../dotnet/set-key-compare-stl-clr.md). Při vytváření sady; můžete zadat objekt uložené delegáta Pokud chcete zadat žádný objekt. delegát, výchozí hodnota je porovnání `operator<(key_type, key_type)`. Přístup k tomuto uloženého objektu voláním členské funkce [set::key_comp (STL/CLR)](../dotnet/set-key-comp-stl-clr.md)`()`.  
  
 Takový objekt delegáta musí uložit přísné slabé seřazení klíčů typu [set::key_type (STL/CLR)](../dotnet/set-key-type-stl-clr.md). To znamená pro jakékoli dva klíče `X` a `Y`:  
  
 `key_comp()(X, Y)` Vrátí výsledek stejný datový typ Boolean při každém volání.  
  
 Pokud `key_comp()(X, Y)` má hodnotu true, pak `key_comp()(Y, X)` musí mít hodnotu false.  
  
 Pokud `key_comp()(X, Y)` má hodnotu true, pak `X` říká, že je řazen před `Y`.  
  
 Pokud `!key_comp()(X, Y) && !key_comp()(Y, X)` má hodnotu true, pak `X` a `Y` se říká, že mají ekvivalentní řazení.  
  
 Pro libovolný element `X` , která předchází `Y` v řízené sekvenci `key_comp()(Y, X)` má hodnotu false. (Pro výchozí objekt delegáta, klíče nikdy snížení hodnoty.) Na rozdíl od třídy šablony [nastavit](../dotnet/set-stl-clr.md), objekt třídy šablony `set` nevyžaduje, aby byly jedinečné klíče pro všechny elementy. (Dva nebo více klíčů může mít odpovídající řazení.)  
  
 Každý prvek slouží jako ey a hodnotu. Sekvence je reprezentována způsobem, který umožňuje vyhledávání, vkládání a odstranění libovolný prvek s počtem operací úměrný logaritmu počtu prvků v sekvenci (logaritmické čas). Vkládání prvků navíc nezruší platnost žádných iterátorů a odstranění prvku zruší platnost pouze těch iterátorů, které odkazují na odstraněný prvek.  
  
 Sada podporuje obousměrné iterátory, což znamená, že přejdete na sousedící prvky zadaný iterátor, který určuje elementu v řízené sekvenci. Speciální hlavního uzlu odpovídá iterátorů vrácené [set::end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`. Tento iterátor, který má přístup po posledním prvku v řízené sekvenci lze snížit, pokud jsou k dispozici. Můžete zvýšit sady iterátor pro přístup k hlavnímu uzlu a budou pak porovnat rovna `end()`. Nelze přistoupit přes ukazatel vrátí iterátor, ale `end()`.  
  
 Všimněte si, že nemůže odkazovat na prvek sady přímo zadané pozici číselné –, který vyžaduje iterátor náhodného přístupu.  
  
 Iterátor sady uloží popisovač do přidružené sady uzlu, který je pak uloží popisovač pro jeho přiřazeným kontejnerem. Iterátory lze použít pouze objekty, které přiřazeným kontejnerem. Iterátor sada je platná tak dlouho, dokud jeho přidružené sady uzlu je přidružen některé sady. Kromě toho je platný iterátoru přesměrovat – slouží k přístupu nebo změnit hodnotu prvku jmenuje--tak dlouho, dokud se nerovná `end()`.  
  
 Smazání nebo odstranění prvku volá destruktor pro jeho uložené hodnotě. Zničení kontejneru vymaže všechny prvky. Kontejner, jehož typ prvku je třídy ref class tak, zajišťuje, že žádné elementy něj kontejneru. Mějte na paměti, ale, že kontejner zpracovává nemá *není* zničit jeho prvků.  
 
## <a name="members"></a>Členové

## <a name="begin"></a>set::begin (STL/CLR)
Určuje začátek řízené sekvence.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
iterator begin();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí obousměrný iterátor, který určuje první prvek řízenou sekvenci nebo přesně za konec k prázdné sekvenci. Můžete ji použít k získání iterátor, který určuje `current` začátek řízené sekvence, ale jeho stav můžete změnit, pokud se změní délka řízené sekvence.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_begin.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    Myset::iterator it = c1.begin();   
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

## <a name="clear"></a>set::clear (STL/CLR)
Odebere všechny prvky.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
void clear();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce efektivně volá [set::erase (STL/CLR)](../dotnet/set-erase-stl-clr.md) `(` [set::begin (STL/CLR)](../dotnet/set-begin-stl-clr.md) `(),` [set::end (STL/CLR)](../dotnet/set-end-stl-clr.md) `())`. Použijete ji k zajištění, že je prázdná řízené sekvence.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_clear.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// add elements and clear again   
    c1.insert(L'a');   
    c1.insert(L'b');   
  
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

## <a name="const_iterator"></a>set::const_iterator (STL/CLR)
Typ konstantního iterátoru řízené sekvence  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef T2 const_iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ popisuje objekt neurčeného typu `T2` , který může sloužit jako konstantní obousměrného iterátoru řízené sekvence.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_const_iterator.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    Myset::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        System::Console::Write(" {0}", *cit);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
```  

## <a name="const_reference"></a>set::const_reference (STL/CLR)
Typ konstantního odkazu na prvek  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef value_type% const_reference;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ, který popisuje konstantní odkaz na element.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_const_reference.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    Myset::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        {   // get a const reference to an element   
        Myset::const_reference cref = *cit;   
        System::Console::Write(" {0}", cref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
```  

## <a name="const_reverse_iterator"></a>set::const_reverse_iterator (STL/CLR)
Typ konstantního zpětného iterátoru řízené sekvence...  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef T4 const_reverse_iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ popisuje objekt neurčeného typu `T4` , který může sloužit jako konstantní zpětného iterátoru řízené sekvence.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_const_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" reversed   
    Myset::const_reverse_iterator crit = c1.rbegin();   
    for (; crit != c1.rend(); ++crit)   
        System::Console::Write(" {0}", *crit);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c b a  
```  

## <a name="count"></a>set::Count (STL/CLR)
Zjistí počet prvků odpovídající zadanému klíči.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
size_type count(key_type key);  
```  
  
#### <a name="parameters"></a>Parametry  
 *Klíč*  
 Hodnota klíče pro hledání.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí počet prvků v řízené sekvenci, která mají stejné pořadí s *klíč*. Použijete ji k určení počtu prvků v řízené sekvenci aktuálně, které odpovídají zadanému klíči.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_count.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("count(L'A') = {0}", c1.count(L'A'));   
    System::Console::WriteLine("count(L'b') = {0}", c1.count(L'b'));   
    System::Console::WriteLine("count(L'C') = {0}", c1.count(L'C'));   
    return (0);   
    }   
```  
  
```Output  
 a b c  
count(L'A') = 0  
count(L'b') = 1  
count(L'C') = 0  
```  

## <a name="difference_type"></a>set::difference_type (STL/CLR)
Typ vzdálenosti se znaménkem mezi dvěma prvky.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef int difference_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ, který popisuje element může být záporný počet.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_difference_type.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    Myset::difference_type diff = 0;   
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)   
        ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
  
// compute negative difference   
    diff = 0;   
    for (Myset::iterator it = c1.end(); it != c1.begin(); --it)   
        --diff;   
    System::Console::WriteLine("begin()-end() = {0}", diff);   
    return (0);   
    }  
```  
  
```Output  
 a b c  
end()-begin() = 3  
begin()-end() = -3  
```  

## <a name="empty"></a>set::Empty (STL/CLR)
Zkouší, zda nejsou přítomny žádné prvky.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
bool empty();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí hodnotu true pro prázdnou řízenou sekvenci. Je ekvivalentní [set::size (STL/CLR)](../dotnet/set-size-stl-clr.md)`() == 0`. Použijete ji k ověření, zda sada byla prázdná.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_empty.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
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

## <a name="end"></a>set::end (STL/CLR)
Určuje konec řízené sekvence.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
iterator end();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí obousměrný iterátor, který ukazuje za konec řízené sekvence. Můžete ji použít k získání iterátor, který určuje konec řízené sekvence; jeho stav kódu ne změnit, pokud se změní délka řízené sekvence.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_end.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last two items   
    Myset::iterator it = c1.end();   
    --it;   
    System::Console::WriteLine("*-- --end() = {0}", *--it);   
    System::Console::WriteLine("*--end() = {0}", *++it);   
    return (0);   
    }  
```  
  
```Output  
 a b c  
*-- --end() = b  
*--end() = c  
```  

## <a name="equal_range"></a>set::equal_range (STL/CLR)
Najde rozsah, který odpovídá zadanému klíči.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
cliext::pair<iterator, iterator> equal_range(key_type key);  
```  
  
#### <a name="parameters"></a>Parametry  
 *Klíč*  
 Hodnota klíče pro hledání.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí pár iterátorů `cliext::pair<iterator, iterator>(` [set::lower_bound (STL/CLR)](../dotnet/set-lower-bound-stl-clr.md) `(key),` [set::upper_bound (STL/CLR)](../dotnet/set-upper-bound-stl-clr.md)`(key))`. Použijete ji k určení rozsahu prvků v řízené sekvenci aktuálně, které odpovídají zadanému klíči.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_equal_range.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
typedef Myset::pair_iter_iter Pairii;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display results of failed search   
    Pairii pair1 = c1.equal_range(L'x');   
    System::Console::WriteLine("equal_range(L'x') empty = {0}",   
        pair1.first == pair1.second);   
  
// display results of successful search   
    pair1 = c1.equal_range(L'b');   
    for (; pair1.first != pair1.second; ++pair1.first)   
        System::Console::Write(" {0}", *pair1.first);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
 a b c  
equal_range(L'x') empty = True  
 b  
``` 

## <a name="erase"></a>set::Erase (STL/CLR)
Odebere prvky v určených pozicích.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
size_type erase(key_type key)  
```  
  
#### <a name="parameters"></a>Parametry  
 *první*  
 Začátek rozsahu vymazat.  
  
 *Klíč*  
 Hodnota klíče vymazat.  
  
 *poslední*  
 Konec rozsahu vymazat.  
  
 *kde*  
 Element vymazat.  
  
### <a name="remarks"></a>Poznámky  
 První členská funkce odstraní prvek řízené sekvence, na které odkazuje *kde*a vrátí iterátor, který určuje první prvek zbývající za prvkem, který odebere, nebo [set::end (STL/CLR) ](../dotnet/set-end-stl-clr.md) `()` Pokud žádný takový prvek neexistuje. Použijete ji k odebrání jeden element.  
  
 Druhá členská funkce odebere prvky řízené sekvence v rozsahu [`first`, `last`) a vrátí iterátor, který určuje první prvek zbývající za všemi odstraněnými prvky, nebo `end()` Pokud žádný takový prvek existuje... Použijete ji k odebrání nula nebo více souvislých prvků.  
  
 Třetí členská funkce odstraní libovolný prvek řízenou sekvenci, jehož klíč má ekvivalentní řazení na *klíč*a vrátí počet prvků, které jsou odebrány. Použijete ho odebrat a spočítat všechny elementy, které odpovídají zadanému klíči.  
  
 Každý prvek mazání trvá určitou dobu úměrný logaritmu počtu prvků v řízené sekvenci.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_erase.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase an element and reinspect   
    System::Console::WriteLine("erase(begin()) = {0}",   
        *c1.erase(c1.begin()));   
  
// add elements and display " b c d e"   
    c1.insert(L'd');   
    c1.insert(L'e');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase all but end   
    Myset::iterator it = c1.end();   
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

## <a name="find"></a>set::Find (STL/CLR)
Vyhledá prvek, který odpovídá zadanému klíči.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
iterator find(key_type key);  
```  
  
#### <a name="parameters"></a>Parametry  
 *Klíč*  
 Hodnota klíče pro hledání.  
  
### <a name="remarks"></a>Poznámky  
 Pokud má alespoň jeden element v řízené sekvenci s odpovídající řazení *klíč*, členská funkce vrátí iterátor určit jeden z těchto elementů; v opačném případě vrátí [set::end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`. Použijete ji k aktuálně vyhledejte elementu v řízené sekvenci, která odpovídá zadanému klíči.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_find.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("find {0} = {1}",   
        L'A', c1.find(L'A') != c1.end());   
    System::Console::WriteLine("find {0} = {1}",   
        L'b', *c1.find(L'b'));   
    System::Console::WriteLine("find {0} = {1}",   
        L'C', c1.find(L'C') != c1.end());   
    return (0);   
    }  
```  
  
```Output  
 a b c  
find A = False  
find b = b  
find C = False  
```  

## <a name="generic_container"></a>set::generic_container (STL/CLR)
Typ obecné rozhraní pro kontejner.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef Microsoft::VisualC::StlClr::  
    ITree<GKey, GValue>  
    generic_container;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ, který popisuje obecné rozhraní pro tuto třídu šablony kontejneru.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_generic_container.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myset::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    gc1->insert(L'd');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify original and display generic   
    c1.insert(L'e');   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
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
  
## <a name="generic_iterator"></a> set::generic_iterator (STL/CLR)
Typ iterátoru pro použití s obecné rozhraní pro kontejner.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef Microsoft::VisualC::StlClr::Generic::  
    ContainerBidirectionalIterator<generic_value>  
    generic_iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ, který popisuje obecný iterátoru, který jde použít s obecné rozhraní pro tuto třídu šablony kontejneru.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_generic_iterator.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myset::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Myset::generic_iterator gcit = gc1->begin();   
    Myset::generic_value gcval = *gcit;   
    System::Console::WriteLine(" {0}", gcval);   
    return (0);   
    }  
```  
  
```Output  
a b c  
a b c  
a  
```  
  
## <a name="generic_reverse_iterator"></a> set::generic_reverse_iterator (STL/CLR)
Typ "reverse iterator" pro použití s obecné rozhraní pro kontejner.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef Microsoft::VisualC::StlClr::Generic::  
    ReverseRandomAccessIterator<generic_value>  
    generic_reverse_iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ, který popisuje obecný zpětný iterátor, který jde použít s obecné rozhraní pro tuto třídu šablony kontejneru.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_generic_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myset::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Myset::generic_reverse_iterator gcit = gc1->rbegin();   
    Myset::generic_value gcval = *gcit;   
    System::Console::WriteLine(" {0}", gcval);   
    return (0);   
    }  
```  
  
```Output  
a b c  
a b c  
c  
```  

## <a name="generic_value"></a> set::generic_value (STL/CLR)
Typ elementu pro použití s obecné rozhraní pro kontejner.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef GValue generic_value;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ, který popisuje objekt typu `GValue` hodnoty uložené elementu pro použití s obecné rozhraní pro tuto třídu šablony kontejneru, který popisuje.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_generic_value.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myset::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Myset::generic_iterator gcit = gc1->begin();   
    Myset::generic_value gcval = *gcit;   
    System::Console::WriteLine(" {0}", gcval);   
    return (0);   
    }  
```  
  
```Output  
a b c  
a b c  
a  
```  
  
## <a name="insert"></a> set::Insert (STL/CLR)
Přidá prvky.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
cliext::pair<iterator, bool> insert(value_type val);  
iterator insert(iterator where, value_type val);  
template<typename InIter>  
    void insert(InIter first, InIter last);  
void insert(System::Collections::Generic::IEnumerable<value_type>^ right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *první*  
 Začátek rozsahu pro vložení.  
  
 *poslední*  
 Konec rozsahu pro vložení.  
  
 *doprava*  
 Výčet pro vložení.  
  
 *Val*  
 Hodnota klíče pro vložení.  
  
 *kde*  
 Kde v kontejneru pro vložení (jenom pro pomocný parametr).  
  
### <a name="remarks"></a>Poznámky  
 Každá z členské funkce vloží pořadí určeném zbývající operandy.  
  
 První členská funkce endeavors vložit element s hodnotou *val*a vrátí dvojice hodnot `X`. Pokud `X.second` má hodnotu true, `X.first` označí nově vložený prvek; v opačném případě `X.first` určuje element s ekvivalentní řazení, která již existuje a je vložen žádný nový prvek. Použijete ji k vložení jeden element.  
  
 Druhá členská funkce vloží prvek s hodnotou *val*s použitím *kde* jako Nápověda (ke zlepšení výkonu) a vrátí iterátor, který určuje nově vložený prvek. Použijete ji k vložení jeden element, který může být vedle elementu, které už znáte.  
  
 Třetí členská funkce vloží sekvenci [`first`, `last`). Použijete ji k vložení nula nebo více elementů zkopírovaných z jiné pořadí.  
  
 Čtvrtá členská funkce vloží pořadí určeném *správné*. Použijete ji k vložení pořadí popsal enumerátor.  
  
 Každý prvek vložení trvá určitou dobu úměrný logaritmu počtu prvků v řízené sekvenci. Vložení situace může nastat v amortizovaném konstantním času, ale zadaný pomocného parametru, který určuje prvek vedle kurzor.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_insert.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
typedef Myset::pair_iter_bool Pairib;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value, unique and duplicate   
    Pairib pair1 = c1.insert(L'x');   
    System::Console::WriteLine("insert(L'x') = [{0} {1}]",   
        *pair1.first, pair1.second);   
  
    pair1 = c1.insert(L'b');   
    System::Console::WriteLine("insert(L'b') = [{0} {1}]",   
        *pair1.first, pair1.second);   
  
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value with hint   
    System::Console::WriteLine("insert(begin(), L'y') = {0}",   
        *c1.insert(c1.begin(), L'y'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    Myset c2;   
    Myset::iterator it = c1.end();   
    c2.insert(c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    Myset c3;   
    c3.insert(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
 a b c  
insert(L'x') = [x True]  
insert(L'b') = [b False]  
 a b c x  
insert(begin(), L'y') = y  
 a b c x y  
 a b c x  
 a b c x y  
```  

## <a name="iterator"></a> set::iterator (STL/CLR)
Typ iterátoru řízené sekvence  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef T1 iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ popisuje objekt neurčeného typu `T1` , který může sloužit jako obousměrný iterátor, který řízené sekvence.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_iterator.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    Myset::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
```  

## <a name="key_comp"></a> set::key_comp (STL/CLR)
Zkopíruje pořadí delegáta pro dva klíče.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
key_compare^key_comp();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí pořadí delegáta, který slouží k seřazení řízené sekvence. Použijete ji k porovnat dva klíče.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_key_comp.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    Myset::key_compare^ kcomp = c1.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Myset c2 = cliext::greater<wchar_t>();   
    kcomp = c2.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    return (0);   
    }  
```  
  
```Output  
compare(L'a', L'a') = False  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
  
compare(L'a', L'a') = False  
compare(L'a', L'b') = False  
compare(L'b', L'a') = True  
```  

## <a name="key_compare"></a> set::key_compare (STL/CLR)
Pořadí delegáta pro dva klíče.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
Microsoft::VisualC::StlClr::BinaryDelegate<GKey, GKey, bool>  
    key_compare;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro delegáta, který určuje řazení klíče argumenty.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_key_compare.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    Myset::key_compare^ kcomp = c1.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Myset c2 = cliext::greater<wchar_t>();   
    kcomp = c2.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    return (0);   
    }  
```  
  
```Output  
compare(L'a', L'a') = False  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
  
compare(L'a', L'a') = False  
compare(L'a', L'b') = False  
compare(L'b', L'a') = True  
```  

## <a name="key_type"></a> set::key_type (STL/CLR)
Typ klíče řazení  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro parametr šablony *klíč*.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_key_type.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" using key_type   
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in key_type object   
        Myset::key_type val = *it;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }   
```  
  
```Output  
a b c  
```  

## <a name="lower_bound"></a> set::lower_bound (STL/CLR)
Vyhledá počátek rozsahu, který odpovídá zadanému klíči.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
iterator lower_bound(key_type key);  
```  
  
#### <a name="parameters"></a>Parametry  
 *Klíč*  
 Hodnota klíče pro hledání.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce určuje první prvek `X` v řízené sekvenci, která má stejné pořadí na *klíč*. Pokud žádný takový prvek neexistuje, vrátí [set::end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`; v opačném případě vrátí iterátor, který určuje `X`. Použijete ji k aktuálně vyhledejte na začátek pořadí prvků v řízené sekvenci, které odpovídají zadanému klíči.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_lower_bound.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",   
        c1.lower_bound(L'x') == c1.end());   
  
    System::Console::WriteLine("*lower_bound(L'a') = {0}",   
        *c1.lower_bound(L'a'));   
    System::Console::WriteLine("*lower_bound(L'b') = {0}",   
        *c1.lower_bound(L'b'));   
    return (0);   
    }  
```  
  
```Output  
 a b c  
lower_bound(L'x')==end() = True  
*lower_bound(L'a') = a  
*lower_bound(L'b') = b  
```  

## <a name="make_value"></a> set::make_value (STL/CLR)
Vytvoří objekt hodnoty.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
static value_type make_value(key_type key);  
```  
  
#### <a name="parameters"></a>Parametry  
 *Klíč*  
 Hodnota klíče používat.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí `value_type` objekt, jehož klíč je *klíč*. Použijete ji k vytvoření objektu vhodný pro použití s několika další členské funkce.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_make_value.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(Myset::make_value(L'a'));   
    c1.insert(Myset::make_value(L'b'));   
    c1.insert(Myset::make_value(L'c'));   
  
// display contents " a b c"   
    for each (Myset::value_type elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }   
```  
  
```Output  
a b c  
```  

## <a name="op_as"></a> set::Operator = (STL/CLR)
Nahradí řízené sekvence.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
set<Key>% operator=(set<Key>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *doprava*  
 Kontejner pro kopírování.  
  
### <a name="remarks"></a>Poznámky  
 Kopie členský operátor *správné* na objekt, vrátí `*this`. Můžete použít k nahraďte kopii řízené sekvence v řízené sekvenci *správné*.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_operator_as.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (Myset::value_type elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myset c2;   
    c2 = c1;   
// display contents " a b c"   
    for each (Myset::value_type elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }   
```  
  
```Output  
a b c  
a b c  
```  

## <a name="rbegin"></a> set::rbegin (STL/CLR)
Určuje začátek řízené obrácené sekvenci.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
reverse_iterator rbegin();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí zpětný iterátor, který určuje poslední prvek řízenou sekvenci nebo hned za začátku k prázdné sekvenci. Proto, označí `beginning` reverzní pořadí. Můžete ji použít k získání iterátor, který určuje `current` začátek řízené sekvence viděli v obráceném pořadí, ale jeho stav můžete změnit, pokud se změní délka řízené sekvence.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_rbegin.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items in reversed sequence   
    Myset::reverse_iterator rit = c1.rbegin();   
    System::Console::WriteLine("*rbegin() = {0}", *rit);   
    System::Console::WriteLine("*++rbegin() = {0}", *++rit);   
    return (0);   
    }  
```  
  
```Output  
 a b c  
*rbegin() = c  
*++rbegin() = b  
```  

## <a name="reference"></a> set::Reference (STL/CLR)
Typ odkazu na prvek  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef value_type% reference;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ, který popisuje odkaz na element.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_reference.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    Myset::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        {   // get a reference to an element   
        Myset::reference ref = *it;   
        System::Console::Write(" {0}", ref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
```

## <a name="rend"></a> set::rend (STL/CLR)
Určuje konec řízené obrácené sekvenci.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
reverse_iterator rend();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí "reverse iterator", který ukazuje za začátek řízené sekvence. Proto, označí `end` reverzní pořadí. Můžete ji použít k získání iterátor, který určuje `current` konec řízené sekvence viděli v obráceném pořadí, ale jeho stav můžete změnit, pokud se změní délka řízené sekvence.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_rend.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    Myset::reverse_iterator rit = c1.rend();   
    --rit;   
    System::Console::WriteLine("*-- --rend() = {0}", *--rit);   
    System::Console::WriteLine("*--rend() = {0}", *++rit);   
    return (0);   
    }  
```  
  
```Output  
 a b c  
*-- --rend() = b  
*--rend() = a  
```    

## <a name="reverse_iterator"></a> set::reverse_iterator (STL/CLR)
Typ "reverse iterator" pro řízenou sekvenci.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef T3 reverse_iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ popisuje objekt neurčeného typu `T3` , který může sloužit jako "reverse iterator" pro řízenou sekvenci.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" reversed   
    Myset::reverse_iterator rit = c1.rbegin();   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" {0}", *rit);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c b a  
```  
  
## <a name="set"></a> set::set (STL/CLR)
Sestaví objekt kontejneru.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
set();  
explicit set(key_compare^ pred);  
set(set<Key>% right);  
set(set<Key>^ right);  
template<typename InIter>  
    setset(InIter first, InIter last);  
template<typename InIter>  
    set(InIter first, InIter last,  
        key_compare^ pred);  
set(System::Collections::Generic::IEnumerable<GValue>^ right);  
set(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred);  
```  
  
#### <a name="parameters"></a>Parametry  
 *první*  
 Začátek rozsahu pro vložení.  
  
 *poslední*  
 Konec rozsahu pro vložení.  
  
 *Před*  
 Řazení predikátu řízené sekvence.  
  
 *doprava*  
 Objekt nebo rozsahu pro vložení.  
  
### <a name="remarks"></a>Poznámky  
 Konstruktor:  
  
 `set();`  
  
 Inicializuje výchozí řazení predikátu řízené sekvence bez prvků `key_compare()`. Použijete ji k určení prázdnou počáteční řízenou sekvenci, s výchozí řazení predikátu.  
  
 Konstruktor:  
  
 `explicit set(key_compare^ pred);`  
  
 Inicializuje řízené sekvence bez prvků pořadí predikátem *před*. Použít prázdnou počáteční řízenou sekvenci, určit se zadanou predikát pořadí.  
  
 Konstruktor:  
  
 `set(set<Key>% right);`  
  
 Inicializuje řízené sekvence s pořadím [`right.begin()`, `right.end()`), s výchozí řazení predikátu. Můžete použít k určení počáteční řízené sekvence, která je kopii sekvence řízenou parametrem objekt set *správné*, s výchozí řazení predikátu.  
  
 Konstruktor:  
  
 `set(set<Key>^ right);`  
  
 Inicializuje řízené sekvence s pořadím [`right->begin()`, `right->end()`), s výchozí řazení predikátu. Můžete použít k určení počáteční řízené sekvence, která je kopii sekvence řízenou parametrem objekt set *správné*, s výchozí řazení predikátu.  
  
 Konstruktor:  
  
 `template<typename InIter> set(InIter first, InIter last);`  
  
 Inicializuje řízené sekvence s pořadím [`first`, `last`), s výchozí řazení predikátu. Používejte aby řízené sekvence kopii jiné pořadí, s výchozí řazení predikátu.  
  
 Konstruktor:  
  
 `template<typename InIter> set(InIter first, InIter last, key_compare^ pred);`  
  
 Inicializuje řízené sekvence s pořadím [`first`, `last`), pořadí predikátem *před*. Použijete ji k vytvoření kopie jiné pořadí se zadanou predikát pořadí řízené sekvence.  
  
 Konstruktor:  
  
 `set(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 Inicializuje řízené sekvence s pořadí určeném enumerátor *správné*, s výchozí řazení predikátu. Použijete ji k vytvoření kopie jiné pořadí popsal čítače, s výchozí řazení predikátu řízené sekvence.  
  
 Konstruktor:  
  
 `set(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`  
  
 Inicializuje řízené sekvence s pořadí určeném enumerátor *správné*, pořadí predikátem *před*. Použijete ji k vytvoření kopie jiné pořadí popsal enumerátor se zadanou predikát pořadí řízené sekvence.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_construct.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
// construct an empty container   
    Myset c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Myset c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Myset c3(c1.begin(), c1.end());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Myset c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Myset c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Myset c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,   
            cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c6)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct from a generic container   
    Myset c7(c4);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Myset c8(%c3);   
    for each (wchar_t elem in c8)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }   
```  
  
```Output  
size() = 0  
 a b c  
size() = 0  
 c b a  
 a b c  
 c b a  
 a b c  
 c b a  
 c b a  
 a b c  
```  

## <a name="size"></a> set::size (STL/CLR)
Spočítá počet prvků.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
size_type size();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí délku objektu řízené sekvence. Použijete ji k určení počtu prvků v řízené sekvenci aktuálně. Pokud vás zajímá, jestli je pořadí má nenulovou velikost, naleznete v tématu [set::empty (STL/CLR)](../dotnet/set-empty-stl-clr.md)`()`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_size.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0} after clearing", c1.size());   
  
// add elements and clear again   
    c1.insert(L'a');   
    c1.insert(L'b');   
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

## <a name="size_type"></a> set::size_type (STL/CLR)
Typ vzdálenosti se znaménkem mezi dvěma elementu.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef int size_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ, který popisuje počet prvků záporná.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_size_type.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    Myset::size_type diff = 0;   
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)   
        ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
    return (0);   
    }  
```  
  
```Output  
 a b c  
end()-begin() = 3  
```  

## <a name="swap"></a> set::swap (STL/CLR)
Zamění obsah dvou kontejnerů.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
void swap(set<Key>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *doprava*  
 Kontejner pro obsah s.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce Zamění řízené sekvence mezi `this` a *správné*. Provádí se v konstantním času a vyvolá žádné výjimky. Můžete použít jako rychlý způsob, jak Zamění obsah dvou kontejnerů.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_swap.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct another container with repetition of values   
    Myset c2;   
    c2.insert(L'd');   
    c2.insert(L'e');   
    c2.insert(L'f');   
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
d e f  
d e f  
a b c  
```  
  
## <a name="to_array"></a> set::to_array (STL/CLR)
Zkopíruje do nového pole řízené sekvence.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
cli::array<value_type>^ to_array();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí pole obsahující řízené sekvence. Použijete ji získat kopii řízenou sekvenci pole formuláře.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_to_array.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// copy the container and modify it   
    cli::array<wchar_t>^ a1 = c1.to_array();   
  
    c1.insert(L'd');   
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

## <a name="upper_bound"></a> set::upper_bound (STL/CLR)
Najde konec rozsahu, který odpovídá zadanému klíči.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
iterator upper_bound(key_type key);  
```  
  
#### <a name="parameters"></a>Parametry  
 *Klíč*  
 Hodnota klíče pro hledání.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce určuje poslední prvek `X` v řízené sekvenci, která má stejné pořadí na *klíč*. Pokud žádný takový prvek neexistuje, nebo pokud `X` je po posledním prvku v řízené sekvenci vrátí [set::end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`; v opačném případě vrátí iterátor, který určuje prvního prvku mimo `X`. Pomocí aktuálně najít konec pořadí prvků v řízené sekvenci, které odpovídají zadanému klíči.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_upper_bound.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",   
        c1.upper_bound(L'x') == c1.end());   
  
    System::Console::WriteLine("*upper_bound(L'a') = {0}",   
        *c1.upper_bound(L'a'));   
    System::Console::WriteLine("*upper_bound(L'b') = {0}",   
        *c1.upper_bound(L'b'));   
    return (0);   
    }  
```  
  
```Output  
 a b c  
upper_bound(L'x')==end() = True  
*upper_bound(L'a') = b  
*upper_bound(L'b') = c  
```  

## <a name="value_comp"></a> set::value_comp (STL/CLR)
Zkopíruje pořadí delegáta pro dvě hodnoty prvků.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
value_compare^ value_comp();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí pořadí delegáta, který slouží k seřazení řízené sekvence. Použijete ji k porovnat dvě hodnoty prvků.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_value_comp.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    Myset::value_compare^ kcomp = c1.value_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
compare(L'a', L'a') = False  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
```  

## <a name="value_compare"></a> set::value_compare (STL/CLR)
Pořadí delegáta pro dvě hodnoty prvků.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
Microsoft::VisualC::StlClr::BinaryDelegate<generic_value, generic_value, bool>  
    value_compare;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro delegáta, který určuje pořadí z argumentů hodnotu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_value_compare.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    Myset::value_compare^ kcomp = c1.value_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
compare(L'a', L'a') = False  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
```  

## <a name="value_type"></a> set::value_type (STL/CLR)
Typ prvku  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef generic_value value_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro `generic_value`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_value_type.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" using value_type   
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in value_type object   
        Myset::value_type val = *it;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
```  

## <a name="op_neq"></a> Operator! = (set) (STL/CLR)
Seznam není rovno porovnání.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Key>  
    bool operator!=(set<Key>% left,  
        set<Key>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *doleva*  
 Levé kontejner k porovnání.  
  
 *doprava*  
 Správném kontejneru pro porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí funkci operátoru `!(left == right)`. Pomocí něho můžete testovat, zda *levé* není stejný jako seřazené *správné* když jsou dvě sady porovnání elementu pomocí elementu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_operator_ne.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myset c2;   
    c2.insert(L'a');   
    c2.insert(L'b');   
    c2.insert(L'd');   
  
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

## <a name="op_lt"></a> operátor&lt; (set) (STL/CLR)
Seznam menší než porovnání.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Key>  
    bool operator<(set<Key>% left,  
        set<Key>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *doleva*  
 Levé kontejner k porovnání.  
  
 *doprava*  
 Správném kontejneru pro porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Operátoru funkce vrátí hodnota true v případě, pro nejnižší pozici `i` pro kterou `!(right[i] < left[i])` je také hodnotu true, který `left[i] < right[i]`. V opačném případě vrátí `left->size() < right->size()` pomocí něho můžete testovat, zda *levé* je řazen před *správné* když jsou dvě sady porovnání elementu pomocí elementu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_operator_lt.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myset c2;   
    c2.insert(L'a');   
    c2.insert(L'b');   
    c2.insert(L'd');   
  
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

## <a name="op_lteq"></a> operátor&lt;= (set) (STL/CLR)
Seznam menší nebo rovna porovnání.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Key>  
    bool operator<=(set<Key>% left,  
        set<Key>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *doleva*  
 Levé kontejner k porovnání.  
  
 *doprava*  
 Správném kontejneru pro porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí funkci operátoru `!(right < left)`. Pomocí něho můžete testovat, zda *levé* není seřazené po *správné* když jsou dvě sady porovnání elementu pomocí elementu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_operator_le.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myset c2;   
    c2.insert(L'a');   
    c2.insert(L'b');   
    c2.insert(L'd');   
  
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
  
## <a name="op_eq"></a> Operator == (set) (STL/CLR)
Porovnání rovna seznamu.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Key>  
    bool operator==(set<Key>% left,  
        set<Key>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *doleva*  
 Levé kontejner k porovnání.  
  
 *doprava*  
 Správném kontejneru pro porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Funkce operátoru vrátí hodnotu true pouze v případě, že řídí sekvencí *levé* a *správné* mít stejnou délku a pro každou pozici `i`, `left[i] ==` `right[i]`. Pomocí něho můžete testovat, zda *levé* je stejný jako seřazené *správné* když jsou dvě sady porovnání elementu pomocí elementu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_operator_eq.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myset c2;   
    c2.insert(L'a');   
    c2.insert(L'b');   
    c2.insert(L'd');   
  
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

## <a name="op_gt"></a> operátor&gt; (set) (STL/CLR)
Seznam je větší než porovnání.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Key>  
    bool operator>(set<Key>% left,  
        set<Key>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *doleva*  
 Levé kontejner k porovnání.  
  
 *doprava*  
 Správném kontejneru pro porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí funkci operátoru `right` `<` `left`. Pomocí něho můžete testovat, zda *levé* seřazené po *správné* když jsou dvě sady porovnání elementu pomocí elementu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_operator_gt.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myset c2;   
    c2.insert(L'a');   
    c2.insert(L'b');   
    c2.insert(L'd');   
  
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

## <a name="op_gteq"></a> operátor&gt;= (set) (STL/CLR)
Seznam větší než nebo rovna porovnání.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Key>  
    bool operator>=(set<Key>% left,  
        set<Key>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *doleva*  
 Levé kontejner k porovnání.  
  
 *doprava*  
 Správném kontejneru pro porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí funkci operátoru `!(left < right)`. Pomocí něho můžete testovat, zda *levé* není řazen před *správné* když jsou dvě sady porovnání elementu pomocí elementu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_set_operator_ge.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myset c2;   
    c2.insert(L'a');   
    c2.insert(L'b');   
    c2.insert(L'd');   
  
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