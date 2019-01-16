---
title: Event – třída (WRL)
ms.date: 09/24/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Event
- corewrappers/Microsoft::WRL::Wrappers::Event::Event
- corewrappers/Microsoft::WRL::Wrappers::Event::operator=
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Event class
- Microsoft::WRL::Wrappers::Event::Event, constructor
- Microsoft::WRL::Wrappers::Event::operator= operator
ms.assetid: 55dfc9fc-62d4-4bb2-9d85-5b6dd88569e8
ms.openlocfilehash: 2d36b4fa3d1824f43e0cfafe55c439a6bdeccb6f
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334921"
---
# <a name="event-class-wrl"></a>Event – třída (WRL)

Představuje událost.

## <a name="syntax"></a>Syntaxe

```cpp
class Event : public HandleT<HandleTraits::EventTraits>;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Název                   | Popis
---------------------- | ------------------------------------------------
[Event::Event](#event) | Inicializuje novou instanci třídy `Event` třídy.

### <a name="public-operators"></a>Veřejné operátory

Název                                 | Popis
------------------------------------ | ------------------------------------------------------------------------
[Event::Operator =](#operator-assign) | Přiřadí zadaný `Event` odkaz na aktuální `Event` instance.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`HandleT`

`Event`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="event"></a>Event::Event

Inicializuje novou instanci třídy `Event` třídy.

```cpp
explicit Event(
   HANDLE h = HandleT::Traits::GetInvalidValue()
);
WRL_NOTHROW Event(
   _Inout_ Event&& h
);
```

### <a name="parameters"></a>Parametry

*h*<br/>
Zpracování události. Ve výchozím nastavení *h* je inicializován na `nullptr`.

## <a name="operator-assign"></a>Event::Operator =

Přiřadí zadaný `Event` odkaz na aktuální `Event` instance.

```cpp
WRL_NOTHROW Event& operator=(
   _Inout_ Event&& h
);
```

### <a name="parameters"></a>Parametry

*h*<br/>
Odkaz rvalue na `Event` instance.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na aktuální `Event` instance.
