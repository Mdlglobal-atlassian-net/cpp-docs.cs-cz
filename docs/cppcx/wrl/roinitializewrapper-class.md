---
title: RoInitializeWrapper – třída
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::HRESULT
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::RoInitializeWrapper
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::~RoInitializeWrapper
helpviewer_keywords:
- Microsoft::WRL::Wrappers::RoInitializeWrapper class
- Microsoft::WRL::Wrappers::RoInitializeWrapper::operator HRESULT operator
- Microsoft::WRL::Wrappers::RoInitializeWrapper::RoInitializeWrapper, constructor
- Microsoft::WRL::Wrappers::RoInitializeWrapper::~RoInitializeWrapper, destructor
ms.assetid: 4055fbe0-63a7-4c06-b5a0-414fda5640e5
ms.openlocfilehash: eba9162f17b98d13a9caf956b4f110b89dd81c37
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371233"
---
# <a name="roinitializewrapper-class"></a>RoInitializeWrapper – třída

Inicializuje prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
class RoInitializeWrapper;
```

## <a name="remarks"></a>Poznámky

`RoInitializeWrapper`je pohodlí, které inicializuje prostředí Windows Runtime a vrátí HRESULT, který označuje, zda byla operace úspěšná. Vzhledem k tomu, `::Windows::Foundation::Uninitialize`že destruktor třídy volá , `RoInitializeWrapper` instance musí být deklarovány v globálním oboru nebo rozsahu nejvyšší úrovně.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Name (Název)                                                                    | Popis
----------------------------------------------------------------------- | -----------------------------------------------------------------
[RoInitializeWrapper::RoInitializeWrapper](#roinitializewrapper)        | Inicializuje novou instanci třídy. `RoInitializeWrapper`
[RoInitializeWrapper::~RoInitializeWrapper](#tilde-roinitializewrapper) | Zničí aktuální instanci `RoInitializeWrapper` třídy.

### <a name="public-operators"></a>Veřejné operátory

Name (Název)                                       | Popis
------------------------------------------ | ------------------------------------------------------------------------
[RoInitializeWrapper::HRESULT()](#hresult) | Načte HRESULT vyrobené `RoInitializeWrapper` konstruktoru.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`RoInitializeWrapper`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Obor názvů:** Microsoft::WRL::Obálky

## <a name="roinitializewrapperhresult"></a><a name="hresult"></a>RoInitializeWrapper::HRESULT()

Načte hodnotu HRESULT vytvořenou posledním `RoInitializeWrapper` konstruktorem.

```cpp
operator HRESULT()
```

## <a name="roinitializewrapperroinitializewrapper"></a><a name="roinitializewrapper"></a>RoInitializeWrapper::RoInitializeWrapper

Inicializuje novou instanci třídy. `RoInitializeWrapper`

```cpp
RoInitializeWrapper(RO_INIT_TYPE flags)
```

### <a name="parameters"></a>Parametry

*příznaky*<br/>
Jeden z RO_INIT_TYPE výčtů, který určuje podporu poskytovanou prostředím Windows Runtime.

### <a name="remarks"></a>Poznámky

Třída `RoInitializeWrapper` vyvolá `Windows::Foundation::Initialize(flags)`.

## <a name="roinitializewrapperroinitializewrapper"></a><a name="tilde-roinitializewrapper"></a>RoInitializeWrapper::~RoInitializeWrapper

Uninitializes prostředí Windows Runtime.

```cpp
~RoInitializeWrapper()
```

### <a name="remarks"></a>Poznámky

Třída `RoInitializeWrapper` vyvolá `Windows::Foundation::Uninitialize()`.
