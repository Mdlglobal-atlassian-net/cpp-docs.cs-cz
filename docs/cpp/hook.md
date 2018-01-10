---
title: __hook | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: __hook_cpp
dev_langs: C++
helpviewer_keywords:
- __hook keyword [C++]
- event handlers [C++], connecting events to
ms.assetid: f4cabb10-d293-4c0e-a1d2-4745ef9cc22c
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dfc9112c79279e3e5c419efbd12f5883349c0e94
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="hook"></a>__hook
Přidruží metoda obslužná rutina události.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      long __hook(  
   &SourceClass::EventMethod,  
   source,  
   &ReceiverClass::HandlerMethod  
   [, receiver = this]  
);  
long __hook(  
   interface,  
   source  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 **&***SourceClass* `::` *EventMethod*  
 Ukazatel na metodu události, ke kterému napojit obslužná rutina události:  
  
-   Nativní C++ události: *SourceClass* je třída zdroje událostí a *EventMethod* je událost.  
  
-   Události COM: *SourceClass* je rozhraní pro zdroje událostí a *EventMethod* je jedním z jeho metody.  
  
-   Spravované události: *SourceClass* je třída zdroje událostí a *EventMethod* je událost.  
  
 `interface`  
 Název rozhraní se připojili k `receiver`, jenom pro přijímače událostí modelu COM, ve kterém *layout_dependent* parametr [event_receiver –](../windows/event-receiver.md) atribut je **true**.  
  
 *zdroj*  
 Ukazatel na instanci zdroj události. V závislosti na kód `type` zadaný v **event_receiver –**, *zdroj* může být jedna z následujících akcí:  
  
-   Nativní událostí zdrojového objektu ukazatel.  
  
-   **IUnknown**– na základě ukazatele (zdroj COM).  
  
-   Ukazatel spravovaného objektu (pro spravované událostí).  
  
 **&***ReceiverClass* `::``HandlerMethod`  
 Ukazatel na metodu obslužné rutiny události pro jazyka pro událost. Obslužná rutina je zadán jako metodu, třídu nebo odkaz na stejnou; Pokud nezadáte název třídy `__hook` předpokládá třídy, která má být, ve kterém se označuje jako.  
  
-   Nativní C++ události: *ReceiverClass* je třída příjemce událostí a `HandlerMethod` je obslužná rutina.  
  
-   Události COM: *ReceiverClass* je rozhraní pro příjemce událostí a `HandlerMethod` je jedním z jeho obslužné rutiny.  
  
-   Spravované události: *ReceiverClass* je třída příjemce událostí a `HandlerMethod` je obslužná rutina.  
  
 `receiver`(volitelné)  
 Ukazatel na instanci třídy příjemce událostí. Pokud nezadáte příjemce, výchozí hodnota je příjemce třídu nebo strukturu, ve kterém `__hook` je volána.  
  
## <a name="usage"></a>Použití  
 Lze použít v oboru všechny funkce, včetně hlavní mimo třídy příjemce událostí.  
  
## <a name="remarks"></a>Poznámky  
 Použijte funkci vnitřní `__hook` v přijímače událostí přidružit nebo napojit metoda obslužná rutina s metodou události. Zadaná obslužná rutina je volána poté, když zdroji vyvolá zadané události. Můžete napojit několik obslužné rutiny pro jednu událost nebo napojit několik událostí k jedné obslužné rutině.  
  
 Existují dvě formy `__hook`. První formulář (čtyři argumentů), ve většině případů můžete konkrétně použít pro přijímače událostí modelu COM, ve kterém *layout_dependent* parametr [event_receiver –](../windows/event-receiver.md) atribut je **false** .  
  
 V takových případech není nutné napojit všechny metody v rozhraní, než se aktivuje událost na jednu z metod; pouze metodu zpracování události je potřeba jazyka. Můžete použít druhý formulář (dva argumentů) z `__hook` pouze pro příjemce událostí COM ve kterém *layout_dependent***= true**.  
  
 `__hook`vrací dlouhou hodnotu. Vrácená nenulová hodnota určuje, že došlo k chybě (spravované události throw výjimku).  
  
 Kompilátor zkontroluje existenci událost a že podpisu události souhlasí s podpisem delegáta.  
  
 S výjimkou události COM `__hook` a `__unhook` lze volat mimo příjemce událostí.  
  
 Alternativu k použití `__hook` je použití += operátor.  
  
 Informace týkající se kódování spravované události v nové syntaxi najdete v tématu [událostí](../windows/event-cpp-component-extensions.md).  
  
> [!NOTE]
>  Třída šablony nebo struktura nemohou obsahovat události.  
  
## <a name="example"></a>Příklad  
 V tématu [zpracování událostí v nativním kódu C++](../cpp/event-handling-in-native-cpp.md) a [zpracování událostí v modelu COM](../cpp/event-handling-in-com.md) ukázek.  
  
## <a name="see-also"></a>Viz také  
 [Klíčová slova](../cpp/keywords-cpp.md)   
 [Zpracování událostí](../cpp/event-handling.md)   
 [event_source –](../windows/event-source.md)   
 [event_receiver –](../windows/event-receiver.md)   
 [__unhook](../cpp/unhook.md)   
 [__raise](../cpp/raise.md)