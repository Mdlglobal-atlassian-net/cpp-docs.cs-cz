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
ms.openlocfilehash: 09c2cc7e08e2dc0e8df42c64d285c37627c5925a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374236"
---
# <a name="verifyinterfacehelper-structure"></a>VerifyInterfaceHelper – struktura

Podporuje infrastrukturu knihovny šablon prostředí Prostředí Windows Runtime C++ a není určen pro použití přímo z vašeho kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template <bool isWinRTInterface, typename I>
struct VerifyInterfaceHelper;

template <typename I>
struct VerifyInterfaceHelper<false, I>;
```

### <a name="parameters"></a>Parametry

*I*<br/>
Rozhraní k ověření.

*isWinRTInterface*

## <a name="remarks"></a>Poznámky

Ověří, zda rozhraní určené parametrem šablony splňuje určité požadavky.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

Name (Název)                                            | Popis
----------------------------------------------- | ---------------------------------------------------------------------------------------------------
[VerifyInterfaceHelper::Verify – metoda](#verify) | Ověří, zda rozhraní určené aktuálním parametrem šablony splňuje určité požadavky.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`VerifyInterfaceHelper`

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Obor názvů:** Microsoft::WRL::Details

## <a name="verifyinterfacehelperverify"></a><a name="verify"></a>VerifyHelper::Ověřit

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
static void Verify();
```

### <a name="remarks"></a>Poznámky

Ověří, zda rozhraní určené aktuálním parametrem šablony splňuje určité požadavky.
