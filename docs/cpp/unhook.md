---
title: __unhook | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __unhook
- __unhook_cpp
dev_langs: C++
helpviewer_keywords:
- event handlers [C++], dissociating events
- __unhook keyword [C++]
ms.assetid: 953a14f3-5199-459d-81e5-fcf015a19878
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6a5f67b0bdc679c055545cea94e726bc99a66cb0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="unhook"></a>__unhook
Dissociates z událost metodu obslužné rutiny.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      long  __unhook(  
   &SourceClass::EventMethod,  
   source,  
   &ReceiverClass::HandlerMethod  
   [, receiver = this]   
);  
long  __unhook(   
   interface,  
   source  
);  
long  __unhook(  
   source   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 **&***SourceClass* `::` *EventMethod*  
 Ukazatel na metodu události, ze kterého vyjmutí obslužná rutina události:  
  
-   Nativní C++ události: *SourceClass* je třída zdroje událostí a *EventMethod* je událost.  
  
-   Události COM: *SourceClass* je rozhraní pro zdroje událostí a *EventMethod* je jedním z jeho metody.  
  
-   Spravované události: *SourceClass* je třída zdroje událostí a *EventMethod* je událost.  
  
 `interface`  
 Název rozhraní se unhooked z `receiver`, jenom pro přijímače událostí modelu COM, ve kterém *layout_dependent* parametr [event_receiver –](../windows/event-receiver.md) atribut je **true**.  
  
 *zdroj*  
 Ukazatel na instanci zdroj události. V závislosti na kód `type` zadaný v **event_receiver –**, *zdroj* může být jedna z následujících akcí:  
  
-   Nativní událostí zdrojového objektu ukazatel.  
  
-   **IUnknown**– na základě ukazatele (zdroj COM).  
  
-   Ukazatel spravovaného objektu (pro spravované událostí).  
  
 **&***ReceiverClass* `::``HandlerMethod`  
 Ukazatel na metodu obslužné rutiny události být unhooked z události. Obslužná rutina je zadán jako metodu, třídu nebo odkaz na stejnou; Pokud nezadáte název třídy `__unhook` předpokládá třídy, která má být, ve kterém se označuje jako.  
  
-   Nativní C++ události: *ReceiverClass* je třída příjemce událostí a `HandlerMethod` je obslužná rutina.  
  
-   Události COM: *ReceiverClass* je rozhraní pro příjemce událostí a `HandlerMethod` je jedním z jeho obslužné rutiny.  
  
-   Spravované události: *ReceiverClass* je třída příjemce událostí a `HandlerMethod` je obslužná rutina.  
  
 `receiver`(volitelné)  
 Ukazatel na instanci třídy příjemce událostí. Pokud nezadáte příjemce, výchozí hodnota je příjemce třídu nebo strukturu, ve kterém `__unhook` je volána.  
  
## <a name="usage"></a>Použití  
 Lze použít v oboru všechny funkce, včetně hlavní mimo třídy příjemce událostí.  
  
## <a name="remarks"></a>Poznámky  
 Použijte funkci vnitřní `__unhook` v přijímače událostí zrušit přidružení nebo "vyjmutí" metoda obslužné rutiny z metody událostí.  
  
 Existují tři způsoby `__unhook`. Ve většině případů můžete použít první formulář (čtyři argumentů). Můžete použít druhý formulář (dva argumentů) z `__unhook` pouze pro příjemce událostí COM; to unhooks rozhraní celá událost. Třetí formuláře (jednoargumentové) slouží k vyjmutí všechny delegáti ze zadaného zdroje.  
  
 Vrácená nenulová hodnota určuje, že došlo k chybě (spravované události vyvolá výjimku).  
  
 Když zavoláte `__unhook` na události a obslužné rutiny události, které nejsou již byl zapojen, bude mít žádný vliv.  
  
 Při kompilaci kompilátor ověří, že událost existuje a nemá parametr kontrola typu s zadaná obslužná rutina.  
  
 S výjimkou události COM `__hook` a `__unhook` lze volat mimo příjemce událostí.  
  
 Alternativu k použití `__unhook` , je použít operátor-=.  
  
 Informace týkající se kódování spravované události v nové syntaxi najdete v tématu [událostí](../windows/event-cpp-component-extensions.md).  
  
> [!NOTE]
>  Třída šablony nebo struktura nemohou obsahovat události.  
  
## <a name="example"></a>Příklad  
 V tématu [zpracování událostí v nativním kódu C++](../cpp/event-handling-in-native-cpp.md) a [zpracování událostí v modelu COM](../cpp/event-handling-in-com.md) ukázek.  
  
## <a name="see-also"></a>Viz také  
 [Klíčová slova](../cpp/keywords-cpp.md)   
 [event_source –](../windows/event-source.md)   
 [event_receiver –](../windows/event-receiver.md)   
 [__Event](../cpp/event.md)   
 [__hook](../cpp/hook.md)   
 [__raise](../cpp/raise.md)