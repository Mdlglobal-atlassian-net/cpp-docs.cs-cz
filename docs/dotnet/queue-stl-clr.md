---
title: fronty (STL/CLR) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- cliext::queue
dev_langs:
- C++
helpviewer_keywords:
- <queue> header [STL/CLR]
- queue class [STL/CLR]
- <cliext/queue> header [STL/CLR]
ms.assetid: 9ea7dec3-ea98-48ff-87d0-a5afc924aaf2
caps.latest.revision: 18
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d5b91a2556a93f3cd74a24ea57306d70f2cbdb41
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
|[queue::const_reference (STL/CLR)](../dotnet/queue-const-reference-stl-clr.md)|Typ konstantního odkazu na prvek|  
|[queue::container_type (STL/CLR)](../dotnet/queue-container-type-stl-clr.md)|Typ základního kontejneru.|  
|[queue::difference_type (STL/CLR)](../dotnet/queue-difference-type-stl-clr.md)|Typ vzdálenosti se znaménkem mezi dvěma prvky|  
|[queue::generic_container (STL/CLR)](../dotnet/queue-generic-container-stl-clr.md)|Typ generické rozhraní pro adaptér kontejneru.|  
|[queue::generic_value (STL/CLR)](../dotnet/queue-generic-value-stl-clr.md)|Typ elementu pro obecné rozhraní pro adaptér kontejneru.|  
|[queue::reference (STL/CLR)](../dotnet/queue-reference-stl-clr.md)|Typ odkazu na prvek|  
|[queue::size_type (STL/CLR)](../dotnet/queue-size-type-stl-clr.md)|Typ vzdálenosti se znaménkem mezi dvěma prvky|  
|[queue::value_type (STL/CLR)](../dotnet/queue-value-type-stl-clr.md)|Typ prvku|  
  
|Členská funkce|Popis|  
|---------------------|-----------------|  
|[queue::assign (STL/CLR)](../dotnet/queue-assign-stl-clr.md)|Nahradí všechny elementy.|  
|[queue::back (STL/CLR)](../dotnet/queue-back-stl-clr.md)|Přístup k posledním elementem.|  
|[queue::empty (STL/CLR)](../dotnet/queue-empty-stl-clr.md)|Zkouší, zda nejsou přítomny žádné prvky.|  
|[queue::front (STL/CLR)](../dotnet/queue-front-stl-clr.md)|Přístup k první prvek.|  
|[queue::get_container (STL/CLR)](../dotnet/queue-get-container-stl-clr.md)|Přístup k podkladové kontejneru.|  
|[queue::pop (STL/CLR)](../dotnet/queue-pop-stl-clr.md)|Odebere první prvek.|  
|[queue::push (STL/CLR)](../dotnet/queue-push-stl-clr.md)|Přidá nový posledním elementem.|  
|[queue::queue (STL/CLR)](../dotnet/queue-queue-stl-clr.md)|Sestaví objekt kontejneru.|  
|[queue::size (STL/CLR)](../dotnet/queue-size-stl-clr.md)|Spočítá počet prvků.|  
|[queue::to_array (STL/CLR)](../dotnet/queue-to-array-stl-clr.md)|Zkopíruje řízené sekvenci do nové pole.|  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|[queue::back_item (STL/CLR)](../dotnet/queue-back-item-stl-clr.md)|Přístup k posledním elementem.|  
|[queue::front_item (STL/CLR)](../dotnet/queue-front-item-stl-clr.md)|Přístup k první prvek.|  
  
|Operátor|Popis|  
|--------------|-----------------|  
|[queue::operator= (STL/CLR)](../dotnet/queue-operator-assign-stl-clr.md)|Nahradí řízené sekvenci.|  
|[operator!= (queue) (STL/CLR)](../dotnet/operator-inequality-queue-stl-clr.md)|Určuje, zda `queue` objekt není rovno jiné `queue` objektu.|  
|[operator< (queue) (STL/CLR)](../dotnet/operator-less-than-queue-stl-clr.md)|Určuje, zda `queue` objektu je menší než jiná `queue` objektu.|  
|[operator<= (queue) (STL/CLR)](../dotnet/operator-less-or-equal-queue-stl-clr.md)|Určuje, zda `queue` objektu je menší než nebo rovna do jiného `queue` objektu.|  
|[operator== (queue) (STL/CLR)](../dotnet/operator-equality-queue-stl-clr.md)|Určuje, zda `queue` objekt rovná jiné `queue` objektu.|  
|[operator> (queue) (STL/CLR)](../dotnet/operator-greater-than-queue-stl-clr.md)|Určuje, zda `queue` je větší než druhý objekt `queue` objektu.|  
|[operator>= (queue) (STL/CLR)](../dotnet/operator-greater-or-equal-queue-stl-clr.md)|Určuje, zda `queue` objekt je větší než nebo rovna hodnotě jiného `queue` objektu.|  
  
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
 [Referenční dokumentace knihoven STL/CLR](../dotnet/stl-clr-library-reference.md)