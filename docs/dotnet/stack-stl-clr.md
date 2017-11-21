---
title: "Zásobník (STL/CLR) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::stack
dev_langs: C++
helpviewer_keywords:
- <stack> header [STL/CLR]
- <cliext/stack> header [STL/CLR]
- stack class [STL/CLR]
ms.assetid: 6ee96b9f-8a33-4cf7-b7e0-6535c24bdefb
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: dad00eecc05b8b3020dcf024b297b4b090317ee4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="stack-stlclr"></a>stack (STL/CLR)
Šablony třídy popisuje objekt, který řídí různých délka pořadí elementů, který má přístup poslední, v jakém byly vytvořeny. Můžete použít adaptér kontejneru `stack` ke správě kontejner základní jako zásobník nabízená dolů.  
  
 V popisu níže `GValue` je stejný jako `Value` Pokud k tomu je typu ref, v takovém případě je `Value^`. Podobně `GContainer` je stejný jako `Container` Pokud k tomu je typu ref, v takovém případě je `Container^`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value,  
    typename Container>  
    ref class stack  
        :   public  
        System::ICloneable,  
        Microsoft::VisualC::StlClr::IStack<GValue, GContainer>  
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
|[Stack::const_reference (STL/CLR)](../dotnet/stack-const-reference-stl-clr.md)|Typ konstantního odkazu na prvek|  
|[Stack::container_type (STL/CLR)](../dotnet/stack-container-type-stl-clr.md)|Typ základního kontejneru.|  
|[Stack::difference_type (STL/CLR)](../dotnet/stack-difference-type-stl-clr.md)|Typ vzdálenosti se znaménkem mezi dvěma prvky|  
|[Stack::generic_container (STL/CLR)](../dotnet/stack-generic-container-stl-clr.md)|Typ generické rozhraní pro adaptér kontejneru.|  
|[Stack::generic_value (STL/CLR)](../dotnet/stack-generic-value-stl-clr.md)|Typ elementu pro obecné rozhraní pro adaptér kontejneru.|  
|[Stack::Reference (STL/CLR)](../dotnet/stack-reference-stl-clr.md)|Typ odkazu na prvek|  
|[Stack::size_type (STL/CLR)](../dotnet/stack-size-type-stl-clr.md)|Typ vzdálenosti se znaménkem mezi dvěma prvky|  
|[Stack::value_type (STL/CLR)](../dotnet/stack-value-type-stl-clr.md)|Typ prvku|  
  
|Členská funkce|Popis|  
|---------------------|-----------------|  
|[Stack::Assign (STL/CLR)](../dotnet/stack-assign-stl-clr.md)|Nahradí všechny elementy.|  
|[Stack::Empty (STL/CLR)](../dotnet/stack-empty-stl-clr.md)|Zkouší, zda nejsou přítomny žádné prvky.|  
|[Stack::get_container (STL/CLR)](../dotnet/stack-get-container-stl-clr.md)|Přístup k podkladové kontejneru.|  
|[Stack::POP (STL/CLR)](../dotnet/stack-pop-stl-clr.md)|Odebere poslední element.|  
|[Stack::push (STL/CLR)](../dotnet/stack-push-stl-clr.md)|Přidá nový posledním elementem.|  
|[Stack::size (STL/CLR)](../dotnet/stack-size-stl-clr.md)|Spočítá počet prvků.|  
|[Stack::Stack (STL/CLR)](../dotnet/stack-stack-stl-clr.md)|Sestaví objekt kontejneru.|  
|[Stack::top (STL/CLR)](../dotnet/stack-top-stl-clr.md)|Přístup k posledním elementem.|  
|[Stack::to_array (STL/CLR)](../dotnet/stack-to-array-stl-clr.md)|Zkopíruje řízené sekvenci do nové pole.|  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|[Stack::top_item (STL/CLR)](../dotnet/stack-top-item-stl-clr.md)|Přístup k posledním elementem.|  
  
|Operátor|Popis|  
|--------------|-----------------|  
|[Stack::Operator = (STL/CLR)](../dotnet/stack-operator-assign-stl-clr.md)|Nahradí řízené sekvenci.|  
|[Operator! = (stack) (STL/CLR)](../dotnet/operator-inequality-stack-stl-clr.md)|Určuje, zda `stack` objekt není rovno jiné `stack` objektu.|  
|[Operator < (stack) (STL/CLR)](../dotnet/operator-less-than-stack-stl-clr.md)|Určuje, zda `stack` objektu je menší než jiná `stack` objektu.|  
|[Operator < = (stack) (STL/CLR)](../dotnet/operator-less-or-equal-stack-stl-clr.md)|Určuje, zda `stack` objektu je menší než nebo rovna do jiného `stack` objektu.|  
|[Operator == (stack) (STL/CLR)](../dotnet/operator-equality-stack-stl-clr.md)|Určuje, zda `stack` objekt rovná jiné `stack` objektu.|  
|[Operator > (stack) (STL/CLR)](../dotnet/operator-greater-than-stack-stl-clr.md)|Určuje, zda `stack` je větší než druhý objekt `stack` objektu.|  
|[Operator > = (stack) (STL/CLR)](../dotnet/operator-greater-or-equal-stack-stl-clr.md)|Určuje, zda `stack` objekt je větší než nebo rovna hodnotě jiného `stack` objektu.|  
  
## <a name="interfaces"></a>Rozhraní  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Duplicitní objekt.|  
|IStack\<hodnota, kontejner >|Udržujte adaptér obecné kontejneru.|  
  
## <a name="remarks"></a>Poznámky  
 Objekt přiděluje a uvolní úložiště pro pořadí jimi řídí prostřednictvím kontejner základní typu `Container`, který ukládá `Value` elementy a zvětšování na vyžádání. Objekt omezuje přístup k vložení a odebrání právě posledním elementem, implementace poslední, v jakém byly vytvořeny fronty (také označované jako LIFO fronty, nebo zásobníku).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / stack >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [seznam (STL/CLR)](../dotnet/list-stl-clr.md)   
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [fronty (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [vektor (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [Referenční příručka knihovny STL/CLR](../dotnet/stl-clr-library-reference.md)