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
ms.openlocfilehash: bb9151e55d133e3e5d8bf10baeb8448101ad6ce0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371544"
---
# <a name="eventsource-class"></a>EventSource – třída

Představuje neagilní událost. `EventSource`členské funkce přidávají, odeberou a vyvolávají obslužné rutiny událostí. Pro agilní události použijte [AgileEventSource](agileeventsource-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template<typename TDelegateInterface>
class EventSource;
```

### <a name="parameters"></a>Parametry

*TDelegateInterface*<br/>
Rozhraní delegáta, který představuje obslužnou rutinu události.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

| Name (Název)                                     | Popis                                            |
| ---------------------------------------- | ------------------------------------------------------ |
| [EventSource::EventSource](#eventsource) | Inicializuje novou instanci třídy. `EventSource` |

### <a name="public-methods"></a>Veřejné metody

| Name (Název)                                 | Popis                                                                                                                                                      |
| ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [EventSource::Přidat](#add)             | Připojí obslužnou rutinu události reprezentovanou zadaným delegátovým rozhraním k sadě obslužných rutin událostí pro aktuální `EventSource` objekt.                     |
| [EventSource::GetSize](#getsize)     | Načte počet obslužných rutin `EventSource` událostí přidružených k aktuálnímu objektu.                                                                         |
| [EventSource::InvokeAll](#invokeall) | Zavolá každou obslužnou rutinu události přidruženou k aktuálnímu `EventSource` objektu pomocí zadaných typů argumentů a argumentů.                                      |
| [EventSource::Odebrat](#remove)       | Odstraní obslužnou rutinu události reprezentovanou zadaným tokenem registrace události ze sady obslužných rutin událostí přidružených k aktuálnímu `EventSource` objektu. |

### <a name="protected-data-members"></a>Členové chráněných dat

| Name (Název)                                                    | Popis                                                                                                                       |
| ------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| [EventSource::addRemoveLock_](#addremovelock)           | Synchronizuje přístup k [poli targets_](#targets) při přidávání, odebírání nebo vyvolání obslužných rutin událostí.                          |
| [EventSource::targets_](#targets)                       | Pole jedné nebo více obslužných rutin událostí.                                                                                           |
| [EventSource::targetsPointerLock_](#targetspointerlock) | Synchronizuje přístup k interním datovým členům i v době, kdy jsou obslužné rutiny událostí pro tento EventSource přidávány, odebírány nebo vyvolány. |

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`EventSource`

## <a name="requirements"></a>Požadavky

**Záhlaví:** event.h

**Obor názvů:** Microsoft::WRL

## <a name="eventsourceadd"></a><a name="add"></a>EventSource::Přidat

Připojí obslužnou rutinu události reprezentovanou zadaným delegátovým rozhraním k sadě obslužných rutin událostí pro aktuální `EventSource` objekt.

```cpp
HRESULT Add(
   _In_ TDelegateInterface* delegateInterface,
   _Out_ EventRegistrationToken* token
);
```

### <a name="parameters"></a>Parametry

*delegateInterface*<br/>
Rozhraní k objektu delegáta, který představuje obslužnou rutinu události.

*token*<br/>
Po dokončení této operace popisovač, který představuje událost. Použijte tento token jako parametr [remove()](#remove) metoda zahodit obslužnou rutinu události.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak HRESULT, který označuje chybu.

## <a name="eventsourceaddremovelock_"></a><a name="addremovelock"></a>EventSource::addRemoveLock_

Synchronizuje přístup k [poli targets_](#targets) při přidávání, odebírání nebo vyvolání obslužných rutin událostí.

```cpp
Wrappers::SRWLock addRemoveLock_;
```

## <a name="eventsourceeventsource"></a><a name="eventsource"></a>EventSource::EventSource

Inicializuje novou instanci třídy. `EventSource`

```cpp
EventSource();
```

## <a name="eventsourcegetsize"></a><a name="getsize"></a>EventSource::GetSize

Načte počet obslužných rutin `EventSource` událostí přidružených k aktuálnímu objektu.

```cpp
size_t GetSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet obslužných rutin událostí v [targets_](#targets).

## <a name="eventsourceinvokeall"></a><a name="invokeall"></a>EventSource::InvokeAll

Zavolá každou obslužnou rutinu události přidruženou k aktuálnímu `EventSource` objektu pomocí zadaných typů argumentů a argumentů.

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
Typ argumentu obslužné rutiny události nulté.

*T1*<br/>
Typ prvního argumentu obslužné rutiny události.

*T2*<br/>
Typ druhého argumentu obslužné rutiny události.

*T3*<br/>
Typ třetího argumentu obslužné rutiny události.

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
Zeroth argument obslužné rutiny události.

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
Sedmý argument obslužné rutiny události.

*arg8*<br/>
Osmý argument obslužné rutiny události.

*arg9*<br/>
Devátý argument obslužné rutiny události.

## <a name="eventsourceremove"></a><a name="remove"></a>EventSource::Odebrat

Odstraní obslužnou rutinu události reprezentovanou zadaným tokenem registrace události ze sady obslužných rutin událostí přidružených k aktuálnímu `EventSource` objektu.

```cpp
HRESULT Remove(
   EventRegistrationToken token
);
```

### <a name="parameters"></a>Parametry

*token*<br/>
Popisovač, který představuje obslužnou rutinu události. Tento token byl vrácen, když byla obslužná rutina události zaregistrována metodou [Add(.](#add)

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak HRESULT, který označuje chybu.

### <a name="remarks"></a>Poznámky

Další informace o `EventRegistrationToken` struktuře naleznete v tématu **Windows::Foundation::EventRegistrationToken Structure** v referenční dokumentaci **prostředí Windows Runtime.**

## <a name="eventsourcetargets_"></a><a name="targets"></a>EventSource::targets_

Pole jedné nebo více obslužných rutin událostí.

```cpp
ComPtr<Details::EventTargetArray> targets_;
```

### <a name="remarks"></a>Poznámky

Dojde-li k události reprezentované aktuálním `EventSource` objektem, jsou volány obslužné rutiny události.

## <a name="eventsourcetargetspointerlock_"></a><a name="targetspointerlock"></a>EventSource::targetsPointerLock_

Synchronizuje přístup k interním datovým členům i v době, kdy `EventSource` jsou obslužné rutiny událostí přidávány, odebírány nebo vyvolány.

```cpp
Wrappers::SRWLock targetsPointerLock_;
```
