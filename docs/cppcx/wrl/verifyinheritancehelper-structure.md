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
ms.openlocfilehash: 3650cfb70ffc12572b3965534eff4e1f2ecb2cf5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374234"
---
# <a name="verifyinheritancehelper-structure"></a>VerifyInheritanceHelper – struktura

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

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

*Základní*<br/>
Jiný typ.

## <a name="remarks"></a>Poznámky

Testuje, zda je jedno rozhraní odvozeno z jiného rozhraní.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

Name (Název)                                       | Popis
------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------
[VerifyInheritanceHelper::Ověřit](#verify) | Testuje dvě rozhraní určená aktuálními parametry šablony a určuje, zda je jedno rozhraní odvozeno od druhého.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`VerifyInheritanceHelper`

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Obor názvů:** Microsoft::WRL::Details

## <a name="verifyinheritancehelperverify"></a><a name="verify"></a>VerifyInheritanceHelper::Ověřit

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
static void Verify();
```

### <a name="remarks"></a>Poznámky

Testuje dvě rozhraní určená aktuálními parametry šablony a určuje, zda je jedno rozhraní odvozeno od druhého.

Chyba je emitován, pokud jedno rozhraní není odvozen od druhého.
