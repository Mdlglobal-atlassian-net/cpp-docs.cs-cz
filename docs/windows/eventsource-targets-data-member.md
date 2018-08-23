---
title: EventSource::targets_ – datový člen | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource::targets_
dev_langs:
- C++
helpviewer_keywords:
- targets_ data member
ms.assetid: 5d5cee05-3315-4514-bce2-19173c923c7d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fcdcb759c90009410f76a4b10039a0d976ca0cc4
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605112"
---
# <a name="eventsourcetargets-data-member"></a>EventSource::targets_ – datový člen

Pole jednoho nebo více obslužných rutin událostí.

## <a name="syntax"></a>Syntaxe

```cpp
ComPtr<Details::EventTargetArray> targets_;
```

## <a name="remarks"></a>Poznámky

Pokud událost, která je reprezentována aktuální **EventSource** dochází k objektu, jsou volány obslužné rutiny události.

## <a name="requirements"></a>Požadavky

**Záhlaví:** event.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také
[EventSource – třída](../windows/eventsource-class.md)