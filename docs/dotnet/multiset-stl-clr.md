---
title: multiset (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::multiset
dev_langs: C++
helpviewer_keywords:
- <cliext/set> header [STL/CLR]
- <set> header [STL/CLR]
- multiset class [STL/CLR]
ms.assetid: 7c46e2b4-cd88-49b7-a9e6-63ad5ae7feb5
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9f964fd511d87d2fd5ca460eb72dc5c9db8351ae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="multiset-stlclr"></a>multiset (STL/CLR)
Šablony třídy popisuje objekt, který řídí různých délka pořadí elementů, která má obousměrný přístup. Použít metodu kontejneru `multiset` spravovat pořadí elementů jako (téměř) vyrovnáváním seřazené strom uzlů, ukládání jeden element.  
  
 V popisu níže `GValue` je stejný jako `GKey`, který naopak je stejný jako `Key` Pokud k tomu je typu ref, v takovém případě je `Key^`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Key>  
    ref class multiset  
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
  
#### <a name="parameters"></a>Parametry  
 Key  
 Typ elementu v řízené sekvenci komponenta klíče.  
  
## <a name="members"></a>Členové  
  
|Definice typu|Popis|  
|---------------------|-----------------|  
|[multiset::const_iterator (STL/CLR)](../dotnet/multiset-const-iterator-stl-clr.md)|Typ konstantního iterátoru řízené sekvence|  
|[multiset::const_reference (STL/CLR)](../dotnet/multiset-const-reference-stl-clr.md)|Typ konstantního odkazu na prvek|  
|[multiset::const_reverse_iterator (STL/CLR)](../dotnet/multiset-const-reverse-iterator-stl-clr.md)|Typ konstantní zpětné iterator pro řízené sekvenci.|  
|[multiset::difference_type (STL/CLR)](../dotnet/multiset-difference-type-stl-clr.md)|Typ (může být podepsaná) vzdálenost mezi dvěma prvky.|  
|[multiset::generic_container (STL/CLR)](../dotnet/multiset-generic-container-stl-clr.md)|Typ generické rozhraní pro kontejner.|  
|[multiset::generic_iterator (STL/CLR)](../dotnet/multiset-generic-iterator-stl-clr.md)|Typ iterace pro obecné rozhraní kontejneru.|  
|[multiset::generic_reverse_iterator (STL/CLR)](../dotnet/multiset-generic-reverse-iterator-stl-clr.md)|Typ zpětné iterator pro obecné rozhraní kontejneru.|  
|[multiset::generic_value (STL/CLR)](../dotnet/multiset-generic-value-stl-clr.md)|Typ elementu pro obecné rozhraní kontejneru.|  
|[multiset::iterator (STL/CLR)](../dotnet/multiset-iterator-stl-clr.md)|Typ iterátoru řízené sekvence|  
|[multiset::key_compare (STL/CLR)](../dotnet/multiset-key-compare-stl-clr.md)|Řazení delegáta pro dva klíče.|  
|[multiset::key_type (STL/CLR)](../dotnet/multiset-key-type-stl-clr.md)|Typ klíče řazení|  
|[multiset::reference (STL/CLR)](../dotnet/multiset-reference-stl-clr.md)|Typ odkazu na prvek|  
|[multiset::reverse_iterator (STL/CLR)](../dotnet/multiset-reverse-iterator-stl-clr.md)|Typ zpětné iterator pro řízené sekvenci.|  
|[multiset::size_type (STL/CLR)](../dotnet/multiset-size-type-stl-clr.md)|Typ (nezáporné) vzdálenost mezi dvěma prvky.|  
|[multiset::value_compare (STL/CLR)](../dotnet/multiset-value-compare-stl-clr.md)|Řazení delegáta pro dvě hodnoty elementu.|  
|[multiset::value_type (STL/CLR)](../dotnet/multiset-value-type-stl-clr.md)|Typ prvku|  
  
|Členská funkce|Popis|  
|---------------------|-----------------|  
|[multiset::begin (STL/CLR)](../dotnet/multiset-begin-stl-clr.md)|Určuje začátek řízené sekvence.|  
|[multiset::clear (STL/CLR)](../dotnet/multiset-clear-stl-clr.md)|Odebere všechny prvky.|  
|[multiset::count (STL/CLR)](../dotnet/multiset-count-stl-clr.md)|Vrátí počet prvků odpovídající zadaného klíče.|  
|[multiset::empty (STL/CLR)](../dotnet/multiset-empty-stl-clr.md)|Zkouší, zda nejsou přítomny žádné prvky.|  
|[multiset::end (STL/CLR)](../dotnet/multiset-end-stl-clr.md)|Určuje konec řízené sekvence.|  
|[multiset::equal_range (STL/CLR)](../dotnet/multiset-equal-range-stl-clr.md)|Najde rozsah, který odpovídá zadanému klíči.|  
|[multiset::erase (STL/CLR)](../dotnet/multiset-erase-stl-clr.md)|Odebere prvky v určených pozicích.|  
|[multiset::find (STL/CLR)](../dotnet/multiset-find-stl-clr.md)|Vyhledá prvek, který odpovídá zadanému klíči.|  
|[multiset::insert (STL/CLR)](../dotnet/multiset-insert-stl-clr.md)|Přidá prvky.|  
|[multiset::key_comp (STL/CLR)](../dotnet/multiset-key-comp-stl-clr.md)|Zkopíruje řazení delegáta pro dva klíče.|  
|[multiset::lower_bound (STL/CLR)](../dotnet/multiset-lower-bound-stl-clr.md)|Najde začátek rozsahu, který odpovídá zadaným klíčem.|  
|[multiset::make_value (STL/CLR)](../dotnet/multiset-make-value-stl-clr.md)|Vytvoří objekt hodnoty.|  
|[multiset::multiset (STL/CLR)](../dotnet/multiset-multiset-stl-clr.md)|Sestaví objekt kontejneru.|  
|[multiset::rbegin (STL/CLR)](../dotnet/multiset-rbegin-stl-clr.md)|Označuje začátek odstínech řízené sekvenci.|  
|[multiset::rend (STL/CLR)](../dotnet/multiset-rend-stl-clr.md)|Označuje konec odstínech řízené sekvenci.|  
|[multiset::size (STL/CLR)](../dotnet/multiset-size-stl-clr.md)|Spočítá počet prvků.|  
|[multiset::swap (STL/CLR)](../dotnet/multiset-swap-stl-clr.md)|Zamění obsah dvou kontejnerů.|  
|[multiset::to_array (STL/CLR)](../dotnet/multiset-to-array-stl-clr.md)|Zkopíruje řízené sekvenci do nové pole.|  
|[multiset::upper_bound (STL/CLR)](../dotnet/multiset-upper-bound-stl-clr.md)|Najde konec rozsahu, který odpovídá zadaným klíčem.|  
|[multiset::value_comp (STL/CLR)](../dotnet/multiset-value-comp-stl-clr.md)|Zkopíruje řazení delegáta pro dvě hodnoty elementu.|  
  
|Operátor|Popis|  
|--------------|-----------------|  
|[multiset::operator= (STL/CLR)](../dotnet/multiset-operator-assign-stl-clr.md)|Nahradí řízené sekvenci.|  
|[operator!= (multiset) (STL/CLR)](../dotnet/operator-inequality-multiset-stl-clr.md)|Určuje, zda `multiset` objekt není rovno jiné `multiset` objektu.|  
|[operator< (multiset) (STL/CLR)](../dotnet/operator-less-than-multiset-stl-clr.md)|Určuje, zda `multiset` objektu je menší než jiná `multiset` objektu.|  
|[operator<= (multiset) (STL/CLR)](../dotnet/operator-less-or-equal-multiset-stl-clr.md)|Určuje, zda `multiset` objektu je menší než nebo rovna do jiného `multiset` objektu.|  
|[operator== (multiset) (STL/CLR)](../dotnet/operator-equality-multiset-stl-clr.md)|Určuje, zda `multiset` objekt rovná jiné `multiset` objektu.|  
|[operator> (multiset) (STL/CLR)](../dotnet/operator-greater-than-multiset-stl-clr.md)|Určuje, zda `multiset` je větší než druhý objekt `multiset` objektu.|  
|[operator>= (multiset) (STL/CLR)](../dotnet/operator-greater-or-equal-multiset-stl-clr.md)|Určuje, zda `multiset` objekt je větší než nebo rovna hodnotě jiného `multiset` objektu.|  
  
## <a name="interfaces"></a>Rozhraní  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Duplicitní objekt.|  
|<xref:System.Collections.IEnumerable>|Pořadí pomocí elementů.|  
|<xref:System.Collections.ICollection>|Údržba skupiny elementů.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Pořadí prostřednictvím typové elementy.|  
|<xref:System.Collections.Generic.ICollection%601>|Údržba skupiny typové elementů.|  
|ITree\<klíče, hodnota >|Udržujte obecné kontejneru.|  
  
## <a name="remarks"></a>Poznámky  
 Objekt přiděluje a uvolní úložiště pro pořadí, které ovládá jako jednotlivé uzly. Vloží elementy na (téměř) vyrovnáváním stromové struktury, která udržuje seřazené změnou propojení mezi uzly, nikdy zkopírováním obsah jednoho uzlu do jiného. To znamená, že můžete vložit a odeberte elementy volně bez narušení zbývající elementy.  
  
 Objekt řadí pořadí jimi řídí voláním objektu uložené delegáta typu [multiset::key_compare (STL/CLR)](../dotnet/multiset-key-compare-stl-clr.md). Objekt uložené delegáta můžete zadat, když vytvoříte multimnožina; Pokud zadáte žádný objekt delegáta, výchozí hodnota je porovnání `operator<(key_type, key_type)`. Přístup k této uložené objekt voláním členské funkce [multiset::key_comp (STL/CLR)](../dotnet/multiset-key-comp-stl-clr.md)`()`.  
  
 Takový objekt delegáta musí použít striktní slabé řazení klíče typu [multiset::key_type (STL/CLR)](../dotnet/multiset-key-type-stl-clr.md). To znamená, pro žádné dva klíče `X` a `Y`:  
  
 `key_comp()(X, Y)`Vrátí stejné logická hodnota způsobit při každém volání.  
  
 Pokud `key_comp()(X, Y)` má hodnotu true, pak `key_comp()(Y, X)` musí mít hodnotu false.  
  
 Pokud `key_comp()(X, Y)` má hodnotu true, pak `X` se říká, že se seřadí před `Y`.  
  
 Pokud `!key_comp()(X, Y) && !key_comp()(Y, X)` má hodnotu true, pak `X` a `Y` se říká, že máte ekvivalentní řazení.  
  
 Pro libovolný element `X` který předchází `Y` v řízené sekvenci `key_comp()(Y, X)` je false. (Pro objekt delegáta výchozí klíče nikdy snížení hodnoty.) Na rozdíl od třídy šablony [nastavit (STL/CLR)](../dotnet/set-stl-clr.md), objekt třídy šablony `multiset` nevyžaduje, aby klíče pro všechny elementy byly jedinečné. (Dvě nebo více klíčů může mít ekvivalentní řazení.)  
  
 Každý prvek slouží jako ey a hodnotu. Pořadí je reprezentována způsobem, který umožňuje vyhledávání, vkládání a odebírání libovolný element s několik operací, které jsou přímo úměrná logaritmus počet elementů v pořadí (logaritmické čas). Vkládání prvků navíc nezruší platnost žádných iterátorů a odstranění prvku zruší platnost pouze těch iterátorů, které odkazují na odstraněný prvek.  
  
 Multimnožina podporuje obousměrné iterátory, což znamená, že můžete tak, aby přiléhající elementy zadané iterátor, který označuje elementu v řízené sekvenci. Speciální hlavního uzlu odpovídá iterator vrácený [multiset::end (STL/CLR)](../dotnet/multiset-end-stl-clr.md)`()`. Tato iterator k dosažení poslední elementu v řízené sekvenci, můžete snížení, pokud je k dispozici. Můžete zvýšit multiset iterator k dosažení hlavního uzlu a pak se porovná rovna `end()`. Ale nemůže dereference iterator vrácený `end()`.  
  
 Všimněte si, že nemůže odkazovat na prvek multiset přímo zadané pořadí umístění – vyžadující iterator náhodný přístup.  
  
 Multimnožinové iterator uloží popisovač pro jeho přidružený multiset uzel, který je pak uloží popisovač pro jeho přidružené kontejneru. Iterátory lze použít pouze jejich přidružené kontejnerové objekty. Multimnožinové iterator zůstane platný tak dlouho, dokud jeho přidružený uzel multiset souvisí s některé multimnožina. Kromě toho je platný iterator dereferencable – slouží k přístupu k nebo alter hodnota elementu se označí – tak dlouho, dokud není rovno `end()`.  
  
 Mazání nebo odebrání element volání destruktoru pro jeho uložené hodnoty. Zničení kontejneru vymaže všechny elementy. Proto kontejner, jehož typ elementu je třída ref zajistí, že žádné elementy outlive kontejneru. Upozorňujeme však, že nemá kontejner popisovače `not` zrušení jeho elementy.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – nebo nastavení >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [hash_map – (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [mapy (STL/CLR)](../dotnet/map-stl-clr.md)   
 [multimnožina](../dotnet/multiset-stl-clr.md)   
 [Sada (STL/CLR)](../dotnet/set-stl-clr.md)   
 [Referenční dokumentace knihoven STL/CLR](../dotnet/stl-clr-library-reference.md)