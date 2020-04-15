---
title: Třída událostí (WRL)
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
ms.openlocfilehash: 85b4c2d1f1a27e90a65e47aa749e079f4aa08739
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371526"
---
# <a name="event-class-wrl"></a>Třída událostí (WRL)

Představuje událost.

## <a name="syntax"></a>Syntaxe

```cpp
class Event : public HandleT<HandleTraits::EventTraits>;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Name (Název)                   | Popis
---------------------- | ------------------------------------------------
[Událost::Událost](#event) | Inicializuje novou instanci třídy. `Event`

### <a name="public-operators"></a>Veřejné operátory

Name (Název)                                 | Popis
------------------------------------ | ------------------------------------------------------------------------
[Událost::operátor=](#operator-assign) | Přiřadí zadaný `Event` odkaz `Event` aktuální instanci.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`HandleT`

`Event`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Obor názvů:** Microsoft::WRL::Obálky

## <a name="eventevent"></a><a name="event"></a>Událost::Událost

Inicializuje novou instanci třídy. `Event`

```cpp
explicit Event(
   HANDLE h = HandleT::Traits::GetInvalidValue()
);
WRL_NOTHROW Event(
   _Inout_ Event&& h
);
```

### <a name="parameters"></a>Parametry

*H*<br/>
Zpracování události. Ve výchozím *h* nastavení je `nullptr`h inicializováno na .

## <a name="eventoperator"></a><a name="operator-assign"></a>Událost::operátor=

Přiřadí zadaný `Event` odkaz `Event` aktuální instanci.

```cpp
WRL_NOTHROW Event& operator=(
   _Inout_ Event&& h
);
```

### <a name="parameters"></a>Parametry

*H*<br/>
Rvalue-odkaz na `Event` instanci.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na aktuální `Event` instanci.
