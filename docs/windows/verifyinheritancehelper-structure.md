---
title: VerifyInheritanceHelper – struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInheritanceHelper
- implements/Microsoft::WRL::Details::VerifyInheritanceHelper::Verify
helpviewer_keywords:
- Microsoft::WRL::Details::VerifyInheritanceHelper structure
- Microsoft::WRL::Details::VerifyInheritanceHelper::Verify method
ms.assetid: 8a48a702-0f71-4807-935b-8311f0a7a8b6
ms.openlocfilehash: c37a0eb74fd65b3d349d5b8b7c792fbaf7d1ac9a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50565422"
---
# <a name="verifyinheritancehelper-structure"></a>VerifyInheritanceHelper – struktura

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename I, typename Base>
struct VerifyInheritanceHelper;

template <typename I>
struct VerifyInheritanceHelper<I, Nil>;
```

### <a name="parameters"></a>Parametry

*I*<br/>
Typ.

*základ*<br/>
Jiného typu.

## <a name="remarks"></a>Poznámky

Ověřuje, zda jedno rozhraní je odvozena od jiného rozhraní.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

Název                                       | Popis
------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------
[Verifyinheritancehelper::Verify –](#verify) | Testuje dvě rozhraní určeném aktuálním parametry šablony a určuje, zda jedno rozhraní je odvozena od druhé.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`VerifyInheritanceHelper`

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL:: details –

## <a name="verify"></a>Verifyinheritancehelper::Verify –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
static void Verify();
```

### <a name="remarks"></a>Poznámky

Testuje dvě rozhraní určeném aktuálním parametry šablony a určuje, zda jedno rozhraní je odvozena od druhé.

Chyba je vygenerován, pokud jedno rozhraní není odvozena od druhé.
