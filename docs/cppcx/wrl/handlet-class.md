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
ms.openlocfilehash: f66fbe23c305be15e09928242175dfa7ce8c141b
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821815"
---
# <a name="handlet-class"></a>HandleT – třída

Představuje popisovač objektu.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename HandleTraits>
class HandleT;
```

### <a name="parameters"></a>Parametry

*HandleTraits*<br/>
Instance struktury [HandleTraits](handletraits-structure.md) , která definuje společné charakteristiky popisovače.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

Name     | Popis
-------- | -----------------------------
`Traits` | Synonymum pro `HandleTraits`.

### <a name="public-constructors"></a>Veřejné konstruktory

Name                                | Popis
----------------------------------- | --------------------------------------------------
[HandleT:: HandleT](#handlet)        | Inicializuje novou instanci třídy `HandleT` třídy.
[HandleT:: ~ HandleT](#tilde-handlet) | Zruší inicializaci instance třídy `HandleT`.

### <a name="public-methods"></a>Veřejné metody

Name                         | Popis
---------------------------- | ----------------------------------------------------------------------
[HandleT:: Attach](#attach)   | Přidruží zadaný popisovač k aktuálnímu objektu `HandleT`.
[HandleT:: Close](#close)     | Zavře aktuální objekt `HandleT`.
[HandleT::D etach](#detach)   | Zruší přidružení aktuálního objektu `HandleT` k jeho základnímu popisovači.
[HandleT:: Get](#get)         | Získá hodnotu podkladového popisovače.
[HandleT::IsValid](#isvalid) | Určuje, zda aktuální objekt `HandleT` představuje popisovač.

### <a name="protected-methods"></a>Chráněné metody

Name                                     | Popis
---------------------------------------- | ------------------------------------
[HandleT::InternalClose](#internalclose) | Zavře aktuální objekt `HandleT`.

### <a name="public-operators"></a>Veřejné operátory

Name                                   | Popis
-------------------------------------- | ----------------------------------------------------------------------------------
[HandleT:: operator =](#operator-assign) | Přesune hodnotu zadaného objektu `HandleT` na aktuální objekt `HandleT`.

### <a name="protected-data-members"></a>Chránění členové dat

Name                        | Popis
--------------------------- | ----------------------------------------------------------------
[Popisovač:: handle_](#handle) | Obsahuje popisovač, který je reprezentován objektem `HandleT`.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`HandleT`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers. h

**Obor názvů:** Microsoft:: WRL:: Wrappers

## <a name="tilde-handlet"></a>HandleT:: ~ HandleT

Zruší inicializaci instance třídy `HandleT`.

```cpp
~HandleT();
```

## <a name="attach"></a>HandleT:: Attach

Přidruží zadaný popisovač k aktuálnímu objektu `HandleT`.

```cpp
void Attach(
   typename HandleTraits::Type h
);
```

### <a name="parameters"></a>Parametry

*h*<br/>
Popisovač.

## <a name="close"></a>HandleT:: Close

Zavře aktuální objekt `HandleT`.

```cpp
void Close();
```

### <a name="remarks"></a>Poznámky

Popisovač, který je v aktuální `HandleT`, je uzavřený a `HandleT` je nastaven na neplatný stav.

Pokud se popisovač neukončí správně, je vyvolána výjimka ve volajícím vlákně.

## <a name="detach"></a>HandleT::D etach

Zruší přidružení aktuálního objektu `HandleT` k jeho základnímu popisovači.

```cpp
typename HandleTraits::Type Detach();
```

### <a name="return-value"></a>Návratová hodnota

Nadřízený popisovač

### <a name="remarks"></a>Poznámky

Po dokončení této operace je aktuální `HandleT` nastavena na neplatný stav.

## <a name="get"></a>HandleT:: Get

Získá hodnotu podkladového popisovače.

```cpp
typename HandleTraits::Type Get() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač.

## <a name="handle"></a>Popisovač:: handle_

Obsahuje popisovač, který je reprezentován objektem `HandleT`.

```cpp
typename HandleTraits::Type handle_;
```

## <a name="handlet"></a>HandleT:: HandleT

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

První konstruktor inicializuje objekt `HandleT`, který není platným popisovačem objektu. Druhý konstruktor vytvoří nový objekt `HandleT` z parametru *h*.

## <a name="internalclose"></a>Popisovač:: InternalClose –

Zavře aktuální objekt `HandleT`.

```cpp
virtual bool InternalClose();
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud se aktuální `HandleT` zavře úspěšně; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

`InternalClose()` je `protected`.

## <a name="isvalid"></a>HandleT:: IsValid

Určuje, zda aktuální objekt `HandleT` představuje popisovač.

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud `HandleT` představuje popisovač; v opačném případě **false**.

## <a name="operator-assign"></a>HandleT:: operator =

Přesune hodnotu zadaného objektu `HandleT` na aktuální objekt `HandleT`.

```cpp
HandleT& operator=(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>Parametry

*h*<br/>
Rvalue – odkaz na popisovač.

### <a name="return-value"></a>Návratová hodnota

Odkaz na aktuální objekt `HandleT`.

### <a name="remarks"></a>Poznámky

Tato operace zruší platnost objektu `HandleT` zadaného parametrem *h*.
