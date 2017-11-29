---
title: "event_source – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.event_source
dev_langs: C++
helpviewer_keywords:
- event handling, attributes
- event logs, event source
- event sources, creating
- event_source attribute
- event sources
- event handling, creating event source
ms.assetid: 0983e36a-6127-4fbb-8a22-8dfec6564c16
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2f7f56e8cfbc8532ad4cd4f1dcfcac4b0ad9fde5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="eventsource"></a>event_source
Vytvoří zdroje událostí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ event_source(  
   type,  
   optimize=[speed | size],  
   decorate=[true | false]  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 `type`  
 Výčet jednoho z následujících hodnot:  
  
-   `native`pro nespravovaného kódu C/C++ (výchozí nastavení pro nespravované třídy).  
  
-   `com`pro kód COM. Je nutné použít `coclass` při `type` = `com`. Tato hodnota vyžaduje, aby následující soubory hlaviček:  
  
    ```  
    #define _ATL_ATTRIBUTES  
    #include <atlbase.h>  
    #include <atlcom.h>  
    ```  
  
 **Optimalizace**  
 Když `type` je **nativní**, můžete zadat **optimalizovat = velikost**, k označení, že 4 bajtů úložišť (minimum) pro všechny události v třídě nebo **optimalizovat = rychlost** (výchozí) k označení, že je 4 * bajtů (# událostí) úložiště.  
  
 **uspořádání**  
 Když `type` je **nativní**, můžete zadat **uspořádání = false**, k označení, že rozšířené název v souboru sloučené (.mrg) by neměla zahrnovat nadřazených název třídy. [/FX](../build/reference/fx-merge-injected-code.md) umožňuje vygenerovat .mrg soubory. **uspořádání = false**, což je výchozí nastavení, výsledkem plně kvalifikovaný typ názvy v sloučené souboru.  
  
## <a name="remarks"></a>Poznámky  
 **Event_source –** C++ atribut určuje, že třídu nebo strukturu, do které se použije bude zdroje událostí.  
  
 **event_source –** se používá ve spojení s [event_receiver –](../windows/event-receiver.md) atribut a [__event](../cpp/event.md) – klíčové slovo. Použití **event_receiver –** vytvoření přijímače událostí. Použití `__event` na metod v rámci zdroji událostí k určení těchto metod jako události.  
  
> [!NOTE]
>  Třída šablony nebo struktura nemohou obsahovat události.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**Třída**,`struct`|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|**Třída typu coclass** při `type` = **com**|  
|**Neplatné atributy**|Žádné|  
  
 Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [Atributy kompilátoru](../windows/compiler-attributes.md)   
 [event_receiver –](../windows/event-receiver.md)   
 [__Event](../cpp/event.md)   
 [__hook](../cpp/hook.md)   
 [__unhook](../cpp/unhook.md)   
 [Class – atributy](../windows/class-attributes.md)   