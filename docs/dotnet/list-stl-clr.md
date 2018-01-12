---
title: seznam (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::list
dev_langs: C++
helpviewer_keywords:
- <cliext/list> header [STL/CLR]
- list class [STL/CLR]
- <list> header [STL/CLR]
ms.assetid: a70c45c8-a257-4f6b-8434-b27ff6685bac
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 40046e2b7263559765c2aab2bef13a17c341f7c8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
  
## <a name="members"></a>Členové  
  
|Definice typu|Popis|  
|---------------------|-----------------|  
|[list::const_iterator (STL/CLR)](../dotnet/list-const-iterator-stl-clr.md)|Typ konstantního iterátoru řízené sekvence|  
|[list::const_reference (STL/CLR)](../dotnet/list-const-reference-stl-clr.md)|Typ konstantního odkazu na prvek|  
|[list::const_reverse_iterator (STL/CLR)](../dotnet/list-const-reverse-iterator-stl-clr.md)|Typ konstantní zpětné iterator pro řízené sekvenci.|  
|[list::difference_type (STL/CLR)](../dotnet/list-difference-type-stl-clr.md)|Typ vzdálenosti se znaménkem mezi dvěma prvky|  
|[list::generic_container (STL/CLR)](../dotnet/list-generic-container-stl-clr.md)|Typ generické rozhraní pro kontejner.|  
|[list::generic_iterator (STL/CLR)](../dotnet/list-generic-iterator-stl-clr.md)|Typ iterace pro obecné rozhraní kontejneru.|  
|[list::generic_reverse_iterator (STL/CLR)](../dotnet/list-generic-reverse-iterator-stl-clr.md)|Typ zpětné iterator pro obecné rozhraní kontejneru.|  
|[list::generic_value (STL/CLR)](../dotnet/list-generic-value-stl-clr.md)|Typ elementu pro obecné rozhraní kontejneru.|  
|[list::iterator (STL/CLR)](../dotnet/list-iterator-stl-clr.md)|Typ iterátoru řízené sekvence|  
|[list::reference (STL/CLR)](../dotnet/list-reference-stl-clr.md)|Typ odkazu na prvek|  
|[list::reverse_iterator (STL/CLR)](../dotnet/list-reverse-iterator-stl-clr.md)|Typ zpětné iterator pro řízené sekvenci.|  
|[list::size_type (STL/CLR)](../dotnet/list-size-type-stl-clr.md)|Typ vzdálenosti se znaménkem mezi dvěma prvky|  
|[list::value_type (STL/CLR)](../dotnet/list-value-type-stl-clr.md)|Typ prvku|  
  
|Členská funkce|Popis|  
|---------------------|-----------------|  
|[list::assign (STL/CLR)](../dotnet/list-assign-stl-clr.md)|Nahradí všechny elementy.|  
|[list::back (STL/CLR)](../dotnet/list-back-stl-clr.md)|Přístup k posledním elementem.|  
|[list::begin (STL/CLR)](../dotnet/list-begin-stl-clr.md)|Určuje začátek řízené sekvence.|  
|[list::clear (STL/CLR)](../dotnet/list-clear-stl-clr.md)|Odebere všechny prvky.|  
|[list::empty (STL/CLR)](../dotnet/list-empty-stl-clr.md)|Zkouší, zda nejsou přítomny žádné prvky.|  
|[list::end (STL/CLR)](../dotnet/list-end-stl-clr.md)|Určuje konec řízené sekvence.|  
|[list::erase (STL/CLR)](../dotnet/list-erase-stl-clr.md)|Odebere prvky v určených pozicích.|  
|[list::front (STL/CLR)](../dotnet/list-front-stl-clr.md)|Přístup k první prvek.|  
|[list::insert (STL/CLR)](../dotnet/list-insert-stl-clr.md)|Přidá elementy na zadané pozici.|  
|[list::list (STL/CLR)](../dotnet/list-list-stl-clr.md)|Sestaví objekt kontejneru.|  
|[list::merge (STL/CLR)](../dotnet/list-merge-stl-clr.md)|Sloučí dvě řízené pořadí řazení.|  
|[list::pop_back (STL/CLR)](../dotnet/list-pop-back-stl-clr.md)|Odebere poslední element.|  
|[list::pop_front (STL/CLR)](../dotnet/list-pop-front-stl-clr.md)|Odebere první prvek.|  
|[list::push_back (STL/CLR)](../dotnet/list-push-back-stl-clr.md)|Přidá nový posledním elementem.|  
|[list::push_front (STL/CLR)](../dotnet/list-push-front-stl-clr.md)|Přidá nový první prvek.|  
|[list::rbegin (STL/CLR)](../dotnet/list-rbegin-stl-clr.md)|Označuje začátek odstínech řízené sekvenci.|  
|[list::remove (STL/CLR)](../dotnet/list-remove-stl-clr.md)|Odebere element se zadanou hodnotou.|  
|[list::remove_if (STL/CLR)](../dotnet/list-remove-if-stl-clr.md)|Odebere prvky, které předávají testu zadaný.|  
|[list::rend (STL/CLR)](../dotnet/list-rend-stl-clr.md)|Označuje konec odstínech řízené sekvenci.|  
|[list::resize (STL/CLR)](../dotnet/list-resize-stl-clr.md)|Změní počet elementů.|  
|[list::reverse (STL/CLR)](../dotnet/list-reverse-stl-clr.md)|Obrátí řízené sekvenci.|  
|[list::size (STL/CLR)](../dotnet/list-size-stl-clr.md)|Spočítá počet prvků.|  
|[list::sort (STL/CLR)](../dotnet/list-sort-stl-clr.md)|Řadí řízené sekvenci.|  
|[list::splice (STL/CLR)](../dotnet/list-splice-stl-clr.md)|Restitches propojení mezi uzly.|  
|[list::swap (STL/CLR)](../dotnet/list-swap-stl-clr.md)|Zamění obsah dvou kontejnerů.|  
|[list::to_array (STL/CLR)](../dotnet/list-to-array-stl-clr.md)|Zkopíruje řízené sekvenci do nové pole.|  
|[list::unique (STL/CLR)](../dotnet/list-unique-stl-clr.md)|Odebere přiléhající prvky, které předávají testu zadaný.|  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|[list::back_item (STL/CLR)](../dotnet/list-back-item-stl-clr.md)|Přístup k posledním elementem.|  
|[list::front_item (STL/CLR)](../dotnet/list-front-item-stl-clr.md)|Přístup k první prvek.|  
  
|Operátor|Popis|  
|--------------|-----------------|  
|[list::operator= (STL/CLR)](../dotnet/list-operator-assign-stl-clr.md)|Nahradí řízené sekvenci.|  
|[operator!= (list) (STL/CLR)](../dotnet/operator-inequality-list-stl-clr.md)|Určuje, zda `list` objekt není rovno jiné `list` objektu.|  
|[operator< (list) (STL/CLR)](../dotnet/operator-less-than-list-stl-clr.md)|Určuje, zda `list` objektu je menší než jiná `list` objektu.|  
|[operator<= (list) (STL/CLR)](../dotnet/operator-less-or-equal-list-stl-clr.md)|Určuje, zda `list` objektu je menší než nebo rovna do jiného `list` objektu.|  
|[operator== (list) (STL/CLR)](../dotnet/operator-equality-list-stl-clr.md)|Určuje, zda `list` objekt rovná jiné `list` objektu.|  
|[operator> (list) (STL/CLR)](../dotnet/operator-greater-than-list-stl-clr.md)|Určuje, zda `list` je větší než druhý objekt `list` objektu.|  
|[operator>= (list) (STL/CLR)](../dotnet/operator-greater-or-equal-list-stl-clr.md)|Určuje, zda `list` objekt je větší než nebo rovna hodnotě jiného `list` objektu.|  
  
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
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – nebo jejich výpisu >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [fronty (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [Zásobník (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [vektor (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [Referenční dokumentace knihoven STL/CLR](../dotnet/stl-clr-library-reference.md)