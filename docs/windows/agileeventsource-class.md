---
title: Třída AgileEventSource | Microsoft Docs
ms.custom: ''
ms.date: 03/22/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::AgileEventSource
- event/Microsoft::WRL::InvokeModeOptions
dev_langs:
- C++
helpviewer_keywords:
- AgileEventSource class
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7d025fc2be86fb5b59107d1deee39962c3c6db04
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="agileeventsource-class"></a>AgileEventSource – třída
Představuje agilní událost. Dědí z [EventSource](eventsource-class.md) a přepíše `Add` – členská funkce s parametrem další typ pro zadání možností, jak má být vyvolán agilní událostí.
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename TDelegateInterface, typename TEventSourceOptions = Microsoft::WRL::InvokeModeOptions<FireAll>>
class AgileEventSource
    : public Microsoft::WRL::EventSource<TDelegateInterface, TEventSourceOptions>;
```  
  
#### <a name="parameters"></a>Parametry  
 `TDelegateInterface`  
 Rozhraní pro delegáta, který představuje obslužnou rutinu události.

 `TEventSourceOptions` [InvokeModeOptions](invokemodeoptions-structure.md) stucture, jejichž invokeMode je nastaveno na `InvokeMode::StopOnFirstError` nebo `InvokeMode::FireAll`.

## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[AgileEventSource::Add – metoda](#add)|Obslužné rutiny události agilní reprezentována rozhraní zadaného delegáta sadu obslužných rutin událostí pro aktuální objekt AgileEventSource připojí.|  

## <a name="add"></a> AgileEventSource::Add – metoda

Připojí reprezentována rozhraní zadaného delegáta sadu obslužných rutin událostí pro aktuální objekt EventSource obslužné rutiny události.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Add(  
   _In_ TDelegateInterface* delegateInterface,  
   _Out_ EventRegistrationToken* token  
);
```

### <a name="parameters"></a>Parametry

*delegateInterface*

Rozhraní objektu delegáta, který reprezentuje obslužnou rutinu události.

*token* po této operaci dokončení popisovač, který představuje událost. Použijte tento token jako parametr metody Remove() k odstranění obslužné rutiny události.

### <a name="return-value"></a>Návratová hodnota
S_OK v případě úspěšného; jinak hodnota HRESULT určující chyba.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `EventSource`  
 `AgileEventSource`
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** event.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)