---
title: Eventtargetarray – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray
- event/Microsoft::WRL::Details::EventTargetArray::AddTail
- event/Microsoft::WRL::Details::EventTargetArray::Begin
- event/Microsoft::WRL::Details::EventTargetArray::End
- event/Microsoft::WRL::Details::EventTargetArray::EventTargetArray
- event/Microsoft::WRL::Details::EventTargetArray::Length
- event/Microsoft::WRL::Details::EventTargetArray::~EventTargetArray
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::EventTargetArray class
- Microsoft::WRL::Details::EventTargetArray::AddTail method
- Microsoft::WRL::Details::EventTargetArray::Begin method
- Microsoft::WRL::Details::EventTargetArray::End method
- Microsoft::WRL::Details::EventTargetArray::EventTargetArray, constructor
- Microsoft::WRL::Details::EventTargetArray::Length method
- Microsoft::WRL::Details::EventTargetArray::~EventTargetArray, destructor
ms.assetid: e3cadb7c-2160-4cbb-a2f8-c28733d1e96d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 36fe16e59edbead54b01ed14dfc08699b526a03a
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48788535"
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

Obslužné rutiny událostí, které jsou přidružené [EventSource](../windows/eventsource-class.md) objektu jsou uloženy v chráněné `EventTargetArray` datový člen.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Název                                                           | Popis
-------------------------------------------------------------- | -----------------------------------------------------------
[Eventtargetarray::eventtargetarray –](#eventtargetarray)        | Inicializuje novou instanci třídy `EventTargetArray` třídy.
[EventTargetArray:: ~ eventtargetarray –](#tilde-eventtargetarray) | Zruší inicializaci aktuální `EventTargetArray` třídy.

### <a name="public-methods"></a>Veřejné metody

Název                                  | Popis
------------------------------------- | ---------------------------------------------------------------------------------------
[Eventtargetarray::addtail –](#addtail) | Obslužné rutiny zadané události připojí na konec vnitřní pole obslužných rutin událostí.
[Eventtargetarray::begin –](#begin)     | Získá adresu prvního prvku v poli interní obslužných rutin událostí.
[Eventtargetarray::end –](#end)         | Získá adresu poslední prvek v poli interní obslužných rutin událostí.
[Eventtargetarray::length –](#length)   | Získá aktuální počet prvků v poli interní obslužných rutin událostí.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`EventTargetArray`

## <a name="requirements"></a>Požadavky

**Záhlaví:** event.h

**Namespace:** Microsoft::WRL:: details –

## <a name="tilde-eventtargetarray"></a>EventTargetArray:: ~ eventtargetarray –

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
