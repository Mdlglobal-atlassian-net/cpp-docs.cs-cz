---
title: HandleT – třída
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Attach
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Close
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Detach
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Get
- corewrappers/Microsoft::WRL::Wrappers::HandleT::handle_
- corewrappers/Microsoft::WRL::Wrappers::HandleT::HandleT
- corewrappers/Microsoft::WRL::Wrappers::HandleT::InternalClose
- corewrappers/Microsoft::WRL::Wrappers::HandleT::IsValid
- corewrappers/Microsoft::WRL::Wrappers::HandleT::operator=
- corewrappers/Microsoft::WRL::Wrappers::HandleT::~HandleT
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleT class
- Microsoft::WRL::Wrappers::HandleT::Attach method
- Microsoft::WRL::Wrappers::HandleT::Close method
- Microsoft::WRL::Wrappers::HandleT::Detach method
- Microsoft::WRL::Wrappers::HandleT::Get method
- Microsoft::WRL::Wrappers::HandleT::handle_ data member
- Microsoft::WRL::Wrappers::HandleT::HandleT, constructor
- Microsoft::WRL::Wrappers::HandleT::InternalClose method
- Microsoft::WRL::Wrappers::HandleT::IsValid method
- Microsoft::WRL::Wrappers::HandleT::operator= operator
- Microsoft::WRL::Wrappers::HandleT::~HandleT, destructor
ms.assetid: 3822b32a-a426-4d94-a54d-919d4df60ee2
ms.openlocfilehash: c7c5951cd966e33d3dda45f9dad504d821838de6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486135"
---
# <a name="handlet-class"></a>HandleT – třída

Reprezentuje popisovač objektu.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename HandleTraits>
class HandleT;
```

### <a name="parameters"></a>Parametry

*Handletraits –*<br/>
Instance [handletraits –](../windows/handletraits-structure.md) stucture, který definuje běžné vlastnosti popisovač.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

Název     | Popis
-------- | -----------------------------
`Traits` | Synonymum pro `HandleTraits`.

### <a name="public-constructors"></a>Veřejné konstruktory

Název                                | Popis
----------------------------------- | --------------------------------------------------
[Handlet::handlet –](#handlet)        | Inicializuje novou instanci třídy `HandleT` třídy.
[HandleT:: ~ handlet –](#tilde-handlet) | Uvolní instanci `HandleT` třídy.

### <a name="public-methods"></a>Veřejné metody

Název                         | Popis
---------------------------- | ----------------------------------------------------------------------
[Handlet::Attach –](#attach)   | Přidruží Zadaný popisovač s aktuálním `HandleT` objektu.
[Handlet::Close –](#close)     | Zavře aktuální `HandleT` objektu.
[Handlet::detach –](#detach)   | Zruší přidružení aktuální `HandleT` objekt z jeho základní popisovač.
[Handlet::Get –](#get)         | Načte hodnotu podkladového popisovače.
[Handlet::IsValid –](#isvalid) | Určuje, zda aktuální `HandleT` objekt představuje popisovač.

### <a name="protected-methods"></a>Chráněné metody

Název                                     | Popis
---------------------------------------- | ------------------------------------
[Handlet::internalclose –](#internalclose) | Zavře aktuální `HandleT` objektu.

### <a name="public-operators"></a>Veřejné operátory

Název                                   | Popis
-------------------------------------- | ----------------------------------------------------------------------------------
[HandleT::operator =](#operator-assign) | Přesune hodnotu zadaného `HandleT` objektů na aktuální `HandleT` objektu.

### <a name="protected-data-members"></a>Chránění členové dat

Název                        | Popis
--------------------------- | ----------------------------------------------------------------
[Handlet::handle_ –](#handle) | Obsahuje popisovač, která je reprezentována `HandleT` objektu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`HandleT`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL:: wrappers –

## <a name="tilde-handlet"></a>HandleT:: ~ handlet –

Uvolní instanci `HandleT` třídy.

```cpp
~HandleT();
```

## <a name="attach"></a>Handlet::Attach –

Přidruží Zadaný popisovač s aktuálním `HandleT` objektu.

```cpp
void Attach(
   typename HandleTraits::Type h
);
```

### <a name="parameters"></a>Parametry

*h*<br/>
Popisovač.

## <a name="close"></a>Handlet::Close –

Zavře aktuální `HandleT` objektu.

```cpp
void Close();
```

### <a name="remarks"></a>Poznámky

Popisovač, které je základem aktuální `HandleT` je zavřená a `HandleT` je nastavena na neplatný stav.

Pokud je popisovač nezavírá správně, je vyvolána výjimka ve volajícím vlákně.

## <a name="detach"></a>Handlet::detach –

Zruší přidružení aktuální `HandleT` objekt z jeho základní popisovač.

```cpp
typename HandleTraits::Type Detach();
```

### <a name="return-value"></a>Návratová hodnota

Základní popisovač.

### <a name="remarks"></a>Poznámky

Když tato operace dokončí, aktuální `HandleT` je nastavena na neplatný stav.

## <a name="get"></a>Handlet::Get –

Načte hodnotu podkladového popisovače.

```cpp
typename HandleTraits::Type Get() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač.

## <a name="handle"></a>Handlet::handle_ –

Obsahuje popisovač, která je reprezentována `HandleT` objektu.

```cpp
typename HandleTraits::Type handle_;
```

## <a name="handlet"></a>Handlet::handlet –

Inicializuje novou instanci třídy `HandleT` třídy.

```cpp
explicit HandleT(
   typename HandleTraits::Type h =
      HandleTraits::GetInvalidValue()
);

HandleT(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>Parametry

*h*<br/>
Popisovač.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje `HandleT` objekt, který není platný popisovač pro objekt. Druhý konstruktor vytvoří novou `HandleT` objekt z parametru *h*.

## <a name="internalclose"></a>Handlet::internalclose –

Zavře aktuální `HandleT` objektu.

```cpp
virtual bool InternalClose();
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud aktuální `HandleT` zavření úspěšně; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

`InternalClose()` je `protected`.

## <a name="isvalid"></a>Handlet::IsValid –

Určuje, zda aktuální `HandleT` objekt představuje popisovač.

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud `HandleT` představuje popisovač; v opačném případě **false**.

## <a name="operator-assign"></a>HandleT::operator =

Přesune hodnotu zadaného `HandleT` objektů na aktuální `HandleT` objektu.

```cpp
HandleT& operator=(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>Parametry

*h*<br/>
Odkaz rvalue na popisovač.

### <a name="return-value"></a>Návratová hodnota

Odkaz na aktuální `HandleT` objektu.

### <a name="remarks"></a>Poznámky

Tato operace zruší platnost `HandleT` objekt zadaný parametrem *h*.
