---
title: mapy (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::map
dev_langs: C++
helpviewer_keywords:
- <map> header [STL/CLR]
- map class [STL/CLR]
- <cliext/map> header [STL/CLR]
ms.assetid: 8b0a7764-b5e4-4175-a802-82b72eb8662a
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c90fcb415b186257cd2aef801867918b367413b6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="map-stlclr"></a>map (STL/CLR)
Šablony třídy popisuje objekt, který řídí různých délka pořadí elementů, která má obousměrný přístup. Použít metodu kontejneru `map` spravovat pořadí elementů jako (téměř) vyrovnáváním seřazené strom uzlů, ukládání jeden element. Element obsahuje klíč, pro řazení sekvenci a namapované hodnotu, kterou má význam pro pravé.  
  
 V popisu níže `GValue` je stejný jako:  
  
 `Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`  
  
 kde:  
  
 `GKey`je stejný jako `Key` Pokud k tomu je typu ref, v takovém případě je`Key^`  
  
 `GMapped`je stejný jako `Mapped` Pokud k tomu je typu ref, v takovém případě je`Mapped^`  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 Key  
 Typ elementu v řízené sekvenci komponenta klíče.  
  
 Mapovat  
 Typ elementu v řízené sekvenci další součásti.  
  
## <a name="members"></a>Členové  
  
|Definice typu|Popis|  
|---------------------|-----------------|  
|[map::const_iterator (STL/CLR)](../dotnet/map-const-iterator-stl-clr.md)|Typ konstantního iterátoru řízené sekvence|  
|[map::const_reference (STL/CLR)](../dotnet/map-const-reference-stl-clr.md)|Typ konstantního odkazu na prvek|  
|[map::const_reverse_iterator (STL/CLR)](../dotnet/map-const-reverse-iterator-stl-clr.md)|Typ konstantní zpětné iterator pro řízené sekvenci.|  
|[map::difference_type (STL/CLR)](../dotnet/map-difference-type-stl-clr.md)|Typ (může být podepsaná) vzdálenost mezi dvěma prvky.|  
|[map::generic_container (STL/CLR)](../dotnet/map-generic-container-stl-clr.md)|Typ generické rozhraní pro kontejner.|  
|[map::generic_iterator (STL/CLR)](../dotnet/map-generic-iterator-stl-clr.md)|Typ iterace pro obecné rozhraní kontejneru.|  
|[map::generic_reverse_iterator (STL/CLR)](../dotnet/map-generic-reverse-iterator-stl-clr.md)|Typ zpětné iterator pro obecné rozhraní kontejneru.|  
|[map::generic_value (STL/CLR)](../dotnet/map-generic-value-stl-clr.md)|Typ elementu pro obecné rozhraní kontejneru.|  
|[map::iterator (STL/CLR)](../dotnet/map-iterator-stl-clr.md)|Typ iterátoru řízené sekvence|  
|[map::key_compare (STL/CLR)](../dotnet/map-key-compare-stl-clr.md)|Řazení delegáta pro dva klíče.|  
|[map::key_type (STL/CLR)](../dotnet/map-key-type-stl-clr.md)|Typ klíče řazení|  
|[map::mapped_type (STL/CLR)](../dotnet/map-mapped-type-stl-clr.md)|Typ namapované hodnotu přidruženou každý klíč.|  
|[map::reference (STL/CLR)](../dotnet/map-reference-stl-clr.md)|Typ odkazu na prvek|  
|[map::reverse_iterator (STL/CLR)](../dotnet/map-reverse-iterator-stl-clr.md)|Typ zpětné iterator pro řízené sekvenci.|  
|[map::size_type (STL/CLR)](../dotnet/map-size-type-stl-clr.md)|Typ (nezáporné) vzdálenost mezi dvěma prvky.|  
|[map::value_compare (STL/CLR)](../dotnet/map-value-compare-stl-clr.md)|Řazení delegáta pro dvě hodnoty elementu.|  
|[map::value_type (STL/CLR)](../dotnet/map-value-type-stl-clr.md)|Typ prvku|  
  
|Členská funkce|Popis|  
|---------------------|-----------------|  
|[map::begin (STL/CLR)](../dotnet/map-begin-stl-clr.md)|Určuje začátek řízené sekvence.|  
|[map::clear (STL/CLR)](../dotnet/map-clear-stl-clr.md)|Odebere všechny prvky.|  
|[map::count (STL/CLR)](../dotnet/map-count-stl-clr.md)|Vrátí počet prvků odpovídající zadaného klíče.|  
|[map::empty (STL/CLR)](../dotnet/map-empty-stl-clr.md)|Zkouší, zda nejsou přítomny žádné prvky.|  
|[map::end (STL/CLR)](../dotnet/map-end-stl-clr.md)|Určuje konec řízené sekvence.|  
|[map::equal_range (STL/CLR)](../dotnet/map-equal-range-stl-clr.md)|Najde rozsah, který odpovídá zadanému klíči.|  
|[map::erase (STL/CLR)](../dotnet/map-erase-stl-clr.md)|Odebere prvky v určených pozicích.|  
|[map::find (STL/CLR)](../dotnet/map-find-stl-clr.md)|Vyhledá prvek, který odpovídá zadanému klíči.|  
|[map::insert (STL/CLR)](../dotnet/map-insert-stl-clr.md)|Přidá prvky.|  
|[map::key_comp (STL/CLR)](../dotnet/map-key-comp-stl-clr.md)|Zkopíruje řazení delegáta pro dva klíče.|  
|[map::lower_bound (STL/CLR)](../dotnet/map-lower-bound-stl-clr.md)|Najde začátek rozsahu, který odpovídá zadaným klíčem.|  
|[map::make_value (STL/CLR)](../dotnet/map-make-value-stl-clr.md)|Vytvoří objekt hodnoty.|  
|[map::map (STL/CLR)](../dotnet/map-map-stl-clr.md)|Sestaví objekt kontejneru.|  
|[map::rbegin (STL/CLR)](../dotnet/map-rbegin-stl-clr.md)|Označuje začátek odstínech řízené sekvenci.|  
|[map::rend (STL/CLR)](../dotnet/map-rend-stl-clr.md)|Označuje konec odstínech řízené sekvenci.|  
|[map::size (STL/CLR)](../dotnet/map-size-stl-clr.md)|Spočítá počet prvků.|  
|[map::swap (STL/CLR)](../dotnet/map-swap-stl-clr.md)|Zamění obsah dvou kontejnerů.|  
|[map::to_array (STL/CLR)](../dotnet/map-to-array-stl-clr.md)|Zkopíruje řízené sekvenci do nové pole.|  
|[map::upper_bound (STL/CLR)](../dotnet/map-upper-bound-stl-clr.md)|Najde konec rozsahu, který odpovídá zadaným klíčem.|  
|[map::value_comp (STL/CLR)](../dotnet/map-value-comp-stl-clr.md)|Zkopíruje řazení delegáta pro dvě hodnoty elementu.|  
  
|Operátor|Popis|  
|--------------|-----------------|  
|[map::operator= (STL/CLR)](../dotnet/map-operator-assign-stl-clr.md)|Nahradí řízené sekvenci.|  
|[map::operator(STL/CLR)](../dotnet/map-operator-stl-clr.md)|Klíč se mapuje na její přidružené hodnoty namapované.|  
|[operator!= (map) (STL/CLR)](../dotnet/operator-inequality-map-stl-clr.md)|Určuje, zda `map` objekt není rovno jiné `map` objektu.|  
|[operator< (map) (STL/CLR)](../dotnet/operator-less-than-map-stl-clr.md)|Určuje, zda `map` objektu je menší než jiná `map` objektu.|  
|[operator<= (map) (STL/CLR)](../dotnet/operator-less-or-equal-map-stl-clr.md)|Určuje, zda `map` objektu je menší než nebo rovna do jiného `map` objektu.|  
|[operator== (map) (STL/CLR)](../dotnet/operator-equality-map-stl-clr.md)|Určuje, zda `map` objekt rovná jiné `map` objektu.|  
|[operator> (map) (STL/CLR)](../dotnet/operator-greater-than-map-stl-clr.md)|Určuje, zda `map` je větší než druhý objekt `map` objektu.|  
|[operator>= (map) (STL/CLR)](../dotnet/operator-greater-or-equal-map-stl-clr.md)|Určuje, zda `map` objekt je větší než nebo rovna hodnotě jiného `map` objektu.|  
  
## <a name="interfaces"></a>Rozhraní  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Duplicitní objekt.|  
|<xref:System.Collections.IEnumerable>|Pořadí pomocí elementů.|  
|<xref:System.Collections.ICollection>|Údržba skupiny elementů.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Pořadí prostřednictvím typové elementy.|  
|<xref:System.Collections.Generic.ICollection%601>|Údržba skupiny typové elementů.|  
|<xref:System.Collections.Generic.IDictionary%602>|Údržba skupiny {klíč a hodnotu} páry.|  
|ITree < klíč, hodnota >|Udržujte obecné kontejneru.|  
  
## <a name="remarks"></a>Poznámky  
 Objekt přiděluje a uvolní úložiště pro pořadí, které ovládá jako jednotlivé uzly. Vloží elementy na (téměř) vyrovnáváním stromové struktury, která udržuje seřazené změnou propojení mezi uzly, nikdy zkopírováním obsah jednoho uzlu do jiného. To znamená, že můžete vložit a odeberte elementy volně bez narušení zbývající elementy.  
  
 Objekt řadí pořadí jimi řídí voláním objektu uložené delegáta typu [map::key_compare (STL/CLR)](../dotnet/map-key-compare-stl-clr.md). Objekt uložené delegáta můžete zadat, když vytvoříte mapy; Pokud zadáte žádný objekt delegáta, výchozí hodnota je porovnání `operator<(key_type, key_type)`. Přístup k této uložené objekt voláním členské funkce [map::key_comp (STL/CLR)](../dotnet/map-key-comp-stl-clr.md)`()`.  
  
 Takový objekt delegáta musí použít striktní slabé řazení klíče typu [map::key_type (STL/CLR)](../dotnet/map-key-type-stl-clr.md). To znamená, pro žádné dva klíče `X` a `Y`:  
  
 `key_comp()(X, Y)`Vrátí stejné logická hodnota způsobit při každém volání.  
  
 Pokud `key_comp()(X, Y)` má hodnotu true, pak `key_comp()(Y, X)` musí mít hodnotu false.  
  
 Pokud `key_comp()(X, Y)` má hodnotu true, pak `X` se říká, že se seřadí před `Y`.  
  
 Pokud `!key_comp()(X, Y) && !key_comp()(Y, X)` má hodnotu true, pak `X` a `Y` se říká, že máte ekvivalentní řazení.  
  
 Pro libovolný element `X` který předchází `Y` v řízené sekvenci `key_comp()(Y, X)` je false. (Pro objekt delegáta výchozí klíče nikdy snížení hodnoty.) Na rozdíl od třídy šablony [mapy](../dotnet/map-stl-clr.md), objekt třídy šablony `map` nevyžaduje, aby klíče pro všechny elementy byly jedinečné. (Dvě nebo více klíčů může mít ekvivalentní řazení.)  
  
 Každý prvek obsahuje samostatné klíč a hodnotu namapované. Pořadí je reprezentována způsobem, který umožňuje vyhledávání, vkládání a odebírání libovolný element s několik operací, které jsou přímo úměrná logaritmus počet elementů v pořadí (logaritmické čas). Vkládání prvků navíc nezruší platnost žádných iterátorů a odstranění prvku zruší platnost pouze těch iterátorů, které odkazují na odstraněný prvek.  
  
 Mapu podporuje obousměrné iterátory, což znamená, že můžete tak, aby přiléhající elementy zadané iterátor, který označuje elementu v řízené sekvenci. Speciální hlavního uzlu odpovídá iterator vrácený [map::end (STL/CLR)](../dotnet/map-end-stl-clr.md)`()`. Tato iterator k dosažení poslední elementu v řízené sekvenci, můžete snížení, pokud je k dispozici. Můžete zvýšit mapy iterator k dosažení hlavního uzlu a bude potom porovnejte rovna `end()`. Ale nemůže dereference iterator vrácený `end()`.  
  
 Všimněte si, že nemůže odkazovat na element mapy přímo zadané pořadí umístění – vyžadující iterator náhodný přístup.  
  
 Iterator mapy uloží popisovač do uzlu přidružené mapy, který je pak uloží popisovač pro jeho přidružené kontejneru. Iterátory lze použít pouze jejich přidružené kontejnerové objekty. Iterator mapy zůstane platný tak dlouho, dokud jeho uzel přidružené mapy souvisí s některé mapy. Kromě toho je platný iterator dereferencable – slouží k přístupu k nebo alter hodnota elementu se označí – tak dlouho, dokud není rovno `end()`.  
  
 Mazání nebo odebrání element volání destruktoru pro jeho uložené hodnoty. Zničení kontejneru vymaže všechny elementy. Proto kontejner, jehož typ elementu je třída ref zajistí, že žádné elementy outlive kontejneru. Upozorňujeme však, že nemá kontejner popisovače `not` zrušení jeho elementy.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / map >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [hash_map – (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_map – (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [mapy](../dotnet/map-stl-clr.md)   
 [multiset (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [Sada (STL/CLR)](../dotnet/set-stl-clr.md)   
 [Referenční dokumentace knihoven STL/CLR](../dotnet/stl-clr-library-reference.md)