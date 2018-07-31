---
title: hash_multiset – (STL/CLR) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_multiset
- cliext::hash_multiset::begin
- cliext::hash_multiset::bucket_count
- cliext::hash_multiset::clear
- cliext::hash_multiset::const_iterator
- cliext::hash_multiset::const_reference
- cliext::hash_multiset::const_reverse_iterator
- cliext::hash_multiset::count
- cliext::hash_multiset::difference_type
- cliext::hash_multiset::empty
- cliext::hash_multiset::end
- cliext::hash_multiset::equal_range
- cliext::hash_multiset::erase
- cliext::hash_multiset::find
- cliext::hash_multiset::generic_container
- cliext::hash_multiset::generic_iterator
- cliext::hash_multiset::generic_reverse_iterator
- cliext::hash_multiset::generic_value
- cliext::hash_multiset::hash_delegate
- cliext::hash_multiset::hash_multiset
- cliext::hash_multiset::hasher
- cliext::hash_multiset::insert
- cliext::hash_multiset::iterator
- cliext::hash_multiset::key_comp
- cliext::hash_multiset::key_compare
- cliext::hash_multiset::key_type
- cliext::hash_multiset::load_factor
- cliext::hash_multiset::lower_bound
- cliext::hash_multiset::make_value
- cliext::hash_multiset::max_load_factor
- cliext::hash_multiset::operator=
- cliext::hash_multiset::rbegin
- cliext::hash_multiset::reference
- cliext::hash_multiset::rehash
- cliext::hash_multiset::rend
- cliext::hash_multiset::reverse_iterator
- cliext::hash_multiset::size
- cliext::hash_multiset::size_type
- cliext::hash_multiset::swap
- cliext::hash_multiset::to_array
- cliext::hash_multiset::upper_bound
- cliext::hash_multiset::value_comp
- cliext::hash_multiset::value_compare
- cliext::hash_multiset::value_type
dev_langs:
- C++
helpviewer_keywords:
- <cliext/hash_set> header [STL/CLR]
- hash_multiset class [STL/CLR]
- <hash_set> header [STL/CLR]
- begin member [STL/CLR]
- bucket_count member [STL/CLR]
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
- hash_delegate member [STL/CLR]
- hash_multiset member [STL/CLR]
- hasher member [STL/CLR]
- insert member [STL/CLR]
- iterator member [STL/CLR]
- key_comp member [STL/CLR]
- key_compare member [STL/CLR]
- key_type member [STL/CLR]
- load_factor member [STL/CLR]
- lower_bound member [STL/CLR]
- make_value member [STL/CLR]
- max_load_factor member [STL/CLR]
- operator= member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rehash member [STL/CLR]
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
ms.assetid: 8462bd21-6829-4dd3-ac81-c42d6fdf92f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 71ae758f969c03ecfd6d14721208a2a496309ec0
ms.sourcegitcommit: bad2441d1930275ff506d44759d283d94cccd1c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/31/2018
ms.locfileid: "39376323"
---
# <a name="hashmultiset-stlclr"></a>hash_multiset (STL/CLR)
Třída šablony popisuje objekt, který řídí různé délky sekvence elementů, která má obousměrný přístup. Použití kontejneru `hash_multiset` spravovat řadu prvků, jako zatřiďovací tabulku, každý záznam tabulky, ukládání obousměrné propojený seznam uzlů a každý uzel ukládání jeden element. Hodnota každého prvku se používá jako klíč, že pořadí řazení.  
  
 V popisu níže `GValue` je stejný jako `GKey`, který je stejný jako *klíč* Pokud je typ odkazu, v takovém případě je `Key^`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Key>  
    ref class hash_multiset  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        Microsoft::VisualC::StlClr::IHash<Gkey, GValue>  
    { ..... };  
```  
  
### <a name="parameters"></a>Parametry  
 *Key*  
 Typ klíčovou komponentou elementu v řízené sekvenci.  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / hash_set >  
  
 **Namespace:** cliext –  
  
## <a name="declarations"></a>Deklarace  
  
|Definice typu|Popis|  
|---------------------|-----------------|  
|[hash_multiset::const_iterator (STL/CLR)](#const_iterator)|Typ konstantního iterátoru řízené sekvence|  
|[hash_multiset::const_reference (STL/CLR)](#const_reference)|Typ konstantního odkazu na prvek|  
|[hash_multiset::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|Typ konstantního zpětného iterátoru řízené sekvence.|  
|[hash_multiset::difference_type (STL/CLR)](#difference_type)|Typ (může být podepsaná) vzdálenosti mezi dvěma prvky.|  
|[hash_multiset::generic_container (STL/CLR)](#generic_container)|Typ obecné rozhraní pro kontejner.|  
|[hash_multiset::generic_iterator (STL/CLR)](#generic_iterator)|Typ iterátoru pro obecné rozhraní pro kontejner.|  
|[hash_multiset::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|Typ "reverse iterator" pro obecné rozhraní pro kontejner.|  
|[hash_multiset::generic_value (STL/CLR)](#generic_value)|Typ elementu pro obecné rozhraní pro kontejner.|  
|[hash_multiset::hasher (STL/CLR)](#hasher)|Hash delegáta pro klíč.|  
|[hash_multiset::iterator (STL/CLR)](#iterator)|Typ iterátoru řízené sekvence|  
|[hash_multiset::key_compare (STL/CLR)](#key_compare)|Pořadí delegáta pro dva klíče.|  
|[hash_multiset::key_type (STL/CLR)](#key_type)|Typ klíče řazení|  
|[hash_multiset::reference (STL/CLR)](#reference)|Typ odkazu na prvek|  
|[hash_multiset::reverse_iterator (STL/CLR)](#reverse_iterator)|Typ "reverse iterator" pro řízenou sekvenci.|  
|[hash_multiset::size_type (STL/CLR)](#size_type)|Typ vzdálenosti (nezáporné) mezi dvěma prvky.|  
|[hash_multiset::value_compare (STL/CLR)](#value_compare)|Pořadí delegáta pro dvě hodnoty prvků.|  
|[hash_multiset::value_type (STL/CLR)](#value_type)|Typ prvku|  
  
|Členská funkce|Popis|  
|---------------------|-----------------|  
|[hash_multiset::begin (STL/CLR)](#begin)|Určuje začátek řízené sekvence.|  
|[hash_multiset::bucket_count (STL/CLR)](#bucket_count)|Spočítá počet kbelíků.|  
|[hash_multiset::clear (STL/CLR)](#clear)|Odebere všechny prvky.|  
|[hash_multiset::count (STL/CLR)](#count)|Vrátí počet prvků odpovídající zadanému klíči.|  
|[hash_multiset::empty (STL/CLR)](#empty)|Zkouší, zda nejsou přítomny žádné prvky.|  
|[hash_multiset::end (STL/CLR)](#end)|Určuje konec řízené sekvence.|  
|[hash_multiset::equal_range (STL/CLR)](#equal_range)|Najde rozsah, který odpovídá zadanému klíči.|  
|[hash_multiset::erase (STL/CLR)](#erase)|Odebere prvky v určených pozicích.|  
|[hash_multiset::find (STL/CLR)](#find)|Vyhledá prvek, který odpovídá zadanému klíči.|  
|[hash_multiset::hash_delegate (STL/CLR)](#hash_delegate)|Zkopíruje hash delegáta pro klíč.|  
|[hash_multiset::hash_multiset (STL/CLR)](#hash_multiset)|Sestaví objekt kontejneru.|  
|[hash_multiset::insert (STL/CLR)](#insert)|Přidá prvky.|  
|[hash_multiset::key_comp (STL/CLR)](#key_comp)|Zkopíruje pořadí delegáta pro dva klíče.|  
|[hash_multiset::load_factor (STL/CLR)](#load_factor)|Spočítá průměrný počet prvků na kbelík.|  
|[hash_multiset::lower_bound (STL/CLR)](#lower_bound)|Vyhledá počátek rozsahu, který odpovídá zadanému klíči.|  
|[hash_multiset::make_value (STL/CLR)](#make_value)|Vytvoří objekt hodnoty.|  
|[hash_multiset::max_load_factor (STL/CLR)](#max_load_factor)|Získá nebo nastaví maximální počet prvků na kbelík.|  
|[hash_multiset::rbegin (STL/CLR)](#rbegin)|Určuje začátek řízené obrácené sekvenci.|  
|[hash_multiset::rehash (STL/CLR)](#rehash)|Znovu vytvoří hashovací tabulku.|  
|[hash_multiset::rend (STL/CLR)](#rend)|Určuje konec řízené obrácené sekvenci.|  
|[hash_multiset::size (STL/CLR)](#size)|Spočítá počet prvků.|  
|[hash_multiset::swap (STL/CLR)](#swap)|Zamění obsah dvou kontejnerů.|  
|[hash_multiset::to_array (STL/CLR)](#to_array)|Zkopíruje do nového pole řízené sekvence.|  
|[hash_multiset::upper_bound (STL/CLR)](#upper_bound)|Najde konec rozsahu, který odpovídá zadanému klíči.|  
|[hash_multiset::value_comp (STL/CLR)](#value_comp)|Zkopíruje pořadí delegáta pro dvě hodnoty prvků.|  
  
|Operátor|Popis|  
|--------------|-----------------|  
|[hash_multiset::operator= (STL/CLR)](#op)|Nahradí řízené sekvence.|  
  
## <a name="interfaces"></a>Rozhraní  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Duplicitní objektu.|  
|<xref:System.Collections.IEnumerable>|Pořadí mezi prvky.|  
|<xref:System.Collections.ICollection>|Údržba skupiny prvků.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Pořadí pomocí zadané elementy.|  
|<xref:System.Collections.Generic.ICollection%601>|Údržba skupiny zadané elementy.|  
|IHash\<klíč, hodnota >|Udržujte obecný kontejneru.|  
  
## <a name="remarks"></a>Poznámky  
 Objekt přiděluje a uvolňuje úložiště pro ovládací prvky jako jednotlivé uzly v propojeném seznamu obousměrné pořadí. K urychlení přístupu, objekt také uchovává různé délky pole ukazatelů do seznamu (zatřiďovací tabulku), efektivní správa celý seznam jako posloupnost podseznamy, nebo intervalů. Vloží prvky do kontejneru, který udržuje seřazený tím, že změna vazby mezi uzly, nikdy zkopírováním obsah jednoho uzlu do jiného. To znamená, že můžete vložit a odebrat elementy volně bez narušení zbývající prvky.  
  
 Objekt seřadí každého kbelíku pomocí volání uloženého delegáta objekt typu [hash_set::key_compare (STL/CLR)](../dotnet/hash-set-key-compare-stl-clr.md). Můžete zadat objekt uložené delegáta při konstrukci hash_set; Pokud chcete zadat žádný objekt. delegát, výchozí hodnota je porovnání `operator<=(key_type, key_type)`.  
  
 Přístup k uložené delegáta objektu voláním členské funkce [hash_set::key_comp (STL/CLR)](../dotnet/hash-set-key-comp-stl-clr.md)`()`. Takový objekt delegáta musí definovat stejné pořadí mezi klíči typu [hash_set::key_type (STL/CLR)](../dotnet/hash-set-key-type-stl-clr.md). To znamená pro jakékoli dva klíče `X` a `Y`:  
  
 `key_comp()(X, Y)` Vrátí výsledek stejný datový typ Boolean při každém volání.  
  
 Pokud `key_comp()(X, Y) && key_comp()(Y, X)` má hodnotu true, pak `X` a `Y` se říká, že mají ekvivalentní řazení.  
  
 Žádné pořadí pravidlo, který se chová jako `operator<=(key_type, key_type)`, `operator>=(key_type, key_type)` nebo `operator==(key_type, key_type)` definuje eqivalent řazení.  
  
 Všimněte si, že zajišťuje kontejneru pouze, že elementy jehož klíče mají ekvivalentní řazení (a které hodnotu hash na stejnou hodnotu celého čísla) sousedí v sadě. Na rozdíl od třídy šablony [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md), objekt třídy šablony `hash_multiset` nevyžaduje, aby byly jedinečné klíče pro všechny elementy. (Dva nebo více klíčů může mít odpovídající řazení.)  
  
 Objekt určuje, které sadě by měl obsahovat daného klíče řazení pomocí volání uloženého delegáta objektu typu [hash_set::hasher (STL/CLR)](../dotnet/hash-set-hasher-stl-clr.md). Přístup k tomuto uloženého objektu voláním členské funkce [hash_set::hash_delegate (STL/CLR)](../dotnet/hash-set-hash-delegate-stl-clr.md) `()` získat celočíselnou hodnotu, která závisí na hodnotě klíče. Můžete zadat objekt uložené delegáta při konstrukci hash_set; Pokud chcete zadat žádný objekt. delegát, výchozí hodnota je funkce `System::Object::hash_value(key_type)`. To znamená pro všechny klíče `X` a `Y`:  
  
 `hash_delegate()(X)` Vrátí při každém volání stejný výsledek celého čísla.  
  
 Pokud `X` a `Y` mají ekvivalentní řazení, pak `hash_delegate()(X)` by měla vrátit stejný výsledek celého čísla jako `hash_delegate()(Y)`.  
  
 Každý prvek slouží jako klíč a hodnotu. Sekvence je reprezentována způsobem, který umožňuje vyhledávání, vkládání a odstranění libovolný prvek s několika operacemi, která je nezávislá počet prvků v sekvenci (konstantní čas) – alespoň v nejlepším případě. Vkládání prvků navíc nezruší platnost žádných iterátorů a odstranění prvku zruší platnost pouze těch iterátorů, které odkazují na odstraněný prvek.  
  
 Pokud se hodnoty hash nejsou rovnoměrně, ale můžete degenerovanou zatřiďovací tabulku. V krajních – pro funkci hash, která vždy vrátí stejnou hodnotu--je úměrný počtu prvků v sekvenci (lineární čas) vyhledávání, vkládání a odstranění. Kontejner endeavors zvolit přiměřené hashovací funkci, střední kontejneru velikost a velikost tabulky hash (celkový počet kbelíků), ale můžete přepsat některé nebo všechny tyto možnosti. Zobrazit, například funkce [hash_set::max_load_factor (STL/CLR)](../dotnet/hash-set-max-load-factor-stl-clr.md) a [hash_set::rehash (STL/CLR)](../dotnet/hash-set-rehash-stl-clr.md).  
  
 Hash_multiset – podporuje obousměrné iterátory, což znamená, že přejdete na sousedící prvky zadaný iterátor, který určuje elementu v řízené sekvenci. Speciální hlavního uzlu odpovídá iterátorů vrácené [hash_multiset::end (STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md)`()`. Tento iterátor, který má přístup po posledním prvku v řízené sekvenci lze snížit, pokud jsou k dispozici. Můžete zvýšit hash_multiset iterátor pro přístup k hlavnímu uzlu a budou pak porovnat rovna `end()`. Nelze přistoupit přes ukazatel vrátí iterátor, ale `end()`.  
  
 Všimněte si, že nemůže odkazovat na prvek hash_multiset přímo zadané pozici číselné –, který vyžaduje iterátor náhodného přístupu.  
  
 Hash_multiset – iterátoru uloží popisovač do přidružené hash_multiset – uzlu, který je pak uloží popisovač pro jeho přiřazeným kontejnerem. Iterátory lze použít pouze objekty, které přiřazeným kontejnerem. Pokud je jeho přidružené hash_multiset uzel přidružené nějaké hash_multiset – iterátor hash_multiset – zůstává v platnosti. Kromě toho je platný iterátoru přesměrovat – slouží k přístupu nebo změnit hodnotu prvku jmenuje--tak dlouho, dokud se nerovná `end()`.  
  
 Smazání nebo odstranění prvku volá destruktor pro jeho uložené hodnotě. Zničení kontejneru vymaže všechny prvky. Kontejner, jehož typ prvku je třídy ref class tak, zajišťuje, že žádné elementy něj kontejneru. Mějte na paměti, ale, že kontejner zpracovává nemá *není* zničit jeho prvků.  
  
## <a name="members"></a>Členové

## <a name="begin"></a> hash_multiset::begin (STL/CLR)
Určuje začátek řízené sekvence.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
iterator begin();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí obousměrný iterátor, který určuje první prvek řízenou sekvenci nebo přesně za konec k prázdné sekvenci. Můžete ji použít k získání iterátor, který určuje `current` začátek řízené sekvence, ale jeho stav můžete změnit, pokud se změní délka řízené sekvence.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_hash_multiset_begin.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    Myhash_multiset::iterator it = c1.begin();   
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

## <a name="bucket_count"></a> hash_multiset::bucket_count (STL/CLR)
Spočítá počet kbelíků.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
int bucket_count();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí aktuální počet kbelíků. Použijete ji k určení velikosti zatřiďovací tabulku.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_hash_multiset_bucket_count.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect current parameters   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    System::Console::WriteLine();   
  
// change max_load_factor and redisplay   
    c1.max_load_factor(0.25f);   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    System::Console::WriteLine();   
  
// rehash and redisplay   
    c1.rehash(100);   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    return (0);   
    }  
```  
  
```Output  
 a b c  
bucket_count() = 16  
load_factor() = 0.1875  
max_load_factor() = 4  
  
bucket_count() = 16  
load_factor() = 0.1875  
max_load_factor() = 0.25  
  
bucket_count() = 128  
load_factor() = 0.0234375  
max_load_factor() = 0.25  
```  

## <a name="clear"></a> hash_multiset::clear (STL/CLR)
Odebere všechny prvky.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
void clear();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce efektivně volá [hash_multiset::erase (STL/CLR)](../dotnet/hash-multiset-erase-stl-clr.md) `(` [hash_multiset::begin (STL/CLR)](../dotnet/hash-multiset-begin-stl-clr.md) `(),` [hash_multiset::end (STL/CLR) ](../dotnet/hash-multiset-end-stl-clr.md)`())`. Použijete ji k zajištění, že je prázdná řízené sekvence.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_hash_multiset_clear.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
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

## <a name="const_iterator"></a> hash_multiset::const_iterator (STL/CLR)
Typ konstantního iterátoru řízené sekvence  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef T2 const_iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ popisuje objekt neurčeného typu `T2` , který může sloužit jako konstantní obousměrného iterátoru řízené sekvence.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_hash_multiset_const_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    Myhash_multiset::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        System::Console::Write(" {0}", *cit);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
```  

## <a name="const_reference"></a> hash_multiset::const_reference (STL/CLR)
Typ konstantního odkazu na prvek  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef value_type% const_reference;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ, který popisuje konstantní odkaz na element.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_hash_multiset_const_reference.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    Myhash_multiset::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        {   // get a const reference to an element   
        Myhash_multiset::const_reference cref = *cit;   
        System::Console::Write(" {0}", cref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
```  

## <a name="const_reverse_iterator"></a> hash_multiset::const_reverse_iterator (STL/CLR)
Typ konstantního zpětného iterátoru řízené sekvence...  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef T4 const_reverse_iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ popisuje objekt neurčeného typu `T4` , který může sloužit jako konstantní zpětného iterátoru řízené sekvence.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_hash_multiset_const_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" reversed   
    Myhash_multiset::const_reverse_iterator crit = c1.rbegin();   
    for (; crit != c1.rend(); ++crit)   
        System::Console::Write(" {0}", *crit);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c b a  
```  

## <a name="count"></a> hash_multiset::Count (STL/CLR)
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
// cliext_hash_multiset_count.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
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
  
## <a name="difference_type"></a> hash_multiset::difference_type (STL/CLR)
Typ vzdálenosti se znaménkem mezi dvěma prvky.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef int difference_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ, který popisuje element může být záporný počet.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_hash_multiset_difference_type.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    Myhash_multiset::difference_type diff = 0;   
    for (Myhash_multiset::iterator it = c1.begin(); it != c1.end(); ++it)   
        ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
  
// compute negative difference   
    diff = 0;   
    for (Myhash_multiset::iterator it = c1.end(); it != c1.begin(); --it)   
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

## <a name="empty"></a> hash_multiset::Empty (STL/CLR)
Zkouší, zda nejsou přítomny žádné prvky.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
bool empty();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí hodnotu true pro prázdnou řízenou sekvenci. Je ekvivalentní [hash_multiset::size (STL/CLR)](../dotnet/hash-multiset-size-stl-clr.md)`() == 0`. Použijete ji k ověření, zda hash_multiset je prázdný.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_hash_multiset_empty.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
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

## <a name="end"></a> hash_multiset::end (STL/CLR)
Určuje konec řízené sekvence.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
iterator end();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí obousměrný iterátor, který ukazuje za konec řízené sekvence. Můžete ji použít k získání iterátor, který určuje konec řízené sekvence; jeho stav kódu ne změnit, pokud se změní délka řízené sekvence.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_hash_multiset_end.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last two items   
    Myhash_multiset::iterator it = c1.end();   
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
  
## <a name="equal_range"></a> hash_multiset::equal_range (STL/CLR)
Najde rozsah, který odpovídá zadanému klíči.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
cliext::pair<iterator, iterator> equal_range(key_type key);  
```  
  
#### <a name="parameters"></a>Parametry  
 *Klíč*  
 Hodnota klíče pro hledání.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí pár iterátorů `cliext::pair<iterator, iterator>(` [hash_multiset::lower_bound (STL/CLR)](../dotnet/hash-multiset-lower-bound-stl-clr.md) `(key),` [hash_multiset::upper_bound (STL/CLR)](../dotnet/hash-multiset-upper-bound-stl-clr.md)`(key))`. Použijete ji k určení rozsahu prvků v řízené sekvenci aktuálně, které odpovídají zadanému klíči.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_hash_multiset_equal_range.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
typedef Myhash_multiset::pair_iter_iter Pairii;   
int main()   
    {   
    Myhash_multiset c1;   
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

## <a name="erase"></a> hash_multiset::Erase (STL/CLR)
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
 První členská funkce odstraní prvek řízené sekvence, na které odkazuje *kde*a vrátí iterátor, který určuje první prvek zbývající za prvkem, který odebere, nebo [hash_multiset::end () STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md) `()` Pokud žádný takový prvek neexistuje. Použijete ji k odebrání jeden element.  
  
 Druhá členská funkce odebere prvky řízené sekvence v rozsahu [`first`, `last`) a vrátí iterátor, který určuje první prvek zbývající za všemi odstraněnými prvky, nebo `end()` Pokud žádný takový prvek existuje... Použijete ji k odebrání nula nebo více souvislých prvků.  
  
 Třetí členská funkce odstraní libovolný prvek řízenou sekvenci, jehož klíč má ekvivalentní řazení na *klíč*a vrátí počet prvků, které jsou odebrány. Použijete ho odebrat a spočítat všechny elementy, které odpovídají zadanému klíči.  
  
 Každý prvek mazání trvá určitou dobu úměrný logaritmu počtu prvků v řízené sekvenci.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_hash_multiset_erase.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
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
    Myhash_multiset::iterator it = c1.end();   
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

## <a name="find"></a> hash_multiset::Find (STL/CLR)
Vyhledá prvek, který odpovídá zadanému klíči.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
iterator find(key_type key);  
```  
  
#### <a name="parameters"></a>Parametry  
 *Klíč*  
 Hodnota klíče pro hledání.  
  
### <a name="remarks"></a>Poznámky  
 Pokud má alespoň jeden element v řízené sekvenci s odpovídající řazení *klíč*, členská funkce vrátí iterátor určit jeden z těchto elementů; v opačném případě vrátí [hash_multiset::end (STL/CLR) ](../dotnet/hash-multiset-end-stl-clr.md)`()`. Použijete ji k aktuálně vyhledejte elementu v řízené sekvenci, která odpovídá zadanému klíči.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_hash_multiset_find.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
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

## <a name="generic_container"></a> hash_multiset::generic_container (STL/CLR)
Typ obecné rozhraní pro kontejner.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef Microsoft::VisualC::StlClr::  
    IHash<GKey, GValue>  
    generic_container;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ, který popisuje obecné rozhraní pro tuto třídu šablony kontejneru.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_hash_multiset_generic_container.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myhash_multiset::generic_container^ gc1 = %c1;   
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
   
## <a name="generic_iterator"></a> hash_multiset::generic_iterator (STL/CLR)
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
// cliext_hash_multiset_generic_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myhash_multiset::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Myhash_multiset::generic_iterator gcit = gc1->begin();   
    Myhash_multiset::generic_value gcval = *gcit;   
    System::Console::WriteLine(" {0}", gcval);   
    return (0);   
    }  
```  
  
```Output  
a b c  
a b c  
a  
```  

## <a name="generic_reverse_iterator"></a> hash_multiset::generic_reverse_iterator (STL/CLR)
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
// cliext_hash_multiset_generic_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myhash_multiset::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Myhash_multiset::generic_reverse_iterator gcit = gc1->rbegin();   
    Myhash_multiset::generic_value gcval = *gcit;   
    System::Console::WriteLine(" {0}", gcval);   
    return (0);   
    }  
```  
  
```Output  
a b c  
a b c  
c  
```  

## <a name="generic_value"></a> hash_multiset::generic_value (STL/CLR)
Typ elementu pro použití s obecné rozhraní pro kontejner.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef GValue generic_value;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ, který popisuje objekt typu `GValue` hodnoty uložené elementu pro použití s obecné rozhraní pro tuto třídu šablony kontejneru, který popisuje.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_hash_multiset_generic_value.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myhash_multiset::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Myhash_multiset::generic_iterator gcit = gc1->begin();   
    Myhash_multiset::generic_value gcval = *gcit;   
    System::Console::WriteLine(" {0}", gcval);   
    return (0);   
    }  
```  
  
```Output  
a b c  
a b c  
a  
```  
  
## <a name="hash_delegate"></a> hash_multiset::hash_delegate (STL/CLR)
Vyhledá prvek, který odpovídá zadanému klíči.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
hasher^ hash_delegate();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí delegáta použít pro převod na celé číslo s hodnotou klíče. Použijete ji k vytvoření hodnoty hash klíče.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_hash_multiset_hash_delegate.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    Myhash_multiset::hasher^ myhash = c1.hash_delegate();   
  
    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));   
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));   
    return (0);   
    }  
```  
  
```Output  
hash(L'a') = 1616896120  
hash(L'b') = 570892832  
```  
  
## <a name="hash_multiset"></a> hash_multiset::hash_multiset (STL/CLR)
Sestaví objekt kontejneru.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
hash_multiset();  
explicit hash_multiset(key_compare^ pred);  
hash_multiset(key_compare^ pred, hasher^ hashfn);  
hash_multiset(hash_multiset<Key>% right);  
hash_multiset(hash_multiset<Key>^ right);  
template<typename InIter>  
    hash_multiset(InIter first, InIter last);  
template<typename InIter>  
    hash_multiset(InIter first, InIter last,  
        key_compare^ pred);  
template<typename InIter>  
    hash_multiset(InIter first, InIter last,  
        key_compare^ pred, hasher^ hashfn);  
hash_multiset(System::Collections::Generic::IEnumerable<GValue>^ right);  
hash_multiset(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred);  
hash_multiset(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred, hasher^ hashfn);  
```  
  
#### <a name="parameters"></a>Parametry  
 *první*  
 Začátek rozsahu pro vložení.  
  
 *hashfn*  
 Hash – funkce pro mapování klíčů do kontejnerů.  
  
 *poslední*  
 Konec rozsahu pro vložení.  
  
 *Před*  
 Řazení predikátu řízené sekvence.  
  
 *doprava*  
 Objekt nebo rozsahu pro vložení.  
  
### <a name="remarks"></a>Poznámky  
 Konstruktor:  
  
 `hash_multiset();`  
  
 Inicializuje výchozí řazení predikátu řízené sekvence bez prvků `key_compare()`a s výchozí funkce hash. Použijete ji k určení prázdnou počáteční řízenou sekvenci, s výchozí řazení predikát a hashovací funkce.  
  
 Konstruktor:  
  
 `explicit hash_multiset(key_compare^ pred);`  
  
 Inicializuje řízené sekvence bez prvků pořadí predikátem *před*a s výchozí funkce hash. Použít prázdnou počáteční řízenou sekvenci, určit se zadanou predikát řazení a výchozí funkce hash.  
  
 Konstruktor:  
  
 `hash_multiset(key_compare^ pred, hasher^ hashfn);`  
  
 Inicializuje řízené sekvence bez prvků pořadí predikátem *před*a hodnotu hash *hashfn*. Použít prázdnou počáteční řízenou sekvenci, určit se zadané pořadí predikát a hashovací funkce.  
  
 Konstruktor:  
  
 `hash_multiset(hash_multiset<Key>% right);`  
  
 Inicializuje řízené sekvence s pořadím [`right.begin()`, `right.end()`), s výchozí řazení predikátu a výchozí funkce hash. Můžete použít k určení počáteční řízené sekvence, který je kopii sekvence řízenou parametrem objektu hash_multiset – *správné*s výchozí pořadí predikátem a funkce hash.  
  
 Konstruktor:  
  
 `hash_multiset(hash_multiset<Key>^ right);`  
  
 Inicializuje řízené sekvence s pořadím [`right->begin()`, `right->end()`), s výchozí řazení predikátu a výchozí funkce hash. Můžete použít k určení počáteční řízené sekvence, který je kopii sekvence řízenou parametrem objektu hash_multiset – *správné*s výchozí pořadí predikátem a funkce hash.  
  
 Konstruktor:  
  
 `template<typename InIter> hash_multiset(InIter first, InIter last);`  
  
 Inicializuje řízené sekvence s pořadím [`first`, `last`), s výchozí řazení predikátu a výchozí funkce hash. Používejte aby řízené sekvence kopii jiné pořadí, s výchozí řazení predikát a hashovací funkce.  
  
 Konstruktor:  
  
 `template<typename InIter> hash_multiset(InIter first, InIter last, key_compare^ pred);`  
  
 Inicializuje řízené sekvence s pořadím [`first`, `last`), pořadí predikátem *před*a s výchozí funkce hash. Použijete ji k vytvoření kopie jiné pořadí se zadanou predikát řazení a výchozí funkce hash řízené sekvence.  
  
 Konstruktor:  
  
 `template<typename InIter> hash_multiset(InIter first, InIter last, key_compare^ pred, hasher^ hashfn);`  
  
 Inicializuje řízené sekvence s pořadím [`first`, `last`), pořadí predikátem *před*a hodnotu hash *hashfn*. Použijte k vytvoření kopie jiné pořadí, pomocí zadané pořadí predikát a hashovací funkce řízené sekvence.  
  
 Konstruktor:  
  
 `hash_multiset(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 Inicializuje řízené sekvence s pořadí určeném enumerátor *správné*, s výchozí řazení predikátu a výchozí funkce hash. Použijte k vytvoření kopie jiné pořadí popsal čítače, s výchozí řazení predikát a hashovací funkce řízené sekvence.  
  
 Konstruktor:  
  
 `hash_multiset(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`  
  
 Inicializuje řízené sekvence s pořadí určeném enumerátor *správné*, pořadí predikátem *před*a s výchozí funkce hash. Použijte k vytvoření kopie jiné pořadí popsal enumerátor pomocí zadaného pořadí predikát a výchozí funkce hash řízené sekvence.  
  
 Konstruktor:  
  
 `hash_multiset(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred, hasher^ hashfn);`  
  
 Inicializuje řízené sekvence s pořadí určeném enumerátor *správné*, pořadí predikátem *před*a hodnotu hash *hashfn*. Použijte k vytvoření kopie jiné pořadí popsal čítače, pomocí zadané pořadí predikát a hashovací funkce řízené sekvence.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_hash_multiset_construct.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
int myfun(wchar_t key)   
    { // hash a key   
    return (key ^ 0xdeadbeef);   
    }   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
// construct an empty container   
    Myhash_multiset c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Myhash_multiset c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule and hash function   
    Myhash_multiset c2h(cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_multiset::hasher(&myfun));   
    System::Console::WriteLine("size() = {0}", c2h.size());   
  
    c2h.insert(c1.begin(), c1.end());   
    for each (wchar_t elem in c2h)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Myhash_multiset c3(c1.begin(), c1.end());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Myhash_multiset c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule and hash function   
    Myhash_multiset c4h(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_multiset::hasher(&myfun));   
    for each (wchar_t elem in c4h)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Myhash_multiset c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Myhash_multiset c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,   
            cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c6)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule and hash function   
    Myhash_multiset c6h(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,   
            cliext::greater_equal<wchar_t>(),   
                gcnew Myhash_multiset::hasher(&myfun));   
    for each (wchar_t elem in c6h)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct from a generic container   
    Myhash_multiset c7(c4);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Myhash_multiset c8(%c3);   
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
 a b c  
size() = 0  
 c b a  
  
 a b c  
 a b c  
 c b a  
  
 a b c  
 a b c  
 c b a  
  
 a b c  
 a b c  
```  

## <a name="hasher"></a> hash_multiset::hasher (STL/CLR)
Hash delegáta pro klíč.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
Microsoft::VisualC::StlClr::UnaryDelegate<GKey, int>  
    hasher;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ, který popisuje delegáta, který převede hodnotu klíče na celé číslo.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_hash_multiset_hasher.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    Myhash_multiset::hasher^ myhash = c1.hash_delegate();   
  
    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));   
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));   
    return (0);   
    }  
```  
  
```Output  
hash(L'a') = 1616896120  
hash(L'b') = 570892832  
```  

## <a name="insert"></a> hash_multiset::Insert (STL/CLR)
Přidá prvky.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
iterator insert(value_type val);  
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
  
 První členská funkce vloží prvek s hodnotou *val*a vrátí iterátor, který určuje nově vložený prvek. Použijete ji k vložení jeden element.  
  
 Druhá členská funkce vloží prvek s hodnotou *val*s použitím *kde* jako Nápověda (ke zlepšení výkonu) a vrátí iterátor, který určuje nově vložený prvek. Použijete ji k vložení jeden element, který může být vedle elementu, které už znáte.  
  
 Třetí členská funkce vloží sekvenci [`first`, `last`). Použijete ji k vložení nula nebo více elementů zkopírovaných z jiné pořadí.  
  
 Čtvrtá členská funkce vloží pořadí určeném *správné*. Použijete ji k vložení pořadí popsal enumerátor.  
  
 Každý prvek vložení trvá určitou dobu úměrný logaritmu počtu prvků v řízené sekvenci. Vložení situace může nastat v amortizovaném konstantním času, ale zadaný pomocného parametru, který určuje prvek vedle kurzor.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_hash_multiset_insert.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value, unique and duplicate   
    System::Console::WriteLine("insert(L'x') = {0}",   
        *c1.insert(L'x'));   
  
    System::Console::WriteLine("insert(L'b') = {0}",   
        *c1.insert(L'b'));   
  
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
    Myhash_multiset c2;   
    Myhash_multiset::iterator it = c1.end();   
    c2.insert(c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    Myhash_multiset c3;   
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
insert(L'x') = x  
insert(L'b') = b  
 a b b c x  
insert(begin(), L'y') = y  
 a b b c x y  
 a b b c x  
 a b b c x y  
```  

## <a name="iterator"></a> hash_multiset::iterator (STL/CLR)
Typ iterátoru řízené sekvence  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef T1 iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ popisuje objekt neurčeného typu `T1` , který může sloužit jako obousměrný iterátor, který řízené sekvence.  
  
### <a name="example"></a>Příklad  
  
```cpp 
// cliext_hash_multiset_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    Myhash_multiset::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
```  

## <a name="key_comp"></a> hash_multiset::key_comp (STL/CLR)
Zkopíruje pořadí delegáta pro dva klíče.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
key_compare^key_comp();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí pořadí delegáta, který slouží k seřazení řízené sekvence. Použijete ji k porovnat dva klíče.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_hash_multiset_key_comp.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    Myhash_multiset::key_compare^ kcomp = c1.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Myhash_multiset c2 = cliext::greater<wchar_t>();   
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
compare(L'a', L'a') = True  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
  
compare(L'a', L'a') = False  
compare(L'a', L'b') = False  
compare(L'b', L'a') = True  
```  

## <a name="key_compare"></a> hash_multiset::key_compare (STL/CLR)
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
// cliext_hash_multiset_key_compare.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    Myhash_multiset::key_compare^ kcomp = c1.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Myhash_multiset c2 = cliext::greater<wchar_t>();   
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
compare(L'a', L'a') = True  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
  
compare(L'a', L'a') = False  
compare(L'a', L'b') = False  
compare(L'b', L'a') = True  
```  

## <a name="key_type"></a> hash_multiset::key_type (STL/CLR)
Typ klíče řazení  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro parametr šablony *klíč*.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_hash_multiset_key_type.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" using key_type   
    for (Myhash_multiset::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in key_type object   
        Myhash_multiset::key_type val = *it;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
```  

## <a name="load_factor"></a> hash_multiset::load_factor (STL/CLR)
Spočítá průměrný počet prvků na kbelík.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
float load_factor();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí `(float)` [hash_multiset::size (STL/CLR)](../dotnet/hash-multiset-size-stl-clr.md) `() /` [hash_multiset::bucket_count (STL/CLR)](../dotnet/hash-multiset-bucket-count-stl-clr.md)`()`. Použijete ji k určení velikosti průměrné intervalu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_hash_multiset_load_factor.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect current parameters   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    System::Console::WriteLine();   
  
// change max_load_factor and redisplay   
    c1.max_load_factor(0.25f);   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    System::Console::WriteLine();   
  
// rehash and redisplay   
    c1.rehash(100);   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    return (0);   
    }  
```  
  
```Output  
 a b c  
bucket_count() = 16  
load_factor() = 0.1875  
max_load_factor() = 4  
  
bucket_count() = 16  
load_factor() = 0.1875  
max_load_factor() = 0.25  
  
bucket_count() = 128  
load_factor() = 0.0234375  
max_load_factor() = 0.25  
```  

## <a name="lower_bound"></a> hash_multiset::lower_bound (STL/CLR)
Vyhledá počátek rozsahu, který odpovídá zadanému klíči.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
iterator lower_bound(key_type key);  
```  
  
#### <a name="parameters"></a>Parametry  
 *Klíč*  
 Hodnota klíče pro hledání.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce určuje první prvek `X` v řízené sekvenci, který vytvoří hodnotu hash na stejném kontejneru jako *klíč* a má stejné pořadí na *klíč*. Pokud žádný takový prvek neexistuje, vrátí [hash_multiset::end (STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md)`()`; v opačném případě vrátí iterátor, který určuje `X`. Použijete ji k aktuálně vyhledejte na začátek pořadí prvků v řízené sekvenci, které odpovídají zadanému klíči.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_hash_multiset_lower_bound.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
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

## <a name="make_value"></a> hash_multiset::make_value (STL/CLR)
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
// cliext_hash_multiset_make_value.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(Myhash_multiset::make_value(L'a'));   
    c1.insert(Myhash_multiset::make_value(L'b'));   
    c1.insert(Myhash_multiset::make_value(L'c'));   
  
// display contents " a b c"   
    for each (Myhash_multiset::value_type elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
```  
  
## <a name="max_load_factor"></a> hash_multiset::max_load_factor (STL/CLR)
Získá nebo nastaví maximální počet prvků na kbelík.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
float max_load_factor();  
void max_load_factor(float new_factor);  
```  
  
#### <a name="parameters"></a>Parametry  
 *new_factor*  
 Nové maximální zatížení faktorem, který je ukládat.  
  
### <a name="remarks"></a>Poznámky  
 První členská funkce vrátí aktuální faktor maximálního zatížení uložené. Použijete ji k určení velikosti maximální průměrná intervalu.  
  
 Druhá členská funkce se nahradí faktor maximálního zatížení úložiště s *new_factor*. Žádné automatické rehashing dojde až do další vložit.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_hash_multiset_max_load_factor.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect current parameters   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    System::Console::WriteLine();   
  
// change max_load_factor and redisplay   
    c1.max_load_factor(0.25f);   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    System::Console::WriteLine();   
  
// rehash and redisplay   
    c1.rehash(100);   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    return (0);   
    }  
```  
  
```Output  
 a b c  
bucket_count() = 16  
load_factor() = 0.1875  
max_load_factor() = 4  
  
bucket_count() = 16  
load_factor() = 0.1875  
max_load_factor() = 0.25  
  
bucket_count() = 128  
load_factor() = 0.0234375  
max_load_factor() = 0.25  
```  

## <a name="op"></a> hash_multiset::Operator = (STL/CLR)
Nahradí řízené sekvence.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
hash_multiset<Key>% operator=(hash_multiset<Key>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *doprava*  
 Kontejner pro kopírování.  
  
### <a name="remarks"></a>Poznámky  
 Kopie členský operátor *správné* na objekt, vrátí `*this`. Můžete použít k nahraďte kopii řízené sekvence v řízené sekvenci *správné*.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_hash_multiset_operator_as.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (Myhash_multiset::value_type elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myhash_multiset c2;   
    c2 = c1;   
// display contents " a b c"   
    for each (Myhash_multiset::value_type elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
a b c  
```  

## <a name="rbegin"></a> hash_multiset::rbegin (STL/CLR)
Určuje začátek řízené obrácené sekvenci.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
reverse_iterator rbegin();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí zpětný iterátor, který určuje poslední prvek řízenou sekvenci nebo hned za začátku k prázdné sekvenci. Proto, označí `beginning` reverzní pořadí. Můžete ji použít k získání iterátor, který určuje `current` začátek řízené sekvence viděli v obráceném pořadí, ale jeho stav můžete změnit, pokud se změní délka řízené sekvence.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_hash_multiset_rbegin.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items in reversed sequence   
    Myhash_multiset::reverse_iterator rit = c1.rbegin();   
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

## <a name="reference"></a> hash_multiset::Reference (STL/CLR)
Typ odkazu na prvek  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef value_type% reference;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ, který popisuje odkaz na element.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_hash_multiset_reference.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    Myhash_multiset::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        {   // get a reference to an element   
        Myhash_multiset::reference ref = *it;   
        System::Console::Write(" {0}", ref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
``` 

## <a name="rehash"></a> hash_multiset::rehash (STL/CLR)
Znovu vytvoří hashovací tabulku.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
void rehash();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce znovu vytvoří tabulku hash, zajistit, aby [hash_multiset::load_factor (STL/CLR)](../dotnet/hash-multiset-load-factor-stl-clr.md) `() <=` [hash_multiset::max_load_factor (STL/CLR)](../dotnet/hash-multiset-max-load-factor-stl-clr.md). V opačném případě zatřiďovací tabulky zvětší velikost, pouze v případě potřeby po vložení. (To zmenšena, nikdy automaticky.) Použít a upravte velikost zatřiďovací tabulku.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_hash_multiset_rehash.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect current parameters   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    System::Console::WriteLine();   
  
// change max_load_factor and redisplay   
    c1.max_load_factor(0.25f);   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    System::Console::WriteLine();   
  
// rehash and redisplay   
    c1.rehash(100);   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    return (0);   
    }  
```  
  
```Output  
 a b c  
bucket_count() = 16  
load_factor() = 0.1875  
max_load_factor() = 4  
  
bucket_count() = 16  
load_factor() = 0.1875  
max_load_factor() = 0.25  
  
bucket_count() = 128  
load_factor() = 0.0234375  
max_load_factor() = 0.25  
```  

## <a name="rend"></a> hash_multiset::rend (STL/CLR)
Určuje konec řízené obrácené sekvenci.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
reverse_iterator rend();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí "reverse iterator", který ukazuje za začátek řízené sekvence. Proto, označí `end` reverzní pořadí. Můžete ji použít k získání iterátor, který určuje `current` konec řízené sekvence viděli v obráceném pořadí, ale jeho stav můžete změnit, pokud se změní délka řízené sekvence.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_hash_multiset_rend.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    Myhash_multiset::reverse_iterator rit = c1.rend();   
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

## <a name="reverse_iterator"></a> hash_multiset::reverse_iterator (STL/CLR)
Typ "reverse iterator" pro řízenou sekvenci.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef T3 reverse_iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ popisuje objekt neurčeného typu `T3` , který může sloužit jako "reverse iterator" pro řízenou sekvenci.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_hash_multiset_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" reversed   
    Myhash_multiset::reverse_iterator rit = c1.rbegin();   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" {0}", *rit);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c b a  
```  

## <a name="size"></a> hash_multiset::size (STL/CLR)
Spočítá počet prvků.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
size_type size();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí délku objektu řízené sekvence. Použijete ji k určení počtu prvků v řízené sekvenci aktuálně. Pokud vás zajímá, jestli je pořadí má nenulovou velikost, naleznete v tématu [hash_multiset::empty (STL/CLR)](../dotnet/hash-multiset-empty-stl-clr.md)`()`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_hash_multiset_size.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
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

## <a name="size_type"></a> hash_multiset::size_type (STL/CLR)
Typ vzdálenosti se znaménkem mezi dvěma elementu.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef int size_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ, který popisuje počet prvků záporná.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_hash_multiset_size_type.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    Myhash_multiset::size_type diff = 0;   
    for (Myhash_multiset::iterator it = c1.begin(); it != c1.end(); ++it)   
        ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
    return (0);   
    }  
```  
  
```Output  
 a b c  
end()-begin() = 3  
```

## <a name="swap"></a> hash_multiset::swap (STL/CLR)
Zamění obsah dvou kontejnerů.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
void swap(hash_multiset<Key>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *doprava*  
 Kontejner pro obsah s.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce Zamění řízené sekvence mezi `this` a *správné*. Provádí se v konstantním času a vyvolá žádné výjimky. Můžete použít jako rychlý způsob, jak Zamění obsah dvou kontejnerů.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_hash_multiset_swap.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct another container with repetition of values   
    Myhash_multiset c2;   
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

## <a name="to_array"></a> hash_multiset::to_array (STL/CLR)
Zkopíruje do nového pole řízené sekvence.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
cli::array<value_type>^ to_array();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí pole obsahující řízené sekvence. Použijete ji získat kopii řízenou sekvenci pole formuláře.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_hash_multiset_to_array.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
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
  
## <a name="upper_bound"></a> hash_multiset::upper_bound (STL/CLR)
Najde konec rozsahu, který odpovídá zadanému klíči.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
iterator upper_bound(key_type key);  
```  
  
#### <a name="parameters"></a>Parametry  
 *Klíč*  
 Hodnota klíče pro hledání.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce určuje poslední prvek `X` v řízené sekvenci, který vytvoří hodnotu hash na stejném kontejneru jako *klíč* a má stejné pořadí na *klíč*. Pokud žádný takový prvek neexistuje, nebo pokud `X` je po posledním prvku v řízené sekvenci vrátí [hash_multiset::end (STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md)`()`; v opačném případě vrátí iterátor, který určuje prvního prvku mimo `X`. Pomocí aktuálně najít konec pořadí prvků v řízené sekvenci, které odpovídají zadanému klíči.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_hash_multiset_upper_bound.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
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

## <a name="value_comp"></a> hash_multiset::value_comp (STL/CLR)
Zkopíruje pořadí delegáta pro dvě hodnoty prvků.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
value_compare^ value_comp();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí pořadí delegáta, který slouží k seřazení řízené sekvence. Použijete ji k porovnat dvě hodnoty prvků.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_hash_multiset_value_comp.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    Myhash_multiset::value_compare^ kcomp = c1.value_comp();   
  
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
compare(L'a', L'a') = True  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
```  

## <a name="value_compare"></a> hash_multiset::value_compare (STL/CLR)
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
// cliext_hash_multiset_value_compare.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    Myhash_multiset::value_compare^ kcomp = c1.value_comp();   
  
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
compare(L'a', L'a') = True  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
```  

## <a name="value_type"></a> hash_multiset::value_type (STL/CLR)
Typ prvku  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef generic_value value_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro `generic_value`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_hash_multiset_value_type.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" using value_type   
    for (Myhash_multiset::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in value_type object   
        Myhash_multiset::value_type val = *it;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
```  