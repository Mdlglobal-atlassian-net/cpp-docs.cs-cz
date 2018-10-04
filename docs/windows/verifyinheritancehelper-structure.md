---
title: Verifyinheritancehelper – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInheritanceHelper
- implements/Microsoft::WRL::Details::VerifyInheritanceHelper::Verify
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::VerifyInheritanceHelper structure
- Microsoft::WRL::Details::VerifyInheritanceHelper::Verify method
ms.assetid: 8a48a702-0f71-4807-935b-8311f0a7a8b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2a011b0583d8221ec49d16236add978ac647acc3
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48788926"
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
