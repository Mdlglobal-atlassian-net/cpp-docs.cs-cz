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
ms.openlocfilehash: 1350e51ff609a888b6a8ad6841be6856b68c7994
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865727"
---
# <a name="eventsource-class"></a>EventSource – třída

Představuje neagilní událost. `EventSource` členské funkce přidávají, odstraňují a vyvolávají obslužné rutiny událostí. Pro agilní události použijte [AgileEventSource](agileeventsource-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template<typename TDelegateInterface>
class EventSource;
```

### <a name="parameters"></a>Parametry

*TDelegateInterface*<br/>
Rozhraní k delegátovi, který představuje obslužnou rutinu události.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

| Název                                     | Popis                                            |
| ---------------------------------------- | ------------------------------------------------------ |
| [EventSource:: EventSource](#eventsource) | Inicializuje novou instanci třídy `EventSource`. |

### <a name="public-methods"></a>Veřejné metody

| Název                                 | Popis                                                                                                                                                      |
| ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [EventSource:: Add](#add)             | Připojí obslužnou rutinu události reprezentované zadaným rozhraním delegáta k sadě obslužných rutin událostí pro aktuální objekt `EventSource`.                     |
| [EventSource:: GetSize](#getsize)     | Načte počet obslužných rutin událostí přidružených k aktuálnímu objektu `EventSource`.                                                                         |
| [EventSource:: InvokeAll –](#invokeall) | Volá jednotlivé obslužné rutiny události přidružené k aktuálnímu objektu `EventSource` pomocí zadaných typů argumentů a argumentů.                                      |
| [EventSource:: Remove](#remove)       | Odstraní obslužnou rutinu události reprezentovanou zadaným registračním tokenem události ze sady obslužných rutin událostí přidružených k aktuálnímu objektu `EventSource`. |

### <a name="protected-data-members"></a>Chránění členové dat

| Název                                                    | Popis                                                                                                                       |
| ------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| [EventSource:: addRemoveLock_](#addremovelock)           | Při přidávání, odebírání nebo vyvolávání obslužných rutin událostí synchronizuje přístup k poli [targets_](#targets) .                          |
| [EventSource:: targets_](#targets)                       | Pole jedné nebo více obslužných rutin událostí.                                                                                           |
| [EventSource:: targetsPointerLock_](#targetspointerlock) | Synchronizuje přístup k interním datovým členům i v případě, že jsou obslužné rutiny událostí pro tento EventSource přidávány, odebrány nebo vyvolány. |

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`EventSource`

## <a name="requirements"></a>Požadavky

**Záhlaví:** Event. h

**Obor názvů:** Microsoft:: WRL

## <a name="add"></a>EventSource:: Add

Připojí obslužnou rutinu události reprezentované zadaným rozhraním delegáta k sadě obslužných rutin událostí pro aktuální objekt `EventSource`.

```cpp
HRESULT Add(
   _In_ TDelegateInterface* delegateInterface,
   _Out_ EventRegistrationToken* token
);
```

### <a name="parameters"></a>Parametry

*delegateInterface*<br/>
Rozhraní objektu delegáta, který představuje obslužnou rutinu události.

*klíčové*<br/>
Po dokončení této operace bude popisovač reprezentující událost. Tento token použijte jako parametr metody [Remove ()](#remove) pro zahození obslužné rutiny události.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě hodnota HRESULT, která označuje chybu.

## <a name="addremovelock"></a>EventSource:: addRemoveLock_

Při přidávání, odebírání nebo vyvolávání obslužných rutin událostí synchronizuje přístup k poli [targets_](#targets) .

```cpp
Wrappers::SRWLock addRemoveLock_;
```

## <a name="eventsource"></a>EventSource:: EventSource

Inicializuje novou instanci třídy `EventSource`.

```cpp
EventSource();
```

## <a name="getsize"></a>EventSource:: GetSize

Načte počet obslužných rutin událostí přidružených k aktuálnímu objektu `EventSource`.

```cpp
size_t GetSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet obslužných rutin událostí v [targets_](#targets).

## <a name="invokeall"></a>EventSource:: InvokeAll –

Volá jednotlivé obslužné rutiny události přidružené k aktuálnímu objektu `EventSource` pomocí zadaných typů argumentů a argumentů.

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
Typ argumentu obslužné rutiny události zeroth

*Lince*<br/>
Typ prvního argumentu obslužné rutiny události.

*T2*<br/>
Typ druhého argumentu obslužné rutiny události

*Typu*<br/>
Typ třetího argumentu obslužné rutiny události.

*T4*<br/>
Typ čtvrtého argumentu obslužné rutiny události

*Výtisk*<br/>
Typ pátého argumentu obslužné rutiny události

*T6*<br/>
Typ šestého argumentu obslužné rutiny události

*T7*<br/>
Typ argumentu sedmé obslužné rutiny události.

*T8*<br/>
Typ osmého argumentu obslužné rutiny události

*T9*<br/>
Typ argumentu pro devátou obslužnou rutinu události

*arg0*<br/>
Argument obslužné rutiny události zeroth

*arg1*<br/>
První argument obslužné rutiny události

*arg2*<br/>
Druhý argument obslužné rutiny události.

*arg3*<br/>
Třetí argument obslužné rutiny události.

*arg4*<br/>
Čtvrtý argument obslužné rutiny události

*arg5*<br/>
Pátý argument obslužné rutiny události

*arg6*<br/>
Šestý argument obslužné rutiny události

*arg7*<br/>
Sedmý argument obslužné rutiny události

*arg8*<br/>
Osmá argument obslužné rutiny události

*arg9*<br/>
Devátý argument obslužné rutiny události

## <a name="remove"></a>EventSource:: Remove

Odstraní obslužnou rutinu události reprezentovanou zadaným registračním tokenem události ze sady obslužných rutin událostí přidružených k aktuálnímu objektu `EventSource`.

```cpp
HRESULT Remove(
   EventRegistrationToken token
);
```

### <a name="parameters"></a>Parametry

*klíčové*<br/>
Popisovač, který představuje obslužnou rutinu události. Tento token byl vrácen, když byla obslužná rutina události registrována metodou [Add ()](#add) .

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě hodnota HRESULT, která označuje chybu.

### <a name="remarks"></a>Poznámky

Další informace o `EventRegistrationToken` struktuře naleznete v tématu **Struktura Windows:: Foundation:: EventRegistrationToken** v referenční dokumentaci **prostředí Windows Runtime** .

## <a name="targets"></a>EventSource:: targets_

Pole jedné nebo více obslužných rutin událostí.

```cpp
ComPtr<Details::EventTargetArray> targets_;
```

### <a name="remarks"></a>Poznámky

Když dojde k události reprezentované aktuálním `EventSource`m objektem, jsou volány obslužné rutiny událostí.

## <a name="targetspointerlock"></a>EventSource:: targetsPointerLock_

Synchronizuje přístup k interním datovým členům i v případě, že jsou obslužné rutiny událostí pro tento `EventSource` přidávány, odebírány nebo vyvolány.

```cpp
Wrappers::SRWLock targetsPointerLock_;
```
