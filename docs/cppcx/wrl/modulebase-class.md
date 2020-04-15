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
ms.openlocfilehash: 13a8ceef3133e9946524e1fcd02e96535eccd7fc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371261"
---
# <a name="modulebase-class"></a>ModuleBase – třída

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

## <a name="syntax"></a>Syntaxe

```cpp
class ModuleBase;
```

## <a name="remarks"></a>Poznámky

Představuje základní třídu [Třídy Module.](module-class.md)

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Name (Název)                                         | Popis
-------------------------------------------- | ---------------------------------------------------------
[ModulBase::ModulBase](#modulebase)        | Inicializuje instanci třídy `Module`.
[ModulBase::~ModuleBase](#tilde-modulebase) | Deinitializes aktuální instance `Module` třídy.

### <a name="public-methods"></a>Veřejné metody

Name (Název)                                                      | Popis
--------------------------------------------------------- | -------------------------------------------------------------------------
[ModulBase::DecrementObjectCount](#decrementobjectcount) | Při implementaci sníží počet objektů sledovaných modulem.
[ModulBase::IncrementObjectCount](#incrementobjectcount) | Při implementaci se zintáží počet objektů sledovaných modulem.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ModuleBase`

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Obor názvů:** Microsoft::WRL::Details

## <a name="modulebasemodulebase"></a><a name="tilde-modulebase"></a>ModulBase::~ModuleBase

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
virtual ~ModuleBase();
```

### <a name="remarks"></a>Poznámky

Deinitializes aktuální instance `ModuleBase` třídy.

## <a name="modulebasedecrementobjectcount"></a><a name="decrementobjectcount"></a>ModulBase::DecrementObjectCount

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
virtual long DecrementObjectCount() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Počet před operací snížení.

### <a name="remarks"></a>Poznámky

Při implementaci sníží počet objektů sledovaných modulem.

## <a name="modulebaseincrementobjectcount"></a><a name="incrementobjectcount"></a>ModulBase::IncrementObjectCount

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
virtual long IncrementObjectCount() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Počet před operací přírůstek.

### <a name="remarks"></a>Poznámky

Při implementaci se zintáží počet objektů sledovaných modulem.

## <a name="modulebasemodulebase"></a><a name="modulebase"></a>ModulBase::ModulBase

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
ModuleBase();
```

### <a name="remarks"></a>Poznámky

Inicializuje instanci třídy `Module`.
