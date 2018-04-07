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
ms.openlocfilehash: c5157fb37dcb0e8388c91b86b65948db79365060
ms.sourcegitcommit: d9ee6f777974d031570f4260c9581ea2c81ad875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2018
---
# <a name="agileeventsource-class"></a>AgileEventSource – třída

Představuje událost, která se vyvolá, což je součást, která je přístupná z libovolného vlákna agilní komponentou. Dědí z [EventSource](eventsource-class.md) a přepíše `Add` – členská funkce s parametrem další typ pro zadání možností, jak má být vyvolán agilní událostí.

## <a name="syntax"></a>Syntaxe

```
template<typename TDelegateInterface, typename TEventSourceOptions = Microsoft::WRL::InvokeModeOptions<FireAll>>
class AgileEventSource
    : public Microsoft::WRL::EventSource<TDelegateInterface, TEventSourceOptions>;
```

## <a name="parameters"></a>Parametry  
 `TDelegateInterface`  

 Rozhraní pro delegáta, který představuje obslužnou rutinu události.

 `TEventSourceOptions`  
 [InvokeModeOptions](invokemodeoptions-structure.md) stucture, jejichž invokeMode je nastaveno na `InvokeMode::StopOnFirstError` nebo `InvokeMode::FireAll`.

## <a name="remarks"></a>Poznámky

Valná většina součásti v prostředí Windows Runtime jsou agilní součásti. Další informace najdete v tématu [dělení na vlákna a zařazování (C + +/ CX)](../cppcx/threading-and-marshaling-c-cx.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

 `EventSource``AgileEventSource`

## <a name="requirements"></a>Požadavky

 **Záhlaví:** event.h

 **Namespace:** Microsoft::WRL

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[AgileEventSource::Add – metoda](#add)|Obslužné rutiny události agilní reprezentována rozhraní zadaného delegáta sadu obslužných rutin událostí pro aktuální objekt AgileEventSource připojí.|

## <a name="add"></a> AgileEventSource::Add – metoda

Připojí obslužné rutiny události reprezentována rozhraní zadaného delegáta sadu obslužných rutin událostí pro aktuální [EventSource](eventsource-class.md) objektu.

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


## <a name="see-also"></a>Viz také

 [Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)
