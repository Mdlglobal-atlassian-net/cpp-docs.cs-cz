---
title: event_receiver | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.event_receiver
dev_langs:
- C++
helpviewer_keywords:
- event_receiver attribute
- event receivers
- events [C++], event receivers (sinks)
- event handling [C++], attributes
- event handling [C++], creating receiver
- event sinks, creating
- event sinks
ms.assetid: bf8fe770-3ea2-4128-b46b-166222ee4097
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0b13acb5d637b4a733f2a2b9c66c8ded977c7847
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2018
ms.locfileid: "39569931"
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
 *Typ*  
 Výčet jedné z následujících hodnot:  
  
-   `native` pro nespravovaný kód jazyka C/C++ (výchozí pro nativní třídy).  
  
-   `com` pro kód v modelu COM. Tato hodnota vyžaduje, aby následující soubory hlaviček:  
  
    ```  
    #define _ATL_ATTRIBUTES  
    #include <atlbase.h>  
    #include <atlcom.h>  
    ```  
  
 **má**  
 Zadejte *layout_dependent* pouze tehdy, pokud `type` = **com**. *layout_dependent* je logická hodnota:  
  
-   **Hodnota TRUE** znamená, že podpis delegáty, v případě, že příjemce musí přesně odpovídat těch, ke kterým jsou připojeny události zdroje. Názvy obslužných rutin událostí příjemce musí shodovat s názvy zadané v zdrojové rozhraní relevantní události. Je nutné použít `coclass` při *layout_dependent* je **true**. Je efektivnější zadejte **true**.  
  
-   **false** (výchozí) znamená, že volání třídy konvence a úložiště (virtuální, statické a další) tak, aby odpovídaly metodu události a obslužné rutiny; nemají ani tak, aby odpovídaly názvy metod rozhraní zdroje událostí potřeba názvy obslužných rutin.  
  
## <a name="remarks"></a>Poznámky  
 **Event_receiver** C++ atribut určuje, zda třídu nebo strukturu, do které se použije přijímače událostí pomocí sjednocené události modelu Visual C++.  
  
 **event_receiver** se používá s [event_source](../windows/event-source.md) atribut a [__hook](../cpp/hook.md) a [__unhook](../cpp/unhook.md) klíčová slova. Použití `event_source` k vytvoření zdroje událostí. Použití **__hook** v rámci metod přijímače událostí k přidružení metody příjemce událostí ("připojení") na události zdroje událostí. Použití **__unhook** zrušení jejich přidružení.  
  
 *má* je určena pouze pro přijímače událostí modelu COM (`type`=**com**). Výchozí nastavení pro *layout_dependent* je **false**.  
  
> [!NOTE]
>  Třída šablony nebo struktura nemohou obsahovat události.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**Třída**, **– struktura**|  
|**Opakovatelné**|Ne|  
|**Vyžadované atributy**|**coclass** při *layout_dependent*=**true**|  
|**Neplatné atributy**|Žádné|  
  
 Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [Atributy kompilátoru](../windows/compiler-attributes.md)   
 [event_source –](../windows/event-source.md)   
 [__Event](../cpp/event.md)   
 [__hook](../cpp/hook.md)   
 [__unhook](../cpp/unhook.md)   
 [Atributy třídy](../windows/class-attributes.md)   