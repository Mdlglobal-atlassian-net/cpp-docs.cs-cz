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
ms.openlocfilehash: bde7d7f1bd6730d96cb0f7a0d191a32eb8ed3e8c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371454"
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
Instance [HandleTraits](handletraits-structure.md) struktury, která definuje společné charakteristiky popisovače.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

Name (Název)     | Popis
-------- | -----------------------------
`Traits` | Synonymum `HandleTraits`pro .

### <a name="public-constructors"></a>Veřejné konstruktory

Name (Název)                                | Popis
----------------------------------- | --------------------------------------------------
[HandleT::HandleT](#handlet)        | Inicializuje novou instanci třídy. `HandleT`
[HandleT::~HandleT](#tilde-handlet) | Deinitializes instance třídy. `HandleT`

### <a name="public-methods"></a>Veřejné metody

Name (Název)                         | Popis
---------------------------- | ----------------------------------------------------------------------
[HandleT::Připojit](#attach)   | Přidruží zadaný `HandleT` popisovač k aktuálnímu objektu.
[HandleT::Zavřít](#close)     | Zavře aktuální `HandleT` objekt.
[HandleT::Detach](#detach)   | Odpojí aktuální `HandleT` objekt od jeho základního popisovače.
[HandleT::Získat](#get)         | Získá hodnotu základního popisovače.
[HandleT::IsValid](#isvalid) | Označuje, zda `HandleT` aktuální objekt představuje popisovač.

### <a name="protected-methods"></a>Chráněné metody

Name (Název)                                     | Popis
---------------------------------------- | ------------------------------------
[HandleT::InternalClose](#internalclose) | Zavře aktuální `HandleT` objekt.

### <a name="public-operators"></a>Veřejné operátory

Name (Název)                                   | Popis
-------------------------------------- | ----------------------------------------------------------------------------------
[HandleT::operátor=](#operator-assign) | Přesune hodnotu zadaného `HandleT` objektu `HandleT` na aktuální objekt.

### <a name="protected-data-members"></a>Členové chráněných dat

Name (Název)                        | Popis
--------------------------- | ----------------------------------------------------------------
[HandleT::handle_](#handle) | Obsahuje popisovač, který `HandleT` je reprezentován objektem.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`HandleT`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Obor názvů:** Microsoft::WRL::Obálky

## <a name="handlethandlet"></a><a name="tilde-handlet"></a>HandleT::~HandleT

Deinitializes instance třídy. `HandleT`

```cpp
~HandleT();
```

## <a name="handletattach"></a><a name="attach"></a>HandleT::Připojit

Přidruží zadaný `HandleT` popisovač k aktuálnímu objektu.

```cpp
void Attach(
   typename HandleTraits::Type h
);
```

### <a name="parameters"></a>Parametry

*H*<br/>
Rukojeť.

## <a name="handletclose"></a><a name="close"></a>HandleT::Zavřít

Zavře aktuální `HandleT` objekt.

```cpp
void Close();
```

### <a name="remarks"></a>Poznámky

Popisovač, který je `HandleT` základem proudu `HandleT` je uzavřen a je nastaven na neplatný stav.

Pokud popisovač nezavře správně, je vyvolána výjimka v volajícívlákno.

## <a name="handletdetach"></a><a name="detach"></a>HandleT::Detach

Odpojí aktuální `HandleT` objekt od jeho základního popisovače.

```cpp
typename HandleTraits::Type Detach();
```

### <a name="return-value"></a>Návratová hodnota

Základní popisovač.

### <a name="remarks"></a>Poznámky

Po dokončení této operace `HandleT` je aktuální nastaven na neplatný stav.

## <a name="handletget"></a><a name="get"></a>HandleT::Získat

Získá hodnotu základního popisovače.

```cpp
typename HandleTraits::Type Get() const;
```

### <a name="return-value"></a>Návratová hodnota

Rukojeť.

## <a name="handlethandle_"></a><a name="handle"></a>HandleT::handle_

Obsahuje popisovač, který `HandleT` je reprezentován objektem.

```cpp
typename HandleTraits::Type handle_;
```

## <a name="handlethandlet"></a><a name="handlet"></a>HandleT::HandleT

Inicializuje novou instanci třídy. `HandleT`

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

*H*<br/>
Rukojeť.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje `HandleT` objekt, který není platným popisovačem objektu. Druhý konstruktor vytvoří `HandleT` nový objekt z parametru *h*.

## <a name="handletinternalclose"></a><a name="internalclose"></a>HandleT::InternalClose

Zavře aktuální `HandleT` objekt.

```cpp
virtual bool InternalClose();
```

### <a name="return-value"></a>Návratová hodnota

**true,** pokud `HandleT` se aktuální úspěšně zavřel; jinak **false**.

### <a name="remarks"></a>Poznámky

`InternalClose()` je `protected`.

## <a name="handletisvalid"></a><a name="isvalid"></a>HandleT::IsValid

Označuje, zda `HandleT` aktuální objekt představuje popisovač.

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>Návratová hodnota

**true,** `HandleT` pokud představuje popisovač; jinak **false**.

## <a name="handletoperator"></a><a name="operator-assign"></a>HandleT::operátor=

Přesune hodnotu zadaného `HandleT` objektu `HandleT` na aktuální objekt.

```cpp
HandleT& operator=(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>Parametry

*H*<br/>
Rvalue odkaz na popisovač.

### <a name="return-value"></a>Návratová hodnota

Odkaz na aktuální `HandleT` objekt.

### <a name="remarks"></a>Poznámky

Tato operace zruší `HandleT` platnost objektu určeného parametrem *h*.
