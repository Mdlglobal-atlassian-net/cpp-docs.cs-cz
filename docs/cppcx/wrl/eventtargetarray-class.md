---
title: EventTargetArray – třída
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray
- event/Microsoft::WRL::Details::EventTargetArray::AddTail
- event/Microsoft::WRL::Details::EventTargetArray::Begin
- event/Microsoft::WRL::Details::EventTargetArray::End
- event/Microsoft::WRL::Details::EventTargetArray::EventTargetArray
- event/Microsoft::WRL::Details::EventTargetArray::Length
- event/Microsoft::WRL::Details::EventTargetArray::~EventTargetArray
helpviewer_keywords:
- Microsoft::WRL::Details::EventTargetArray class
- Microsoft::WRL::Details::EventTargetArray::AddTail method
- Microsoft::WRL::Details::EventTargetArray::Begin method
- Microsoft::WRL::Details::EventTargetArray::End method
- Microsoft::WRL::Details::EventTargetArray::EventTargetArray, constructor
- Microsoft::WRL::Details::EventTargetArray::Length method
- Microsoft::WRL::Details::EventTargetArray::~EventTargetArray, destructor
ms.assetid: e3cadb7c-2160-4cbb-a2f8-c28733d1e96d
ms.openlocfilehash: 1f3f8e299dba1f4b6ae5a5767f11989dc2fe8370
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58786557"
---
# <a name="eventtargetarray-class"></a>EventTargetArray – třída

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
class EventTargetArray :
    public Microsoft::WRL::RuntimeClass<
        Microsoft::WRL::RuntimeClassFlags<ClassicCom>,
        IUnknown
    >;
```

## <a name="remarks"></a>Poznámky

Reprezentuje pole prvků obslužných rutin událostí.

Obslužné rutiny událostí, které jsou přidružené [EventSource](eventsource-class.md) objektu jsou uloženy v chráněné `EventTargetArray` datový člen.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Name                                                           | Popis
-------------------------------------------------------------- | -----------------------------------------------------------
[Eventtargetarray::eventtargetarray –](#eventtargetarray)        | Inicializuje novou instanci třídy `EventTargetArray` třídy.
[EventTargetArray::~EventTargetArray](#tilde-eventtargetarray) | Zruší inicializaci aktuální `EventTargetArray` třídy.

### <a name="public-methods"></a>Veřejné metody

Název                                  | Popis
------------------------------------- | ---------------------------------------------------------------------------------------
[Eventtargetarray::addtail –](#addtail) | Obslužné rutiny zadané události připojí na konec vnitřní pole obslužných rutin událostí.
[EventTargetArray::Begin](#begin)     | Získá adresu prvního prvku v poli interní obslužných rutin událostí.
[Eventtargetarray::end –](#end)         | Získá adresu poslední prvek v poli interní obslužných rutin událostí.
[Eventtargetarray::length –](#length)   | Získá aktuální počet prvků v poli interní obslužných rutin událostí.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`EventTargetArray`

## <a name="requirements"></a>Požadavky

**Záhlaví:** event.h

**Namespace:** Microsoft::WRL::Details

## <a name="tilde-eventtargetarray"></a>EventTargetArray::~EventTargetArray

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
~EventTargetArray();
```

### <a name="remarks"></a>Poznámky

Zruší inicializaci aktuální `EventTargetArray` třídy.

## <a name="addtail"></a>Eventtargetarray::addtail –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
void AddTail(
   _In_ IUnknown* element
);
```

### <a name="parameters"></a>Parametry

*– Element*<br/>
Ukazatel na obslužnou rutinu události pro připojení.

### <a name="remarks"></a>Poznámky

Obslužné rutiny zadané události připojí na konec vnitřní pole obslužných rutin událostí.

`AddTail()` je určena pro použití interně pomocí pouze `EventSource` třídy.

## <a name="begin"></a>Eventtargetarray::begin –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
ComPtr<IUnknown>* Begin();
```

### <a name="return-value"></a>Návratová hodnota

Adresa první prvek v poli interní obslužných rutin událostí.

### <a name="remarks"></a>Poznámky

Získá adresu prvního prvku v poli interní obslužných rutin událostí.

## <a name="end"></a>Eventtargetarray::end –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
ComPtr<IUnknown>* End();
```

### <a name="return-value"></a>Návratová hodnota

Adresa poslední prvek v poli interní obslužných rutin událostí.

### <a name="remarks"></a>Poznámky

Získá adresu poslední prvek v poli interní obslužných rutin událostí.

## <a name="eventtargetarray"></a>Eventtargetarray::eventtargetarray –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
EventTargetArray(
   _Out_ HRESULT* hr,
   size_t items
);
```

### <a name="parameters"></a>Parametry

*hr*<br/>
Po operacích tento konstruktor parametr *hr* označuje, zda přidělení pole bylo úspěšné nebo neúspěšné. V následující seznamu jsou uvedeny možné hodnoty pro *hr*.

+   S_OK<br/>
    Operace byla úspěšná.

+   E_OUTOFMEMORY<br/>
    Nepodařilo se přidělit paměť pro pole.

+   S_FALSE<br/>
    Parametr *položky* je menší než nebo rovna nule.

*Položky*<br/>
Počet prvků pole pro přidělení.

### <a name="remarks"></a>Poznámky

Inicializuje novou instanci třídy `EventTargetArray` třídy.

`EventTargetArray` Umožňuje ponechat pole obslužné rutiny událostí v `EventSource` objektu.

## <a name="length"></a>Eventtargetarray::length –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
size_t Length();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální počet prvků v poli interní obslužných rutin událostí.

### <a name="remarks"></a>Poznámky

Získá aktuální počet prvků v poli interní obslužných rutin událostí.
