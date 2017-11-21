---
title: fronty (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::queue
dev_langs: C++
helpviewer_keywords:
- <queue> header [STL/CLR]
- queue class [STL/CLR]
- <cliext/queue> header [STL/CLR]
ms.assetid: 9ea7dec3-ea98-48ff-87d0-a5afc924aaf2
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e55cb83461ed1a0229babf98c384b74de357aeb8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="queue-stlclr"></a>queue (STL/CLR)
Šablony třídy popisuje objekt, který řídí různých délka pořadí elementů, který má přístup první, v jakém byly vytvořeny. Můžete použít adaptér kontejneru `queue` ke správě kontejner základní jako fronty.  
  
 V popisu níže `GValue` je stejný jako `Value` Pokud k tomu je typu ref, v takovém případě je `Value^`. Podobně `GContainer` je stejný jako `Container` Pokud k tomu je typu ref, v takovém případě je `Container^`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value,  
    typename Container>  
    ref class queue  
        :   public  
        System::ICloneable,  
        Microsoft::VisualC::StlClr::IQueue<GValue, GContainer>  
    { ..... };  
```  
  
#### <a name="parameters"></a>Parametry  
 Hodnota  
 Typ elementu v řízené sekvenci  
  
 kontejner  
 Typ základního kontejneru.  
  
## <a name="members"></a>Členové  
  
|Definice typu|Popis|  
|---------------------|-----------------|  
|[Queue::const_reference (STL/CLR)](../dotnet/queue-const-reference-stl-clr.md)|Typ konstantního odkazu na prvek|  
|[Queue::container_type (STL/CLR)](../dotnet/queue-container-type-stl-clr.md)|Typ základního kontejneru.|  
|[Queue::difference_type (STL/CLR)](../dotnet/queue-difference-type-stl-clr.md)|Typ vzdálenosti se znaménkem mezi dvěma prvky|  
|[Queue::generic_container (STL/CLR)](../dotnet/queue-generic-container-stl-clr.md)|Typ generické rozhraní pro adaptér kontejneru.|  
|[Queue::generic_value (STL/CLR)](../dotnet/queue-generic-value-stl-clr.md)|Typ elementu pro obecné rozhraní pro adaptér kontejneru.|  
|[Queue::Reference (STL/CLR)](../dotnet/queue-reference-stl-clr.md)|Typ odkazu na prvek|  
|[Queue::size_type (STL/CLR)](../dotnet/queue-size-type-stl-clr.md)|Typ vzdálenosti se znaménkem mezi dvěma prvky|  
|[Queue::value_type (STL/CLR)](../dotnet/queue-value-type-stl-clr.md)|Typ prvku|  
  
|Členská funkce|Popis|  
|---------------------|-----------------|  
|[Queue::Assign (STL/CLR)](../dotnet/queue-assign-stl-clr.md)|Nahradí všechny elementy.|  
|[Queue::back (STL/CLR)](../dotnet/queue-back-stl-clr.md)|Přístup k posledním elementem.|  
|[Queue::Empty (STL/CLR)](../dotnet/queue-empty-stl-clr.md)|Zkouší, zda nejsou přítomny žádné prvky.|  
|[Queue::front (STL/CLR)](../dotnet/queue-front-stl-clr.md)|Přístup k první prvek.|  
|[Queue::get_container (STL/CLR)](../dotnet/queue-get-container-stl-clr.md)|Přístup k podkladové kontejneru.|  
|[Queue::POP (STL/CLR)](../dotnet/queue-pop-stl-clr.md)|Odebere první prvek.|  
|[Queue::push (STL/CLR)](../dotnet/queue-push-stl-clr.md)|Přidá nový posledním elementem.|  
|[Queue::Queue (STL/CLR)](../dotnet/queue-queue-stl-clr.md)|Sestaví objekt kontejneru.|  
|[Queue::size (STL/CLR)](../dotnet/queue-size-stl-clr.md)|Spočítá počet prvků.|  
|[Queue::to_array (STL/CLR)](../dotnet/queue-to-array-stl-clr.md)|Zkopíruje řízené sekvenci do nové pole.|  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|[Queue::back_item (STL/CLR)](../dotnet/queue-back-item-stl-clr.md)|Přístup k posledním elementem.|  
|[Queue::front_item (STL/CLR)](../dotnet/queue-front-item-stl-clr.md)|Přístup k první prvek.|  
  
|Operátor|Popis|  
|--------------|-----------------|  
|[Queue::Operator = (STL/CLR)](../dotnet/queue-operator-assign-stl-clr.md)|Nahradí řízené sekvenci.|  
|[Operator! = (queue) (STL/CLR)](../dotnet/operator-inequality-queue-stl-clr.md)|Určuje, zda `queue` objekt není rovno jiné `queue` objektu.|  
|[Operator < (queue) (STL/CLR)](../dotnet/operator-less-than-queue-stl-clr.md)|Určuje, zda `queue` objektu je menší než jiná `queue` objektu.|  
|[Operator < = (queue) (STL/CLR)](../dotnet/operator-less-or-equal-queue-stl-clr.md)|Určuje, zda `queue` objektu je menší než nebo rovna do jiného `queue` objektu.|  
|[Operator == (queue) (STL/CLR)](../dotnet/operator-equality-queue-stl-clr.md)|Určuje, zda `queue` objekt rovná jiné `queue` objektu.|  
|[Operator > (queue) (STL/CLR)](../dotnet/operator-greater-than-queue-stl-clr.md)|Určuje, zda `queue` je větší než druhý objekt `queue` objektu.|  
|[Operator > = (queue) (STL/CLR)](../dotnet/operator-greater-or-equal-queue-stl-clr.md)|Určuje, zda `queue` objekt je větší než nebo rovna hodnotě jiného `queue` objektu.|  
  
## <a name="interfaces"></a>Rozhraní  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Duplicitní objekt.|  
|IQueue\<hodnota, kontejner >|Udržujte adaptér obecné kontejneru.|  
  
## <a name="remarks"></a>Poznámky  
 Objekt přiděluje a uvolní úložiště pro pořadí jimi řídí prostřednictvím kontejner základní typu `Container`, který ukládá `Value` elementy a zvětšování na vyžádání. Objekt omezuje přístup jenom vkládání první prvek a odebrání posledním elementem, implementace ven first-in fronty (také označované jako fronty FIFO nebo jednoduše fronty).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / fronty >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [seznam (STL/CLR)](../dotnet/list-stl-clr.md)   
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [Zásobník (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [vektor (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [Referenční příručka knihovny STL/CLR](../dotnet/stl-clr-library-reference.md)