---
title: priority_queue (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::priority_queue
dev_langs: C++
helpviewer_keywords:
- priority_queue class [STL/CLR]
- <queue> header [STL/CLR]
- <cliext/queue> header [STL/CLR]
ms.assetid: 4d0000d3-68ff-4c4b-8157-7060540136f5
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7eb84d1979d3655c49e5fe089fe04d44708d16a0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="priorityqueue-stlclr"></a>priority_queue (STL/CLR)
Šablony třídy popisuje objekt, který řídí různých délkou seřazené pořadí prvků, které má omezený přístup. Můžete použít adaptér kontejneru `priority_queue` ke správě kontejner základní jako priority fronty.  
  
 V popisu níže `GValue` je stejný jako `Value` Pokud k tomu je typu ref, v takovém případě je `Value^`. Podobně `GContainer` je stejný jako `Container` Pokud k tomu je typu ref, v takovém případě je `Container^`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value,  
    typename Container>  
    ref class priority_queue  
        System::ICloneable,  
        Microsoft::VisualC::StlClr::IPriorityQueue<GValue, GContainer>  
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
|[priority_queue::const_reference (STL/CLR)](../dotnet/priority-queue-const-reference-stl-clr.md)|Typ konstantního odkazu na prvek|  
|[priority_queue::container_type (STL/CLR)](../dotnet/priority-queue-container-type-stl-clr.md)|Typ základního kontejneru.|  
|[priority_queue::difference_type (STL/CLR)](../dotnet/priority-queue-difference-type-stl-clr.md)|Typ vzdálenosti se znaménkem mezi dvěma prvky|  
|[priority_queue::generic_container (STL/CLR)](../dotnet/priority-queue-generic-container-stl-clr.md)|Typ generické rozhraní pro adaptér kontejneru.|  
|[priority_queue::generic_value (STL/CLR)](../dotnet/priority-queue-generic-value-stl-clr.md)|Typ elementu pro obecné rozhraní pro adaptér kontejneru.|  
|[priority_queue::Reference (STL/CLR)](../dotnet/priority-queue-reference-stl-clr.md)|Typ odkazu na prvek|  
|[priority_queue::size_type (STL/CLR)](../dotnet/priority-queue-size-type-stl-clr.md)|Typ vzdálenosti se znaménkem mezi dvěma prvky|  
|[priority_queue::value_compare (STL/CLR)](../dotnet/priority-queue-value-compare-stl-clr.md)|Řazení delegáta pro dva elementy.|  
|[priority_queue::value_type (STL/CLR)](../dotnet/priority-queue-value-type-stl-clr.md)|Typ prvku|  
  
|Členská funkce|Popis|  
|---------------------|-----------------|  
|[priority_queue::Assign (STL/CLR)](../dotnet/priority-queue-assign-stl-clr.md)|Nahradí všechny elementy.|  
|[priority_queue::Empty (STL/CLR)](../dotnet/priority-queue-empty-stl-clr.md)|Zkouší, zda nejsou přítomny žádné prvky.|  
|[priority_queue::get_container (STL/CLR)](../dotnet/priority-queue-get-container-stl-clr.md)|Přístup k podkladové kontejneru.|  
|[priority_queue::POP (STL/CLR)](../dotnet/priority-queue-pop-stl-clr.md)|Odebere element hghest priority.|  
|[priority_queue::priority_queue (STL/CLR)](../dotnet/priority-queue-priority-queue-stl-clr.md)|Sestaví objekt kontejneru.|  
|[priority_queue::push (STL/CLR)](../dotnet/priority-queue-push-stl-clr.md)|Přidá nového elementu.|  
|[priority_queue::size (STL/CLR)](../dotnet/priority-queue-size-stl-clr.md)|Spočítá počet prvků.|  
|[priority_queue::top (STL/CLR)](../dotnet/priority-queue-top-stl-clr.md)|Přístup k elementu nejvyšší prioritou.|  
|[priority_queue::to_array (STL/CLR)](../dotnet/priority-queue-to-array-stl-clr.md)|Zkopíruje řízené sekvenci do nové pole.|  
|[priority_queue::value_comp (STL/CLR)](../dotnet/priority-queue-value-comp-stl-clr.md)|Zkopíruje řazení delegáta pro dva elementy.|  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|[priority_queue::top_item (STL/CLR)](../dotnet/priority-queue-top-item-stl-clr.md)|Přístup k elementu nejvyšší prioritou.|  
  
|Operátor|Popis|  
|--------------|-----------------|  
|[priority_queue::Operator = (STL/CLR)](../dotnet/priority-queue-operator-assign-stl-clr.md)|Nahradí řízené sekvenci.|  
  
## <a name="interfaces"></a>Rozhraní  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Duplicitní objekt.|  
|IPriorityQueue\<hodnota, kontejner >|Udržujte adaptér obecné kontejneru.|  
  
## <a name="remarks"></a>Poznámky  
 Objekt přiděluje a uvolní úložiště pro pořadí jimi řídí prostřednictvím kontejner základní typu `Container`, který ukládá `Value` elementy a zvětšování na vyžádání. Pořadí řazení jako haldy, s nejvyšší prioritou elementem (element nejvyšší) snadno přístupné a vyměnitelné udržuje. Objekt omezuje přístup k vložení nové prvky a odebrání právě nejvyšší prioritou elementu implementace priority fronty.  
  
 Objekt řadí pořadí jimi řídí voláním objektu uložené delegáta typu [priority_queue::value_compare (STL/CLR)](../dotnet/priority-queue-value-compare-stl-clr.md). Objekt uložené delegáta můžete zadat, když vytvoříte priority_queue; Pokud zadáte žádný objekt delegáta, výchozí hodnota je porovnání `operator<(value_type, value_type)`. Přístup k této uložené objekt voláním členské funkce [priority_queue::value_comp (STL/CLR)](../dotnet/priority-queue-value-comp-stl-clr.md)`()`.  
  
 Takový objekt delegáta musí použít striktní slabé řazení hodnoty typu [priority_queue::value_type (STL/CLR)](../dotnet/priority-queue-value-type-stl-clr.md). To znamená, pro žádné dva klíče `X` a `Y`:  
  
 `value_comp()(X, Y)`Vrátí stejné logická hodnota způsobit při každém volání.  
  
 Pokud `value_comp()(X, Y)` má hodnotu true, pak `value_comp()(Y, X)` musí mít hodnotu false.  
  
 Pokud `value_comp()(X, Y)` má hodnotu true, pak `X` se říká, že se seřadí před `Y`.  
  
 Pokud `!value_comp()(X, Y) && !value_comp()(Y, X)` má hodnotu true, pak `X` a `Y` se říká, že máte ekvivalentní řazení.  
  
 Pro libovolný element `X` který předchází `Y` v řízené sekvenci `key_comp()(Y, X)` je false. (Pro objekt delegáta výchozí klíče nikdy snížení hodnoty.)  
  
 Element nejvyšší prioritou, je proto jeden z elementů, které není seřadí před jiného elementu.  
  
 Vzhledem k tomu, že základní kontejneru udržuje elementy seřadit jako haldy:  
  
 Kontejner musí podporovat iterátory náhodný přístup.  
  
 Prvky s ekvivalentní řazení může být odebrány v jiném pořadí než byly; automaticky instalovat. (Řazení není stabilní.)  
  
 Proto kandidáty pro základní kontejneru zahrnují [deque (STL/CLR)](../dotnet/deque-stl-clr.md) a [vektoru (STL/CLR)](../dotnet/vector-stl-clr.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / fronty >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [fronty (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [Zásobník (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [vektor (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [Referenční příručka knihovny STL/CLR](../dotnet/stl-clr-library-reference.md)