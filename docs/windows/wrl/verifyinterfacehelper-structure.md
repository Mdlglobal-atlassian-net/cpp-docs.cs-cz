---
title: VerifyInterfaceHelper – struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInterfaceHelper
- implements/Microsoft::WRL::Details::VerifyInterfaceHelper::Verify
helpviewer_keywords:
- Microsoft::WRL::Details::VerifyInterfaceHelper structure
- Microsoft::WRL::Details::VerifyInterfaceHelper::Verify method
ms.assetid: ea95b641-199a-4fdf-964b-186b40cb3ba7
ms.openlocfilehash: cdd0272953b2399cd71efe207eb1c56e5de154e6
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334755"
---
# <a name="verifyinterfacehelper-structure"></a>VerifyInterfaceHelper – struktura

Podporuje knihovny šablon jazyka C++ Windows Runtime infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template <bool isWinRTInterface, typename I>
struct VerifyInterfaceHelper;

template <typename I>
struct VerifyInterfaceHelper<false, I>;
```

### <a name="parameters"></a>Parametry

*I*<br/>
Rozhraní pro ověření.

*isWinRTInterface*

## <a name="remarks"></a>Poznámky

Ověřuje, že rozhraní určené parametrem šablony splňuje určité požadavky.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

Název                                            | Popis
----------------------------------------------- | ---------------------------------------------------------------------------------------------------
[VerifyInterfaceHelper::Verify – metoda](#verify) | Ověřuje, že rozhraní určené typem parametru aktuální šablony splňuje určité požadavky.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`VerifyInterfaceHelper`

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="verify"></a>VerifyInterfaceHelper::Verify

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
static void Verify();
```

### <a name="remarks"></a>Poznámky

Ověřuje, že rozhraní určené typem parametru aktuální šablony splňuje určité požadavky.