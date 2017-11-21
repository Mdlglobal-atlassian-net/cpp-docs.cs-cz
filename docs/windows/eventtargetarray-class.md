---
title: "EventTargetArray – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: event/Microsoft::WRL::Details::EventTargetArray
dev_langs: C++
helpviewer_keywords: EventTargetArray class
ms.assetid: e3cadb7c-2160-4cbb-a2f8-c28733d1e96d
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b7f23265601411c0a1913b1e06b9fffa62bfa07f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="eventtargetarray-class"></a>EventTargetArray – třída
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class EventTargetArray : public Microsoft::WRL::RuntimeClass<Microsoft::WRL::RuntimeClassFlags<ClassicCom>, IUnknown>;  
```  
  
## <a name="remarks"></a>Poznámky  
 Představuje pole obslužné rutiny událostí.  
  
 Obslužné rutiny událostí, které jsou přidružené [EventSource](../windows/eventsource-class.md) objekt jsou uložené v chráněného člena EventTargetArray data.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Eventtargetarray::eventtargetarray – konstruktor](../windows/eventtargetarray-eventtargetarray-constructor.md)|Inicializuje novou instanci třídy EventTargetArray.|  
|[EventTargetArray:: ~ eventtargetarray – destruktor](../windows/eventtargetarray-tilde-eventtargetarray-destructor.md)|Deinitializes aktuální EventTargetArray – třída.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Eventtargetarray::addtail – metoda](../windows/eventtargetarray-addtail-method.md)|Přidá zadanou událost obslužné rutiny na konec interní pole obslužné rutiny událostí.|  
|[Eventtargetarray::begin – metoda](../windows/eventtargetarray-begin-method.md)|Získá adresu první prvek v poli interní obslužných rutin událostí.|  
|[Eventtargetarray::end – metoda](../windows/eventtargetarray-end-method.md)|Získá adresu posledním prvkem v poli interní obslužných rutin událostí.|  
|[Eventtargetarray::length – metoda](../windows/eventtargetarray-length-method.md)|Získá aktuální počet prvků v poli interní obslužných rutin událostí.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `EventTargetArray`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** event.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL:: details – Namespace](../windows/microsoft-wrl-details-namespace.md)