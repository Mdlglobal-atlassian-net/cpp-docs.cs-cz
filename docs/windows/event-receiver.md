---
title: "event_receiver – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.event_receiver
dev_langs: C++
helpviewer_keywords:
- event_receiver attribute
- event receivers
- events [C++], event receivers (sinks)
- event handling [C++], attributes
- event handling [C++], creating receiver
- event sinks, creating
- event sinks
ms.assetid: bf8fe770-3ea2-4128-b46b-166222ee4097
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 50ea26172e2f5112e760aa02d9247d07afbead2b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="eventreceiver"></a>event_receiver
Vytvoří přijímače událostí (jímky).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ event_receiver(  
   type   
   [, layout_dependent=false]   
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 `type`  
 Výčet jednoho z následujících hodnot:  
  
-   `native`pro nespravovaného kódu C/C++ (výchozí nastavení pro nativní třídy).  
  
-   `com`pro kód COM. Tato hodnota vyžaduje, aby následující soubory hlaviček:  
  
    ```  
    #define _ATL_ATTRIBUTES  
    #include <atlbase.h>  
    #include <atlcom.h>  
    ```  
  
 **layout_dependent**  
 Zadejte *layout_dependent* pouze v případě `type` = **com**. *layout_dependent* je logická hodnota:  
  
-   **Hodnota TRUE,** znamená, že podpis delegáty v případě, že příjemce musí přesně shodovat těch, na které se jsou byl zapojen události zdroje. Názvy obslužná rutina příjemce událostí musí odpovídat názvům zadaný v rozhraní zdroj relevantní události. Je nutné použít **třída typu coclass** při *layout_dependent* je **true**. Je něco víc efektivní zadejte **true**.  
  
-   **false** (výchozí) znamená, že volání třída konvence a úložiště (virtuální, statické a jiné) nemusí odpovídat metodu událostí a obslužných rutin; ani názvy obslužná rutina potřebujete odpovídat názvům rozhraní metoda zdroje událostí.  
  
## <a name="remarks"></a>Poznámky  
 **Event_receiver –** C++ atribut určuje, že třídu nebo strukturu, do které se použije bude přijímače událostí pomocí modelu jednotná událostí Visual C++.  
  
 **event_receiver –** se používá s [event_source –](../windows/event-source.md) atribut a [__hook](../cpp/hook.md) a [__unhook](../cpp/unhook.md) klíčová slova. Použití **event_source –** k vytvoření zdroje událostí. Použití `__hook` v rámci metod příjemce událostí přidružit metody příjemce událostí ("háku") k událostem zdroje událostí. Použití `__unhook` zrušení jejich přidružení.  
  
 *layout_dependent* je určena pouze pro přijímače událostí modelu COM (`type`=**com**). Výchozí hodnota pro *layout_dependent* je **false**.  
  
> [!NOTE]
>  Třída šablony nebo struktura nemohou obsahovat události.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**Třída**,`struct`|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|**Třída typu coclass** při *layout_dependent*=**true**|  
|**Neplatné atributy**|Žádné|  
  
 Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [Atributy kompilátoru](../windows/compiler-attributes.md)   
 [event_source –](../windows/event-source.md)   
 [__Event](../cpp/event.md)   
 [__hook](../cpp/hook.md)   
 [__unhook](../cpp/unhook.md)   
 [Atributy třídy](../windows/class-attributes.md)   
