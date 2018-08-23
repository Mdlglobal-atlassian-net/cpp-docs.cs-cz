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
ms.openlocfilehash: 00f3275095648a41eb25d10bac1f34637b2ac242
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604569"
---
# <a name="eventsourceremove-method"></a>EventSource::Remove – metoda

Odstraní obslužná rutina události reprezentována zadanou událost registračního tokenu ze sady obslužné rutiny událostí, které jsou přidružené k aktuální **EventSource** objektu.

## <a name="syntax"></a>Syntaxe

```cpp
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

Další informace o `EventRegistrationToken` struktury, přečtěte si téma **Windows::Foundation:: struktura** téma v **modulu Windows Runtime** referenční dokumentaci.

## <a name="requirements"></a>Požadavky

**Záhlaví:** event.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také
[EventSource – třída](../windows/eventsource-class.md)