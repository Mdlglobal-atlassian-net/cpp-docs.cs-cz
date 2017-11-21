---
title: vektor (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::vector
dev_langs: C++
helpviewer_keywords:
- vector class [STL/CLR]
- <cliext/vector> header [STL/CLR]
- <vector> header [STL/CLR]
ms.assetid: f90060d5-097a-4e9d-9a26-a634b5b9c6c2
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4ee3debcaf651a2a11ef51cac405edf816c5b8ba
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="vector-stlclr"></a>vector (STL/CLR)
Šablony třídy popisuje objekt, který řídí různých délka pořadí elementů s náhodným přístupem. Použít metodu kontejneru `vector` ke správě pořadí elementů jako souvislý blok úložiště. Blok je implementovaný jako pole, které zvětšování na vyžádání.  
  
 V popisu níže `GValue` je stejný jako `Value` Pokud k tomu je typu ref, v takovém případě je `Value^`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value>  
    ref class vector  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        Microsoft::VisualC::StlClr::IVector<GValue>  
    { ..... };  
```  
  
#### <a name="parameters"></a>Parametry  
 Hodnota  
 Typ elementu v řízené sekvenci  
  
## <a name="members"></a>Členové  
  
|Definice typu|Popis|  
|---------------------|-----------------|  
|[Vector::const_iterator (STL/CLR)](../dotnet/vector-const-iterator-stl-clr.md)|Typ konstantního iterátoru řízené sekvence|  
|[Vector::const_reference (STL/CLR)](../dotnet/vector-const-reference-stl-clr.md)|Typ konstantního odkazu na prvek|  
|[Vector::const_reverse_iterator (STL/CLR)](../dotnet/vector-const-reverse-iterator-stl-clr.md)|Typ konstantní zpětné iterator pro řízené sekvenci.|  
|[Vector::difference_type (STL/CLR)](../dotnet/vector-difference-type-stl-clr.md)|Typ vzdálenosti se znaménkem mezi dvěma prvky|  
|[Vector::generic_container (STL/CLR)](../dotnet/vector-generic-container-stl-clr.md)|Typ generické rozhraní pro kontejner.|  
|[Vector::generic_iterator (STL/CLR)](../dotnet/vector-generic-iterator-stl-clr.md)|Typ iterace pro obecné rozhraní kontejneru.|  
|[Vector::generic_reverse_iterator (STL/CLR)](../dotnet/vector-generic-reverse-iterator-stl-clr.md)|Typ zpětné iterator pro obecné rozhraní kontejneru.|  
|[Vector::generic_value (STL/CLR)](../dotnet/vector-generic-value-stl-clr.md)|Typ elementu pro obecné rozhraní kontejneru.|  
|[Vector::iterator (STL/CLR)](../dotnet/vector-iterator-stl-clr.md)|Typ iterátoru řízené sekvence|  
|[Vector::Reference (STL/CLR)](../dotnet/vector-reference-stl-clr.md)|Typ odkazu na prvek|  
|[Vector::reverse_iterator (STL/CLR)](../dotnet/vector-reverse-iterator-stl-clr.md)|Typ zpětné iterator pro řízené sekvenci.|  
|[Vector::size_type (STL/CLR)](../dotnet/vector-size-type-stl-clr.md)|Typ vzdálenosti se znaménkem mezi dvěma prvky|  
|[Vector::value_type (STL/CLR)](../dotnet/vector-value-type-stl-clr.md)|Typ prvku|  
  
|Členská funkce|Popis|  
|---------------------|-----------------|  
|[Vector::Assign (STL/CLR)](../dotnet/vector-assign-stl-clr.md)|Nahradí všechny elementy.|  
|[Vector::AT (STL/CLR)](../dotnet/vector-at-stl-clr.md)|Přístup k elementu na zadané pozici.|  
|[Vector::back (STL/CLR)](../dotnet/vector-back-stl-clr.md)|Přístup k posledním elementem.|  
|[Vector::begin (STL/CLR)](../dotnet/vector-begin-stl-clr.md)|Určuje začátek řízené sekvence.|  
|[Vector::Capacity (STL/CLR)](../dotnet/vector-capacity-stl-clr.md)|Oznamuje velikost úložiště přidělené kontejneru.|  
|[Vector::clear (STL/CLR)](../dotnet/vector-clear-stl-clr.md)|Odebere všechny prvky.|  
|[Vector::Empty (STL/CLR)](../dotnet/vector-empty-stl-clr.md)|Zkouší, zda nejsou přítomny žádné prvky.|  
|[Vector::end (STL/CLR)](../dotnet/vector-end-stl-clr.md)|Určuje konec řízené sekvence.|  
|[Vector::Erase (STL/CLR)](../dotnet/vector-erase-stl-clr.md)|Odebere prvky v určených pozicích.|  
|[Vector::front (STL/CLR)](../dotnet/vector-front-stl-clr.md)|Přístup k první prvek.|  
|[Vector::Insert (STL/CLR)](../dotnet/vector-insert-stl-clr.md)|Přidá elementy na zadané pozici.|  
|[Vector::pop_back (STL/CLR)](../dotnet/vector-pop-back-stl-clr.md)|Odebere poslední element.|  
|[Vector::push_back (STL/CLR)](../dotnet/vector-push-back-stl-clr.md)|Přidá nový posledním elementem.|  
|[Vector::rbegin (STL/CLR)](../dotnet/vector-rbegin-stl-clr.md)|Označuje začátek odstínech řízené sekvenci.|  
|[Vector::rend (STL/CLR)](../dotnet/vector-rend-stl-clr.md)|Označuje konec odstínech řízené sekvenci.|  
|[Vector::Reserve (STL/CLR)](../dotnet/vector-reserve-stl-clr.md)|Zajišťuje růstu minimální kapacitu kontejneru.|  
|[Vector::Resize (STL/CLR)](../dotnet/vector-resize-stl-clr.md)|Změní počet elementů.|  
|[Vector::size (STL/CLR)](../dotnet/vector-size-stl-clr.md)|Spočítá počet prvků.|  
|[Vector::swap (STL/CLR)](../dotnet/vector-swap-stl-clr.md)|Zamění obsah dvou kontejnerů.|  
|[Vector::to_array (STL/CLR)](../dotnet/vector-to-array-stl-clr.md)|Zkopíruje řízené sekvenci do nové pole.|  
|[Vector::Vector (STL/CLR)](../dotnet/vector-vector-stl-clr.md)|Sestaví objekt kontejneru.|  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|[Vector::back_item (STL/CLR)](../dotnet/vector-back-item-stl-clr.md)|Přístup k posledním elementem.|  
|[Vector::front_item (STL/CLR)](../dotnet/vector-front-item-stl-clr.md)|Přístup k první prvek.|  
  
|Operátor|Popis|  
|--------------|-----------------|  
|[Vector::Operator = (STL/CLR)](../dotnet/vector-operator-assign-stl-clr.md)|Nahradí řízené sekvenci.|  
|[Vector::Operator(STL/CLR)](../dotnet/vector-operator-stl-clr.md)|Přístup k elementu na zadané pozici.|  
|[Operator! = (vector) (STL/CLR)](../dotnet/operator-inequality-vector-stl-clr.md)|Určuje, zda `vector` objekt není rovno jiné `vector` objektu.|  
|[Operator < (vector) (STL/CLR)](../dotnet/operator-less-than-vector-stl-clr.md)|Určuje, zda `vector` objektu je menší než jiná `vector` objektu.|  
|[Operator < = (vector) (STL/CLR)](../dotnet/operator-less-or-equal-vector-stl-clr.md)|Určuje, zda `vector` objektu je menší než nebo rovna do jiného `vector` objektu.|  
|[Operator == (vector) (STL/CLR)](../dotnet/operator-equality-vector-stl-clr.md)|Určuje, zda `vector` objekt rovná jiné `vector` objektu.|  
|[Operator > (vector) (STL/CLR)](../dotnet/operator-greater-than-vector-stl-clr.md)|Určuje, zda `vector` je větší než druhý objekt `vector` objektu.|  
|[Operator > = (vector) (STL/CLR)](../dotnet/operator-greater-or-equal-vector-stl-clr.md)|Určuje, zda `vector` objekt je větší než nebo rovna hodnotě jiného `vector` objektu.|  
  
## <a name="interfaces"></a>Rozhraní  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Duplicitní objekt.|  
|<xref:System.Collections.IEnumerable>|Pořadí pomocí elementů.|  
|<xref:System.Collections.ICollection>|Údržba skupiny elementů.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Pořadí prostřednictvím typové elementy.|  
|<xref:System.Collections.Generic.ICollection%601>|Údržba skupiny typové elementů.|  
|<xref:System.Collections.Generic.IList%601>|Údržba seřazené skupiny typové elementů.|  
|IVector < hodnota\>|Udržujte obecné kontejneru.|  
  
## <a name="remarks"></a>Poznámky  
 Objekt přiděluje a uvolní úložiště pro pořadí jimi řídí prostřednictvím uložené pole `Value` prvky, které zvětšování na vyžádání. Růst nastane tak, že náklady na připojování nového elementu je amortizovaný konstantní čas. Jinými slovy náklady na přidání prvků na konci nezvyšuje, v průměru jako délku větší řízené sekvenci získá. Proto vektor je vhodným kandidátem pro základní kontejner pro třídu šablony [zásobníku (STL/CLR)](../dotnet/stack-stl-clr.md).  
  
 A `vector` iterátory podporuje náhodný přístup, což znamená, mohou odkazovat na element přímo zadané číselné pozici, počítáno od nuly pro první prvek (vpředu) k `size() - 1` pro posledním elementem (zpět). Také znamená, že vektor je vhodným kandidátem pro základní kontejner pro třídu šablony [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md).  
  
 Iterator vektoru uloží popisovač pro jeho přidružené vektoru objekt spolu s odchylka elementu, které určí. Iterátory lze použít pouze jejich přidružené kontejnerové objekty. Posun vektoru elementu je stejná jako jeho umístění.  
  
 Vložení nebo vymazání prvky můžete změnit hodnota elementu, které jsou uloženy na dané pozici, takže hodnota určené iterace, které můžete také změnit. (Kontejner může být nutné zkopírovat elementy nahoru nebo dolů k vytvoření hierarchie před typu vložení nebo k vyplnění díru po vymazání.) Nicméně, zůstane vektoru iterator platný tak dlouho, dokud je její posun v rozsahu `[0, size()]`. Kromě toho platný iterator zůstane dereferencable – slouží k přístupu k nebo alter hodnota elementu se označí – tak dlouho, dokud jeho odchylka není rovno `size()`.  
  
 Mazání nebo odebrání element volání destruktoru pro jeho uložené hodnoty. Zničení kontejneru vymaže všechny elementy. Proto kontejner, jehož typ elementu je třída ref zajistí, že žádné elementy outlive kontejneru. Upozorňujeme však, že kontejner popisovače nezničí jejích elementů.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / vektoru >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [seznam (STL/CLR)](../dotnet/list-stl-clr.md)   
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [fronty (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [Zásobník (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [Vector::size (STL/CLR)](../dotnet/vector-size-stl-clr.md)  
 [Referenční příručka knihovny STL/CLR](../dotnet/stl-clr-library-reference.md)