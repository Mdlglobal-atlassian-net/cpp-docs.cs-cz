---
title: ModuleBase – třída
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ModuleBase
- implements/Microsoft::WRL::Details::ModuleBase::DecrementObjectCount
- implements/Microsoft::WRL::Details::ModuleBase::IncrementObjectCount
- implements/Microsoft::WRL::Details::ModuleBase::ModuleBase
- implements/Microsoft::WRL::Details::ModuleBase::~ModuleBase
helpviewer_keywords:
- ModuleBase class
- Microsoft::WRL::Details::ModuleBase::DecrementObjectCount method
- Microsoft::WRL::Details::ModuleBase::IncrementObjectCount method
- Microsoft::WRL::Details::ModuleBase::ModuleBase, constructor
- Microsoft::WRL::Details::ModuleBase::~ModuleBase, destructor
ms.assetid: edce7591-6893-46f7-94a7-382827775548
ms.openlocfilehash: 254796c03d25a77da22c48881c086a41ffbfeb82
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58786688"
---
# <a name="modulebase-class"></a>ModuleBase – třída

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
class ModuleBase;
```

## <a name="remarks"></a>Poznámky

Představuje základní třídu [modulu](module-class.md) třídy.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Name                                         | Popis
-------------------------------------------- | ---------------------------------------------------------
[ModuleBase::ModuleBase](#modulebase)        | Inicializuje novou instanci `Module` třídy.
[ModuleBase::~ModuleBase](#tilde-modulebase) | Zruší inicializaci aktuální instance `Module` třídy.

### <a name="public-methods"></a>Veřejné metody

Name                                                      | Popis
--------------------------------------------------------- | -------------------------------------------------------------------------
[Modulebase::decrementobjectcount –](#decrementobjectcount) | Při implementaci, sníží počet objektů sledování modulu.
[Modulebase::incrementobjectcount –](#incrementobjectcount) | Při implementaci, zvýší počet objektů, které jsou sledovány v rámci modulu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ModuleBase`

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="tilde-modulebase"></a>ModuleBase::~ModuleBase

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
virtual ~ModuleBase();
```

### <a name="remarks"></a>Poznámky

Zruší inicializaci aktuální instance `ModuleBase` třídy.

## <a name="decrementobjectcount"></a>Modulebase::decrementobjectcount –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
virtual long DecrementObjectCount() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Počet před provedením operace dekrementace.

### <a name="remarks"></a>Poznámky

Při implementaci, sníží počet objektů sledování modulu.

## <a name="incrementobjectcount"></a>Modulebase::incrementobjectcount –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
virtual long IncrementObjectCount() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Počet před provedením operace Inkrementace.

### <a name="remarks"></a>Poznámky

Při implementaci, zvýší počet objektů, které jsou sledovány v rámci modulu.

## <a name="modulebase"></a>ModuleBase::ModuleBase

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
ModuleBase();
```

### <a name="remarks"></a>Poznámky

Inicializuje novou instanci `Module` třídy.
