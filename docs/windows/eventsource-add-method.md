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
ms.openlocfilehash: 65e8576f069cce7d7aec2eae18ad577820ca93a4
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644739"
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