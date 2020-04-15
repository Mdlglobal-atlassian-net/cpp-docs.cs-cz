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
ms.openlocfilehash: 9ea8800aa22a6b5cae0b3342cf337786fb53fc76
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371481"
---
# <a name="eventtargetarray-class"></a>EventTargetArray – třída

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

## <a name="syntax"></a>Syntaxe

```cpp
class EventTargetArray :
    public Microsoft::WRL::RuntimeClass<
        Microsoft::WRL::RuntimeClassFlags<ClassicCom>,
        IUnknown
    >;
```

## <a name="remarks"></a>Poznámky

Představuje pole obslužné rutiny událostí.

Obslužné rutiny událostí, které jsou přidruženy k objektu [EventSource,](eventsource-class.md) jsou uloženy v chráněném `EventTargetArray` datovém členu.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Name (Název)                                                           | Popis
-------------------------------------------------------------- | -----------------------------------------------------------
[EventTargetArray::EventTargetArray](#eventtargetarray)        | Inicializuje novou instanci třídy. `EventTargetArray`
[EventTargetArray::~EventTargetArray](#tilde-eventtargetarray) | Deinitializes aktuální `EventTargetArray` třídy.

### <a name="public-methods"></a>Veřejné metody

Name (Název)                                  | Popis
------------------------------------- | ---------------------------------------------------------------------------------------
[EventTargetArray::AddTail](#addtail) | Připojí zadanou obslužnou rutinu události na konec interního pole obslužných rutin událostí.
[EventTargetArray::Begin](#begin)     | Získá adresu prvního prvku v interní matné pole obslužné rutiny událostí.
[EventTargetArray::Konec](#end)         | Získá adresu poslední prvek v interní pole obslužné rutiny událostí.
[EventTargetArray::Délka](#length)   | Získá aktuální počet prvků v interní matné pole obslužné rutiny událostí.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`EventTargetArray`

## <a name="requirements"></a>Požadavky

**Záhlaví:** event.h

**Obor názvů:** Microsoft::WRL::Details

## <a name="eventtargetarrayeventtargetarray"></a><a name="tilde-eventtargetarray"></a>EventTargetArray::~EventTargetArray

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
~EventTargetArray();
```

### <a name="remarks"></a>Poznámky

Deinitializes aktuální `EventTargetArray` třídy.

## <a name="eventtargetarrayaddtail"></a><a name="addtail"></a>EventTargetArray::AddTail

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
void AddTail(
   _In_ IUnknown* element
);
```

### <a name="parameters"></a>Parametry

*Prvek*<br/>
Ukazatel na obslužnou rutinu události připojit.

### <a name="remarks"></a>Poznámky

Připojí zadanou obslužnou rutinu události na konec interního pole obslužných rutin událostí.

`AddTail()`je určen k internímu použití `EventSource` pouze třídou.

## <a name="eventtargetarraybegin"></a><a name="begin"></a>EventTargetArray::Begin

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
ComPtr<IUnknown>* Begin();
```

### <a name="return-value"></a>Návratová hodnota

Adresa prvního prvku v interním poli obslužných rutin událostí.

### <a name="remarks"></a>Poznámky

Získá adresu prvního prvku v interní matné pole obslužné rutiny událostí.

## <a name="eventtargetarrayend"></a><a name="end"></a>EventTargetArray::Konec

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
ComPtr<IUnknown>* End();
```

### <a name="return-value"></a>Návratová hodnota

Adresa posledního prvku v interním poli obslužných rutin událostí.

### <a name="remarks"></a>Poznámky

Získá adresu poslední prvek v interní pole obslužné rutiny událostí.

## <a name="eventtargetarrayeventtargetarray"></a><a name="eventtargetarray"></a>EventTargetArray::EventTargetArray

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
EventTargetArray(
   _Out_ HRESULT* hr,
   size_t items
);
```

### <a name="parameters"></a>Parametry

*Hr*<br/>
Po operacích tohoto konstruktoru parametr *hr* označuje, zda bylo přidělení pole úspěšné nebo neúspěšné. V následujícím seznamu jsou uvedeny možné hodnoty pro *hr*.

- S_OK<br/>
  Operace byla úspěšná.

- E_OUTOFMEMORY<br/>
  Pro pole nelze přidělit paměť.

- S_FALSE<br/>
  *Parametr položky* je menší nebo rovna nule.

*Položky*<br/>
Počet prvků pole, které chcete přidělit.

### <a name="remarks"></a>Poznámky

Inicializuje novou instanci třídy. `EventTargetArray`

`EventTargetArray`se používá k uchování pole `EventSource` obslužných rutin událostí v objektu.

## <a name="eventtargetarraylength"></a><a name="length"></a>EventTargetArray::Délka

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
size_t Length();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální počet prvků v interním poli obslužných rutin událostí.

### <a name="remarks"></a>Poznámky

Získá aktuální počet prvků v interní matné pole obslužné rutiny událostí.
