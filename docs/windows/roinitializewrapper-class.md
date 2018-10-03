---
title: Roinitializewrapper – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/24/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::HRESULT
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::RoInitializeWrapper
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::~RoInitializeWrapper
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::RoInitializeWrapper class
- Microsoft::WRL::Wrappers::RoInitializeWrapper::operator HRESULT operator
- Microsoft::WRL::Wrappers::RoInitializeWrapper::RoInitializeWrapper, constructor
- Microsoft::WRL::Wrappers::RoInitializeWrapper::~RoInitializeWrapper, destructor
ms.assetid: 4055fbe0-63a7-4c06-b5a0-414fda5640e5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 22271435db3a66095da5b6065a6b9cc9463b3de2
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2018
ms.locfileid: "48233746"
---
# <a name="roinitializewrapper-class"></a>RoInitializeWrapper – třída

Inicializuje modul Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
class RoInitializeWrapper
```

## <a name="remarks"></a>Poznámky

`RoInitializeWrapper` je usnadnění práce, která inicializuje modul Windows Runtime a vrátí HRESULT, která určuje, zda operace byla úspěšná. Vzhledem k tomu volá destruktor třídy `::Windows::Foundation::Uninitialize`, výskyty `RoInitializeWrapper` musí být deklarovány v oboru globálním správcem nebo nejvyšší úrovně.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Název                                                                    | Popis
----------------------------------------------------------------------- | -----------------------------------------------------------------
[Roinitializewrapper::roinitializewrapper –](#roinitializewrapper)        | Inicializuje novou instanci třídy `RoInitializeWrapper` třídy.
[RoInitializeWrapper:: ~ roinitializewrapper –](#tilde-roinitializewrapper) | Odstraní aktuální instanci aplikace `RoInitializeWrapper` třídy.

### <a name="public-operators"></a>Veřejné operátory

Název                                       | Popis
------------------------------------------ | ------------------------------------------------------------------------
[Roinitializewrapper:: HRESULT()](#hresult) | Načte hodnotu HRESULT vytvořené metodou `RoInitializeWrapper` konstruktoru.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`RoInitializeWrapper`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL:: wrappers –

## <a name="hresult"></a>Roinitializewrapper:: HRESULT()

Načte hodnotu HRESULT vytvářených poslední `RoInitializeWrapper` konstruktoru.

```cpp
operator HRESULT()  
```

## <a name="roinitializewrapper"></a>Roinitializewrapper::roinitializewrapper –

Inicializuje novou instanci třídy `RoInitializeWrapper` třídy.

```cpp
RoInitializeWrapper(   RO_INIT_TYPE flags)  
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
