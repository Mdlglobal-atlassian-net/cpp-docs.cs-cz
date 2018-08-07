---
title: Eventtargetarray – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray
dev_langs:
- C++
helpviewer_keywords:
- EventTargetArray class
ms.assetid: e3cadb7c-2160-4cbb-a2f8-c28733d1e96d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2757589509e4a2b091c5057ef2065866a8829494
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570418"
---
# <a name="eventtargetarray-class"></a>EventTargetArray – třída
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class EventTargetArray : public Microsoft::WRL::RuntimeClass<Microsoft::WRL::RuntimeClassFlags<ClassicCom>, IUnknown>;  
```  
  
## <a name="remarks"></a>Poznámky  
 Reprezentuje pole prvků obslužných rutin událostí.  
  
 Obslužné rutiny událostí, které jsou přidružené [EventSource](../windows/eventsource-class.md) objektu jsou uloženy v chráněné **EventTargetArray** datový člen.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[EventTargetArray::EventTargetArray – konstruktor](../windows/eventtargetarray-eventtargetarray-constructor.md)|Inicializuje novou instanci třídy **EventTargetArray** třídy.|  
|[EventTargetArray::~EventTargetArray – destruktor](../windows/eventtargetarray-tilde-eventtargetarray-destructor.md)|Zruší inicializaci aktuální **EventTargetArray** třídy.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[EventTargetArray::AddTail – metoda](../windows/eventtargetarray-addtail-method.md)|Obslužné rutiny zadané události připojí na konec vnitřní pole obslužných rutin událostí.|  
|[EventTargetArray::Begin – metoda](../windows/eventtargetarray-begin-method.md)|Získá adresu prvního prvku v poli interní obslužných rutin událostí.|  
|[EventTargetArray::End – metoda](../windows/eventtargetarray-end-method.md)|Získá adresu poslední prvek v poli interní obslužných rutin událostí.|  
|[EventTargetArray::Length – metoda](../windows/eventtargetarray-length-method.md)|Získá aktuální počet prvků v poli interní obslužných rutin událostí.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `EventTargetArray`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** event.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)