---
title: event_source | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.event_source
dev_langs:
- C++
helpviewer_keywords:
- event handling, attributes
- event logs, event source
- event sources, creating
- event_source attribute
- event sources
- event handling, creating event source
ms.assetid: 0983e36a-6127-4fbb-8a22-8dfec6564c16
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e44b5757ea7b9e469275688443ba7ed1e3810571
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2018
ms.locfileid: "39571386"
---
# <a name="eventsource"></a>event_source
Vytvoří zdroj událostí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ event_source(  
   type,  
   optimize=[speed | size],  
   decorate=[true | false]  
) ]  
```  
  
### <a name="parameters"></a>Parametry  
 *Typ*  
 Výčet jedné z následujících hodnot:  
  
-   `native` pro nespravovaný kód jazyka C/C++ (výchozí nastavení pro nespravované třídy).  
  
-   `com` pro kód v modelu COM. Je nutné použít `coclass` při `type` = `com`. Tato hodnota vyžaduje, aby následující soubory hlaviček:  
  
    ```  
    #define _ATL_ATTRIBUTES  
    #include <atlbase.h>  
    #include <atlcom.h>  
    ```  
  
 *optimize*  
 Když *typ* je `native`, můžete zadat `optimize=size`, pro indikaci, že je 4 bajty úložiště (minimum) pro všechny události v třídě nebo `optimize=speed` (výchozí), že je 4 * (počet událostí) bajtů úložiště.  
  
 *vyplnění*  
 Když *typ* je `native`, můžete zadat `decorate=false`, pro indikaci, že rozbalený název souboru sloučeného (.mrg) by neměla obsahovat název nadřazené třídy. [/FX](../build/reference/fx-merge-injected-code.md) umožňuje generovat soubory .mrg. `decorate=false`, což je výchozí nastavení, výsledkem názvy typů plně kvalifikovaný v sloučený soubor.  
  
## <a name="remarks"></a>Poznámky  
 **Event_source** C++ atribut určuje, zda třídu nebo strukturu, do které se použije zdroj událostí.  
  
 **event_source** se používá ve spojení s [event_receiver](../windows/event-receiver.md) atribut a [__event](../cpp/event.md) – klíčové slovo. Použití `event_receiver` vytvoření přijímače událostí. Použití **__event** pro metody v rámci zdroje událostí k určení těchto metod jako události.  
  
> [!NOTE]
>  Třída šablony nebo struktura nemohou obsahovat události.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**Třída**, **– struktura**|  
|**Opakovatelné**|Ne|  
|**Vyžadované atributy**|**coclass** při `type`=`com`|  
|**Neplatné atributy**|Žádné|  
  
 Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [Atributy kompilátoru](../windows/compiler-attributes.md)   
 [event_receiver](../windows/event-receiver.md)   
 [__Event](../cpp/event.md)   
 [__hook](../cpp/hook.md)   
 [__unhook](../cpp/unhook.md)   
 [Atributy třídy](../windows/class-attributes.md)   