---
title: Třída CSimpleMapEqualHelper
ms.date: 11/04/2016
f1_keywords:
- CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualValue
helpviewer_keywords:
- CSimpleMapEqualHelper class
ms.assetid: 9bb2968a-d609-405c-8272-ff3b42df6164
ms.openlocfilehash: d137a35a517ea93139f036f6e9a7a8de06d518a7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330746"
---
# <a name="csimplemapequalhelper-class"></a>Třída CSimpleMapEqualHelper

Tato třída je pomocníkem pro [CSimpleMap](../../atl/reference/csimplemap-class.md) třídy.

## <a name="syntax"></a>Syntaxe

```
template <class TKey, class TVal>
class CSimpleMapEqualHelper
```

#### <a name="parameters"></a>Parametry

*Tkey*<br/>
Klíčovým prvkem.

*Tval (Tval)*<br/>
Prvek hodnoty.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CSimpleMapEqualHelper::IsEqualKey](#isequalkey)|(Statické) Testuje dva klíče pro rovnost.|
|[CSimpleMapEqualHelper::IsEqualValue](#isequalvalue)|(Statické) Testuje dvě hodnoty rovnosti.|

## <a name="remarks"></a>Poznámky

Tato třída vlastností je `CSimpleMap` doplňkem třídy. Poskytuje metody pro porovnání `CSimpleMap` dvou prvků objektu (konkrétně klíčových a hodnotových komponent) pro rovnost. Ve výchozím nastavení jsou klíče a hodnoty porovnány pomocí **operator==()**, ale pokud mapa obsahuje komplexní datové typy, které postrádají vlastní operátor rovnosti, může být tato třída přepsána, aby poskytovala další požadované funkce.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsimpcoll.h

## <a name="csimplemapequalhelperisequalkey"></a><a name="isequalkey"></a>CSimpleMapEqualHelper::IsEqualKey

Testuje dva klíče pro rovnost.

```
static bool IsEqualKey(const TKey& k1, const TKey& k2);
```

### <a name="parameters"></a>Parametry

*k1*<br/>
První klíč.

*k2*<br/>
Druhý klíč.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud jsou klíče stejné, false jinak.

## <a name="csimplemapequalhelperisequalvalue"></a><a name="isequalvalue"></a>CSimpleMapEqualHelper::IsEqualValue

Testuje dvě hodnoty rovnosti.

```
static bool IsEqualValue(const TVal& v1, const TVal& v2);
```

### <a name="parameters"></a>Parametry

*v1*<br/>
První hodnota.

*v2*<br/>
Druhá hodnota.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud jsou hodnoty stejné, false otherwise.

## <a name="see-also"></a>Viz také

[Třída CSimpleMapEqualHelperFalse](../../atl/reference/csimplemapequalhelperfalse-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
