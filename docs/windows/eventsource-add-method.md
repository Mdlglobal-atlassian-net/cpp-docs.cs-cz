---
title: EventSource::add – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource::Add
dev_langs:
- C++
helpviewer_keywords:
- Add method
ms.assetid: 8bded85b-929e-4425-a464-e5de67bb774c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a13c5b48a7e242f47903fda038331fd126832dcf
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42592228"
---
# <a name="eventsourceadd-method"></a>EventSource::Add – metoda

Připojí obslužnou rutinu události reprezentována rozhraní zadaného delegáta k sadě obslužné rutiny událostí pro aktuální **EventSource** objektu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Add(
   _In_ TDelegateInterface* delegateInterface,
   _Out_ EventRegistrationToken* token
);
```

### <a name="parameters"></a>Parametry

*delegateInterface*  
Rozhraní pro objekt delegáta, který představuje obslužnou rutinu události.

*Token*  
Po dokončení této operace, popisovač, který představuje událost. Používat tento token parametru [Remove()](../windows/eventsource-remove-method.md) metoda zahodíte obslužné rutiny události.

## <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** event.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také
[EventSource – třída](../windows/eventsource-class.md)