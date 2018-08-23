---
title: EventSource::getsize – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource::GetSize
dev_langs:
- C++
helpviewer_keywords:
- GetSize method
ms.assetid: 7825aab5-1a6b-465f-9159-3a6684142d1f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9e852f2664e03ee0ac788fb426951c244f895bb6
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42581100"
---
# <a name="eventsourcegetsize-method"></a>EventSource::GetSize – metoda

Získá počet obslužných rutin událostí, které jsou přidružené k aktuální **EventSource** objektu

## <a name="syntax"></a>Syntaxe

```cpp
size_t GetSize() const;
```

## <a name="return-value"></a>Návratová hodnota

Počet obslužných rutin událostí v [targets_ –](../windows/eventsource-targets-data-member.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** event.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[EventSource – třída](../windows/eventsource-class.md)