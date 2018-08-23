---
title: EventSource – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 03/22/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource
dev_langs:
- C++
helpviewer_keywords:
- EventSource class
ms.assetid: 91f1c072-6af4-44e6-b6d8-ac6d0c688dde
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8805547c5803ae665178330063e6b77b1b3c662e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42596208"
---
# <a name="eventsource-class"></a>EventSource – třída

Představuje událost agile. **EventSource** členské funkce přidání, odebrání a vyvolání obslužných rutin událostí. Agilní události, použijte [agileeventsource –](agileeventsource-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template<typename TDelegateInterface>
class EventSource;
```

### <a name="parameters"></a>Parametry

*TDelegateInterface*  
Rozhraní pro delegáta, který představuje obslužnou rutinu události.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[EventSource::EventSource – konstruktor](../windows/eventsource-eventsource-constructor.md)|Inicializuje novou instanci třídy **EventSource** třídy.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[EventSource::Add – metoda](../windows/eventsource-add-method.md)|Připojí obslužnou rutinu události reprezentována rozhraní zadaného delegáta k sadě obslužné rutiny událostí pro aktuální **EventSource** objektu.|
|[EventSource::GetSize – metoda](../windows/eventsource-getsize-method.md)|Získá počet obslužných rutin událostí, které jsou přidružené k aktuální **EventSource** objektu|
|[EventSource::InvokeAll – metoda](../windows/eventsource-invokeall-method.md)|Volá Každá obslužná rutina události spojené s aktuálním **EventSource** pomocí zadanými typy argumentu a argumenty.|
|[EventSource::Remove – metoda](../windows/eventsource-remove-method.md)|Odstraní obslužná rutina události reprezentována zadanou událost registračního tokenu ze sady obslužné rutiny událostí, které jsou přidružené k aktuální **EventSource** objektu.|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[EventSource::addRemoveLock_ – datový člen](../windows/eventsource-addremovelock-data-member.md)|Synchronizuje přístup k [targets_ –](../windows/eventsource-targets-data-member.md) pole při přidání, odebrání nebo volání obslužné rutiny událostí.|
|[EventSource::targets_ – datový člen](../windows/eventsource-targets-data-member.md)|Pole jednoho nebo více obslužných rutin událostí.|
|[EventSource::targetsPointerLock_ – datový člen](../windows/eventsource-targetspointerlock-data-member.md)|Synchronizuje přístup k interní datových členů, dokonce i za běhu obslužné rutiny událostí pro EventSource se neustále přidávají, odebrat nebo vyvolána.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`EventSource`

## <a name="requirements"></a>Požadavky

**Záhlaví:** event.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)  
[AgileEventSource – třída](agileeventsource-class.md)