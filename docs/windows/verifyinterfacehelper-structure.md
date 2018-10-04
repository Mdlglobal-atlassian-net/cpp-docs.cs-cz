---
title: Verifyinterfacehelper – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInterfaceHelper
- implements/Microsoft::WRL::Details::VerifyInterfaceHelper::Verify
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::VerifyInterfaceHelper structure
- Microsoft::WRL::Details::VerifyInterfaceHelper::Verify method
ms.assetid: ea95b641-199a-4fdf-964b-186b40cb3ba7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b70155566695ade6b6778ade3b4758faebb3ea67
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48788862"
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

**Namespace:** Microsoft::WRL:: details –

## <a name="verify"></a>Verifyinterfacehelper::Verify –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
static void Verify();
```

### <a name="remarks"></a>Poznámky

Ověřuje, že rozhraní určené typem parametru aktuální šablony splňuje určité požadavky.
