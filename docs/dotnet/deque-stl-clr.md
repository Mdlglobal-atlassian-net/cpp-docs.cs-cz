---
title: deque (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::deque
dev_langs: C++
helpviewer_keywords:
- deque class [STL/CLR]
- <deque> header [STL/CLR]
- <cliext/deque> header [STL/CLR]
ms.assetid: dd669da3-3c0e-45e9-8596-f6b483720941
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9bd847b2641e6670a91d2edf1eb926aca423ad2f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="deque-stlclr"></a>deque (STL/CLR)
Šablony třídy popisuje objekt, který řídí různých délka pořadí elementů s náhodným přístupem. Použít metodu kontejneru `deque` ke správě pořadí elementů, který vypadá jako souvislý blok úložiště, ale které zvětšit nebo zmenšit na obou koncích, aniž by bylo nutné zkopírovat všechny zbývající elementy. Proto můžete implementovat efektivně `double-ended queue`. (Proto název.)  
  
 V popisu níže `GValue` je stejný jako `Value` Pokud k tomu je typu ref, v takovém případě je `Value^`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value>  
    ref class deque  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        Microsoft::VisualC::StlClr::IDeque<GValue>  
    { ..... };  
```  
  
#### <a name="parameters"></a>Parametry  
 GValue  
 Obecný typ elementu v řízené sekvenci.  
  
 Hodnota  
 Typ elementu v řízené sekvenci  
  
## <a name="members"></a>Členové  
  
|Definice typu|Popis|  
|---------------------|-----------------|  
|[deque::const_iterator (STL/CLR)](../dotnet/deque-const-iterator-stl-clr.md)|Typ konstantního iterátoru řízené sekvence|  
|[deque::const_reference (STL/CLR)](../dotnet/deque-const-reference-stl-clr.md)|Typ konstantního odkazu na prvek|  
|[deque::const_reverse_iterator (STL/CLR)](../dotnet/deque-const-reverse-iterator-stl-clr.md)|Typ konstantní zpětné iterator pro řízené sekvenci.|  
|[deque::difference_type (STL/CLR)](../dotnet/deque-difference-type-stl-clr.md)|Typ vzdálenosti se znaménkem mezi dvěma prvky|  
|[deque::generic_container (STL/CLR)](../dotnet/deque-generic-container-stl-clr.md)|Typ generické rozhraní pro kontejner.|  
|[deque::generic_iterator (STL/CLR)](../dotnet/deque-generic-iterator-stl-clr.md)|Typ iterace pro obecné rozhraní kontejneru.|  
|[deque::generic_reverse_iterator (STL/CLR)](../dotnet/deque-generic-reverse-iterator-stl-clr.md)|Typ zpětné iterator pro obecné rozhraní kontejneru.|  
|[deque::generic_value (STL/CLR)](../dotnet/deque-generic-value-stl-clr.md)|Typ elementu pro obecné rozhraní kontejneru.|  
|[deque::iterator (STL/CLR)](../dotnet/deque-iterator-stl-clr.md)|Typ iterátoru řízené sekvence|  
|[deque::reference (STL/CLR)](../dotnet/deque-reference-stl-clr.md)|Typ odkazu na prvek|  
|[deque::reverse_iterator (STL/CLR)](../dotnet/deque-reverse-iterator-stl-clr.md)|Typ zpětné iterator pro řízené sekvenci.|  
|[deque::size_type (STL/CLR)](../dotnet/deque-size-type-stl-clr.md)|Typ vzdálenosti se znaménkem mezi dvěma prvky|  
|[deque::value_type (STL/CLR)](../dotnet/deque-value-type-stl-clr.md)|Typ prvku|  
  
|Členská funkce|Popis|  
|---------------------|-----------------|  
|[deque::assign (STL/CLR)](../dotnet/deque-assign-stl-clr.md)|Nahradí všechny elementy.|  
|[deque::at (STL/CLR)](../dotnet/deque-at-stl-clr.md)|Přístup k elementu na zadané pozici.|  
|[deque::back (STL/CLR)](../dotnet/deque-back-stl-clr.md)|Přístup k posledním elementem.|  
|[deque::begin (STL/CLR)](../dotnet/deque-begin-stl-clr.md)|Určuje začátek řízené sekvence.|  
|[deque::clear (STL/CLR)](../dotnet/deque-clear-stl-clr.md)|Odebere všechny prvky.|  
|[deque::deque (STL/CLR)](../dotnet/deque-deque-stl-clr.md)|Sestaví objekt kontejneru.|  
|[deque::empty (STL/CLR)](../dotnet/deque-empty-stl-clr.md)|Zkouší, zda nejsou přítomny žádné prvky.|  
|[deque::end (STL/CLR)](../dotnet/deque-end-stl-clr.md)|Určuje konec řízené sekvence.|  
|[deque::erase (STL/CLR)](../dotnet/deque-erase-stl-clr.md)|Odebere prvky v určených pozicích.|  
|[deque::front (STL/CLR)](../dotnet/deque-front-stl-clr.md)|Přístup k první prvek.|  
|[deque::insert (STL/CLR)](../dotnet/deque-insert-stl-clr.md)|Přidá elementy na zadané pozici.|  
|[deque::pop_back (STL/CLR)](../dotnet/deque-pop-back-stl-clr.md)|Odebere poslední element.|  
|[deque::pop_front (STL/CLR)](../dotnet/deque-pop-front-stl-clr.md)|Odebere první prvek.|  
|[deque::push_back (STL/CLR)](../dotnet/deque-push-back-stl-clr.md)|Přidá nový posledním elementem.|  
|[deque::push_front (STL/CLR)](../dotnet/deque-push-front-stl-clr.md)|Přidá nový první prvek.|  
|[deque::rbegin (STL/CLR)](../dotnet/deque-rbegin-stl-clr.md)|Označuje začátek odstínech řízené sekvenci.|  
|[deque::rend (STL/CLR)](../dotnet/deque-rend-stl-clr.md)|Označuje konec odstínech řízené sekvenci.|  
|[deque::resize (STL/CLR)](../dotnet/deque-resize-stl-clr.md)|Změní počet elementů.|  
|[deque::size (STL/CLR)](../dotnet/deque-size-stl-clr.md)|Spočítá počet prvků.|  
|[deque::swap (STL/CLR)](../dotnet/deque-swap-stl-clr.md)|Zamění obsah dvou kontejnerů.|  
|[deque::to_array (STL/CLR)](../dotnet/deque-to-array-stl-clr.md)|Zkopíruje řízené sekvenci do nové pole.|  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|[deque::back_item (STL/CLR)](../dotnet/deque-back-item-stl-clr.md)|Přístup k posledním elementem.|  
|[deque::front_item (STL/CLR)](../dotnet/deque-front-item-stl-clr.md)|Přístup k první prvek.|  
  
|Operátor|Popis|  
|--------------|-----------------|  
|[deque::operator!= (STL/CLR)](../dotnet/deque-operator-inequality-stl-clr.md)|Určuje, zda dva `deque` objekty nejsou stejné.|  
|[deque::operator(STL/CLR)](../dotnet/deque-operator-stl-clr.md)|Přístup k elementu na zadané pozici.|  
|[operator< (deque) (STL/CLR)](../dotnet/operator-less-than-deque-stl-clr.md)|Určuje, zda `deque` objektu je menší než jiná `deque` objektu.|  
|[operator<= (deque) (STL/CLR)](../dotnet/operator-less-or-equal-deque-stl-clr.md)|Určuje, zda `deque` objektu je menší než nebo rovna do jiného `deque` objektu.|  
|[operator= (deque) (STL/CLR)](../dotnet/operator-assign-deque-stl-clr.md)|Nahradí řízené sekvenci.|  
|[operator== (deque) (STL/CLR)](../dotnet/operator-equality-deque-stl-clr.md)|Určuje, zda `deque` objekt rovná jiné `deque` objektu.|  
|[operator> (deque) (STL/CLR)](../dotnet/operator-greater-than-deque-stl-clr.md)|Určuje, zda `deque` je větší než druhý objekt `deque` objektu.|  
|[operator>= (deque) (STL/CLR)](../dotnet/operator-greater-or-equal-deque-stl-clr.md)|Určuje, zda `deque` objekt je větší než nebo rovna hodnotě jiného `deque` objektu.|  
  
## <a name="interfaces"></a>Rozhraní  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Duplicitní objekt.|  
|<xref:System.Collections.IEnumerable>|Pořadí pomocí elementů.|  
|<xref:System.Collections.ICollection>|Údržba skupiny elementů.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Pořadí prostřednictvím typové elementy.|  
|<xref:System.Collections.Generic.ICollection%601>|Údržba skupiny typové elementů.|  
|<xref:System.Collections.Generic.IList%601>|Údržba seřazené skupiny typové elementů.|  
|IDeque < hodnota\>|Udržujte obecné kontejneru.|  
  
## <a name="remarks"></a>Poznámky  
 Objekt přiděluje a uvolní úložiště pro pořadí jimi řídí prostřednictvím uložené pole popisovače, které určit bloky `Value` elementy. Pole zvětšování na vyžádání. Růst nastane tak, že náklady na předřazení nebo připojování nového elementu je konstantní čas a žádné zbývající elementy jsou narušen. Rovněž můžete odebrat prvek na obou koncích konstantní včas a bez narušení zbývající elementy. Proto deque je vhodným kandidátem pro základní kontejner pro třídu šablony [fronty (STL/CLR)](../dotnet/queue-stl-clr.md) nebo třída šablony [zásobníku (STL/CLR)](../dotnet/stack-stl-clr.md).  
  
 A `deque` objekt podporuje iterátory náhodný přístup, což znamená, že mohou odkazovat na prvek přímo zadané pořadí umístění, počítáno od nuly pro první prvek (front), k [deque::size (STL/CLR)](../dotnet/deque-size-stl-clr.md) `() - 1` poslední (zpět) elementu. Také znamená, že je deque vhodným kandidátem pro základní kontejner pro třídu šablony [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md).  
  
 Deque iterator uloží popisovač pro jeho přidružené deque objekt, společně s odchylka elementu, které určí. Iterátory lze použít pouze jejich přidružené kontejnerové objekty. Je posun elementu deque `not` nutně stejné jako jeho umístění. První prvek vložit má odchylka nula, na další prvek připojením nemá odchylka 1, ale na další prvek prepended má odchylka -1.  
  
 Vložení nebo vymazání prvky na obou koncích nemá `not` alter hodnota elementu uloží všechny platné odchylka. Vložení nebo vymazání vnitřních elementu, ale `can` změnit hodnota elementu, které jsou uloženy na danou odchylka, takže hodnota určené iterace, které můžete také změnit. (Kontejner může být nutné zkopírovat elementy nahoru nebo dolů k vytvoření hierarchie před typu vložení nebo k vyplnění díru po vymazání.) Nicméně zůstane deque iterator platný tak dlouho, dokud jeho odchylka označí platný element. Kromě toho platný iterator zůstane dereferencable – slouží k přístupu k nebo alter hodnota elementu se označí – tak dlouho, dokud jeho odchylka není roven posun iterator vrácený `end()`.  
  
 Mazání nebo odebrání element volání destruktoru pro jeho uložené hodnoty. Zničení kontejneru vymaže všechny elementy. Proto kontejner, jehož typ elementu je třída ref zajistí, že žádné elementy outlive kontejneru. Upozorňujeme však, že nemá kontejner popisovače `not` zrušení jeho elementy.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / deque >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [seznam (STL/CLR)](../dotnet/list-stl-clr.md)   
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [fronty (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [Zásobník (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [vektor (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [Referenční dokumentace knihoven STL/CLR](../dotnet/stl-clr-library-reference.md)