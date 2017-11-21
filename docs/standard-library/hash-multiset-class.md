---
title: "hash_multiset – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- hash_set/stdext::hash_multiset
- hash_set/stdext::hash_multiset::allocator_type
- hash_set/stdext::hash_multiset::const_iterator
- hash_set/stdext::hash_multiset::const_pointer
- hash_set/stdext::hash_multiset::const_reference
- hash_set/stdext::hash_multiset::const_reverse_iterator
- hash_set/stdext::hash_multiset::difference_type
- hash_set/stdext::hash_multiset::iterator
- hash_set/stdext::hash_multiset::key_compare
- hash_set/stdext::hash_multiset::key_type
- hash_set/stdext::hash_multiset::pointer
- hash_set/stdext::hash_multiset::reference
- hash_set/stdext::hash_multiset::reverse_iterator
- hash_set/stdext::hash_multiset::size_type
- hash_set/stdext::hash_multiset::value_compare
- hash_set/stdext::hash_multiset::value_type
- hash_set/stdext::hash_multiset::begin
- hash_set/stdext::hash_multiset::cbegin
- hash_set/stdext::hash_multiset::cend
- hash_set/stdext::hash_multiset::clear
- hash_set/stdext::hash_multiset::count
- hash_set/stdext::hash_multiset::crbegin
- hash_set/stdext::hash_multiset::crend
- hash_set/stdext::hash_multiset::emplace
- hash_set/stdext::hash_multiset::emplace_hint
- hash_set/stdext::hash_multiset::empty
- hash_set/stdext::hash_multiset::end
- hash_set/stdext::hash_multiset::equal_range
- hash_set/stdext::hash_multiset::erase
- hash_set/stdext::hash_multiset::find
- hash_set/stdext::hash_multiset::get_allocator
- hash_set/stdext::hash_multiset::insert
- hash_set/stdext::hash_multiset::key_comp
- hash_set/stdext::hash_multiset::lower_bound
- hash_set/stdext::hash_multiset::max_size
- hash_set/stdext::hash_multiset::rbegin
- hash_set/stdext::hash_multiset::rend
- hash_set/stdext::hash_multiset::size
- hash_set/stdext::hash_multiset::swap
- hash_set/stdext::hash_multiset::upper_bound
- hash_set/stdext::hash_multiset::value_comp
dev_langs: C++
helpviewer_keywords:
- stdext::hash_multiset
- stdext::hash_multiset::allocator_type
- stdext::hash_multiset::const_iterator
- stdext::hash_multiset::const_pointer
- stdext::hash_multiset::const_reference
- stdext::hash_multiset::const_reverse_iterator
- stdext::hash_multiset::difference_type
- stdext::hash_multiset::iterator
- stdext::hash_multiset::key_compare
- stdext::hash_multiset::key_type
- stdext::hash_multiset::pointer
- stdext::hash_multiset::reference
- stdext::hash_multiset::reverse_iterator
- stdext::hash_multiset::size_type
- stdext::hash_multiset::value_compare
- stdext::hash_multiset::value_type
- stdext::hash_multiset::begin
- stdext::hash_multiset::cbegin
- stdext::hash_multiset::cend
- stdext::hash_multiset::clear
- stdext::hash_multiset::count
- stdext::hash_multiset::crbegin
- stdext::hash_multiset::crend
- stdext::hash_multiset::emplace
- stdext::hash_multiset::emplace_hint
- stdext::hash_multiset::empty
- stdext::hash_multiset::end
- stdext::hash_multiset::equal_range
- stdext::hash_multiset::erase
- stdext::hash_multiset::find
- stdext::hash_multiset::get_allocator
- stdext::hash_multiset::insert
- stdext::hash_multiset::key_comp
- stdext::hash_multiset::lower_bound
- stdext::hash_multiset::max_size
- stdext::hash_multiset::rbegin
- stdext::hash_multiset::rend
- stdext::hash_multiset::size
- stdext::hash_multiset::swap
- stdext::hash_multiset::upper_bound
- stdext::hash_multiset::value_comp
ms.assetid: 0580397a-a76e-40ad-aea2-5c6f3a9d0a21
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 019a80bd6752ea1fa974e9f567cde953d8cb2370
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2017
---
# <a name="hashmultiset-class"></a>hash_multiset – třída
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Hash_multiset – třída kontejneru je rozšířením standardní knihovna C++ a slouží k ukládání a rychlé načítání dat z kolekce, ve kterém hodnoty elementů obsažených sloužit jako hodnoty klíče a nemusí být jedinečný.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class Key, class Traits =hash_compare<Key, less <Key>>, class Allocator =allocator <Key>>  
class hash_multiset  
```  
  
#### <a name="parameters"></a>Parametry  
 *Klíč*  
 Datový typ elementu k uložení do hash_multiset.  
  
 `Traits`  
 Typ, který obsahuje dva objekty funkce, jeden třídy porovnat to znamená predikátu Binární možnost k porovnání dvou hodnot element jako klíči řazení určit jejich relativní pořadí a funkce hash klíče hodnoty unárních predikátem mapování elementů na nepodepsané celá čísla typu **size_t –**. Tento argument je volitelný a `hash_compare` *< klíč,* **menší***\<klíč >>* je výchozí hodnota.  
  
 `Allocator`  
 Typ, který představuje uložené allocator objekt, který zapouzdřuje informace o přidělení a zrušení přidělení paměti hash_multiset. Tento argument je volitelný a výchozí hodnota je **allocator***\<klíč >.*  
  
## <a name="remarks"></a>Poznámky  
 Hash_multiset je:  
  
-   Asociativní kontejner, což je kontejner proměnné velikosti, který podporuje efektivní načtení hodnoty prvku založené na přiřazené hodnotě klíče. Dále je to jednoduchý asociativní kontejner, protože jeho hodnoty prvku jsou jeho hodnoty klíče.  
  
-   Oboustranný, protože poskytuje obousměrný iterátor pro přístup k jeho prvkům.  
  
-   Algoritmus hash, protože jeho prvky jsou seskupeny do sad na základě hodnoty hash funkci použité pro hodnoty klíče elementů.  
  
-   Jedinečný v tom smyslu, že každý z jeho prvků musí mít jedinečný klíč. Protože hash_multiset je také jednoduché asociativní kontejner, jeho prvky jsou také jedinečný.  
  
-   Šablony třídy protože poskytuje funkce je obecný a proto nezávislé na konkrétní typ data obsažená jako elementy nebo klíče. Datové typy použité pro prvky a klíče jsou místo toho zadány jako parametry v šabloně třídy společně s funkcí porovnání a alokátorem.  
  
 Hlavní výhodou použití algoritmu hash přes řazení je vyšší efektivity: úspěšné algoritmu hash provádí vkládání, odstraňování a vyhledá v porovnání s čas konstantní Průměrná doba úměrná logaritmus počet elementů v kontejneru pro řazení techniky. Hodnotu prvku v sadě nelze změnit přímo. Místo toho musíte odstranit staré hodnoty a vložit prvky s novými hodnotami.  
  
 Volba typu kontejneru by měla obecně vycházet z typu vyhledávání a vkládání vyžadovaného aplikací. Hash asociativní kontejnery jsou optimalizované pro operace vyhledávání, vkládání a odebrání. Členské funkce, které explicitně podporují tyto operace jsou efektivní, pokud se používá s dobře navrženou hash funkce, provádět v čase, který je v průměru konstant a není závislá na počet elementů v kontejneru. Funkce dobře navrženou hash vytváří rovnoměrné rozdělení hodnot hash a minimalizuje počet kolizí, kde kolize říká, že je dojít, když odlišné hodnoty klíče jsou namapované na stejnou hodnotu hash. V nejhorším případě s funkci nejhorší možné hash počet operací je úměrná počet elementů v pořadí (lineární čas).  
  
 Hash_multiset by měl být, že splňuje asociativní kontejner volba, pokud jsou podmínky přidružení hodnoty k jejich klíče aplikací. Elementy hash_multiset může být více a sloužit jako vlastní řazení klíče, takže klíče nejsou jedinečné. Model pro tento typ struktury je uspořádaný seznam slov, v němž se slova mohou vyskytovat více než jednou. Kdyby více výskytů slova byla povolená, pak hash_set by byl strukturu odpovídajícího kontejneru. Pokud jedinečný definice byly připojené jako hodnoty do seznamu jedinečný klíčová slova, hash_map bude vhodné struktury tak, aby obsahovala tato data. Pokud místo toho definice nebyly jedinečný, hash_multimap by kontejneru výběru.  
  
 Hash_multiset řadí pořadí jimi řídí voláním objekt vlastnosti uložené hodnoty hash typu [value_compare –](#value_compare). Tento objekt uložené přístupná voláním členské funkce [key_comp –](#key_comp). Funkce objektu musí chovají stejně jako objekt třídy `hash_compare` *< klíč,* **menší***\<klíč >>.* Konkrétně pro všechny hodnoty *klíč* typu **klíč**, volání **znak**( *klíč*) vypočítá distribuci hodnot typu **size_t –**.  
  
 Obecně, tyto prvky musí být menší než srovnatelné pro toto pořadí, což znamená, že když jsou uvedeny dva prvky, může být stanoveno, zda jsou ekvivalentní (v tom smyslu, že ani jeden není menší než ten druhý), nebo že jeden je menší než druhý. To má za výsledek řazení mezi neekvivalentními prvky. Technicky je funkce porovnání binárním predikátem, který indukuje přísné slabé řazení, standardním matematickým způsobem. Predikát binární *f*( *x*, *y*) je objekt funkce, která má dva objekty argument x a y a návratovou hodnotu PRAVDA nebo NEPRAVDA. Řazení vynucená pro hash_multiset je striktní weak řazení Pokud binární predikát je Nereflexivní, antisymetrického a přenositelné a pokud ekvivalenční přenositelné, kde dva objekty x a y jsou definovány jako ekvivalentní při obě *f* ( *x*, *y*) a *f*( *y*, *x*) jsou false. Pokud silnější podmínka rovnosti mezi klíči nahradí ekvivalenci, stane se pořadí celkovým (v tom smyslu, že všechny prvky jsou uspořádány ve vztahu k sobě navzájem) a odpovídající klíče budou od sebe nerozeznatelné.  
  
 Skutečné pořadí prvků v řízené sekvenci závisí na funkci hash, funkci řazení a aktuální velikost tabulku hash uložené v objektu kontejneru. Aktuální velikost zatřiďovací tabulku nelze určit, takže nemůžete obecně předpovědět pořadí prvků v řízené sekvenci. Vkládání prvků nezruší platnost žádných iterátorů a odstranění prvků zruší platnost pouze těch iterátorů, které výslovně odkazovaly na odstraněné prvky.  
  
 Iterator poskytované hash_multiset – třída je iterator obousměrného ale vložit členské funkce tříd a hash_multiset mají verze, které jako parametry šablony trvat slabší vstupní iterator, jejichž požadavky na funkce jsou minimální více než ty zaručit třídou iterátory obousměrné. Různé koncepty iterátorů tvoří rodinu týkající se upřesnění jejich funkčnosti. Každý koncept iterator má svou vlastní hash_multiset požadavky a algoritmy, které pracují s nimi musí omezit jejich předpoklady pro splnění požadavků poskytované daný typ iterator. Lze předpokládat, že ke vstupnímu iterátoru lze přistoupit přes ukazatel pro odkazování na některý objekt a že může být zvýšen na další iterátor v pořadí. Toto je minimální hash_multiset funkcí, ale stačí mohli srozumitelně mluvit o rozsah iterátory [ `first`, `last`) v kontextu členské funkce tříd.  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[hash_multiset –](#hash_multiset)|Vytvoří `hash_multiset` který je prázdný nebo který je kopie všech nebo některých jiných součástí `hash_multiset`.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[allocator_type –](#allocator_type)|Typ, který reprezentuje `allocator` třídy pro `hash_multiset` objektu.|  
|[const_iterator –](#const_iterator)|Typ, který poskytuje obousměrné iterator, který může číst `const` element v `hash_multiset`.|  
|[const_pointer –](#const_pointer)|Typ, který poskytuje odkazy `const` element v `hash_multiset`.|  
|[const_reference –](#const_reference)|Typ, který obsahuje odkaz na `const` element uložené v `hash_multiset` pro čtení a provádění `const` operace.|  
|[const_reverse_iterator –](#const_reverse_iterator)|Typ, který poskytuje obousměrné iterator, který může číst všechny `const` element v `hash_multiset`.|  
|[difference_type –](#difference_type)|Typ se znaménkem, který poskytuje rozdíl mezi dvěma iterátory, které řeší elementů v rámci stejné `hash_multiset`.|  
|[iterator](#iterator)|Typ, který poskytuje obousměrné iterator, který může číst nebo upravovat libovolný element v `hash_multiset`.|  
|[key_compare –](#key_compare)|Typ, který poskytuje funkce objekt, který můžete porovnat dva klíče řazení k určení relativních pořadí dva elementy v `hash_multiset`.|  
|[key_type –](#key_type)|Typ, který popisuje objekt uložené jako element `hash_set` jako klíč řazení.|  
|[ukazatele](#pointer)|Typ, který poskytuje ukazatel na prvek v `hash_multiset`.|  
|[referenční dokumentace](#reference)|Typ, který obsahuje odkaz na element uložené v `hash_multiset`.|  
|[reverse_iterator –](#reverse_iterator)|Typ, který poskytuje obousměrné iterator, které můžou číst nebo upravte element v odstínech `hash_multiset`.|  
|[size_type –](#size_type)|Typ celé číslo bez znaménka, která představuje počet elementů ve `hash_multiset`.|  
|[value_compare –](#value_compare)|Typ, který poskytuje dva objekty funkce, binární predikátu porovnání – třída, která můžete porovnat dvě hodnoty elementu `hash_multiset` určit jejich relativní pořadí a unární operátor predikátu, vytvoří hodnotu hash elementy.|  
|[value_type](#value_type)|Typ, který popisuje objekt uložené jako element `hash_multiset` jako hodnotu.|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[začít](#begin)|Vrátí iterátor, který řeší prvním elementem v `hash_multiset`.|  
|[cbegin –](#cbegin)|Vrátí const iterator adresování prvním elementem v `hash_multiset`.|  
|[cend –](#cend)|Vrátí const iterator, která řeší úspěšné posledním prvkem v umístění `hash_multiset`.|  
|[Vymazat](#clear)|Vymaže všechny elementy `hash_multiset`.|  
|[počet](#count)|Vrátí počet prvků v `hash_multiset` jejichž klíč odpovídá parametru zadaný klíč|  
|[crbegin –](#crbegin)|Vrátí const iterator adresování prvním elementem v odstínech `hash_multiset`.|  
|[crend –](#crend)|Vrátí const iterator, která řeší umístění úspěšné posledním prvkem v odstínech `hash_multiset`.|  
|[emplace –](#emplace)|Vloží element v místě do zkonstruovat `hash_multiset`.|  
|[emplace_hint –](#emplace_hint)|Vloží element v místě do zkonstruovat `hash_multiset`, s pomocným parametrem umístění.|  
|[prázdný](#empty)|Pokud testy `hash_multiset` je prázdný.|  
|[end](#end)|Vrátí iterátor, který řeší úspěšné posledním prvkem v umístění `hash_multiset`.|  
|[equal_range –](#equal_range)|Vrátí pár iterátory prvním elementem v v uvedeném pořadí `hash_multiset` s klíčem, který je větší, než je zadaný klíč a prvním elementem v `hash_multiset` s klíčem, který je rovna nebo větší než klíč.|  
|[vymazání](#erase)|Odebere element nebo rozsah elementů v `hash_multiset` ze zadaných pozic nebo odebere elementy, které odpovídají zadaným klíčem.|  
|[Najít](#find)|Vrátí iterovat adresování umístění elementu v `hash_multiset` který má klíč ekvivalentní k zadanému klíči.|  
|[get_allocator –](#get_allocator)|Vrátí kopii `allocator` objekt použitý k vytvoření `hash_multiset`.|  
|[Vložení](#insert)|Vloží elementu nebo rozsahu prvků do `hash_multiset`.|  
|[key_comp –](#key_compare)|Načte kopii porovnání objekt použitý k pořadí klíčů v `hash_multiset`.|  
|[lower_bound –](#lower_bound)|Vrátí iterovat prvním elementem v `hash_multiset` s klíčem, který je rovna nebo větší než je zadaný klíč.|  
|[max_size –](#max_size)|Vrátí maximální délka `hash_multiset`.|  
|[rbegin –](#rbegin)|Vrátí iterovat adresování prvním elementem v odstínech `hash_multiset`.|  
|[rend –](#rend)|Vrátí iterátor, který řeší umístění úspěšné posledním prvkem v odstínech `hash_multiset`.|  
|[velikost](#size)|Vrátí počet prvků v `hash_multiset`.|  
|[swap](#swap)|Výměny dva elementy `hash_multiset`s.|  
|[upper_bound –](#upper_bound)|Vrátí iterovat prvním elementem v `hash_multiset` , s klíčem, který je rovna nebo větší než je zadaný klíč.|  
|[value_comp –](#value_comp)|Načte kopii objekt hash vlastnosti použít k hash a pořadí klíčové hodnoty v elementu `hash_multiset`.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[hash_multiset::Operator =](#op_eq)|Elementy hash_multiset nahradí kopii jiného hash_multiset.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<hash_set >  
  
 **Namespace:** stdext –  
  
##  <a name="allocator_type"></a>hash_multiset::allocator_type  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Typ, který reprezentuje allocator – třída objektu hash_multiset.  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;  
```  
  
### <a name="example"></a>Příklad  
  Podívejte se příklad [get_allocator –](#get_allocator) pro příklad použití`allocator_type`  
  
##  <a name="begin"></a>hash_multiset::begin  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Vrátí iterátor, který řeší prvním elementem v hash_multiset.  
  
```  
const_iterator begin() const;

iterator begin();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Adresování prvním elementem v hash_multiset nebo umístění úspěšné prázdný hash_multiset iterator obousměrné.  
  
### <a name="remarks"></a>Poznámky  
 Pokud vrátí hodnotu, která **začít** je přiřazena k `const_iterator`, elementy v objektu hash_multiset nemůže být upraven. Pokud vrátí hodnotu, která **začít** je přiřazena k **iterator**, elementy v objektu hash_multiset je možné upravit.  
  
   
  
### <a name="example"></a>Příklad  
  
```cpp  
// hash_multiset_begin.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> hms1;  
   hash_multiset <int>::iterator hms1_Iter;  
   hash_multiset <int>::const_iterator hms1_cIter;  
  
   hms1.insert( 1 );  
   hms1.insert( 2 );  
   hms1.insert( 3 );  
  
   hms1_Iter = hms1.begin( );  
   cout << "The first element of hms1 is " << *hms1_Iter << endl;  
  
   hms1_Iter = hms1.begin( );  
   hms1.erase( hms1_Iter );  
  
   // The following 2 lines would err because the iterator is const  
   // hms1_cIter = hms1.begin( );  
   // hms1.erase( hms1_cIter );  
  
   hms1_cIter = hms1.begin( );  
   cout << "The first element of hms1 is now " << *hms1_cIter << endl;  
}  
```  
  
```Output  
The first element of hms1 is 1  
The first element of hms1 is now 2  
```  
  
##  <a name="cbegin"></a>hash_multiset::cbegin  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Vrátí const iterator, která řeší prvním elementem v hash_multiset.  
  
```  
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Const iterator obousměrného adresování prvním elementem v [hash_multiset](../standard-library/hash-multiset-class.md) nebo umístění úspěšné prázdnou `hash_multiset`.  
  
### <a name="remarks"></a>Poznámky  
 S návratovou hodnotou `cbegin`, elementů v `hash_multiset` objekt nelze změnit.  
  
   
  
### <a name="example"></a>Příklad  
  
```cpp  
// hash_multiset_cbegin.cpp  
// compile with: /EHsc  
#include <hash_multiset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> hs1;  
   hash_multiset <int>::const_iterator hs1_cIter;  
  
   hs1.insert( 1 );  
   hs1.insert( 2 );  
   hs1.insert( 3 );  
  
   hs1_cIter = hs1.cbegin( );  
   cout << "The first element of hs1 is " << *hs1_cIter << endl;  
}  
```  
  
```Output  
The first element of hs1 is 1  
```  
  
##  <a name="cend"></a>hash_multiset::cend  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Vrátí const iterator, která řeší úspěšné posledním prvkem v hash_multiset umístění.  
  
```  
const_iterator cend() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Const iterator obousměrného, která řeší úspěšné posledním prvkem v umístění [hash_multiset](../standard-library/hash-multiset-class.md). Pokud `hash_multiset` je prázdný, pak `hash_multiset::cend == hash_multiset::begin`.  
  
### <a name="remarks"></a>Poznámky  
 `cend`slouží k otestování, jestli iterovat byl dosažen konec jeho `hash_multiset`. Hodnoty vrácené `cend` by neměl být vyhodnoceny odkazy.  
  
   
  
### <a name="example"></a>Příklad  
  
```cpp  
// hash_multiset_cend.cpp  
// compile with: /EHsc  
#include <hash_multiset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> hs1;  
   hash_multiset <int> :: const_iterator hs1_cIter;  
  
   hs1.insert( 1 );  
   hs1.insert( 2 );  
   hs1.insert( 3 );  
  
   hs1_cIter = hs1.cend( );  
   hs1_cIter--;  
   cout << "The last element of hs1 is " << *hs1_cIter << endl;  
}  
```  
  
```Output  
The last element of hs1 is 3  
```  
  
##  <a name="clear"></a>hash_multiset::clear  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Vymaže všechny elementy hash_multiset.  
  
```  
void clear();
```  
  
### <a name="remarks"></a>Poznámky  
   
  
### <a name="example"></a>Příklad  
  
```cpp  
// hash_multiset_clear.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> hms1;  
  
   hms1.insert( 1 );  
   hms1.insert( 2 );  
  
   cout << "The size of the hash_multiset is initially " << hms1.size( )  
        << "." << endl;  
  
   hms1.clear( );  
   cout << "The size of the hash_multiset after clearing is "   
        << hms1.size( ) << "." << endl;  
}  
```  
  
```Output  
The size of the hash_multiset is initially 2.  
The size of the hash_multiset after clearing is 0.  
```  
  
##  <a name="const_iterator"></a>hash_multiset::const_iterator  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Typ, který poskytuje obousměrné iterator, který může číst **const** element v hash_multiset.  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ `const_iterator` nelze použít k úpravě hodnota elementu.  
  
   
  
### <a name="example"></a>Příklad  
  Podívejte se příklad [začít](#begin) pro příklad použití `const_iterator`.  
  
##  <a name="const_pointer"></a>hash_multiset::const_pointer  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Typ, který poskytuje odkazy **const** element v hash_multiset.  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ `const_pointer` nelze použít k úpravě hodnota elementu.  
  
 Ve většině případů [const_iterator –](#const_iterator) se má použít pro přístup k elementům v **const** hash_multiset objektu.  
  
   
  
##  <a name="const_reference"></a>hash_multiset::const_reference  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Typ, který obsahuje odkaz na **const** element uložené v hash_multiset pro čtení a provádění **const** operace.  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_reference const_reference;  
```  
  
### <a name="remarks"></a>Poznámky  
   
  
### <a name="example"></a>Příklad  
  
```cpp  
// hash_multiset_const_reference.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> hms1;  
  
   hms1.insert( 10 );  
   hms1.insert( 20 );  
  
   // Declare and initialize a const_reference &Ref1   
   // to the 1st element  
   const int &Ref1 = *hms1.begin( );  
  
   cout << "The first element in the hash_multiset is "  
        << Ref1 << "." << endl;  
  
   // The following line would cause an error because the   
   // const_reference cannot be used to modify the hash_multiset  
   // Ref1 = Ref1 + 5;  
}  
```  
  
```Output  
The first element in the hash_multiset is 10.  
```  
  
##  <a name="const_reverse_iterator"></a>hash_multiset::const_reverse_iterator  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Typ, který poskytuje obousměrné iterator, který může číst všechny **const** element v hash_multiset.  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ `const_reverse_iterator` nelze změnit hodnotu elementu a je použít k iteraci v rámci hash_multiset pozpátku.  
  
   
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [rend](#rend) příklad toho, jak deklarace a používání `const_reverse_iterator`.  
  
##  <a name="count"></a>hash_multiset::Count  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Vrátí počet prvků v hash_multiset, jehož klíč odpovídá parametru zadaný klíč.  
  
```  
size_type count(const Key& key) const;
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klíč elementy lze porovnat z hash_multiset.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet elementů v hash_multiset klíčem zadán parametr.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí počet prvků v následujícím rozsahu:  
  
 [ `lower_bound` (_ `Key` ), `upper_bound` (\_ `Key` ) ).  
  
   
  
### <a name="example"></a>Příklad  
  Následující příklad ukazuje použití hash_multiset::count – členská funkce.  
  
```  
// hash_multiset_count.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
    using namespace std;  
    using namespace stdext;  
    hash_multiset<int> hms1;  
    hash_multiset<int>::size_type i;  
  
    hms1.insert(1);  
    hms1.insert(1);  
  
    // Keys do not need to be unique in hash_multiset,  
    // so duplicates may exist.  
    i = hms1.count(1);  
    cout << "The number of elements in hms1 with a sort key of 1 is: "  
         << i << "." << endl;  
  
    i = hms1.count(2);  
    cout << "The number of elements in hms1 with a sort key of 2 is: "  
         << i << "." << endl;  
}  
```  
  
```Output  
The number of elements in hms1 with a sort key of 1 is: 2.  
The number of elements in hms1 with a sort key of 2 is: 0.  
```  
  
##  <a name="crbegin"></a>hash_multiset::crbegin  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Vrátí const iterator adresování prvním elementem v invertovaných hash_multiset.  
  
```  
const_reverse_iterator crbegin() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Const reverse obousměrného iterator adresování prvním elementem v odstínech [hash_multiset](../standard-library/hash-multiset-class.md) nebo řešení, co je posledním prvkem v unreversed `hash_multiset`.  
  
### <a name="remarks"></a>Poznámky  
 `crbegin`se používá s odstínech `hash_multiset` stejně jako [hash_multiset::begin](#begin) se používá s `hash_multiset`.  
  
 S návratovou hodnotou `crbegin`, `hash_multiset` objekt nelze změnit.  
  
 `crbegin`lze použít k iteraci v rámci `hash_multiset` zpětné.  
  
   
  
### <a name="example"></a>Příklad  
  
```cpp  
// hash_multiset_crbegin.cpp  
// compile with: /EHsc  
#include <hash_multiset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> hs1;  
   hash_multiset <int>::const_reverse_iterator hs1_crIter;  
  
   hs1.insert( 10 );  
   hs1.insert( 20 );  
   hs1.insert( 30 );  
  
   hs1_crIter = hs1.crbegin( );  
   cout << "The first element in the reversed hash_multiset is "  
        << *hs1_crIter << "." << endl;  
}  
```  
  
```Output  
The first element in the reversed hash_multiset is 30.  
```  
  
##  <a name="crend"></a>hash_multiset::crend  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Vrátí const iterator, která řeší úspěšné posledním prvkem v invertovaných hash_multiset umístění.  
  
```  
const_reverse_iterator crend() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Const reverse iterator obousměrného, která řeší umístění úspěšné posledním prvkem v odstínech [hash_multiset](../standard-library/hash-multiset-class.md) (umístění, které měl před prvním elementem v unreversed `hash_multiset`).  
  
### <a name="remarks"></a>Poznámky  
 `crend`se používá s odstínech `hash_multiset` stejně jako [hash_multiset::end](#end) se používá s `hash_multiset`.  
  
 S návratovou hodnotou `crend`, `hash_multiset` objekt nelze změnit.  
  
 `crend`slouží k testování, aby se jestli zpětné iterator dosáhne konce své hash_multiset.  
  
   
  
### <a name="example"></a>Příklad  
  
```cpp  
// hash_multiset_crend.cpp  
// compile with: /EHsc  
#include <hash_multiset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> hs1;  
   hash_multiset <int>::const_reverse_iterator hs1_crIter;  
  
   hs1.insert( 10 );  
   hs1.insert( 20 );  
   hs1.insert( 30 );  
  
   hs1_crIter = hs1.crend( );  
   hs1_crIter--;  
   cout << "The last element in the reversed hash_multiset is "  
        << *hs1_crIter << "." << endl;  
}  
```  
  
```Output  
The last element in the reversed hash_multiset is 10.  
```  
  
##  <a name="difference_type"></a>hash_multiset::difference_type  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Typ se znaménkem, který poskytuje rozdíl mezi dvěma iterátory, které řeší elementů v rámci stejné hash_multiset.  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::difference_type difference_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 `difference_type` Je typ vrácena, pokud odečtením nebo zvyšování prostřednictvím iterátory kontejneru. `difference_type` Se obvykle používá k reprezentování počet elementů v rozsahu [ `first`, `last`) mezi iterátory `first` a `last`, obsahuje element, na kterou odkazuje `first` a rozsah elementů než , ale bez zahrnutí elementu, na kterou odkazuje `last`.  
  
 Všimněte si, že i když `difference_type` je k dispozici pro všechny iterátory, které splňují požadavky vstupní iterator, který obsahuje třídu obousměrného iterátory nepodporuje reverzibilního kontejnery, jako jsou sady. Odčítání mezi iterátory je podporována pouze poskytované kontejner náhodný přístup například vektoru nebo deque iterátory náhodný přístup.  
  
   
  
### <a name="example"></a>Příklad  
  
```cpp  
// hash_multiset_diff_type.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <hash_set>  
#include <algorithm>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
  
   hash_multiset <int> hms1;  
   hash_multiset <int>::iterator hms1_Iter, hms1_bIter, hms1_eIter;  
  
   hms1.insert( 20 );  
   hms1.insert( 10 );  
  
   // hash_multiset elements need not be unique  
   hms1.insert( 20 );  
  
   hms1_bIter = hms1.begin( );  
   hms1_eIter = hms1.end( );  
  
   hash_multiset <int>::difference_type   df_typ5, df_typ10,  
        df_typ20;  
  
   df_typ5 = count( hms1_bIter, hms1_eIter, 5 );  
   df_typ10 = count( hms1_bIter, hms1_eIter, 10 );  
   df_typ20 = count( hms1_bIter, hms1_eIter, 20 );  
  
   // The keys & hence the elements of a hash_multiset  
   // need not be unique and may occur multiple times  
   cout << "The number '5' occurs " << df_typ5  
        << " times in hash_multiset hms1.\n";  
   cout << "The number '10' occurs " << df_typ10  
        << " times in hash_multiset hms1.\n";  
   cout << "The number '20' occurs " << df_typ20  
        << " times in hash_multiset hms1.\n";  
  
   // Count the number of elements in a hash_multiset  
   hash_multiset <int>::difference_type  df_count = 0;  
   hms1_Iter = hms1.begin( );  
   while ( hms1_Iter != hms1_eIter)  
   {  
      df_count++;  
      hms1_Iter++;  
   }  
  
   cout << "The number of elements in the hash_multiset hms1 is "   
        << df_count << "." << endl;  
}  
```  
  
```Output  
The number '5' occurs 0 times in hash_multiset hms1.  
The number '10' occurs 1 times in hash_multiset hms1.  
The number '20' occurs 2 times in hash_multiset hms1.  
The number of elements in the hash_multiset hms1 is 3.  
```  
  
##  <a name="emplace"></a>hash_multiset::emplace  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Vloží element sestavený na místě do hash_multiset.  
  
```  
template <class ValTy>  
iterator insert(ValTy&& val);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|`val`|Hodnota elementu, který má být vložen do [hash_multiset](../standard-library/hash-multiset-class.md) Pokud `hash_multiset` již obsahuje daný element nebo více obecně element, jehož klíč je ekvivalentně řazení.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `emplace` – Členská funkce vrátí iterátor, který odkazuje na pozici, kde byla vložena nového elementu.  
  
### <a name="remarks"></a>Poznámky  
   
  
### <a name="example"></a>Příklad  
  
```cpp  
// hash_multiset_emplace.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
#include <string>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset<string> hms3;  
   string str1("a");  
  
   hms3.emplace(move(str1));  
   cout << "After the emplace insertion, hms3 contains "  
      << *hms3.begin() << "." << endl;  
}  
```  
  
```Output  
After the emplace insertion, hms3 contains a.  
```  
  
##  <a name="emplace_hint"></a>hash_multiset::emplace_hint  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Vloží element sestavený na místě do hash_multiset, s pomocným parametrem umístění.  
  
```  
template <class ValTy>  
iterator insert(
    const_iterator _Where,  
    ValTy&& val);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|`val`|Hodnota elementu, který má být vložen do [hash_multiset](../standard-library/hash-multiset-class.md) Pokud `hash_multiset` již obsahuje daný element nebo více obecně element, jehož klíč je ekvivalentně řazení.|  
|`_Where`|Místo zahájení vyhledání správného bodu vložení. (Vložení se může objevit v amortizovaný konstantní čas, místo logaritmické čas, pokud bod vložení následuje `_Where`.)|  
  
### <a name="return-value"></a>Návratová hodnota  
 [Hash_multiset::emplace](#emplace) – členská funkce vrátí iterátor, který odkazuje na pozici, kde byl nový element vložený do `hash_multiset`.  
  
### <a name="remarks"></a>Poznámky  
 Vložení se může objevit v amortizovaný konstantní čas, místo logaritmické čas, pokud bod vložení následuje `_Where`.  
  
   
  
### <a name="example"></a>Příklad  
  
```cpp  
// hash_multiset_emplace_hint.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
#include <string>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset<string> hms1;  
   string str1("a");  
  
   hms1.insert(hms1.begin(), move(str1));  
   cout << "After the emplace insertion, hms1 contains "  
      << *hms1.begin() << "." << endl;  
}  
```  
  
```Output  
After the emplace insertion, hms1 contains a.  
```  
  
##  <a name="empty"></a>hash_multiset::Empty  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Testy, pokud hash_multiset je prázdný.  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud hash_multiset je prázdná. **false** Pokud je hash_multiset neprázdný.  
  
### <a name="remarks"></a>Poznámky  
   
  
### <a name="example"></a>Příklad  
  
```cpp  
// hash_multiset_empty.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> hms1, hms2;  
   hms1.insert ( 1 );  
  
   if ( hms1.empty( ) )  
      cout << "The hash_multiset hms1 is empty." << endl;  
   else  
      cout << "The hash_multiset hms1 is not empty." << endl;  
  
   if ( hms2.empty( ) )  
      cout << "The hash_multiset hms2 is empty." << endl;  
   else  
      cout << "The hash_multiset hms2 is not empty." << endl;  
}  
```  
  
```Output  
The hash_multiset hms1 is not empty.  
The hash_multiset hms2 is empty.  
```  
  
##  <a name="end"></a>hash_multiset::end  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Vrátí iterátor, který řeší úspěšné posledním prvkem v hash_multiset umístění.  
  
```  
const_iterator end() const;

iterator end();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterator obousměrného, která řeší úspěšné posledním prvkem v hash_multiset umístění. Pokud hash_multiset je prázdný, hash_multiset::end == hash_multiset::begin.  
  
### <a name="remarks"></a>Poznámky  
 **end** slouží k otestování, jestli iterovat dosáhne konce své hash_multiset. Hodnoty vrácené **end** by neměl být vyhodnoceny odkazy.  
  
   
  
### <a name="example"></a>Příklad  
  
```cpp  
// hash_multiset_end.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> hms1;  
   hash_multiset <int> :: iterator hms1_Iter;  
   hash_multiset <int> :: const_iterator hms1_cIter;  
  
   hms1.insert( 1 );  
   hms1.insert( 2 );  
   hms1.insert( 3 );  
  
   hms1_Iter = hms1.end( );  
   hms1_Iter--;  
   cout << "The last element of hms1 is " << *hms1_Iter << endl;  
  
   hms1.erase( hms1_Iter );  
  
   // The following 3 lines would err because the iterator is const  
   // hms1_cIter = hms1.end( );  
   // hms1_cIter--;  
   // hms1.erase( hms1_cIter );  
  
   hms1_cIter = hms1.end( );  
   hms1_cIter--;  
   cout << "The last element of hms1 is now " << *hms1_cIter << endl;  
}  
```  
  
```Output  
The last element of hms1 is 3  
The last element of hms1 is now 2  
```  
  
##  <a name="equal_range"></a>hash_multiset::equal_range  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Vrátí funkce pár iterátory prvním elementem v hash_multiset s klíčem, který je větší než je zadaný klíč a prvním elementem v hash_multiset s klíčem, který je rovna nebo větší než klíč.  
  
```  
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Argument klíč, který se má porovnat s klíč řazení elementu z hash_multiset prohledávaný.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pár iterátory, kde je první [lower_bound –](#lower_bound) klíč a druhý je [upper_bound –](#upper_bound) klíče.  
  
 Pro přístup k první iterator páru `pr` vrácené funkcí člen, použijte `pr`. **první** a pokud chcete dereference iterator dolní mez, použijte \*( `pr`. **nejprve**). Pro přístup k druhý iterator páru `pr` vrácené funkcí člen, použijte `pr`. **druhý** a pokud chcete dereference iterator horní mez, použijte \*( `pr`. **druhý**).  
  
   
  
### <a name="example"></a>Příklad  
  
```cpp  
// hash_multiset_equal_range.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   typedef hash_multiset<int> IntHSet;  
   IntHSet hms1;  
   hash_multiset <int> :: const_iterator hms1_RcIter;  
  
   hms1.insert( 10 );  
   hms1.insert( 20 );  
   hms1.insert( 30 );  
  
   pair <IntHSet::const_iterator, IntHSet::const_iterator> p1, p2;  
   p1 = hms1.equal_range( 20 );  
  
   cout << "The upper bound of the element with "  
        << "a key of 20\nin the hash_multiset hms1 is: "  
        << *(p1.second) << "." << endl;  
  
   cout << "The lower bound of the element with "  
        << "a key of 20\nin the hash_multiset hms1 is: "  
        << *(p1.first) << "." << endl;  
  
   // Compare the upper_bound called directly   
   hms1_RcIter = hms1.upper_bound( 20 );  
   cout << "A direct call of upper_bound( 20 ) gives "  
        << *hms1_RcIter << "," << endl  
        << "matching the 2nd element of the pair"  
        << " returned by equal_range( 20 )." << endl;  
  
   p2 = hms1.equal_range( 40 );  
  
   // If no match is found for the key,  
   // both elements of the pair return end( )  
   if ( ( p2.first == hms1.end( ) )   
      && ( p2.second == hms1.end( ) ) )  
      cout << "The hash_multiset hms1 doesn't have an element "  
           << "with a key less than 40." << endl;  
   else  
      cout << "The element of hash_multiset hms1"  
           << "with a key >= 40 is: "  
           << *(p1.first) << "." << endl;  
}  
```  
  
```Output  
The upper bound of the element with a key of 20  
in the hash_multiset hms1 is: 30.  
The lower bound of the element with a key of 20  
in the hash_multiset hms1 is: 20.  
A direct call of upper_bound( 20 ) gives 30,  
matching the 2nd element of the pair returned by equal_range( 20 ).  
The hash_multiset hms1 doesn't have an element with a key less than 40.  
```  
  
##  <a name="erase"></a>hash_multiset::Erase  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Odebere element nebo rozsah elementů v hash_multiset ze zadaných pozic nebo odebere prvky, které odpovídají zadaným klíčem.  
  
```  
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```  
  
### <a name="parameters"></a>Parametry  
 `_Where`  
 Pozice elementu, který má být odebrán z hash_multiset.  
  
 `first`  
 Pozice první prvek odebrán z hash_multiset.  
  
 `last`  
 Pozice bezprostředně za posledním elementem odebrán z hash_multiset.  
  
 `key`  
 Klíč elementů má být odebrán z hash_multiset.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pro první dva členské funkce obousměrné iterator, označí první prvek zbývající nad rámec žádné elementy, odebrat nebo odkazy na konec hash_multiset, pokud neexistuje žádný takový prvek. Třetí funkce člen, počet elementů, které byly odebrány z hash_multiset.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce nikdy vyvolat výjimku.  
  
   
  
### <a name="example"></a>Příklad  
  Následující příklad ukazuje použití hash_multiset::erase – členská funkce.  
  
```  
// hash_multiset_erase.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    using namespace stdext;  
    hash_multiset<int> hms1, hms2, hms3;  
    hash_multiset<int> :: iterator pIter, Iter1, Iter2;  
    int i;  
    hash_multiset<int>::size_type n;  
  
    for (i = 1; i < 5; i++)  
    {  
        hms1.insert(i);  
        hms2.insert(i * i);  
        hms3.insert(i - 1);  
    }  
  
    // The 1st member function removes an element at a given position  
    Iter1 = ++hms1.begin();  
    hms1.erase(Iter1);  
  
    cout << "After the 2nd element is deleted,\n "  
         << "the hash_multiset hms1 is:" ;  
    for (pIter = hms1.begin(); pIter != hms1.end(); pIter++)  
        cout << " " << *pIter;  
    cout << "." << endl;  
  
    // The 2nd member function removes elements  
    // in the range [ first,  last)  
    Iter1 = ++hms2.begin();  
    Iter2 = --hms2.end();  
    hms2.erase(Iter1, Iter2);  
  
    cout << "After the middle two elements are deleted,\n "  
         << "the hash_multiset hms2 is:" ;  
    for (pIter = hms2.begin(); pIter != hms2.end(); pIter++)  
        cout << " " << *pIter;  
    cout << "." << endl;  
  
    // The 3rd member function removes elements with a given  key  
    n = hms3.erase(2);  
  
    cout << "After the element with a key of 2 is deleted,\n "  
         << "the hash_multiset hms3 is:" ;  
    for (pIter = hms3.begin(); pIter != hms3.end(); pIter++)  
        cout << " " << *pIter;  
    cout << "." << endl;  
  
    // The 3rd member function returns the number of elements removed  
    cout << "The number of elements removed from hms3 is: "  
         << n << "." << endl;  
  
    // The dereferenced iterator can also be used to specify a key  
    Iter1 = ++hms3.begin();  
    hms3.erase(Iter1);  
  
    cout << "After another element with a key "  
         << "equal to that of the 2nd element\n is deleted, "  
         << "the hash_multiset hms3 is:" ;  
    for (pIter = hms3.begin(); pIter != hms3.end(); pIter++)  
        cout << " " << *pIter;  
    cout << "." << endl;  
}  
```  
  
```Output  
After the 2nd element is deleted,  
 the hash_multiset hms1 is: 1 3 4.  
After the middle two elements are deleted,  
 the hash_multiset hms2 is: 16 4.  
After the element with a key of 2 is deleted,  
 the hash_multiset hms3 is: 0 1 3.  
The number of elements removed from hms3 is: 1.  
After another element with a key equal to that of the 2nd element  
 is deleted, the hash_multiset hms3 is: 0 3.  
```  
  
##  <a name="find"></a>hash_multiset::Find  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Vrátí iterovat adresování umístění elementu v hash_multiset, s klíčem ekvivalentní k zadanému klíči.  
  
```  
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Argument klíč odpovídala klíč řazení elementu z hash_multiset být vyhledán.  
  
### <a name="return-value"></a>Návratová hodnota  
 [Iterator](#iterator) nebo [const_iterator –](#const_iterator) , který se týká umístění element ekvivalentní k zadanému klíči nebo který adres umístění posledním prvkem v hash_multiset úspěšné, pokud je nalezena žádná shoda pro klíč nalezen.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí iterátor, který řeší element v hash_multiset, jehož klíč řazení je **ekvivalentní** argument klíč v predikátu Binární indukuje řazení na základě méně – než srovnání vztah.  
  
 Pokud vrátí hodnotu, která **najít** je přiřazena k `const_iterator`, hash_multiset objekt nelze změnit. Pokud vrátí hodnotu, která **najít** je přiřazena k **iterator**, objekt hash_multiset je možné upravit.  
  
   
  
### <a name="example"></a>Příklad  
  
```cpp  
// hash_multiset_find.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> hms1;  
   hash_multiset <int> :: const_iterator hms1_AcIter, hms1_RcIter;  
  
   hms1.insert( 10 );  
   hms1.insert( 20 );  
   hms1.insert( 30 );  
  
   hms1_RcIter = hms1.find( 20 );  
   cout << "The element of hash_multiset hms1 with a key of 20 is: "  
        << *hms1_RcIter << "." << endl;  
  
   hms1_RcIter = hms1.find( 40 );  
  
   // If no match is found for the key, end( ) is returned  
   if ( hms1_RcIter == hms1.end( ) )  
      cout << "The hash_multiset hms1 doesn't have an element "  
           << "with a key of 40." << endl;  
   else  
      cout << "The element of hash_multiset hms1 with a key of 40 is: "  
           << *hms1_RcIter << "." << endl;  
  
   // The element at a specific location in the hash_multiset can be found   
   // by using a dereferenced iterator addressing the location  
   hms1_AcIter = hms1.end( );  
   hms1_AcIter--;  
   hms1_RcIter = hms1.find( *hms1_AcIter );  
   cout << "The element of hms1 with a key matching "  
        << "that of the last element is: "  
        << *hms1_RcIter << "." << endl;  
}  
```  
  
```Output  
The element of hash_multiset hms1 with a key of 20 is: 20.  
The hash_multiset hms1 doesn't have an element with a key of 40.  
The element of hms1 with a key matching that of the last element is: 30.  
```  
  
##  <a name="get_allocator"></a>hash_multiset::get_allocator  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Vrátí kopii allocator objekt použitý k vytvoření hash_multiset.  
  
```  
Allocator get_allocator() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Allocator slouží ke správě paměti, což je parametr šablony třídy hash_multiset `Allocator`.  
  
 Další informace o `Allocator`, najdete v části poznámky [hash_multiset – třída](../standard-library/hash-multiset-class.md) tématu.  
  
### <a name="remarks"></a>Poznámky  
 Alokátorů pro třídu hash_multiset zadejte, jak třída spravuje úložiště. Alokátorů výchozí součástí standardní knihovna C++ – třídy kontejnerů postačí pro většinu programovacích potřeb. Psaní a pomocí vlastní allocator – třída je rozšířená C++.  
  
   
  
### <a name="example"></a>Příklad  
  
```cpp  
// hash_multiset_get_allocator.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
  
   // The following lines declare objects  
   // that use the default allocator.  
   hash_multiset <int, hash_compare <int, less<int> > > hms1;  
   hash_multiset <int, hash_compare <int, greater<int> > > hms2;  
   hash_multiset <double, hash_compare <double,  
      less<double> >, allocator<double> > hms3;  
  
   hash_multiset <int, hash_compare <int,  
      greater<int> > >::allocator_type hms2_Alloc;  
   hash_multiset <double>::allocator_type hms3_Alloc;  
   hms2_Alloc = hms2.get_allocator( );  
  
   cout << "The number of integers that can be allocated"  
        << endl << "before free memory is exhausted: "  
        << hms1.max_size( ) << "." << endl;  
  
   cout << "The number of doubles that can be allocated"  
        << endl << "before free memory is exhausted: "  
        << hms3.max_size( ) <<  "." << endl;  
  
   // The following lines create a hash_multiset hms4  
   // with the allocator of hash_multiset hms1.  
   hash_multiset <int>::allocator_type hms4_Alloc;  
   hash_multiset <int> hms4;  
   hms4_Alloc = hms2.get_allocator( );  
  
   // Two allocators are interchangeable if  
   // storage allocated from each can be  
   // deallocated by the other  
   if( hms2_Alloc == hms4_Alloc )  
   {  
      cout << "The allocators are interchangeable."  
           << endl;  
   }  
   else  
   {  
      cout << "The allocators are not interchangeable."  
           << endl;  
   }  
}  
```  
  
##  <a name="hash_multiset"></a>hash_multiset::hash_multiset  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Vytvoří `hash_multiset` který je prázdný nebo který je kopie všech nebo některých jiných součástí `hash_multiset`.  
  
```  
hash_multiset();

explicit hash_multiset(
    const Traits& Comp);

hash_multiset(
    const Traits& Comp,  
    const Allocator& Al);

hash_multiset(
    const hash_multiset<Key, Traits, Allocator>& Right);

hash_multiset(
    hash_multiset&& Right  
};  
hash_multiset (initializer_list<Type> IList);

hash_multiset(
    initializer_list<Tu[e> IList, const Compare& Comp):  
hash_multiset(
    initializer_list<Type> IList, const Compare& Comp, const Allocator& Al);

template <class InputIterator>  
hash_multiset(
 InputIterator First,  
    InputIterator Last);

template <class InputIterator>  
hash_multiset(
 InputIterator First,  
    InputIterator Last,  
    const Traits& Comp);

template <class InputIterator>  
hash_multiset(
 InputIterator First,  
    InputIterator Last,  
    const Traits& Comp,  
    const Allocator& Al);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|`Al`|Allocator – třída úložiště má být použit pro toto `hash_multiset` objekt, který se standardně `Allocator`.|  
|`Comp`|Funkci porovnání typu `const Traits` sloužící k uspořádání elementů v `hash_multiset`, což výchozí nastavení `hash_compare`.|  
|`Right`|`hash_multiset` z nich konstruovaný objekt `hash_multiset` má být kopie.|  
|`First`|Pozice první prvek v rozsahu elementy, které se mají zkopírovat.|  
|`Last`|Pozice první prvek mimo rozsah elementy, které se mají zkopírovat.|  
|`IList`|Initializer_list, který obsahuje prvky, které mají být zkopírovány.|  
  
### <a name="remarks"></a>Poznámky  
 Typ allocator objekt, který spravuje paměti úložiště pro ukládání všechny konstruktory `hash_multiset` a který se může vracet později voláním [hash_multiset::get_allocator](#get_allocator). Parametr allocator je často v deklaraci třídy vynechán a makra předběžného zpracování jsou použita k nahrazení alternativních alokátorů.  
  
 Všechny konstruktory inicializovat jejich hash_multisets.  
  
 Všechny konstruktory uložit objekt funkce typu `Traits` který se používá k navázání pořadí mezi klíče `hash_multiset` a který se může vracet později voláním [hash_multiset::key_comp](#key_comp). Další informace o `Traits` najdete v článku [hash_multiset – třída](../standard-library/hash-multiset-class.md) tématu.  
  
 První tři konstruktory zadat prázdný počáteční `hash_multiset`, druhý určující typ porovnání – funkce ( `Comp`) pro použití při vytváření pořadí elementy a třetí explicitně zadání přidělujícího modulu zadejte ( `Al`) má být použit. Klíčové slovo `explicit` potlačí určité druhy převod automatické typu.  
  
 Čtvrtý konstruktor přesune `hash_multiset` `Right`.  
  
 Pátý, šestinu a sedmý konstruktory použít initializer_list.  
  
 Poslední tři konstruktory zkopírujte rozsahu [ `First`, `Last`) z `hash_multiset` se zvýšeným explicitness v určení typu funkci porovnání třídy porovnání a přidělení.  
  
 Skutečné pořadí prvků v kontejneru hash set závisí na funkci hash funkci řazení a aktuální velikost zatřiďovací tabulku a nelze, předpovědět obecně platí, jako to bylo možné v kontejneru sady, kde byl určen ve funkci řazení samostatně.  
  
##  <a name="insert"></a>hash_multiset::Insert  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Vloží do hash_multiset elementu nebo rozsahu prvků.  
  
```  
iterator insert(
    const Type& Val);

iterator insert(
    iterator Where,  
    const Type& Al);

void insert(
    initializer_list<Type> IList);

iterator insert(
    const Type& Val);

iterator insert(
    Iterator Where,   
    const Type& Val);

template <class InputIterator>  
void insert(
    InputIterator First,  
    InputIterator Last);

template <class ValTy>  
iterator insert(
    ValTy&& Val);

template <class ValTy>  
iterator insert(
    const_iterator Where,  
    ValTy&& Val);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|`Val`|Hodnota elementu vložit do hash_multiset – Pokud hash_multiset již obsahuje daný element nebo obecně platí, element, jehož klíč je ekvivalentně řazení.|  
|`Where`|Místo zahájení vyhledání správného bodu vložení. (Vložení se může objevit v amortizovaný konstantní čas, místo logaritmické čas, pokud bod vložení následuje `_Where`.)|  
|`First`|Pozice první prvek zkopírovány z hash_multiset.|  
|`Last`|Pozice bezprostředně za posledním elementem zkopírovány z hash_multiset.|  
|`IList`|Initializer_list, která obsahuje elementy pro kopírování.|  
  
### <a name="return-value"></a>Návratová hodnota  
 První dvě vložení členské funkce vrátí iterátor, který odkazuje na pozici, kde byla vložena nového elementu.  
  
 Následující tři členské funkce použijte initializer_list.  
  
 Třetí členská funkce vloží pořadí hodnot element do hash_multiset, odpovídající každý prvek řešené pomocí iterace v rozsahu [ `First`, `Last`) ze zadané hash_multiset.  
  
### <a name="remarks"></a>Poznámky  
 Vložení se může objevit v amortizovaný konstantní dobu pomocný parametr verzi vložení, místo logaritmické čas, pokud bod vložení následuje `Where`.  
  
##  <a name="iterator"></a>hash_multiset::iterator  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Typ, který poskytuje obousměrné iterator, který může číst nebo upravovat libovolný element v hash_multiset.  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ **iterator** lze upravit hodnotu elementu.  
  
   
  
### <a name="example"></a>Příklad  
  Podívejte se příklad [začít](#begin) příklad toho, jak deklarace a používání **iterator**.  
  
##  <a name="key_comp"></a>hash_multiset::key_comp  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Načte kopii porovnání objekt použitý k pořadí klíčů v hash_multiset.  
  
```  
key_compare key_comp() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí parametr šablony hash_multiset `Traits`, který obsahuje objekty funkcí, které se používají k hash a k uspořádání elementy kontejneru.  
  
 Další informace o `Traits` najdete v článku [hash_multiset – třída](../standard-library/hash-multiset-class.md) tématu.  
  
### <a name="remarks"></a>Poznámky  
 Objekt uložené definuje členské funkce:  
  
 **BOOL – operátor**( **const klíč &** *_xVal,* **const klíč &** _ `yVal`);  
  
 která vrací **true** Pokud `_xVal` předchází a není rovno `_yVal` v pořadí řazení.  
  
 Všimněte si, že oba [key_compare –](#key_compare) a [value_compare –](#value_compare) jsou synonyma pro parametr šablony **vlastnosti**. Oba typy jsou uvedené pro hash_multiset a hash_multiset třídy, kde jsou identické pro kompatibilitu s třídy hash_map a hash_multimap tam, kde jsou odlišné.  
  
   
  
### <a name="example"></a>Příklad  
  
```cpp  
// hash_multiset_key_comp.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
  
   hash_multiset <int, hash_compare < int, less<int> > >hms1;  
   hash_multiset<int, hash_compare < int, less<int> > >::key_compare kc1  
          = hms1.key_comp( ) ;  
   bool result1 = kc1( 2, 3 ) ;  
   if( result1 == true )  
   {  
      cout << "kc1( 2,3 ) returns value of true, "  
           << "where kc1 is the function object of hms1."  
           << endl;  
   }  
   else  
   {  
      cout << "kc1( 2,3 ) returns value of false "  
           << "where kc1 is the function object of hms1."  
        << endl;  
   }  
  
   hash_multiset <int, hash_compare < int, greater<int> > > hms2;  
   hash_multiset<int, hash_compare < int, greater<int> > >::key_compare  
         kc2 = hms2.key_comp( ) ;  
   bool result2 = kc2( 2, 3 ) ;  
   if( result2 == true )  
   {  
      cout << "kc2( 2,3 ) returns value of true, "  
           << "where kc2 is the function object of hms2."  
           << endl;  
   }  
   else  
   {  
      cout << "kc2( 2,3 ) returns value of false, "  
           << "where kc2 is the function object of hms2."  
           << endl;  
   }  
}  
```  
  
##  <a name="key_compare"></a>hash_multiset::key_compare  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Typ, který poskytuje dva objekty funkce binární predikátu porovnání třída, která můžete porovnat dvě hodnoty element hash_multiset určit jejich relativní pořadí a predikát unární, který vytvoří hodnotu hash elementy.  
  
```  
typedef Traits key_compare;  
```  
  
### <a name="remarks"></a>Poznámky  
 **key_compare –** je synonymum pro parametr šablony `Traits`.  
  
 Další informace o `Traits` najdete v článku [hash_multiset – třída](../standard-library/hash-multiset-class.md) tématu.  
  
 Všimněte si, že oba `key_compare` a value_compare – jsou synonyma pro parametr šablony **vlastnosti**. Oba typy jsou uvedené pro třídy hash_set a hash_multiset tam, kde jsou stejné pro kompatibilitu s třídy hash_map a hash_multimap tam, kde jsou odlišné.  
  
   
  
### <a name="example"></a>Příklad  
  Podívejte se příklad [key_comp –](#key_comp) příklad toho, jak deklarace a používání `key_compare`.  
  
##  <a name="key_type"></a>hash_multiset::key_type  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Typ, který poskytuje funkce objekt, který můžete porovnat klíči řazení k určení relativní pořadí dva elementy v hash_multiset.  
  
```  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 **key_type –** je synonymum pro parametr šablony `Key`.  
  
 Všimněte si, že oba `key_type` a [value_type](../standard-library/hash-set-class.md#value_type) jsou synonyma pro parametr šablony **klíč**. Oba typy jsou uvedené pro sady a multiset třídy, tam, kde jsou identické, zajištění kompatibility se službou mapy a multimap třídy, které jsou jedinečné.  
  
 Další informace o `Key`, najdete v části poznámky [hash_multiset – třída](../standard-library/hash-multiset-class.md) tématu.  
  
   
  
### <a name="example"></a>Příklad  
  Podívejte se příklad [value_type](#value_type) příklad toho, jak deklarace a používání `key_type`.  
  
##  <a name="lower_bound"></a>hash_multiset::lower_bound  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Vrátí iterovat prvním elementem v hash_multiset s klíčem, který je rovna nebo větší než je zadaný klíč.  
  
```  
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Argument klíč, který se má porovnat s klíč řazení elementu z hash_multiset prohledávaný.  
  
### <a name="return-value"></a>Návratová hodnota  
 [Iterator](#iterator) nebo [const_iterator –](#const_iterator) , který se týká umístění prvním elementem v hash_multiset s klíčem, která je rovna nebo větší než argument klíč nebo, který se týká umístění úspěšné posledním prvkem v hash_multiset, pokud není nalezena žádná shoda pro klíč.  
  
### <a name="remarks"></a>Poznámky  
   
  
### <a name="example"></a>Příklad  
  
```cpp  
// hash_multiset_lower_bound.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main() {  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> hms1;  
   hash_multiset <int> :: const_iterator hms1_AcIter, hms1_RcIter;  
  
   hms1.insert( 10 );  
   hms1.insert( 20 );  
   hms1.insert( 30 );  
  
   hms1_RcIter = hms1.lower_bound( 20 );  
   cout << "The element of hash_multiset hms1 with a key of 20 is: "  
        << *hms1_RcIter << "." << endl;  
  
   hms1_RcIter = hms1.lower_bound( 40 );  
  
   // If no match is found for the key, end( ) is returned  
   if ( hms1_RcIter == hms1.end( ) )  
      cout << "The hash_multiset hms1 doesn't have an element "  
           << "with a key of 40." << endl;  
   else  
      cout << "The element of hash_multiset hms1 with a key of 40 is: "  
           << *hms1_RcIter << "." << endl;  
  
   // An element at a specific location in the hash_multiset can be found   
   // by using a dereferenced iterator that addresses the location  
   hms1_AcIter = hms1.end( );  
   hms1_AcIter--;  
   hms1_RcIter = hms1.lower_bound( *hms1_AcIter );  
   cout << "The element of hms1 with a key matching "  
        << "that of the last element is: "  
        << *hms1_RcIter << "." << endl;  
}  
```  
  
##  <a name="max_size"></a>hash_multiset::max_size  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Vrátí maximální délka hash_multiset.  
  
```  
size_type max_size() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Maximální možné délku hash_multiset.  
  
### <a name="remarks"></a>Poznámky  
   
  
### <a name="example"></a>Příklad  
  
```cpp  
// hash_multiset_max_size.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> hms1;  
   hash_multiset <int>::size_type i;  
  
   i = hms1.max_size( );     
   cout << "The maximum possible length "  
        << "of the hash_multiset is " << i << "." << endl;  
}  
```  
  
##  <a name="op_eq"></a>hash_multiset::Operator =  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Elementy hash_multiset nahradí kopii jiného hash_multiset.  
  
```  
hash_multiset& operator=(const hash_multiset& right);

hash_multiset& operator=(hash_multiset&& right);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|`right`|[Hash_multiset](../standard-library/hash-multiset-class.md) se zkopírují `hash_multiset`.|  
  
### <a name="remarks"></a>Poznámky  
 Po vymazání v žádné stávající elementy `hash_multiset`, `operator=` buď kopíruje nebo přesouvá obsah `right` do `hash_multiset`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// hash_multiset_operator_as.cpp  
// compile with: /EHsc  
#include <hash_multiset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset<int> v1, v2, v3;  
   hash_multiset<int>::iterator iter;  
  
   v1.insert(10);  
  
   cout << "v1 = " ;  
   for (iter = v1.begin(); iter != v1.end(); iter++)  
      cout << iter << " ";  
   cout << endl;  
  
   v2 = v1;  
   cout << "v2 = ";  
   for (iter = v2.begin(); iter != v2.end(); iter++)  
      cout << iter << " ";  
   cout << endl;  
  
// move v1 into v2  
   v2.clear();  
   v2 = move(v1);  
   cout << "v2 = ";  
   for (iter = v2.begin(); iter != v2.end(); iter++)  
      cout << iter << " ";  
   cout << endl;  
}  
```  
  
##  <a name="pointer"></a>hash_multiset::Pointer  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Typ, který poskytuje ukazatel na prvek v hash_multiset.  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::pointer pointer;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ **ukazatel** lze upravit hodnotu elementu.  
  
 Ve většině případů [iterator](#iterator) se má použít pro přístup k elementům v multiset objektu.  
  
   
  
##  <a name="rbegin"></a>hash_multiset::rbegin  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Vrátí iterator adresování prvním elementem v invertovaných hash_multiset.  
  
```  
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterator zpětné obousměrného adresování prvním elementem v invertovaných hash_multiset nebo řešení, co je posledním prvkem v unreversed hash_multiset.  
  
### <a name="remarks"></a>Poznámky  
 `rbegin`se používá s odstínech hash_multiset – stejně jako [začít](#begin) se používá s hash_multiset.  
  
 Pokud vrátí hodnotu, která `rbegin` je přiřazena k `const_reverse_iterator`, pak hash_multiset objekt nelze změnit. Pokud vrátí hodnotu, která `rbegin` je přiřazena k `reverse_iterator`, pak je možné upravit objekt hash_multiset.  
  
 `rbegin`můžete použít k iteraci v rámci hash_multiset zpětné.  
  
   
  
### <a name="example"></a>Příklad  
  
```cpp  
// hash_multiset_rbegin.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> hms1;  
   hash_multiset <int>::iterator hms1_Iter;  
   hash_multiset <int>::reverse_iterator hms1_rIter;  
  
   hms1.insert( 10 );  
   hms1.insert( 20 );  
   hms1.insert( 30 );  
  
   hms1_rIter = hms1.rbegin( );  
   cout << "The first element in the reversed hash_multiset is "  
        << *hms1_rIter << "." << endl;  
  
   // begin can be used to start an iteration   
   // throught a hash_multiset in a forward order  
   cout << "The hash_multiset is: ";  
   for ( hms1_Iter = hms1.begin( ) ; hms1_Iter != hms1.end( );  
         hms1_Iter++ )  
      cout << *hms1_Iter << " ";  
   cout << endl;  
  
   // rbegin can be used to start an iteration   
   // throught a hash_multiset in a reverse order  
   cout << "The reversed hash_multiset is: ";  
   for ( hms1_rIter = hms1.rbegin( ) ; hms1_rIter != hms1.rend( );  
         hms1_rIter++ )  
      cout << *hms1_rIter << " ";  
   cout << endl;  
  
   // A hash_multiset element can be erased by dereferencing to its key   
   hms1_rIter = hms1.rbegin( );  
   hms1.erase ( *hms1_rIter );  
  
   hms1_rIter = hms1.rbegin( );  
   cout << "After the erasure, the first element "  
        << "in the reversed hash_multiset is "<< *hms1_rIter << "."  
        << endl;  
}  
```  
  
```Output  
The first element in the reversed hash_multiset is 30.  
The hash_multiset is: 10 20 30   
The reversed hash_multiset is: 30 20 10   
After the erasure, the first element in the reversed hash_multiset is 20.  
```  
  
##  <a name="reference"></a>hash_multiset::Reference  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Typ, který obsahuje odkaz na element uložené v hash_multiset.  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::reference reference;  
```  
  
### <a name="remarks"></a>Poznámky  
   
  
### <a name="example"></a>Příklad  
  
```cpp  
// hash_multiset_reference.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   using namespace stdext;  
   hash_multiset <int> hms1;  
  
   hms1.insert( 10 );  
   hms1.insert( 20 );  
  
   // Declare and initialize a reference &Ref1 to the 1st element  
   int &Ref1 = *hms1.begin( );  
  
   cout << "The first element in the hash_multiset is "  
        << Ref1 << "." << endl;  
  
   // The value of the 1st element of the hash_multiset can be  
   // changed by operating on its (non const) reference  
   Ref1 = Ref1 + 5;  
  
   cout << "The first element in the hash_multiset is now "  
        << *hms1.begin() << "." << endl;  
}  
```  
  
```Output  
The first element in the hash_multiset is 10.  
The first element in the hash_multiset is now 15.  
```  
  
##  <a name="rend"></a>hash_multiset::rend  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Vrátí iterátor, který řeší úspěšné posledním prvkem v invertovaných hash_multiset umístění.  
  
```  
const_reverse_iterator rend() const;

reverse_iterator rend();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterator zpětné obousměrného, která řeší umístění úspěšné posledním prvkem v invertovaných hash_multiset (umístění, které měl před prvním elementem v unreversed hash_multiset).  
  
### <a name="remarks"></a>Poznámky  
 `rend`se používá s odstínech hash_multiset – stejně jako [end](#end) se používá s hash_multiset.  
  
 Pokud vrátí hodnotu, která `rend` je přiřazena k `const_reverse_iterator`, pak hash_multiset objekt nelze změnit. Pokud vrátí hodnotu, která `rend` je přiřazena k `reverse_iterator`, pak je možné upravit objekt hash_multiset. Hodnoty vrácené `rend` by neměl být vyhodnoceny odkazy.  
  
 `rend`slouží k testování, aby se jestli zpětné iterator dosáhne konce své hash_multiset.  
  
   
  
### <a name="example"></a>Příklad  
  
```cpp  
// hash_multiset_rend.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> hms1;  
   hash_multiset <int>::iterator hms1_Iter;  
   hash_multiset <int>::reverse_iterator hms1_rIter;  
   hash_multiset <int>::const_reverse_iterator hms1_crIter;  
  
   hms1.insert( 10 );  
   hms1.insert( 20 );  
   hms1.insert( 30 );  
  
   hms1_rIter = hms1.rend( );  
   hms1_rIter--;  
   cout << "The last element in the reversed hash_multiset is "  
        << *hms1_rIter << "." << endl;  
  
   // end can be used to terminate an iteration   
   // through a hash_multiset in a forward order  
   cout << "The hash_multiset is: ";  
   for ( hms1_Iter = hms1.begin( ) ; hms1_Iter != hms1.end( );  
         hms1_Iter++ )  
      cout << *hms1_Iter << " ";  
   cout << "." << endl;  
  
   // rend can be used to terminate an iteration   
   // throught a hash_multiset in a reverse order  
   cout << "The reversed hash_multiset is: ";  
   for ( hms1_rIter = hms1.rbegin( ) ; hms1_rIter != hms1.rend( );  
         hms1_rIter++ )  
      cout << *hms1_rIter << " ";  
   cout << "." << endl;  
  
   hms1_rIter = hms1.rend( );  
   hms1_rIter--;  
   hms1.erase ( *hms1_rIter );  
  
   hms1_rIter = hms1.rend( );  
   hms1_rIter--;  
   cout << "After the erasure, the last element in the "  
        << "reversed hash_multiset is " << *hms1_rIter << "."  
        << endl;  
}  
```  
  
```Output  
The last element in the reversed hash_multiset is 10.  
The hash_multiset is: 10 20 30 .  
The reversed hash_multiset is: 30 20 10 .  
After the erasure, the last element in the reversed hash_multiset is 20.  
```  
  
##  <a name="reverse_iterator"></a>hash_multiset::reverse_iterator  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Typ, který poskytuje obousměrné iterator, které můžou číst nebo upravte element v invertovaných hash_multiset.  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ `reverse_iterator` je použít k iteraci v rámci hash_multiset pozpátku.  
  
   
  
### <a name="example"></a>Příklad  
  Podívejte se příklad [rbegin –](#rbegin) příklad toho, jak deklarace a používání `reverse_iterator`.  
  
##  <a name="size"></a>hash_multiset::size  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Vrátí počet prvků hash_multiset.  
  
```  
size_type size() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální délka hash_multiset.  
  
### <a name="remarks"></a>Poznámky  
   
  
### <a name="example"></a>Příklad  
  
```cpp  
// hash_multiset_size.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> hms1;  
   hash_multiset <int> :: size_type i;  
  
   hms1.insert( 1 );  
   i = hms1.size( );  
   cout << "The hash_multiset length is " << i << "." << endl;  
  
   hms1.insert( 2 );  
   i = hms1.size( );  
   cout << "The hash_multiset length is now " << i << "." << endl;  
}  
```  
  
```Output  
The hash_multiset length is 1.  
The hash_multiset length is now 2.  
```  
  
##  <a name="size_type"></a>hash_multiset::size_type  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Typ celé číslo bez znaménka, která představuje počet elementů ve hash_multiset.  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;  
```  
  
### <a name="remarks"></a>Poznámky  
   
  
### <a name="example"></a>Příklad  
  Podívejte se příklad [velikost](#size) příklad toho, jak deklarace a používání`size_type`  
  
##  <a name="swap"></a>hash_multiset::swap  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Elementy dvě hash_multisets výměny.  
  
```  
void swap(hash_multiset& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Hash_multiset – argument poskytování elementy pro si místo se hash_multiset cíl.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce by způsobila neplatnost žádné odkazy, ukazatele nebo iterátory, které určit elementů ve dvou hash_multisets, jehož elementy jsou během výměny.  
  
   
  
### <a name="example"></a>Příklad  
  
```cpp  
// hash_multiset_swap.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> hms1, hms2, hms3;  
   hash_multiset <int>::iterator hms1_Iter;  
  
   hms1.insert( 10 );  
   hms1.insert( 20 );  
   hms1.insert( 30 );  
   hms2.insert( 100 );  
   hms2.insert( 200 );  
   hms3.insert( 300 );  
  
   cout << "The original hash_multiset hms1 is:";  
   for ( hms1_Iter = hms1.begin( ); hms1_Iter != hms1.end( );  
         hms1_Iter++ )  
         cout << " " << *hms1_Iter;  
   cout   << "." << endl;  
  
   // This is the member function version of swap  
   hms1.swap( hms2 );  
  
   cout << "After swapping with hms2, list hms1 is:";  
   for ( hms1_Iter = hms1.begin( ); hms1_Iter != hms1.end( );  
         hms1_Iter++ )  
         cout << " " << *hms1_Iter;  
   cout  << "." << endl;  
  
   // This is the specialized template version of swap  
   swap( hms1, hms3 );  
  
   cout << "After swapping with hms3, list hms1 is:";  
   for ( hms1_Iter = hms1.begin( ); hms1_Iter != hms1.end( );  
         hms1_Iter++ )  
         cout << " " << *hms1_Iter;  
   cout   << "." << endl;  
}  
```  
  
```Output  
The original hash_multiset hms1 is: 10 20 30.  
After swapping with hms2, list hms1 is: 200 100.  
After swapping with hms3, list hms1 is: 300.  
```  
  
##  <a name="upper_bound"></a>hash_multiset::upper_bound  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Vrátí iterator na prvním elementem v hash_multiset s klíčem, který je větší než je zadaný klíč.  
  
```  
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Argument klíč, který se má porovnat s klíč řazení elementu z hash_multiset prohledávaný.  
  
### <a name="return-value"></a>Návratová hodnota  
 [Iterator](#iterator) nebo [const_iterator –](#const_iterator) , který se týká umístění prvním elementem v hash_multiset klíčem, který je větší než argument klíč nebo který adres úspěšné posledním prvkem v umístění hash_multiset –, pokud není nalezena žádná shoda pro klíč.  
  
### <a name="remarks"></a>Poznámky  
   
  
### <a name="example"></a>Příklad  
  
```cpp  
// hash_multiset_upper_bound.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> hms1;  
   hash_multiset <int> :: const_iterator hms1_AcIter, hms1_RcIter;  
  
   hms1.insert( 10 );  
   hms1.insert( 20 );  
   hms1.insert( 30 );  
  
   hms1_RcIter = hms1.upper_bound( 20 );  
   cout << "The first element of hash_multiset hms1" << endl  
        << " with a key greater than 20 is: "  
        << *hms1_RcIter << "." << endl;  
  
   hms1_RcIter = hms1.upper_bound( 30 );  
  
   // If no match is found for the key, end( ) is returned  
   if ( hms1_RcIter == hms1.end( ) )  
      cout << "The hash_multiset hms1 doesn't have an element "  
           << "\n with a key greater than 30." << endl;  
   else  
      cout << "The element of hash_multiset hms1"  
           << "with a key > 40 is: "  
           << *hms1_RcIter << "." << endl;  
  
   // An element at a specific location in the hash_multiset can be  
   // found by using a dereferenced iterator addressing the location  
   hms1_AcIter = hms1.begin( );  
   hms1_RcIter = hms1.upper_bound( *hms1_AcIter );  
   cout << "The first element of hms1\n with a key greater than "  
        << endl << "that of the initial element of hms1 is: "  
        << *hms1_RcIter << "." << endl;  
}  
```  
  
```Output  
The first element of hash_multiset hms1  
 with a key greater than 20 is: 30.  
The hash_multiset hms1 doesn't have an element   
 with a key greater than 30.  
The first element of hms1  
 with a key greater than   
that of the initial element of hms1 is: 20.  
```  
  
##  <a name="value_comp"></a>hash_multiset::value_comp  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Načte kopii porovnání objekt použitý k hodnoty element pořadí v hash_multiset.  
  
```  
value_compare value_comp() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí parametr šablony hash_multiset `Traits`, který obsahuje objekty funkcí, které se používají k hash a na pořadí elementy kontejneru.  
  
 Další informace o `Traits` najdete v článku [hash_multiset – třída](../standard-library/hash-multiset-class.md) tématu.  
  
### <a name="remarks"></a>Poznámky  
 Objekt uložené definuje členské funkce:  
  
 **BOOL – operátor**( **constKey &**`_xVal`, **const klíč &** *_yVal*);  
  
 která vrací **true** Pokud `_xVal` předchází a není rovno `_yVal` v pořadí řazení.  
  
 Všimněte si, že oba [key_compare –](#key_compare) a [value_compare –](#value_compare) jsou synonyma pro parametr šablony **vlastnosti**. Oba typy jsou uvedené pro hash_multiset a hash_multiset třídy, kde jsou identické pro kompatibilitu s třídy hash_map a hash_multimap tam, kde jsou odlišné.  
  
   
  
### <a name="example"></a>Příklad  
  
```cpp  
// hash_multiset_value_comp.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
  
   hash_multiset <int, hash_compare < int, less<int> > > hms1;  
   hash_multiset <int, hash_compare < int, less<int> > >::value_compare  
      vc1 = hms1.value_comp( );  
   bool result1 = vc1( 2, 3 );  
   if( result1 == true )  
   {  
      cout << "vc1( 2,3 ) returns value of true, "  
           << "where vc1 is the function object of hms1."  
           << endl;  
   }  
   else  
   {  
      cout << "vc1( 2,3 ) returns value of false, "  
           << "where vc1 is the function object of hms1."  
           << endl;  
   }  
  
   hash_multiset <int, hash_compare < int, greater<int> > > hms2;  
   hash_multiset<int, hash_compare < int, greater<int> > >::  
           value_compare vc2 = hms2.value_comp( );  
   bool result2 = vc2( 2, 3 );  
   if( result2 == true )  
   {  
      cout << "vc2( 2,3 ) returns value of true, "  
           << "where vc2 is the function object of hms2."  
           << endl;  
   }  
   else  
   {  
      cout << "vc2( 2,3 ) returns value of false, "  
           << "where vc2 is the function object of hms2."  
           << endl;  
   }  
}  
```  
  
```Output  
vc1( 2,3 ) returns value of true, where vc1 is the function object of hms1.  
vc2( 2,3 ) returns value of false, where vc2 is the function object of hms2.  
```  
  
##  <a name="value_compare"></a>hash_multiset::value_compare  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Typ, který poskytuje dva objekty funkce binární predikátu porovnání třída, která můžete porovnat dvě hodnoty element hash_multiset určit jejich relativní pořadí a predikát unární, který vytvoří hodnotu hash elementy.  
  
```  
typedef key_compare value_compare;  
```  
  
### <a name="remarks"></a>Poznámky  
 **value_compare –** je synonymum pro parametr šablony `Traits`.  
  
 Další informace o `Traits` najdete v článku [hash_multiset – třída](../standard-library/hash-multiset-class.md) tématu.  
  
 Všimněte si, že oba [key_compare –](#key_compare) a **value_compare –** jsou synonyma pro parametr šablony **vlastnosti**. Oba typy jsou uvedené pro třídy sady a multiset tam, kde jsou identické, zajištění kompatibility se službou mapy třídy a multimap, kde jsou jedinečné.  
  
   
  
### <a name="example"></a>Příklad  
  Podívejte se příklad [value_comp –](#value_comp) příklad toho, jak deklarace a používání `value_compare`.  
  
##  <a name="value_type"></a>hash_multiset::value_type  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset – třída](../standard-library/unordered-multiset-class.md).  
  
 Typ, který popisuje objekt uložené jako element jako hash_multiset jako hodnotu.  
  
```  
typedef Key value_type;  
```  
  
### <a name="example"></a>Příklad  
  
```cpp  
// hash_multiset_value_type.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> hms1;  
   hash_multiset <int>::iterator hms1_Iter;  
  
   // Declare value_type  
   hash_multiset <int> :: value_type hmsvt_Int;   
  
   hmsvt_Int = 10;   // Initialize value_type  
  
   // Declare key_type  
   hash_multiset <int> :: key_type hmskt_Int;  
   hmskt_Int = 20;             // Initialize key_type  
  
   hms1.insert( hmsvt_Int );         // Insert value into s1  
   hms1.insert( hmskt_Int );         // Insert key into s1  
  
   // A hash_multiset accepts key_types or value_types as elements  
   cout << "The hash_multiset has elements:";  
   for ( hms1_Iter = hms1.begin() ; hms1_Iter != hms1.end( );  
         hms1_Iter++)  
      cout << " " << *hms1_Iter;  
      cout << "." << endl;  
}  
```  
  
```Output  
The hash_multiset has elements: 10 20.  
```  
  
## <a name="see-also"></a>Viz také  
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Standardní C++ – referenční dokumentace knihoven](../standard-library/cpp-standard-library-reference.md)

