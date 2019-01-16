---
title: IsSame – struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsSame
- internal/Microsoft::WRL::Details::IsSame::value
helpviewer_keywords:
- Microsoft::WRL::Details::IsSame structure
- Microsoft::WRL::Details::IsSame::value constant
ms.assetid: 1eddbc3f-3cc5-434f-8495-e4477e1f868e
ms.openlocfilehash: b659f832756b79289181db34fa8d6fc0d974609d
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334923"
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

**Namespace:** Microsoft::WRL::Details

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

`value` je **true** Pokud parametrů šablony jsou stejné, a **false** Pokud se liší parametry šablony.
