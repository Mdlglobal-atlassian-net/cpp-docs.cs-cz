---
title: Mapa (STL/CLR) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::map
- cliext::map::begin
- cliext::map::clear
- cliext::map::const_iterator
- cliext::map::const_reference
- cliext::map::const_reverse_iterator
- cliext::map::count
- cliext::map::difference_type
- cliext::map::empty
- cliext::map::end
- cliext::map::equal_range
- cliext::map::erase
- cliext::map::find
- cliext::map::generic_container
- cliext::map::generic_iterator
- cliext::map::generic_reverse_iterator
- cliext::map::generic_value
- cliext::map::insert
- cliext::map::iterator
- cliext::map::key_comp
- cliext::map::key_compare
- cliext::map::key_type
- cliext::map::lower_bound
- cliext::map::make_value
- cliext::map::map
- cliext::map::mapped_type
- cliext::map::operator=
- cliext::map::operator
- cliext::map::rbegin
- cliext::map::reference
- cliext::map::rend
- cliext::map::reverse_iterator
- cliext::map::size
- cliext::map::size_type
- cliext::map::swap
- cliext::map::to_array
- cliext::map::upper_bound
- cliext::map::value_comp
- cliext::map::value_compare
- cliext::map::value_type
- cliext::operator!= (map)
- cliext::operator< (map)
- cliext::operator<= (map)
- cliext::operator== (map)
- cliext::operator> (map)
- cliext::operator>= (map)
dev_langs:
- C++
helpviewer_keywords:
- <map> header [STL/CLR]
- map class [STL/CLR]
- <cliext/map> header [STL/CLR]
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
- map member [STL/CLR]
- mapped_type member [STL/CLR]
- operator= member [STL/CLR]
- operator member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rend member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- upper_bound member [STL/CLR]
- value_comp member [STL/CLR]
- value_compare member [STL/CLR]
- value_type member [STL/CLR]
- operator!= (map) member [STL/CLR]
- operator< (map) member [STL/CLR]
- operator<= (map) member [STL/CLR]
- operator== (map) member [STL/CLR]
- operator> (map) member [STL/CLR]
- operator>= (map) member [STL/CLR]
ms.assetid: 8b0a7764-b5e4-4175-a802-82b72eb8662a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 99a809753b244f442bf2eb321c58f4a07c5ba546
ms.sourcegitcommit: bad2441d1930275ff506d44759d283d94cccd1c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/31/2018
ms.locfileid: "39376349"
---
# <a name="map-stlclr"></a>map (STL/CLR)
Třída šablony popisuje objekt, který řídí různé délky sekvence elementů, která má obousměrný přístup. Použití kontejneru `map` , spravovat řadu prvků, jako větve (téměř) s vyrovnáváním seřazených uzlů, každý ukládání jeden element. Element se skládá z klíče pro seřazení, pořadí a mapované hodnoty, které nenastane pravé.  
  
 V popisu níže `GValue` je stejný jako:  
  
 `Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`  
  
 kde:  
  
 `GKey` je stejný jako *klíč* Pokud je typ odkazu, v takovém případě je `Key^`  
  
 `GMapped` je stejný jako *mapované* Pokud je typ odkazu, v takovém případě je `Mapped^`  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Key,  
    typename Mapped>  
    ref class map  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        System::Collections::Generic::IDictionary<Gkey, GMapped>,  
        Microsoft::VisualC::StlClr::ITree<Gkey, GValue>  
    { ..... };  
```  
  
### <a name="parameters"></a>Parametry  
 *Key*  
 Typ klíčovou komponentou elementu v řízené sekvenci.  
  
 *Mapovat*  
 Typ elementu v řízené sekvenci další komponenty.  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / map >  
  
 **Namespace:** cliext –  
  
## <a name="declarations"></a>Deklarace
  
|Definice typu|Popis|  
|---------------------|-----------------|  
|[map::const_iterator (STL/CLR)](#const_iterator)|Typ konstantního iterátoru řízené sekvence|  
|[map::const_reference (STL/CLR)](#const_reference)|Typ konstantního odkazu na prvek|  
|[map::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|Typ konstantního zpětného iterátoru řízené sekvence.|  
|[map::difference_type (STL/CLR)](#difference_type)|Typ (může být podepsaná) vzdálenosti mezi dvěma prvky.|  
|[map::generic_container (STL/CLR)](#generic_container)|Typ obecné rozhraní pro kontejner.|  
|[map::generic_iterator (STL/CLR)](#generic_iterator)|Typ iterátoru pro obecné rozhraní pro kontejner.|  
|[map::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|Typ "reverse iterator" pro obecné rozhraní pro kontejner.|  
|[map::generic_value (STL/CLR)](#generic_value)|Typ elementu pro obecné rozhraní pro kontejner.|  
|[map::iterator (STL/CLR)](#iterator)|Typ iterátoru řízené sekvence|  
|[map::key_compare (STL/CLR)](#key_compare)|Pořadí delegáta pro dva klíče.|  
|[map::key_type (STL/CLR)](#key_type)|Typ klíče řazení|  
|[map::mapped_type (STL/CLR)](#mapped_type)|Typ mapované hodnoty přiřazené ke každému klíči.|  
|[map::reference (STL/CLR)](#reference)|Typ odkazu na prvek|  
|[map::reverse_iterator (STL/CLR)](#reverse_iterator)|Typ "reverse iterator" pro řízenou sekvenci.|  
|[map::size_type (STL/CLR)](#size_type)|Typ vzdálenosti (nezáporné) mezi dvěma prvky.|  
|[map::value_compare (STL/CLR)](#value_compare)|Pořadí delegáta pro dvě hodnoty prvků.|  
|[map::value_type (STL/CLR)](#value_type)|Typ prvku|  
  
|Členská funkce|Popis|  
|---------------------|-----------------|  
|[map::begin (STL/CLR)](#begin)|Určuje začátek řízené sekvence.|  
|[map::clear (STL/CLR)](#clear)|Odebere všechny prvky.|  
|[map::count (STL/CLR)](#count)|Vrátí počet prvků odpovídající zadanému klíči.|  
|[map::empty (STL/CLR)](#empty)|Zkouší, zda nejsou přítomny žádné prvky.|  
|[map::end (STL/CLR)](#end)|Určuje konec řízené sekvence.|  
|[map::equal_range (STL/CLR)](#equal_range)|Najde rozsah, který odpovídá zadanému klíči.|  
|[map::erase (STL/CLR)](#erase)|Odebere prvky v určených pozicích.|  
|[map::find (STL/CLR)](#find)|Vyhledá prvek, který odpovídá zadanému klíči.|  
|[map::insert (STL/CLR)](#insert)|Přidá prvky.|  
|[map::key_comp (STL/CLR)](#key_comp)|Zkopíruje pořadí delegáta pro dva klíče.|  
|[map::lower_bound (STL/CLR)](#lower_bound)|Vyhledá počátek rozsahu, který odpovídá zadanému klíči.|  
|[map::make_value (STL/CLR)](#make_value)|Vytvoří objekt hodnoty.|  
|[map::map (STL/CLR)](#map)|Sestaví objekt kontejneru.|  
|[map::rbegin (STL/CLR)](#rbegin)|Určuje začátek řízené obrácené sekvenci.|  
|[map::rend (STL/CLR)](#rend)|Určuje konec řízené obrácené sekvenci.|  
|[map::size (STL/CLR)](#size)|Spočítá počet prvků.|  
|[map::swap (STL/CLR)](#swap)|Zamění obsah dvou kontejnerů.|  
|[map::to_array (STL/CLR)](#to_array)|Zkopíruje do nového pole řízené sekvence.|  
|[map::upper_bound (STL/CLR)](#upper_bound)|Najde konec rozsahu, který odpovídá zadanému klíči.|  
|[map::value_comp (STL/CLR)](#value_comp)|Zkopíruje pořadí delegáta pro dvě hodnoty prvků.|  
  
|Operátor|Popis|  
|--------------|-----------------|  
|[map::operator= (STL/CLR)](#op_as)|Nahradí řízené sekvence.|  
|[map::operator(STL/CLR)](#op)|Mapuje klíč na její přidružené mapované hodnoty.|  
|[operator!= (map) (STL/CLR)](#op_neq)|Určuje, zda `map` není roven jinému objektu `map` objektu.|  
|[operator< (map) (STL/CLR)](#op_lt)|Určuje, zda `map` je menší než jiný objekt `map` objektu.|  
|[operator<= (map) (STL/CLR)](#op_lteq)|Určuje, zda `map` objekt je menší nebo rovna jiné `map` objektu.|  
|[operator== (map) (STL/CLR)](#op_eq)|Určuje, zda `map` je roven jinému objektu `map` objektu.|  
|[operator> (map) (STL/CLR)](#op_gt)|Určuje, zda `map` je větší než jiný objekt `map` objektu.|  
|[operator>= (map) (STL/CLR)](#op_gteq)|Určuje, zda `map` objekt je větší než nebo roven jinému `map` objektu.|  
  
## <a name="interfaces"></a>Rozhraní  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Duplicitní objektu.|  
|<xref:System.Collections.IEnumerable>|Pořadí mezi prvky.|  
|<xref:System.Collections.ICollection>|Údržba skupiny prvků.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Pořadí pomocí zadané elementy.|  
|<xref:System.Collections.Generic.ICollection%601>|Údržba skupiny zadané elementy.|  
|<xref:System.Collections.Generic.IDictionary%602>|Údržba skupiny {klíč, hodnota} dvojice.|  
|ITree < klíč, hodnota >|Udržujte obecný kontejneru.|  
  
## <a name="remarks"></a>Poznámky  
 Objekt přiděluje a uvolňuje úložiště pro sekvenci, ovládací prvky jako jednotlivé uzly. Vloží prvky do (téměř) s vyrovnáváním strom, který udržuje seřazený tím, že změna vazby mezi uzly, nikdy zkopírováním obsah jednoho uzlu do jiného. To znamená, že můžete vložit a odebrat elementy volně bez narušení zbývající prvky.  
  
 Objekt seřadí sekvence pomocí volání uloženého delegáta objekt typu [map::key_compare (STL/CLR)](../dotnet/map-key-compare-stl-clr.md). Při vytvoření objektu map; můžete zadat objekt uložené delegáta Pokud chcete zadat žádný objekt. delegát, výchozí hodnota je porovnání `operator<(key_type, key_type)`. Přístup k tomuto uloženého objektu voláním členské funkce [map::key_comp (STL/CLR)](../dotnet/map-key-comp-stl-clr.md)`()`.  
  
 Takový objekt delegáta musí uložit přísné slabé seřazení klíčů typu [map::key_type (STL/CLR)](../dotnet/map-key-type-stl-clr.md). To znamená pro jakékoli dva klíče `X` a `Y`:  
  
 `key_comp()(X, Y)` Vrátí výsledek stejný datový typ Boolean při každém volání.  
  
 Pokud `key_comp()(X, Y)` má hodnotu true, pak `key_comp()(Y, X)` musí mít hodnotu false.  
  
 Pokud `key_comp()(X, Y)` má hodnotu true, pak `X` říká, že je řazen před `Y`.  
  
 Pokud `!key_comp()(X, Y) && !key_comp()(Y, X)` má hodnotu true, pak `X` a `Y` se říká, že mají ekvivalentní řazení.  
  
 Pro libovolný element `X` , která předchází `Y` v řízené sekvenci `key_comp()(Y, X)` má hodnotu false. (Pro výchozí objekt delegáta, klíče nikdy snížení hodnoty.) Na rozdíl od třídy šablony [mapy](../dotnet/map-stl-clr.md), objekt třídy šablony `map` nevyžaduje, aby byly jedinečné klíče pro všechny elementy. (Dva nebo více klíčů může mít odpovídající řazení.)  
  
 Každý prvek obsahuje samostatný klíč a hodnotu pro mapovanou. Sekvence je reprezentována způsobem, který umožňuje vyhledávání, vkládání a odstranění libovolný prvek s počtem operací úměrný logaritmu počtu prvků v sekvenci (logaritmické čas). Vkládání prvků navíc nezruší platnost žádných iterátorů a odstranění prvku zruší platnost pouze těch iterátorů, které odkazují na odstraněný prvek.  
  
 Mapu podporuje obousměrné iterátory, což znamená, že přejdete na sousedící prvky zadaný iterátor, který určuje elementu v řízené sekvenci. Speciální hlavního uzlu odpovídá iterátorů vrácené [map::end (STL/CLR)](../dotnet/map-end-stl-clr.md)`()`. Tento iterátor, který má přístup po posledním prvku v řízené sekvenci lze snížit, pokud jsou k dispozici. Můžete zvýšit mapy iterátor pro přístup k hlavnímu uzlu a budou pak porovnat rovna `end()`. Nelze přistoupit přes ukazatel vrátí iterátor, ale `end()`.  
  
 Všimněte si, že nemůže odkazovat na element mapy přímo zadané pozici číselné –, který vyžaduje iterátor náhodného přístupu.  
  
 Iterátor mapy uloží popisovač do uzlu přidružené map, který je pak uloží popisovač pro jeho přiřazeným kontejnerem. Iterátory lze použít pouze objekty, které přiřazeným kontejnerem. Iterátor mapy platná tak dlouho, dokud jeho přidružené mapy uzel souvisí s některé mapy. Kromě toho je platný iterátoru přesměrovat – slouží k přístupu nebo změnit hodnotu prvku jmenuje--tak dlouho, dokud se nerovná `end()`.  
  
 Smazání nebo odstranění prvku volá destruktor pro jeho uložené hodnotě. Zničení kontejneru vymaže všechny prvky. Kontejner, jehož typ prvku je třídy ref class tak, zajišťuje, že žádné elementy něj kontejneru. Mějte na paměti, ale, že kontejner zpracovává nemá *není* zničit jeho prvků.  
  
## <a name="members"></a>Členové

## <a name="begin"></a> map::begin (STL/CLR)
Určuje začátek řízené sekvence.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
iterator begin();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí obousměrný iterátor, který určuje první prvek řízenou sekvenci nebo přesně za konec k prázdné sekvenci. Můžete ji použít k získání iterátor, který určuje `current` začátek řízené sekvence, ale jeho stav můžete změnit, pokud se změní délka řízené sekvence.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_map_begin.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// inspect first two items   
    Mymap::iterator it = c1.begin();   
    System::Console::WriteLine("*begin() = [{0} {1}]",   
        it->first, it->second);   
    ++it;   
    System::Console::WriteLine("*++begin() = [{0} {1}]",   
        it->first, it->second);   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
*begin() = [a 1]  
*++begin() = [b 2]  
```  

## <a name="clear"></a> map::clear (STL/CLR)
Odebere všechny prvky.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
void clear();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce efektivně volá [map::erase (STL/CLR)](../dotnet/map-erase-stl-clr.md) `(` [map::begin (STL/CLR)](../dotnet/map-begin-stl-clr.md) `(),` [map::end (STL/CLR)](../dotnet/map-end-stl-clr.md) `())`. Použijete ji k zajištění, že je prázdná řízené sekvence.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_map_clear.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
  
// display contents " [a 1] [b 2]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
size() = 0  
 [a 1] [b 2]  
size() = 0  
```  

## <a name="const_iterator"></a> map::const_iterator (STL/CLR)
Typ konstantního iterátoru řízené sekvence  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef T2 const_iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ popisuje objekt neurčeného typu `T2` , který může sloužit jako konstantní obousměrného iterátoru řízené sekvence.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_map_const_iterator.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    Mymap::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        System::Console::Write(" [{0} {1}]", cit->first, cit->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```  

## <a name="const_reference"></a> map::const_reference (STL/CLR)
Typ konstantního odkazu na prvek  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef value_type% const_reference;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ, který popisuje konstantní odkaz na element.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_map_const_reference.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    Mymap::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        {   // get a const reference to an element   
        Mymap::const_reference cref = *cit;   
        System::Console::Write(" [{0} {1}]", cref->first, cref->second);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```  

## <a name="const_reverse_iterator"></a> map::const_reverse_iterator (STL/CLR)
Typ konstantního zpětného iterátoru řízené sekvence...  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef T4 const_reverse_iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ popisuje objekt neurčeného typu `T4` , který může sloužit jako konstantní zpětného iterátoru řízené sekvence.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_map_const_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]" reversed   
    Mymap::const_reverse_iterator crit = c1.rbegin();   
    for (; crit != c1.rend(); ++crit)   
        System::Console::Write(" [{0} {1}]", crit->first, crit->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
[c 3] [b 2] [a 1]  
```  

## <a name="count"></a> map::Count (STL/CLR)
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
// cliext_map_count.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("count(L'A') = {0}", c1.count(L'A'));   
    System::Console::WriteLine("count(L'b') = {0}", c1.count(L'b'));   
    System::Console::WriteLine("count(L'C') = {0}", c1.count(L'C'));   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
count(L'A') = 0  
count(L'b') = 1  
count(L'C') = 0  
```  

## <a name="difference_type"></a> map::difference_type (STL/CLR)
Typ vzdálenosti se znaménkem mezi dvěma prvky.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef int difference_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ, který popisuje element může být záporný počet.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_map_difference_type.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// compute positive difference   
    Mymap::difference_type diff = 0;   
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)   
        ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
  
// compute negative difference   
    diff = 0;   
    for (Mymap::iterator it = c1.end(); it != c1.begin(); --it)   
        --diff;   
    System::Console::WriteLine("begin()-end() = {0}", diff);   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
end()-begin() = 3  
begin()-end() = -3  
```  

## <a name="empty"></a> map::Empty (STL/CLR)
Zkouší, zda nejsou přítomny žádné prvky.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
bool empty();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí hodnotu true pro prázdnou řízenou sekvenci. Je ekvivalentní [map::size (STL/CLR)](../dotnet/map-size-stl-clr.md)`() == 0`. Použijete ji k ověření, zda na mapě je prázdný.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_map_empty.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
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
 [a 1] [b 2] [c 3]  
size() = 3  
empty() = False  
size() = 0  
empty() = True  
```  

## <a name="end"></a> map::end (STL/CLR)
Určuje konec řízené sekvence.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
iterator end();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí obousměrný iterátor, který ukazuje za konec řízené sekvence. Můžete ji použít k získání iterátor, který určuje konec řízené sekvence; jeho stav kódu ne změnit, pokud se změní délka řízené sekvence.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_map_end.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// inspect last two items   
    Mymap::iterator it = c1.end();   
    --it;   
    --it;   
    System::Console::WriteLine("*-- --end() = [{0} {1}]",   
        it->first, it->second);   
    ++it;   
    System::Console::WriteLine("*--end() = [{0} {1}]",   
        it->first, it->second);   
    return (0);   
    }  
```  

## <a name="equal_range"></a> map::equal_range (STL/CLR)
Najde rozsah, který odpovídá zadanému klíči.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
cliext::pair<iterator, iterator> equal_range(key_type key);  
```  
  
#### <a name="parameters"></a>Parametry  
 *Klíč*  
 Hodnota klíče pro hledání.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí pár iterátorů `cliext::pair<iterator, iterator>(` [map::lower_bound (STL/CLR)](../dotnet/map-lower-bound-stl-clr.md) `(key),` [map::upper_bound (STL/CLR)](../dotnet/map-upper-bound-stl-clr.md)`(key))`. Použijete ji k určení rozsahu prvků v řízené sekvenci aktuálně, které odpovídají zadanému klíči.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_map_equal_range.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
typedef Mymap::pair_iter_iter Pairii;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// display results of failed search   
    Pairii pair1 = c1.equal_range(L'x');   
    System::Console::WriteLine("equal_range(L'x') empty = {0}",   
        pair1.first == pair1.second);   
  
// display results of successful search   
    pair1 = c1.equal_range(L'b');   
    for (; pair1.first != pair1.second; ++pair1.first)   
        System::Console::Write(" [{0} {1}]",   
            pair1.first->first, pair1.first->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
equal_range(L'x') empty = True  
 [b 2]  
```  
  
## <a name="erase"></a> map::Erase (STL/CLR)
Odebere prvky v určených pozicích.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
bool erase(key_type key)  
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
 První členská funkce odstraní prvek řízené sekvence, na které odkazuje *kde*a vrátí iterátor, který určuje první prvek zbývající za prvkem, který odebere, nebo [map::end (STL/CLR) ](../dotnet/map-end-stl-clr.md) `()` Pokud žádný takový prvek neexistuje. Použijete ji k odebrání jeden element.  
  
 Druhá členská funkce odebere prvky řízené sekvence v rozsahu [`first`, `last`) a vrátí iterátor, který určuje první prvek zbývající za všemi odstraněnými prvky, nebo `end()` Pokud žádný takový prvek existuje... Použijete ji k odebrání nula nebo více souvislých prvků.  
  
 Třetí členská funkce odstraní libovolný prvek řízenou sekvenci, jehož klíč má ekvivalentní řazení na *klíč*a vrátí počet prvků, které jsou odebrány. Použijete ho odebrat a spočítat všechny elementy, které odpovídají zadanému klíči.  
  
 Každý prvek mazání trvá určitou dobu úměrný logaritmu počtu prvků v řízené sekvenci.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_map_erase.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    cliext::map<wchar_t, int> c1;   
    c1.insert(cliext::map<wchar_t, int>::make_value(L'a', 1));   
    c1.insert(cliext::map<wchar_t, int>::make_value(L'b', 2));   
    c1.insert(cliext::map<wchar_t, int>::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (cliext::map<wchar_t, int>::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// erase an element and reinspect   
    cliext::map<wchar_t, int>::iterator it =   
        c1.erase(c1.begin());   
    System::Console::WriteLine("erase(begin()) = [{0} {1}]",   
        it->first, it->second);   
  
// add elements and display " b c d e"   
    c1.insert(cliext::map<wchar_t, int>::make_value(L'd', 4));   
    c1.insert(cliext::map<wchar_t, int>::make_value(L'e', 5));   
    for each (cliext::map<wchar_t, int>::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// erase all but end   
    it = c1.end();   
    it = c1.erase(c1.begin(), --it);   
    System::Console::WriteLine("erase(begin(), end()-1) = [{0} {1}]",   
        it->first, it->second);   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// erase end   
    System::Console::WriteLine("erase(L'x') = {0}", c1.erase(L'x'));   
    System::Console::WriteLine("erase(L'e') = {0}", c1.erase(L'e'));   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
erase(begin()) = [b 2]  
 [b 2] [c 3] [d 4] [e 5]  
erase(begin(), end()-1) = [e 5]  
size() = 1  
erase(L'x') = 0  
erase(L'e') = 1  
```  
  
## <a name="find"></a> map::Find (STL/CLR)
Vyhledá prvek, který odpovídá zadanému klíči.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
iterator find(key_type key);  
```  
  
#### <a name="parameters"></a>Parametry  
 *Klíč*  
 Hodnota klíče pro hledání.  
  
### <a name="remarks"></a>Poznámky  
 Pokud má alespoň jeden element v řízené sekvenci s odpovídající řazení *klíč*, členská funkce vrátí iterátor určit jeden z těchto elementů; v opačném případě vrátí [map::end (STL/CLR)](../dotnet/map-end-stl-clr.md)`()`. Použijete ji k aktuálně vyhledejte elementu v řízené sekvenci, která odpovídá zadanému klíči.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_map_find.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("find {0} = {1}",   
        L'A', c1.find(L'A') != c1.end());   
  
    Mymap::iterator it = c1.find(L'b');   
    System::Console::WriteLine("find {0} = [{1} {2}]",   
        L'b', it->first, it->second);   
  
    System::Console::WriteLine("find {0} = {1}",   
        L'C', c1.find(L'C') != c1.end());   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
find A = False  
find b = [b 2]  
find C = False  
```  

## <a name="generic_container"></a> map::generic_container (STL/CLR)
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
// cliext_map_generic_container.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Mymap::generic_container^ gc1 = %c1;   
    for each (Mymap::value_type elem in gc1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    gc1->insert(Mymap::make_value(L'd', 4));   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// modify original and display generic   
    c1.insert(Mymap::make_value(L'e', 5));   
    for each (Mymap::value_type elem in gc1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
[a 1] [b 2] [c 3]  
[a 1] [b 2] [c 3]  
[a 1] [b 2] [c 3] [d 4]  
[a 1] [b 2] [c 3] [d 4] [e 5]  
```  

## <a name="generic_iterator"></a> map::generic_iterator (STL/CLR)
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
// cliext_map_generic_iterator.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Mymap::generic_container^ gc1 = %c1;   
    for each (Mymap::value_type elem in gc1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Mymap::generic_iterator gcit = gc1->begin();   
    Mymap::generic_value gcval = *gcit;   
    System::Console::Write(" [{0} {1}]", gcval->first, gcval->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
[a 1] [b 2] [c 3]  
[a 1] [b 2] [c 3]  
[a 1]  
```  

## <a name="generic_reverse_iterator"></a> map::generic_reverse_iterator (STL/CLR)
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
// cliext_map_generic_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Mymap::generic_container^ gc1 = %c1;   
    for each (Mymap::value_type elem in gc1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Mymap::generic_reverse_iterator gcit = gc1->rbegin();   
    Mymap::generic_value gcval = *gcit;   
    System::Console::WriteLine(" [{0} {1}]", gcval->first, gcval->second);   
    return (0);   
    }  
```  
  
```Output  
[a 1] [b 2] [c 3]  
[a 1] [b 2] [c 3]  
[c 3]  
```  

## <a name="generic_value"></a> map::generic_value (STL/CLR)
Typ elementu pro použití s obecné rozhraní pro kontejner.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef GValue generic_value;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ, který popisuje objekt typu `GValue` hodnoty uložené elementu pro použití s obecné rozhraní pro tuto třídu šablony kontejneru, který popisuje.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_map_generic_value.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Mymap::generic_container^ gc1 = %c1;   
    for each (Mymap::value_type elem in gc1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Mymap::generic_iterator gcit = gc1->begin();   
    Mymap::generic_value gcval = *gcit;   
    System::Console::WriteLine(" [{0} {1}]", gcval->first, gcval->second);   
    return (0);   
    }  
```  
  
```Output  
[a 1] [b 2] [c 3]  
[a 1] [b 2] [c 3]  
[a 1]  
```  

## <a name="insert"></a> map::Insert (STL/CLR)
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
// cliext_map_insert.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
typedef Mymap::pair_iter_bool Pairib;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert a single value, unique and duplicate   
// insert a single value, success and failure   
    Pairib pair1 = c1.insert(Mymap::make_value(L'x', 24));   
    System::Console::WriteLine("insert([L'x' 24]) = [[{0} {1}] {2}]",   
        pair1.first->first, pair1.first->second, pair1.second);   
  
    pair1 = c1.insert(Mymap::make_value(L'b', 2));   
    System::Console::WriteLine("insert([L'b' 2]) = [[{0} {1}] {2}]",   
        pair1.first->first, pair1.first->second, pair1.second);   
  
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert a single value with hint   
    Mymap::iterator it =   
        c1.insert(c1.begin(), Mymap::make_value(L'y', 25));   
    System::Console::WriteLine("insert(begin(), [L'y' 25]) = [{0} {1}]",   
        it->first, it->second);   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    Mymap c2;   
    it = c1.end();   
    c2.insert(c1.begin(), --it);   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    Mymap c3;   
    c3.insert(   // NOTE: cast is not needed   
        (System::Collections::Generic::   
            IEnumerable<Mymap::value_type>^)%c1);   
    for each (Mymap::value_type elem in c3)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
insert([L'x' 24]) = [[x 24] True]  
insert([L'b' 2]) = [[b 2] False]  
 [a 1] [b 2] [c 3] [x 24]  
insert(begin(), [L'y' 25]) = [y 25]  
 [a 1] [b 2] [c 3] [x 24] [y 25]  
 [a 1] [b 2] [c 3] [x 24]  
 [a 1] [b 2] [c 3] [x 24] [y 25]  
```  

## <a name="iterator"></a> map::iterator (STL/CLR)
Typ iterátoru řízené sekvence  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef T1 iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ popisuje objekt neurčeného typu `T1` , který může sloužit jako obousměrný iterátor, který řízené sekvence.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_map_iterator.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    Mymap::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" [{0} {1}]", it->first, it->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```  
  

## <a name="key_comp"></a> map::key_comp (STL/CLR)
Zkopíruje pořadí delegáta pro dva klíče.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
key_compare^key_comp();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí pořadí delegáta, který slouží k seřazení řízené sekvence. Použijete ji k porovnat dva klíče.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_map_key_comp.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    Mymap::key_compare^ kcomp = c1.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Mymap c2 = cliext::greater<wchar_t>();   
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

## <a name="key_compare"></a> map::key_compare (STL/CLR)
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
// cliext_map_key_compare.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    Mymap::key_compare^ kcomp = c1.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Mymap c2 = cliext::greater<wchar_t>();   
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

## <a name="key_type"></a> map::key_type (STL/CLR)
Typ klíče řazení  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro parametr šablony *klíč*.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_map_key_type.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]" using key_type   
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in key_type object   
        Mymap::key_type val = it->first;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
```  

## <a name="lower_bound"></a> map::lower_bound (STL/CLR)
Vyhledá počátek rozsahu, který odpovídá zadanému klíči.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
iterator lower_bound(key_type key);  
```  
  
#### <a name="parameters"></a>Parametry  
 *Klíč*  
 Hodnota klíče pro hledání.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce určuje první prvek `X` v řízené sekvenci, která má stejné pořadí na *klíč*. Pokud žádný takový prvek neexistuje, vrátí [map::end (STL/CLR)](../dotnet/map-end-stl-clr.md)`()`; v opačném případě vrátí iterátor, který určuje `X`. Použijete ji k aktuálně vyhledejte na začátek pořadí prvků v řízené sekvenci, které odpovídají zadanému klíči.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_map_lower_bound.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",   
        c1.lower_bound(L'x') == c1.end());   
  
    Mymap::iterator it = c1.lower_bound(L'a');   
    System::Console::WriteLine("*lower_bound(L'a') = [{0} {1}]",   
        it->first, it->second);   
    it = c1.lower_bound(L'b');   
    System::Console::WriteLine("*lower_bound(L'b') = [{0} {1}]",   
        it->first, it->second);   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
lower_bound(L'x')==end() = True  
*lower_bound(L'a') = [a 1]  
*lower_bound(L'b') = [b 2]  
```  

## <a name="make_value"></a> map::make_value (STL/CLR)
Vytvoří objekt hodnoty.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
static value_type make_value(key_type key, mapped_type mapped);  
```  
  
#### <a name="parameters"></a>Parametry  
 *Klíč*  
 Hodnota klíče používat.  
  
 *mapovat*  
 Mapovaná hledanou hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí `value_type` objekt, jehož klíč je *klíč* a jejichž mapované hodnoty se *namapované*. Použijete ji k vytvoření objektu vhodný pro použití s několika další členské funkce.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_map_make_value.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```  

## <a name="map"></a> map::map (STL/CLR)
Sestaví objekt kontejneru.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
map();  
explicit map(key_compare^ pred);  
map(map<Key, Mapped>% right);  
map(map<Key, Mapped>^ right);  
template<typename InIter>  
    mapmap(InIter first, InIter last);  
template<typename InIter>  
    map(InIter first, InIter last,  
        key_compare^ pred);  
map(System::Collections::Generic::IEnumerable<GValue>^ right);  
map(System::Collections::Generic::IEnumerable<GValue>^ right,  
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
  
 `map();`  
  
 Inicializuje výchozí řazení predikátu řízené sekvence bez prvků `key_compare()`. Použijete ji k určení prázdnou počáteční řízenou sekvenci, s výchozí řazení predikátu.  
  
 Konstruktor:  
  
 `explicit map(key_compare^ pred);`  
  
 Inicializuje řízené sekvence bez prvků pořadí predikátem *před*. Použít prázdnou počáteční řízenou sekvenci, určit se zadanou predikát pořadí.  
  
 Konstruktor:  
  
 `map(map<Key, Mapped>% right);`  
  
 Inicializuje řízené sekvence s pořadím [`right.begin()`, `right.end()`), s výchozí řazení predikátu. Můžete použít k určení počáteční řízené sekvence, která je kopii sekvence řízenou parametrem objekt map *správné*, s výchozí řazení predikátu.  
  
 Konstruktor:  
  
 `map(map<Key, Mapped>^ right);`  
  
 Inicializuje řízené sekvence s pořadím [`right->begin()`, `right->end()`), s výchozí řazení predikátu. Můžete použít k určení počáteční řízené sekvence, která je kopii sekvence řízenou parametrem objekt map *správné*, s výchozí řazení predikátu.  
  
 Konstruktor:  
  
 `template<typename InIter> map(InIter first, InIter last);`  
  
 Inicializuje řízené sekvence s pořadím [`first`, `last`), s výchozí řazení predikátu. Používejte aby řízené sekvence kopii jiné pořadí, s výchozí řazení predikátu.  
  
 Konstruktor:  
  
 `template<typename InIter> map(InIter first, InIter last, key_compare^ pred);`  
  
 Inicializuje řízené sekvence s pořadím [`first`, `last`), pořadí predikátem *před*. Použijete ji k vytvoření kopie jiné pořadí se zadanou predikát pořadí řízené sekvence.  
  
 Konstruktor:  
  
 `map(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 Inicializuje řízené sekvence s pořadí určeném enumerátor *správné*, s výchozí řazení predikátu. Použijete ji k vytvoření kopie jiné pořadí popsal čítače, s výchozí řazení predikátu řízené sekvence.  
  
 Konstruktor:  
  
 `map(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`  
  
 Inicializuje řízené sekvence s pořadí určeném enumerátor *správné*, pořadí predikátem *před*. Použijete ji k vytvoření kopie jiné pořadí popsal enumerátor se zadanou predikát pořadí řízené sekvence.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_map_construct.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
// construct an empty container   
    Mymap c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Mymap c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Mymap c3(c1.begin(), c1.end());   
    for each (Mymap::value_type elem in c3)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Mymap c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (Mymap::value_type elem in c4)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Mymap c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Mymap::value_type>^)%c3);   
    for each (Mymap::value_type elem in c5)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Mymap c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Mymap::value_type>^)%c3,   
                cliext::greater_equal<wchar_t>());   
    for each (Mymap::value_type elem in c6)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mymap c7(c4);   
    for each (Mymap::value_type elem in c7)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    Mymap c8(%c3);   
    for each (Mymap::value_type elem in c8)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
size() = 0  
 [a 1] [b 2] [c 3]  
size() = 0  
 [c 3] [b 2] [a 1]  
 [a 1] [b 2] [c 3]  
 [c 3] [b 2] [a 1]  
 [a 1] [b 2] [c 3]  
 [c 3] [b 2] [a 1]  
 [c 3] [b 2] [a 1]  
 [a 1] [b 2] [c 3]  
```  

## <a name="mapped_type"></a> map::mapped_type (STL/CLR)
Typ mapované hodnoty přiřazené ke každému klíči  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef Mapped mapped_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro parametr šablony *mapované*.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_map_mapped_type.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]" using mapped_type   
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in mapped_type object   
        Mymap::mapped_type val = it->second;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
1 2 3  
```  
  
## <a name="op_as"></a> map::Operator = (STL/CLR)
Nahradí řízené sekvence.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
map<Key, Mapped>% operator=(map<Key, Mapped>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *doprava*  
 Kontejner pro kopírování.  
  
### <a name="remarks"></a>Poznámky  
 Kopie členský operátor *správné* na objekt, vrátí `*this`. Můžete použít k nahraďte kopii řízené sekvence v řízené sekvenci *správné*.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_map_operator_as.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mymap c2;   
    c2 = c1;   
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
[a 1] [b 2] [c 3]  
[a 1] [b 2] [c 3]  
```  

## <a name="op"></a> map::Operator(STL/CLR)
Mapuje klíč na její přidružené mapované hodnoty.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
mapped_type operator[](key_type key);  
```  
  
#### <a name="parameters"></a>Parametry  
 *Klíč*  
 Hodnota klíče pro hledání.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce přejeme vyhledání elementu s odpovídající řazení na *klíč*. Pokud jeden najde, vrátí související namapovanou hodnotu; v opačném případě vloží `value_type(key, mapped_type())` a vrátí přidružený namapované hodnotu (výchozí). Použijte ho k vyhledání mapované hodnoty zadané jeho přidružený klíč a ujistěte se, že položka existuje pro klíč, pokud žádná se nenašla.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_map_operator_sub.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("c1[{0}] = {1}",   
        L'A', c1[L'A']);   
    System::Console::WriteLine("c1[{0}] = {1}",   
        L'b', c1[L'b']);   
  
// redisplay altered contents   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// alter mapped values and redisplay   
    c1[L'A'] = 10;   
    c1[L'c'] = 13;   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
c1[A] = 0  
c1[b] = 2  
 [A 0] [a 1] [b 2] [c 3]  
 [A 10] [a 1] [b 2] [c 13]  
```  

## <a name="rbegin"></a> map::rbegin (STL/CLR)
Určuje začátek řízené obrácené sekvenci.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
reverse_iterator rbegin();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí zpětný iterátor, který určuje poslední prvek řízenou sekvenci nebo hned za začátku k prázdné sekvenci. Proto, označí `beginning` reverzní pořadí. Můžete ji použít k získání iterátor, který určuje `current` začátek řízené sekvence viděli v obráceném pořadí, ale jeho stav můžete změnit, pokud se změní délka řízené sekvence.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_map_rbegin.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// inspect first two items in reversed sequence   
    Mymap::reverse_iterator rit = c1.rbegin();   
    System::Console::WriteLine("*rbegin() = [{0} {1}]",   
        rit->first, rit->second);   
    ++rit;   
    System::Console::WriteLine("*++rbegin() = [{0} {1}]",   
        rit->first, rit->second);   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
*rbegin() = [c 3]  
*++rbegin() = [b 2]  
```  

## <a name="reference"></a> map::Reference (STL/CLR)
Typ odkazu na prvek  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef value_type% reference;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ, který popisuje odkaz na element.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_map_reference.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    Mymap::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        {   // get a reference to an element   
        Mymap::reference ref = *it;   
        System::Console::Write(" [{0} {1}]", ref->first, ref->second);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
[a 1] [b 2] [c 3]  
``` 

## <a name="rend"></a> map::rend (STL/CLR)
Určuje konec řízené obrácené sekvenci.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
reverse_iterator rend();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí "reverse iterator", který ukazuje za začátek řízené sekvence. Proto, označí `end` reverzní pořadí. Můžete ji použít k získání iterátor, který určuje `current` konec řízené sekvence viděli v obráceném pořadí, ale jeho stav můžete změnit, pokud se změní délka řízené sekvence.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_map_rend.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// inspect first two items in reversed sequence   
    Mymap::reverse_iterator rit = c1.rend();   
    --rit;   
    --rit;   
    System::Console::WriteLine("*-- --rend() = [{0} {1}]",   
        rit->first, rit->second);   
    ++rit;   
    System::Console::WriteLine("*--rend() = [{0} {1}]",   
        rit->first, rit->second);   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
*-- --rend() = [b 2]  
*--rend() = [a 1]  
```   

## <a name="reverse_iterator"></a> map::reverse_iterator (STL/CLR)
Typ "reverse iterator" pro řízenou sekvenci.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
typedef T3 reverse_iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ popisuje objekt neurčeného typu `T3` , který může sloužit jako "reverse iterator" pro řízenou sekvenci.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_map_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]" reversed   
    Mymap::reverse_iterator rit = c1.rbegin();   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" [{0} {1}]", rit->first, rit->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
[c 3] [b 2] [a 1]  
```  

## <a name="size"></a> map::size (STL/CLR)
Spočítá počet prvků.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
size_type size();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí délku objektu řízené sekvence. Použijete ji k určení počtu prvků v řízené sekvenci aktuálně. Pokud vás zajímá, jestli je pořadí má nenulovou velikost, naleznete v tématu [map::empty (STL/CLR)](../dotnet/map-empty-stl-clr.md)`()`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_map_size.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0} after clearing", c1.size());   
  
// add elements and clear again   
    c1.insert(Mymap::make_value(L'd', 4));   
    c1.insert(Mymap::make_value(L'e', 5));   
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
size() = 0 after clearing  
size() = 2 after adding 2  
```  

## <a name="size_type"></a> map::size_type (STL/CLR)
Typ vzdálenosti se znaménkem mezi dvěma elementu.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef int size_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ, který popisuje počet prvků záporná.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_map_size_type.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// compute positive difference   
    Mymap::size_type diff = 0;   
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)   
        ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
end()-begin() = 3  
```  
  
## <a name="swap"></a> map::swap (STL/CLR)
Zamění obsah dvou kontejnerů.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
void swap(map<Key, Mapped>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *doprava*  
 Kontejner pro obsah s.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce Zamění řízené sekvence mezi `this` a *správné*. Provádí se v konstantním času a vyvolá žádné výjimky. Můžete použít jako rychlý způsob, jak Zamění obsah dvou kontejnerů.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_map_swap.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct another container with repetition of values   
    Mymap c2;   
    c2.insert(Mymap::make_value(L'd', 4));   
    c2.insert(Mymap::make_value(L'e', 5));   
    c2.insert(Mymap::make_value(L'f', 6));   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// swap and redisplay   
    c1.swap(c2);   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
[a 1] [b 2] [c 3]  
[d 4] [e 5] [f 6]  
[d 4] [e 5] [f 6]  
[a 1] [b 2] [c 3]  
```  

## <a name="to_array"></a> map::to_array (STL/CLR)
Zkopíruje do nového pole řízené sekvence.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
cli::array<value_type>^ to_array();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí pole obsahující řízené sekvence. Použijete ji získat kopii řízenou sekvenci pole formuláře.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_map_to_array.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// copy the container and modify it   
    cli::array<Mymap::value_type>^ a1 = c1.to_array();   
  
    c1.insert(Mymap::make_value(L'd', 4));   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// display the earlier array copy   
    for each (Mymap::value_type elem in a1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
[a 1] [b 2] [c 3] [d 4]  
[a 1] [b 2] [c 3]  
```  

## <a name="upper_bound"></a> map::upper_bound (STL/CLR)
Najde konec rozsahu, který odpovídá zadanému klíči.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
iterator upper_bound(key_type key);  
```  
  
#### <a name="parameters"></a>Parametry  
 *Klíč*  
 Hodnota klíče pro hledání.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce určuje poslední prvek `X` v řízené sekvenci, která má stejné pořadí na *klíč*. Pokud žádný takový prvek neexistuje, nebo pokud `X` je po posledním prvku v řízené sekvenci vrátí [map::end (STL/CLR)](../dotnet/map-end-stl-clr.md)`()`; v opačném případě vrátí iterátor, který určuje prvního prvku mimo `X`. Pomocí aktuálně najít konec pořadí prvků v řízené sekvenci, které odpovídají zadanému klíči.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_map_upper_bound.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",   
        c1.upper_bound(L'x') == c1.end());   
  
    Mymap::iterator it = c1.upper_bound(L'a');   
    System::Console::WriteLine("*upper_bound(L'a') = [{0} {1}]",   
        it->first, it->second);   
    it = c1.upper_bound(L'b');   
    System::Console::WriteLine("*upper_bound(L'b') = [{0} {1}]",   
        it->first, it->second);   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
upper_bound(L'x')==end() = True  
*upper_bound(L'a') = [b 2]  
*upper_bound(L'b') = [c 3]  
```  

## <a name="value_comp"></a> map::value_comp (STL/CLR)
Zkopíruje pořadí delegáta pro dvě hodnoty prvků.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
value_compare^ value_comp();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí pořadí delegáta, který slouží k seřazení řízené sekvence. Použijete ji k porovnat dvě hodnoty prvků.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_map_value_comp.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    Mymap::value_compare^ kcomp = c1.value_comp();   
  
    System::Console::WriteLine("compare([L'a', 1], [L'a', 1]) = {0}",   
        kcomp(Mymap::make_value(L'a', 1),   
            Mymap::make_value(L'a', 1)));   
    System::Console::WriteLine("compare([L'a', 1], [L'b', 2]) = {0}",   
        kcomp(Mymap::make_value(L'a', 1),   
            Mymap::make_value(L'b', 2)));   
    System::Console::WriteLine("compare([L'b', 2], [L'a', 1]) = {0}",   
        kcomp(Mymap::make_value(L'b', 2),   
            Mymap::make_value(L'a', 1)));   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
compare([L'a', 1], [L'a', 1]) = False  
compare([L'a', 1], [L'b', 2]) = True  
compare([L'b', 2], [L'a', 1]) = False  
```  
  
## <a name="value_compare"></a> map::value_compare (STL/CLR)
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
// cliext_map_value_compare.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    Mymap::value_compare^ kcomp = c1.value_comp();   
  
    System::Console::WriteLine("compare([L'a', 1], [L'a', 1]) = {0}",   
        kcomp(Mymap::make_value(L'a', 1),   
            Mymap::make_value(L'a', 1)));   
    System::Console::WriteLine("compare([L'a', 1], [L'b', 2]) = {0}",   
        kcomp(Mymap::make_value(L'a', 1),   
            Mymap::make_value(L'b', 2)));   
    System::Console::WriteLine("compare([L'b', 2], [L'a', 1]) = {0}",   
        kcomp(Mymap::make_value(L'b', 2),   
            Mymap::make_value(L'a', 1)));   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
compare([L'a', 1], [L'a', 1]) = False  
compare([L'a', 1], [L'b', 2]) = True  
compare([L'b', 2], [L'a', 1]) = False  
```  

## <a name="value_type"></a> map::value_type (STL/CLR)
Typ prvku  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef generic_value value_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro `generic_value`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_map_value_type.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]" using value_type   
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in value_type object   
        Mymap::value_type val = *it;   
        System::Console::Write(" [{0} {1}]", val->first, val->second);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```  

## <a name="op_neq"></a> Operator! = (map) (STL/CLR)
Seznam není rovno porovnání.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Key,  
    typename Mapped>  
    bool operator!=(map<Key, Mapped>% left,  
        map<Key, Mapped>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *doleva*  
 Levé kontejner k porovnání.  
  
 *doprava*  
 Správném kontejneru pro porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí funkci operátoru `!(left == right)`. Pomocí něho můžete testovat, zda *levé* není stejný jako seřazené *správné* když jsou dvě mapy porovnání elementu pomocí elementu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_map_operator_ne.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mymap c2;   
    c2.insert(Mymap::make_value(L'a', 1));   
    c2.insert(Mymap::make_value(L'b', 2));   
    c2.insert(Mymap::make_value(L'd', 4));   
  
// display contents " [a 1] [b 2] [d 4]"   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] != [a b c] is {0}",   
        c1 != c1);   
    System::Console::WriteLine("[a b c] != [a b d] is {0}",   
        c1 != c2);   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
 [a 1] [b 2] [d 4]  
[a b c] != [a b c] is False  
[a b c] != [a b d] is True  
```  
  
## <a name="op_lt"></a> operátor&lt; (map) (STL/CLR)
Seznam menší než porovnání.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Key,  
    typename Mapped>  
    bool operator<(map<Key, Mapped>% left,  
        map<Key, Mapped>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *doleva*  
 Levé kontejner k porovnání.  
  
 *doprava*  
 Správném kontejneru pro porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Operátoru funkce vrátí hodnota true v případě, pro nejnižší pozici `i` pro kterou `!(right[i] < left[i])` je také hodnotu true, který `left[i] < right[i]`. V opačném případě vrátí `left->size() < right->size()` pomocí něho můžete testovat, zda *levé* je řazen před *správné* když jsou dvě mapy porovnání elementu pomocí elementu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_map_operator_lt.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mymap c2;   
    c2.insert(Mymap::make_value(L'a', 1));   
    c2.insert(Mymap::make_value(L'b', 2));   
    c2.insert(Mymap::make_value(L'd', 4));   
  
// display contents " [a 1] [b 2] [d 4]"   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] < [a b c] is {0}",   
        c1 < c1);   
    System::Console::WriteLine("[a b c] < [a b d] is {0}",   
        c1 < c2);   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
 [a 1] [b 2] [d 4]  
[a b c] < [a b c] is False  
[a b c] < [a b d] is True  
```  

## <a name="op_lteq"></a> operátor&lt;= (map) (STL/CLR)
Seznam menší nebo rovna porovnání.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Key,  
    typename Mapped>  
    bool operator<=(map<Key, Mapped>% left,  
        map<Key, Mapped>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *doleva*  
 Levé kontejner k porovnání.  
  
 *doprava*  
 Správném kontejneru pro porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí funkci operátoru `!(right < left)`. Pomocí něho můžete testovat, zda *levé* není seřazené po *správné* když jsou dvě mapy porovnání elementu pomocí elementu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_map_operator_le.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mymap c2;   
    c2.insert(Mymap::make_value(L'a', 1));   
    c2.insert(Mymap::make_value(L'b', 2));   
    c2.insert(Mymap::make_value(L'd', 4));   
  
// display contents " [a 1] [b 2] [d 4]"   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] <= [a b c] is {0}",   
        c1 <= c1);   
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",   
        c2 <= c1);   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
 [a 1] [b 2] [d 4]  
[a b c] <= [a b c] is True  
[a b d] <= [a b c] is False  
```  

## <a name="op_eq"></a> Operator == (map) (STL/CLR)
Porovnání rovna seznamu.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Key,  
    typename Mapped>  
    bool operator==(map<Key, Mapped>% left,  
        map<Key, Mapped>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *doleva*  
 Levé kontejner k porovnání.  
  
 *doprava*  
 Správném kontejneru pro porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Funkce operátoru vrátí hodnotu true pouze v případě, že řídí sekvencí *levé* a *správné* mít stejnou délku a pro každou pozici `i`, `left[i] ==` `right[i]`. Pomocí něho můžete testovat, zda *levé* je stejný jako seřazené *správné* když jsou dvě mapy porovnání elementu pomocí elementu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_map_operator_eq.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mymap c2;   
    c2.insert(Mymap::make_value(L'a', 1));   
    c2.insert(Mymap::make_value(L'b', 2));   
    c2.insert(Mymap::make_value(L'd', 4));   
  
// display contents " [a 1] [b 2] [d 4]"   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] == [a b c] is {0}",   
        c1 == c1);   
    System::Console::WriteLine("[a b c] == [a b d] is {0}",   
        c1 == c2);   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
 [a 1] [b 2] [d 4]  
[a b c] == [a b c] is True  
[a b c] == [a b d] is False  
```  

## <a name="op_gt"></a> operátor&gt; (map) (STL/CLR)
Seznam je větší než porovnání.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Key,  
    typename Mapped>  
    bool operator>(map<Key, Mapped>% left,  
        map<Key, Mapped>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *doleva*  
 Levé kontejner k porovnání.  
  
 *doprava*  
 Správném kontejneru pro porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí funkci operátoru `right` `<` `left`. Pomocí něho můžete testovat, zda *levé* seřazené po *správné* když jsou dvě mapy porovnání elementu pomocí elementu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_map_operator_gt.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mymap c2;   
    c2.insert(Mymap::make_value(L'a', 1));   
    c2.insert(Mymap::make_value(L'b', 2));   
    c2.insert(Mymap::make_value(L'd', 4));   
  
// display contents " [a 1] [b 2] [d 4]"   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] > [a b c] is {0}",   
        c1 > c1);   
    System::Console::WriteLine("[a b d] > [a b c] is {0}",   
        c2 > c1);   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
 [a 1] [b 2] [d 4]  
[a b c] > [a b c] is False  
[a b d] > [a b c] is True  
```  

## <a name="op_gteq"></a> operátor&gt;= (map) (STL/CLR)
Seznam větší než nebo rovna porovnání.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Key,  
    typename Mapped>  
    bool operator>=(map<Key, Mapped>% left,  
        map<Key, Mapped>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *doleva*  
 Levé kontejner k porovnání.  
  
 *doprava*  
 Správném kontejneru pro porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí funkci operátoru `!(left` `<` `right)`. Pomocí něho můžete testovat, zda *levé* není řazen před *správné* když jsou dvě mapy porovnání elementu pomocí elementu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_map_operator_ge.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mymap c2;   
    c2.insert(Mymap::make_value(L'a', 1));   
    c2.insert(Mymap::make_value(L'b', 2));   
    c2.insert(Mymap::make_value(L'd', 4));   
  
// display contents " [a 1] [b 2] [d 4]"   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] >= [a b c] is {0}",   
        c1 >= c1);   
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",   
        c1 >= c2);   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
 [a 1] [b 2] [d 4]  
[a b c] >= [a b c] is True  
[a b c] >= [a b d] is False  
``` 