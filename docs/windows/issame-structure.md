---
title: Issame – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsSame
- internal/Microsoft::WRL::Details::IsSame::value
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::IsSame structure
- Microsoft::WRL::Details::IsSame::value constant
ms.assetid: 1eddbc3f-3cc5-434f-8495-e4477e1f868e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 26ecab69c2c31db51e137ad012bf67541e03a095
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48788458"
---
# <a name="issame-structure"></a>IsSame – struktura

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T1, typename T2>
struct IsSame;

template <typename T1>
struct IsSame<T1, T1>;
```

### <a name="parameters"></a>Parametry

*T1*<br/>
Typ.

*T2*<br/>
Jiného typu.

## <a name="remarks"></a>Poznámky

Testy, zda jeden zadaný typ je stejný jako jiný určený typ.

## <a name="members"></a>Členové

### <a name="public-constants"></a>Veřejné konstanty

Název                    | Popis
----------------------- | --------------------------------------------------
[IsSame::value](#value) | Označuje, zda jeden typ. je stejný jako jiný.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IsSame`

## <a name="requirements"></a>Požadavky

**Záhlaví:** internal.h

**Namespace:** Microsoft::WRL:: details –

## <a name="value"></a>IsSame::value

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
template <typename T1, typename T2>
struct IsSame
{
    static const bool value = false;
};

template <typename T1>
struct IsSame<T1, T1>
{
    static const bool value = true;
};
```

### <a name="remarks"></a>Poznámky

Označuje, zda jeden typ. je stejný jako jiný.

`value` je `true` Pokud parametrů šablony jsou stejné, a `false` Pokud se liší parametry šablony.
