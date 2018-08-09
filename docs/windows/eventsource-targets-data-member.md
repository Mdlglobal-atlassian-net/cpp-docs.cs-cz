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
ms.openlocfilehash: ea08cdc8657100e1c1e0157a8a542a44ea34cd4d
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642370"
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