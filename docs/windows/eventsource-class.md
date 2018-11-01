---
title: EventSource – třída
ms.date: 09/12/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource
- event/Microsoft::WRL::EventSource::Add
- event/Microsoft::WRL::EventSource::addRemoveLock_
- event/Microsoft::WRL::EventSource::EventSource
- event/Microsoft::WRL::EventSource::GetSize
- event/Microsoft::WRL::EventSource::InvokeAll
- event/Microsoft::WRL::EventSource::Remove
- event/Microsoft::WRL::EventSource::targets_
- event/Microsoft::WRL::EventSource::targetsPointerLock_
helpviewer_keywords:
- Microsoft::WRL::EventSource class
- Microsoft::WRL::EventSource::Add method
- Microsoft::WRL::EventSource::addRemoveLock_ data member
- Microsoft::WRL::EventSource::EventSource, constructor
- Microsoft::WRL::EventSource::GetSize method
- Microsoft::WRL::EventSource::InvokeAll method
- Microsoft::WRL::EventSource::Remove method
- Microsoft::WRL::EventSource::targets_ data member
- Microsoft::WRL::EventSource::targetsPointerLock_ data member
ms.assetid: 91f1c072-6af4-44e6-b6d8-ac6d0c688dde
ms.openlocfilehash: e9070fe756410e3e1bb1e5840eb3f06e29c2f46b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50561275"
---
# <a name="eventsource-class"></a>EventSource – třída

Představuje událost agile. `EventSource` Členské funkce přidání, odebrání a vyvolání obslužných rutin událostí. Agilní události, použijte [agileeventsource –](agileeventsource-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template<typename TDelegateInterface>
class EventSource;
```

### <a name="parameters"></a>Parametry

*TDelegateInterface*<br/>
Rozhraní pro delegáta, který představuje obslužnou rutinu události.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

| Název                                     | Popis                                            |
| ---------------------------------------- | ------------------------------------------------------ |
| [EventSource::EventSource –](#eventsource) | Inicializuje novou instanci třídy `EventSource` třídy. |

### <a name="public-methods"></a>Veřejné metody

| Název                                 | Popis                                                                                                                                                      |
| ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [EventSource::add –](#add)             | Připojí obslužnou rutinu události reprezentována rozhraní zadaného delegáta k sadě obslužné rutiny událostí pro aktuální `EventSource` objektu.                     |
| [EventSource::getsize –](#getsize)     | Získá počet obslužných rutin událostí, které jsou přidružené k aktuální `EventSource` objektu.                                                                         |
| [EventSource::invokeall –](#invokeall) | Volá Každá obslužná rutina události spojené s aktuálním `EventSource` pomocí zadanými typy argumentu a argumenty.                                      |
| [EventSource::Remove –](#remove)       | Odstraní obslužná rutina události reprezentována zadanou událost registračního tokenu ze sady obslužné rutiny událostí, které jsou přidružené k aktuální `EventSource` objektu. |

### <a name="protected-data-members"></a>Chránění členové dat

| Název                                                    | Popis                                                                                                                       |
| ------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| [EventSource::addremovelock_ –](#addremovelock)           | Synchronizuje přístup k [targets_ –](#targets) pole při přidání, odebrání nebo volání obslužné rutiny událostí.                          |
| [EventSource::targets_ –](#targets)                       | Pole jednoho nebo více obslužných rutin událostí.                                                                                           |
| [EventSource::targetspointerlock_ –](#targetspointerlock) | Synchronizuje přístup k interní datových členů, dokonce i za běhu obslužné rutiny událostí pro EventSource se neustále přidávají, odebrat nebo vyvolána. |

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`EventSource`

## <a name="requirements"></a>Požadavky

**Záhlaví:** event.h

**Namespace:** Microsoft::WRL

## <a name="add"></a>EventSource::add –

Připojí obslužnou rutinu události reprezentována rozhraní zadaného delegáta k sadě obslužné rutiny událostí pro aktuální `EventSource` objektu.

```cpp
HRESULT Add(
   _In_ TDelegateInterface* delegateInterface,
   _Out_ EventRegistrationToken* token
);
```

### <a name="parameters"></a>Parametry

*delegateInterface*<br/>
Rozhraní pro objekt delegáta, který představuje obslužnou rutinu události.

*Token*<br/>
Po dokončení této operace, popisovač, který představuje událost. Používat tento token parametru [Remove()](#remove) metoda zahodíte obslužné rutiny události.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu.

## <a name="addremovelock"></a>EventSource::addremovelock_ –

Synchronizuje přístup k [targets_ –](#targets) pole při přidání, odebrání nebo volání obslužné rutiny událostí.

```cpp
Wrappers::SRWLock addRemoveLock_;
```

## <a name="eventsource"></a>EventSource::EventSource –

Inicializuje novou instanci třídy `EventSource` třídy.

```cpp
EventSource();
```

## <a name="getsize"></a>EventSource::getsize –

Získá počet obslužných rutin událostí, které jsou přidružené k aktuální `EventSource` objektu.

```cpp
size_t GetSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet obslužných rutin událostí v [targets_ –](#targets).

## <a name="invokeall"></a>EventSource::invokeall –

Volá Každá obslužná rutina události spojené s aktuálním `EventSource` pomocí zadanými typy argumentu a argumenty.

```cpp
void InvokeAll();
template <
   typename T0
>
void InvokeAll(
   T0arg0
);
template <
   typename T0,
   typename T1
>
void InvokeAll(
   T0arg0,
   T1arg1
);
template <
   typename T0,
   typename T1,
   typename T2
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6,
   typename T7
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6,
   T7arg7
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6,
   typename T7,
   typename T8
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6,
   T7arg7,
   T8arg8
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6,
   typename T7,
   typename T8,
   typename T9
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6,
   T7arg7,
   T8arg8,
   T9arg9
);
```

### <a name="parameters"></a>Parametry

*T0*<br/>
Typ argumentu ID nultého obslužné rutiny události.

*T1*<br/>
Typ prvního argumentu obslužné rutiny události.

*T2*<br/>
Typ druhého argumentu obslužné rutiny události.

*T3*<br/>
Typ třetí argument obslužné rutiny události.

*T4*<br/>
Typ čtvrtého argumentu obslužné rutiny události.

*T5*<br/>
Typ pátého argumentu obslužné rutiny události.

*T6*<br/>
Typ šestého argumentu obslužné rutiny události.

*T7*<br/>
Typ sedmého argumentu obslužné rutiny události.

*T8*<br/>
Typ osmého argumentu obslužné rutiny události.

*T9*<br/>
Typ devátého argumentu obslužné rutiny události.

*arg0*<br/>
Argument obslužné rutiny události ID nultého.

*arg1*<br/>
První argument obslužné rutiny události.

*arg2*<br/>
Druhý argument obslužné rutiny události.

*arg3*<br/>
Třetí argument obslužné rutiny události.

*arg4*<br/>
Čtvrtý argument obslužné rutiny události.

*arg5*<br/>
Pátý argument obslužné rutiny události.

*arg6*<br/>
Šestý argument obslužné rutiny události.

*arg7*<br/>
Sedmého argumentu obslužné rutiny události.

*arg8*<br/>
Argument obslužné rutiny události osmého.

*arg9*<br/>
Devátého argumentu obslužné rutiny události.

## <a name="remove"></a>EventSource::Remove –

Odstraní obslužná rutina události reprezentována zadanou událost registračního tokenu ze sady obslužné rutiny událostí, které jsou přidružené k aktuální `EventSource` objektu.

```cpp
HRESULT Remove(
   EventRegistrationToken token
);
```

### <a name="parameters"></a>Parametry

*Token*<br/>
Popisovač, který představuje obslužnou rutinu události. Tento token byl vrácen při registraci obslužné rutiny události byl [Add()](#add) metody.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu.

### <a name="remarks"></a>Poznámky

Další informace o `EventRegistrationToken` struktury, přečtěte si téma **Windows::Foundation:: struktura** téma v **modulu Windows Runtime** referenční dokumentaci.

## <a name="targets"></a>EventSource::targets_ –

Pole jednoho nebo více obslužných rutin událostí.

```cpp
ComPtr<Details::EventTargetArray> targets_;
```

### <a name="remarks"></a>Poznámky

Pokud událost, která je reprezentována aktuální `EventSource` dochází k objektu, jsou volány obslužné rutiny události.

## <a name="targetspointerlock"></a>EventSource::targetspointerlock_ –

Synchronizuje přístup k interní datové členy i v průběhu obslužné rutiny události pro tento `EventSource` se neustále přidávají, odstraněné nebo vyvolaný.

```cpp
Wrappers::SRWLock targetsPointerLock_;
```
