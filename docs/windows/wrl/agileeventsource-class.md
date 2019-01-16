---
title: Agileeventsource – třída
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::AgileEventSource
- event/Microsoft::WRL::InvokeModeOptions
helpviewer_keywords:
- AgileEventSource class
ms.openlocfilehash: a18b4fd7873bcc0895354186dc9b0cc7e6b71bd4
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334714"
---
# <a name="agileeventsource-class"></a>Agileeventsource – třída

Představuje událost, která je vyvolána agilní komponentu, která je komponenta, která je přístupná z libovolného vlákna. Dědí z [EventSource](eventsource-class.md) a přepíše `Add` členskou funkci s parametrem další typu pro zadání možností pro vyvolání události agile.

## <a name="syntax"></a>Syntaxe

```cpp
template<
    typename TDelegateInterface,
    typename TEventSourceOptions = Microsoft::WRL::InvokeModeOptions<FireAll>
>
class AgileEventSource :
    public Microsoft::WRL::EventSource<
        TDelegateInterface, TEventSourceOptions>;
```

## <a name="parameters"></a>Parametry

*TDelegateInterface*<br/>
Rozhraní pro delegáta, který představuje obslužnou rutinu události.

*TEventSourceOptions*<br/>
[Invokemodeoptions –](invokemodeoptions-structure.md) stucture jehož invokeMode je nastaveno na `InvokeMode::StopOnFirstError` nebo `InvokeMode::FireAll`.

## <a name="remarks"></a>Poznámky

Většinu komponent v prostředí Windows Runtime jsou agilní komponenty. Další informace najdete v tématu [vláken a zařazování (C + +/ CX)](../../cppcx/threading-and-marshaling-c-cx.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`EventSource`

`AgileEventSource`

## <a name="requirements"></a>Požadavky

**Záhlaví:** event.h

**Namespace:** Microsoft::WRL

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[AgileEventSource::Add – metoda](#add)|Připojí obslužnou rutinu události agilní reprezentována rozhraní zadaného delegáta k sadě obslužné rutiny událostí pro aktuální **agileeventsource –** objektu.|

## <a name="add"></a> AgileEventSource::Add – metoda

Připojí obslužnou rutinu události reprezentována rozhraní zadaného delegáta k sadě obslužné rutiny událostí pro aktuální [EventSource](eventsource-class.md) objektu.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Add(
   _In_ TDelegateInterface* delegateInterface,
   _Out_ EventRegistrationToken* token
);
```

### <a name="parameters"></a>Parametry

*delegateInterface*<br/>
Rozhraní pro objekt delegáta, který představuje obslužnou rutinu události.

*token*<br/>
Po dokončení této operace, popisovač, který představuje událost. Používat tento token parametru `Remove()` metoda zahodíte obslužné rutiny události.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu.

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](microsoft-wrl-namespace.md)