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
ms.openlocfilehash: b43d5bb2f553d298584ab2ae497c22637d3beb0d
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58786542"
---
# <a name="roinitializewrapper-class"></a>RoInitializeWrapper – třída

Inicializuje modul Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
class RoInitializeWrapper;
```

## <a name="remarks"></a>Poznámky

`RoInitializeWrapper` je usnadnění práce, která inicializuje modul Windows Runtime a vrátí HRESULT, která určuje, zda operace byla úspěšná. Vzhledem k tomu volá destruktor třídy `::Windows::Foundation::Uninitialize`, výskyty `RoInitializeWrapper` musí být deklarovány v oboru globálním správcem nebo nejvyšší úrovně.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Název                                                                    | Popis
----------------------------------------------------------------------- | -----------------------------------------------------------------
[RoInitializeWrapper::RoInitializeWrapper](#roinitializewrapper)        | Inicializuje novou instanci třídy `RoInitializeWrapper` třídy.
[RoInitializeWrapper::~RoInitializeWrapper](#tilde-roinitializewrapper) | Odstraní aktuální instanci aplikace `RoInitializeWrapper` třídy.

### <a name="public-operators"></a>Veřejné operátory

Name                                       | Popis
------------------------------------------ | ------------------------------------------------------------------------
[RoInitializeWrapper::HRESULT()](#hresult) | Načte hodnotu HRESULT vytvořené metodou `RoInitializeWrapper` konstruktoru.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`RoInitializeWrapper`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="hresult"></a>Roinitializewrapper:: HRESULT()

Načte hodnotu HRESULT vytvářených poslední `RoInitializeWrapper` konstruktoru.

```cpp
operator HRESULT()
```

## <a name="roinitializewrapper"></a>Roinitializewrapper::roinitializewrapper –

Inicializuje novou instanci třídy `RoInitializeWrapper` třídy.

```cpp
RoInitializeWrapper(RO_INIT_TYPE flags)
```

### <a name="parameters"></a>Parametry

*příznaky*<br/>
Jeden z výčtů RO_INIT_TYPE, které určuje podporu poskytovaný modulem Windows Runtime.

### <a name="remarks"></a>Poznámky

`RoInitializeWrapper` Třída vyvolá `Windows::Foundation::Initialize(flags)`.

## <a name="tilde-roinitializewrapper"></a>RoInitializeWrapper:: ~ roinitializewrapper –

Zruší inicializaci modulu Windows Runtime.

```cpp
~RoInitializeWrapper()
```

### <a name="remarks"></a>Poznámky

`RoInitializeWrapper` Třída vyvolá `Windows::Foundation::Uninitialize()`.