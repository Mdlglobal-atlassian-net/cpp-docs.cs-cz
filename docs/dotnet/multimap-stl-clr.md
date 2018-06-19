---
title: multimap (STL/CLR) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::multimap
dev_langs:
- C++
helpviewer_keywords:
- <map> header [STL/CLR]
- <cliext/map> header [STL/CLR]
- multimap class [STL/CLR]
ms.assetid: 3dfe329d-a078-462a-b050-7999ce6110ad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 168c6afec0f8f195d1315a54eff2794f7e3fd07e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33137914"
---
# <a name="multimap-stlclr"></a>multimap (STL/CLR)
Šablony třídy popisuje objekt, který řídí různých délka pořadí elementů, která má obousměrný přístup. Použít metodu kontejneru `multimap` spravovat pořadí elementů jako (téměř) vyrovnáváním seřazené strom uzlů, ukládání jeden element. Element obsahuje klíč, pro řazení sekvenci a namapované hodnotu, kterou má význam pro pravé.  
  
 V popisu níže `GValue` je stejný jako:  
  
 `Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`  
  
 kde:  
  
 `GKey` je stejný jako `Key` Pokud k tomu je typu ref, v takovém případě je `Key^`  
  
 `GMapped` je stejný jako `Mapped` Pokud k tomu je typu ref, v takovém případě je `Mapped^`  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Key,  
    typename Mapped>  
    ref class multimap  
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
  
 Mapovat  
 Typ elementu v řízené sekvenci další součásti.  
  
## <a name="members"></a>Členové  
  
|Definice typu|Popis|  
|---------------------|-----------------|  
|[multimap::const_iterator (STL/CLR)](../dotnet/multimap-const-iterator-stl-clr.md)|Typ konstantního iterátoru řízené sekvence|  
|[multimap::const_reference (STL/CLR)](../dotnet/multimap-const-reference-stl-clr.md)|Typ konstantního odkazu na prvek|  
|[multimap::const_reverse_iterator (STL/CLR)](../dotnet/multimap-const-reverse-iterator-stl-clr.md)|Typ konstantní zpětné iterator pro řízené sekvenci.|  
|[multimap::difference_type (STL/CLR)](../dotnet/multimap-difference-type-stl-clr.md)|Typ (může být podepsaná) vzdálenost mezi dvěma prvky.|  
|[multimap::generic_container (STL/CLR)](../dotnet/multimap-generic-container-stl-clr.md)|Typ generické rozhraní pro kontejner.|  
|[multimap::generic_iterator (STL/CLR)](../dotnet/multimap-generic-iterator-stl-clr.md)|Typ iterace pro obecné rozhraní kontejneru.|  
|[multimap::generic_reverse_iterator (STL/CLR)](../dotnet/multimap-generic-reverse-iterator-stl-clr.md)|Typ zpětné iterator pro obecné rozhraní kontejneru.|  
|[multimap::generic_value (STL/CLR)](../dotnet/multimap-generic-value-stl-clr.md)|Typ elementu pro obecné rozhraní kontejneru.|  
|[multimap::iterator (STL/CLR)](../dotnet/multimap-iterator-stl-clr.md)|Typ iterátoru řízené sekvence|  
|[multimap::key_compare (STL/CLR)](../dotnet/multimap-key-compare-stl-clr.md)|Řazení delegáta pro dva klíče.|  
|[multimap::key_type (STL/CLR)](../dotnet/multimap-key-type-stl-clr.md)|Typ klíče řazení|  
|[multimap::mapped_type (STL/CLR)](../dotnet/multimap-mapped-type-stl-clr.md)|Typ namapované hodnotu přidruženou každý klíč.|  
|[multimap::reference (STL/CLR)](../dotnet/multimap-reference-stl-clr.md)|Typ odkazu na prvek|  
|[multimap::reverse_iterator (STL/CLR)](../dotnet/multimap-reverse-iterator-stl-clr.md)|Typ zpětné iterator pro řízené sekvenci.|  
|[multimap::size_type (STL/CLR)](../dotnet/multimap-size-type-stl-clr.md)|Typ (nezáporné) vzdálenost mezi dvěma prvky.|  
|[multimap::value_compare (STL/CLR)](../dotnet/multimap-value-compare-stl-clr.md)|Řazení delegáta pro dvě hodnoty elementu.|  
|[multimap::value_type (STL/CLR)](../dotnet/multimap-value-type-stl-clr.md)|Typ prvku|  
  
|Členská funkce|Popis|  
|---------------------|-----------------|  
|[multimap::begin (STL/CLR)](../dotnet/multimap-begin-stl-clr.md)|Určuje začátek řízené sekvence.|  
|[multimap::clear (STL/CLR)](../dotnet/multimap-clear-stl-clr.md)|Odebere všechny prvky.|  
|[multimap::count (STL/CLR)](../dotnet/multimap-count-stl-clr.md)|Vrátí počet prvků odpovídající zadaného klíče.|  
|[multimap::empty (STL/CLR)](../dotnet/multimap-empty-stl-clr.md)|Zkouší, zda nejsou přítomny žádné prvky.|  
|[multimap::end (STL/CLR)](../dotnet/multimap-end-stl-clr.md)|Určuje konec řízené sekvence.|  
|[multimap::equal_range (STL/CLR)](../dotnet/multimap-equal-range-stl-clr.md)|Najde rozsah, který odpovídá zadanému klíči.|  
|[multimap::erase (STL/CLR)](../dotnet/multimap-erase-stl-clr.md)|Odebere prvky v určených pozicích.|  
|[multimap::find (STL/CLR)](../dotnet/multimap-find-stl-clr.md)|Vyhledá prvek, který odpovídá zadanému klíči.|  
|[multimap::insert (STL/CLR)](../dotnet/multimap-insert-stl-clr.md)|Přidá prvky.|  
|[multimap::key_comp (STL/CLR)](../dotnet/multimap-key-comp-stl-clr.md)|Zkopíruje řazení delegáta pro dva klíče.|  
|[multimap::lower_bound (STL/CLR)](../dotnet/multimap-lower-bound-stl-clr.md)|Najde začátek rozsahu, který odpovídá zadaným klíčem.|  
|[multimap::make_value (STL/CLR)](../dotnet/multimap-make-value-stl-clr.md)|Vytvoří objekt hodnoty.|  
|[multimap::multimap (STL/CLR)](../dotnet/multimap-multimap-stl-clr.md)|Sestaví objekt kontejneru.|  
|[multimap::rbegin (STL/CLR)](../dotnet/multimap-rbegin-stl-clr.md)|Označuje začátek odstínech řízené sekvenci.|  
|[multimap::rend (STL/CLR)](../dotnet/multimap-rend-stl-clr.md)|Označuje konec odstínech řízené sekvenci.|  
|[multimap::size (STL/CLR)](../dotnet/multimap-size-stl-clr.md)|Spočítá počet prvků.|  
|[multimap::swap (STL/CLR)](../dotnet/multimap-swap-stl-clr.md)|Zamění obsah dvou kontejnerů.|  
|[multimap::to_array (STL/CLR)](../dotnet/multimap-to-array-stl-clr.md)|Zkopíruje řízené sekvenci do nové pole.|  
|[multimap::upper_bound (STL/CLR)](../dotnet/multimap-upper-bound-stl-clr.md)|Najde konec rozsahu, který odpovídá zadaným klíčem.|  
|[multimap::value_comp (STL/CLR)](../dotnet/multimap-value-comp-stl-clr.md)|Zkopíruje řazení delegáta pro dvě hodnoty elementu.|  
  
|Operátor|Popis|  
|--------------|-----------------|  
|[multimap::operator= (STL/CLR)](../dotnet/multimap-operator-assign-stl-clr.md)|Nahradí řízené sekvenci.|  
|[operator!= (multimap) (STL/CLR)](../dotnet/operator-inequality-multimap-stl-clr.md)|Určuje, zda `multimap` objekt není rovno jiné `multimap` objektu.|  
|[operator< (multimap) (STL/CLR)](../dotnet/operator-less-than-multimap-stl-clr.md)|Určuje, zda `multimap` objektu je menší než jiná `multimap` objektu.|  
|[operator<= (multimap) (STL/CLR)](../dotnet/operator-less-or-equal-multimap-stl-clr.md)|Určuje, zda `multimap` objektu je menší než nebo rovna do jiného `multimap` objektu.|  
|[operator== (multimap) (STL/CLR)](../dotnet/operator-equality-multimap-stl-clr.md)|Určuje, zda `multimap` objekt rovná jiné `multimap` objektu.|  
|[operator> (multimap) (STL/CLR)](../dotnet/operator-greater-than-multimap-stl-clr.md)|Určuje, zda `multimap` je větší než druhý objekt `multimap` objektu.|  
|[operator>= (multimap) (STL/CLR)](../dotnet/operator-greater-or-equal-multimap-stl-clr.md)|Určuje, zda `multimap` objekt je větší než nebo rovna hodnotě jiného `multimap` objektu.|  
  
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
  
 Objekt řadí pořadí jimi řídí voláním objektu uložené delegáta typu [multimap::key_compare (STL/CLR)](../dotnet/multimap-key-compare-stl-clr.md). Objekt uložené delegáta můžete zadat, když vytvoříte multimap; Pokud zadáte žádný objekt delegáta, výchozí hodnota je porovnání `operator<(key_type, key_type)`. Přístup k této uložené objekt voláním členské funkce [multimap::key_comp (STL/CLR)](../dotnet/multimap-key-comp-stl-clr.md)`()`.  
  
 Takový objekt delegáta musí použít striktní slabé řazení klíče typu [multimap::key_type (STL/CLR)](../dotnet/multimap-key-type-stl-clr.md). To znamená, pro žádné dva klíče `X` a `Y`:  
  
 `key_comp()(X, Y)` Vrátí stejné logická hodnota způsobit při každém volání.  
  
 Pokud `key_comp()(X, Y)` má hodnotu true, pak `key_comp()(Y, X)` musí mít hodnotu false.  
  
 Pokud `key_comp()(X, Y)` má hodnotu true, pak `X` se říká, že se seřadí před `Y`.  
  
 Pokud `!key_comp()(X, Y) && !key_comp()(Y, X)` má hodnotu true, pak `X` a `Y` se říká, že máte ekvivalentní řazení.  
  
 Pro libovolný element `X` který předchází `Y` v řízené sekvenci `key_comp()(Y, X)` je false. (Pro objekt delegáta výchozí klíče nikdy snížení hodnoty.) Na rozdíl od třídy šablony [mapy (STL/CLR)](../dotnet/map-stl-clr.md), objekt třídy šablony `multimap` nevyžaduje, aby klíče pro všechny elementy byly jedinečné. (Dvě nebo více klíčů může mít ekvivalentní řazení.)  
  
 Každý prvek obsahuje samostatné klíč a hodnotu namapované. Pořadí je reprezentována způsobem, který umožňuje vyhledávání, vkládání a odebírání libovolný element s několik operací, které jsou přímo úměrná logaritmus počet elementů v pořadí (logaritmické čas). Vkládání prvků navíc nezruší platnost žádných iterátorů a odstranění prvku zruší platnost pouze těch iterátorů, které odkazují na odstraněný prvek.  
  
 Multimap podporuje obousměrné iterátory, což znamená, že můžete tak, aby přiléhající elementy zadané iterátor, který označuje elementu v řízené sekvenci. Speciální hlavního uzlu odpovídá iterator vrácený [multimap::end (STL/CLR)](../dotnet/multimap-end-stl-clr.md)`()`. Tato iterator k dosažení poslední elementu v řízené sekvenci, můžete snížení, pokud je k dispozici. Můžete zvýšit multimap iterator k dosažení hlavního uzlu a pak se porovná rovna `end()`. Ale nemůže dereference iterator vrácený `end()`.  
  
 Všimněte si, že nemůže odkazovat na prvek multimap přímo zadané pořadí umístění – vyžadující iterator náhodný přístup.  
  
 Multimap iterator uloží popisovač pro jeho přidružený multimap uzel, který je pak uloží popisovač pro jeho přidružené kontejneru. Iterátory lze použít pouze jejich přidružené kontejnerové objekty. Tak dlouho, dokud jeho přidružený uzel multimap souvisí s některé multimap multimap iterator zůstává v platnosti. Kromě toho je platný iterator dereferencable – slouží k přístupu k nebo alter hodnota elementu se označí – tak dlouho, dokud není rovno `end()`.  
  
 Mazání nebo odebrání element volání destruktoru pro jeho uložené hodnoty. Zničení kontejneru vymaže všechny elementy. Proto kontejner, jehož typ elementu je třída ref zajistí, že žádné elementy outlive kontejneru. Upozorňujeme však, že nemá kontejner popisovače `not` zrušení jeho elementy.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / map >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [hash_map – (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_multimap (STL/CLR)](../dotnet/hash-multimap-stl-clr.md)   
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [mapy (STL/CLR)](../dotnet/map-stl-clr.md)   
 [multiset (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [Sada (STL/CLR)](../dotnet/set-stl-clr.md)   
 [Referenční dokumentace knihoven STL/CLR](../dotnet/stl-clr-library-reference.md)