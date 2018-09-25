---
title: Issame – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/21/2018
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
ms.openlocfilehash: a6d1e22d52a2e618357357555a549437ae453abe
ms.sourcegitcommit: edb46b0239a0e616af4ec58906e12338c3e8d2c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47169694"
---
# <a name="issame-structure"></a>IsSame – struktura

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   typename T1,
   typename T2
>
struct IsSame;
template <
   typename T1
>
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
