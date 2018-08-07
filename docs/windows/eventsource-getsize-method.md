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
ms.openlocfilehash: e38bd233c302d0a2bd054a1cbf2efb301089a003
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2018
ms.locfileid: "39569667"
---
# <a name="eventsourcegetsize-method"></a>EventSource::GetSize – metoda
Získá počet obslužných rutin událostí, které jsou přidružené k aktuální **EventSource** objektu  
  
## <a name="syntax"></a>Syntaxe  
  
```  
size_t GetSize() const;  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Počet obslužných rutin událostí v [targets_ –](../windows/eventsource-targets-data-member.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** event.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [EventSource – třída](../windows/eventsource-class.md)