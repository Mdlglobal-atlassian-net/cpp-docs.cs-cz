---
title: Nastavte (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::set
dev_langs: C++
helpviewer_keywords:
- <cliext/set> header [STL/CLR]
- <set> header [STL/CLR]
- set class [STL/CLR]
ms.assetid: 27d3628c-741a-43a7-bef1-5085536f679e
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9624f08c54629657e7f52c2c688d2083aa557a56
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="set-stlclr"></a>set (STL/CLR)
Šablony třídy popisuje objekt, který řídí různých délka pořadí elementů, která má obousměrný přístup. Použít metodu kontejneru `set` spravovat pořadí elementů jako (téměř) vyrovnáváním seřazené strom uzlů, ukládání jeden element.  
  
 V popisu níže `GValue` je stejný jako `GKey`, který naopak je stejný jako `Key` Pokud k tomu je typu ref, v takovém případě je `Key^`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 Key  
 Typ elementu v řízené sekvenci komponenta klíče.  
  
## <a name="members"></a>Členové  
  
|Definice typu|Popis|  
|---------------------|-----------------|  
|[set::const_iterator (STL/CLR)](../dotnet/set-const-iterator-stl-clr.md)|Typ konstantního iterátoru řízené sekvence|  
|[set::const_reference (STL/CLR)](../dotnet/set-const-reference-stl-clr.md)|Typ konstantního odkazu na prvek|  
|[set::const_reverse_iterator (STL/CLR)](../dotnet/set-const-reverse-iterator-stl-clr.md)|Typ konstantní zpětné iterator pro řízené sekvenci.|  
|[set::difference_type (STL/CLR)](../dotnet/set-difference-type-stl-clr.md)|Typ (může být podepsaná) vzdálenost mezi dvěma prvky.|  
|[set::generic_container (STL/CLR)](../dotnet/set-generic-container-stl-clr.md)|Typ generické rozhraní pro kontejner.|  
|[set::generic_iterator (STL/CLR)](../dotnet/set-generic-iterator-stl-clr.md)|Typ iterace pro obecné rozhraní kontejneru.|  
|[set::generic_reverse_iterator (STL/CLR)](../dotnet/set-generic-reverse-iterator-stl-clr.md)|Typ zpětné iterator pro obecné rozhraní kontejneru.|  
|[set::generic_value (STL/CLR)](../dotnet/set-generic-value-stl-clr.md)|Typ elementu pro obecné rozhraní kontejneru.|  
|[set::iterator (STL/CLR)](../dotnet/set-iterator-stl-clr.md)|Typ iterátoru řízené sekvence|  
|[set::key_compare (STL/CLR)](../dotnet/set-key-compare-stl-clr.md)|Řazení delegáta pro dva klíče.|  
|[set::key_type (STL/CLR)](../dotnet/set-key-type-stl-clr.md)|Typ klíče řazení|  
|[set::reference (STL/CLR)](../dotnet/set-reference-stl-clr.md)|Typ odkazu na prvek|  
|[set::reverse_iterator (STL/CLR)](../dotnet/set-reverse-iterator-stl-clr.md)|Typ zpětné iterator pro řízené sekvenci.|  
|[set::size_type (STL/CLR)](../dotnet/set-size-type-stl-clr.md)|Typ (nezáporné) vzdálenost mezi dvěma prvky.|  
|[set::value_compare (STL/CLR)](../dotnet/set-value-compare-stl-clr.md)|Řazení delegáta pro dvě hodnoty elementu.|  
|[set::value_type (STL/CLR)](../dotnet/set-value-type-stl-clr.md)|Typ prvku|  
  
|Členská funkce|Popis|  
|---------------------|-----------------|  
|[set::begin (STL/CLR)](../dotnet/set-begin-stl-clr.md)|Určuje začátek řízené sekvence.|  
|[set::clear (STL/CLR)](../dotnet/set-clear-stl-clr.md)|Odebere všechny prvky.|  
|[set::count (STL/CLR)](../dotnet/set-count-stl-clr.md)|Vrátí počet prvků odpovídající zadaného klíče.|  
|[set::empty (STL/CLR)](../dotnet/set-empty-stl-clr.md)|Zkouší, zda nejsou přítomny žádné prvky.|  
|[set::end (STL/CLR)](../dotnet/set-end-stl-clr.md)|Určuje konec řízené sekvence.|  
|[set::equal_range (STL/CLR)](../dotnet/set-equal-range-stl-clr.md)|Najde rozsah, který odpovídá zadanému klíči.|  
|[set::erase (STL/CLR)](../dotnet/set-erase-stl-clr.md)|Odebere prvky v určených pozicích.|  
|[set::find (STL/CLR)](../dotnet/set-find-stl-clr.md)|Vyhledá prvek, který odpovídá zadanému klíči.|  
|[set::insert (STL/CLR)](../dotnet/set-insert-stl-clr.md)|Přidá prvky.|  
|[set::key_comp (STL/CLR)](../dotnet/set-key-comp-stl-clr.md)|Zkopíruje řazení delegáta pro dva klíče.|  
|[set::lower_bound (STL/CLR)](../dotnet/set-lower-bound-stl-clr.md)|Najde začátek rozsahu, který odpovídá zadaným klíčem.|  
|[set::make_value (STL/CLR)](../dotnet/set-make-value-stl-clr.md)|Vytvoří objekt hodnoty.|  
|[set::rbegin (STL/CLR)](../dotnet/set-rbegin-stl-clr.md)|Označuje začátek odstínech řízené sekvenci.|  
|[set::rend (STL/CLR)](../dotnet/set-rend-stl-clr.md)|Označuje konec odstínech řízené sekvenci.|  
|[set::set (STL/CLR)](../dotnet/set-set-stl-clr.md)|Sestaví objekt kontejneru.|  
|[set::size (STL/CLR)](../dotnet/set-size-stl-clr.md)|Spočítá počet prvků.|  
|[set::swap (STL/CLR)](../dotnet/set-swap-stl-clr.md)|Zamění obsah dvou kontejnerů.|  
|[set::to_array (STL/CLR)](../dotnet/set-to-array-stl-clr.md)|Zkopíruje řízené sekvenci do nové pole.|  
|[set::upper_bound (STL/CLR)](../dotnet/set-upper-bound-stl-clr.md)|Najde konec rozsahu, který odpovídá zadaným klíčem.|  
|[set::value_comp (STL/CLR)](../dotnet/set-value-comp-stl-clr.md)|Zkopíruje řazení delegáta pro dvě hodnoty elementu.|  
  
|Operátor|Popis|  
|--------------|-----------------|  
|[set::operator= (STL/CLR)](../dotnet/set-operator-assign-stl-clr.md)|Nahradí řízené sekvenci.|  
|[operator!= (set) (STL/CLR)](../dotnet/operator-inequality-set-stl-clr.md)|Určuje, zda `set` objekt není rovno jiné `set` objektu.|  
|[operator< (set) (STL/CLR)](../dotnet/operator-less-than-set-stl-clr.md)|Určuje, zda `set` objektu je menší než jiná `set` objektu.|  
|[operator<= (set) (STL/CLR)](../dotnet/operator-less-or-equal-set-stl-clr.md)|Určuje, zda `set` objektu je menší než nebo rovna do jiného `set` objektu.|  
|[operator== (set) (STL/CLR)](../dotnet/operator-equality-set-stl-clr.md)|Určuje, zda `set` objekt rovná jiné `set` objektu.|  
|[operator> (set) (STL/CLR)](../dotnet/operator-greater-than-set-stl-clr.md)|Určuje, zda `set` je větší než druhý objekt `set` objektu.|  
|[operator>= (set) (STL/CLR)](../dotnet/operator-greater-or-equal-set-stl-clr.md)|Určuje, zda `set` objekt je větší než nebo rovna hodnotě jiného `set` objektu.|  
  
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
  
 Objekt řadí pořadí jimi řídí voláním objektu uložené delegáta typu [set::key_compare (STL/CLR)](../dotnet/set-key-compare-stl-clr.md). Objekt uložené delegáta můžete zadat, když vytvoříte sadu; Pokud zadáte žádný objekt delegáta, výchozí hodnota je porovnání `operator<(key_type, key_type)`. Přístup k této uložené objekt voláním členské funkce [set::key_comp (STL/CLR)](../dotnet/set-key-comp-stl-clr.md)`()`.  
  
 Takový objekt delegáta musí použít striktní slabé řazení klíče typu [set::key_type (STL/CLR)](../dotnet/set-key-type-stl-clr.md). To znamená, pro žádné dva klíče `X` a `Y`:  
  
 `key_comp()(X, Y)`Vrátí stejné logická hodnota způsobit při každém volání.  
  
 Pokud `key_comp()(X, Y)` má hodnotu true, pak `key_comp()(Y, X)` musí mít hodnotu false.  
  
 Pokud `key_comp()(X, Y)` má hodnotu true, pak `X` se říká, že se seřadí před `Y`.  
  
 Pokud `!key_comp()(X, Y) && !key_comp()(Y, X)` má hodnotu true, pak `X` a `Y` se říká, že máte ekvivalentní řazení.  
  
 Pro libovolný element `X` který předchází `Y` v řízené sekvenci `key_comp()(Y, X)` je false. (Pro objekt delegáta výchozí klíče nikdy snížení hodnoty.) Na rozdíl od třídy šablony [nastavit](../dotnet/set-stl-clr.md), objekt třídy šablony `set` nevyžaduje, aby klíče pro všechny elementy byly jedinečné. (Dvě nebo více klíčů může mít ekvivalentní řazení.)  
  
 Každý prvek slouží jako ey a hodnotu. Pořadí je reprezentována způsobem, který umožňuje vyhledávání, vkládání a odebírání libovolný element s několik operací, které jsou přímo úměrná logaritmus počet elementů v pořadí (logaritmické čas). Vkládání prvků navíc nezruší platnost žádných iterátorů a odstranění prvku zruší platnost pouze těch iterátorů, které odkazují na odstraněný prvek.  
  
 Sada podporuje obousměrné iterátory, což znamená, že můžete tak, aby přiléhající elementy zadané iterátor, který označuje elementu v řízené sekvenci. Speciální hlavního uzlu odpovídá iterator vrácený [set::end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`. Tato iterator k dosažení poslední elementu v řízené sekvenci, můžete snížení, pokud je k dispozici. Můžete zvýšit sadu iterator k dosažení hlavního uzlu a bude potom porovnejte rovna `end()`. Ale nemůže dereference iterator vrácený `end()`.  
  
 Všimněte si, že nemůže odkazovat na prvek sady přímo zadané pořadí umístění – vyžadující iterator náhodný přístup.  
  
 Iterator sadu uloží popisovač do přidruženou sadu uzlu, který je pak uloží popisovač pro jeho přidružené kontejneru. Iterátory lze použít pouze jejich přidružené kontejnerové objekty. Iterator sadu zůstane platný tak dlouho, dokud je přidružený některé sadou jeho přidruženou sadu uzel. Kromě toho je platný iterator dereferencable – slouží k přístupu k nebo alter hodnota elementu se označí – tak dlouho, dokud není rovno `end()`.  
  
 Mazání nebo odebrání element volání destruktoru pro jeho uložené hodnoty. Zničení kontejneru vymaže všechny elementy. Proto kontejner, jehož typ elementu je třída ref zajistí, že žádné elementy outlive kontejneru. Upozorňujeme však, že nemá kontejner popisovače `not` zrušení jeho elementy.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – nebo nastavení >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [hash_map – (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [mapy (STL/CLR)](../dotnet/map-stl-clr.md)   
 [nastavení](../dotnet/set-stl-clr.md)   
 [nastavení](../dotnet/set-stl-clr.md)   
 [Referenční dokumentace knihoven STL/CLR](../dotnet/stl-clr-library-reference.md)