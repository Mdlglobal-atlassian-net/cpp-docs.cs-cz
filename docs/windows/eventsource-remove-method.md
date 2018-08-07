---
title: EventSource::Remove – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource::Remove
dev_langs:
- C++
helpviewer_keywords:
- Remove method
ms.assetid: afafedf5-3665-4408-a639-fb6884f7c5f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9dd026158a2bbc76e7a3e195bc5346f65821f2b7
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2018
ms.locfileid: "39569492"
---
# <a name="eventsourceremove-method"></a>EventSource::Remove – metoda
Odstraní obslužná rutina události reprezentována zadanou událost registračního tokenu ze sady obslužné rutiny událostí, které jsou přidružené k aktuální **EventSource** objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Remove(  
   EventRegistrationToken token  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *Token*  
 Popisovač, který představuje obslužnou rutinu události. Tento token byl vrácen při registraci obslužné rutiny události byl [Add()](../windows/eventsource-add-method.md) metody.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu.  
  
## <a name="remarks"></a>Poznámky  
 Další informace o struktuře EventRegistrationToken, najdete v článku `Windows::Foundation::EventRegistrationToken` struktura tématu v referenční dokumentaci modulu Windows Runtime.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** event.h  
  
 **Namespace:** Microsoft::WRL
 
 ## <a name="see-also"></a>Viz také
 [EventSource – třída](../windows/eventsource-class.md)