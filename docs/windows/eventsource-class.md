---
title: "EventSource – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource
dev_langs:
- C++
helpviewer_keywords:
- EventSource class
ms.assetid: 91f1c072-6af4-44e6-b6d8-ac6d0c688dde
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 705260547d5a42b463d61b79c38592874f9dfa19
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="eventsource-class"></a>EventSource – třída
Představuje událost. Členské funkce EventSource přidejte, odeberte a vyvolání obslužné rutiny událostí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<  
   typename TDelegateInterface  
>  
class EventSource;  
```  
  
#### <a name="parameters"></a>Parametry  
 `TDelegateInterface`  
 Rozhraní pro delegáta, který představuje obslužnou rutinu události.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[EventSource::EventSource – konstruktor](../windows/eventsource-eventsource-constructor.md)|Inicializuje novou instanci třídy EventSource.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[EventSource::Add – metoda](../windows/eventsource-add-method.md)|Připojí reprezentována rozhraní zadaného delegáta sadu obslužných rutin událostí pro aktuální objekt EventSource obslužné rutiny události.|  
|[EventSource::GetSize – metoda](../windows/eventsource-getsize-method.md)|Načte číslo přidružené k aktuálnímu objektu EventSource obslužné rutiny událostí|  
|[EventSource::InvokeAll – metoda](../windows/eventsource-invokeall-method.md)|Volá každý obslužná rutina události související s aktuálním objektem EventSource pomocí zadané typy argumentů a argumenty.|  
|[EventSource::Remove – metoda](../windows/eventsource-remove-method.md)|Odstraní reprezentována registrační token zadané události ze sady obslužné rutiny událostí, které jsou přidružené k aktuálnímu objektu EventSource obslužné rutiny události.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[EventSource::addRemoveLock_ – datový člen](../windows/eventsource-addremovelock-data-member.md)|Přístup k synchronizaci [targets_ –](../windows/eventsource-targets-data-member.md) pole při přidání, odebrání nebo volání obslužné rutiny událostí.|  
|[EventSource::targets_ – datový člen](../windows/eventsource-targets-data-member.md)|Pole jeden nebo více obslužných rutin událostí.|  
|[EventSource::targetsPointerLock_ – datový člen](../windows/eventsource-targetspointerlock-data-member.md)|Synchronizuje přístupu ke členům interních datových i obslužné rutiny události pro tento EventSource se přidávají, odebrat nebo vyvolána.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `EventSource`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** event.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)