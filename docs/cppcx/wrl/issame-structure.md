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
ms.openlocfilehash: fcaf33309521b44163022e0ffa9b1e03e53e2551
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371349"
---
# <a name="issame-structure"></a>IsSame – struktura

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

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
Jiný typ.

## <a name="remarks"></a>Poznámky

Testuje, zda je jeden zadaný typ stejný jako jiný zadaný typ.

## <a name="members"></a>Členové

### <a name="public-constants"></a>Veřejné konstanty

Name (Název)                    | Popis
----------------------- | --------------------------------------------------
[IsSame::hodnota](#value) | Označuje, zda je jeden typ stejný jako jiný.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IsSame`

## <a name="requirements"></a>Požadavky

**Záhlaví:** internal.h

**Obor názvů:** Microsoft::WRL::Details

## <a name="issamevalue"></a><a name="value"></a>IsSame::hodnota

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

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

Označuje, zda je jeden typ stejný jako jiný.

`value`**true,** pokud parametry šablony jsou stejné, a **false,** pokud parametry šablony se liší.
