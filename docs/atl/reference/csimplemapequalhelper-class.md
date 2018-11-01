---
title: Csimplemapequalhelper – třída
ms.date: 11/04/2016
f1_keywords:
- CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualValue
helpviewer_keywords:
- CSimpleMapEqualHelper class
ms.assetid: 9bb2968a-d609-405c-8272-ff3b42df6164
ms.openlocfilehash: a530254bbaabce723b97d21313abb81e1b375833
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50527385"
---
# <a name="csimplemapequalhelper-class"></a>Csimplemapequalhelper – třída

Tato třída je pomocné rutiny pro [csimplemap –](../../atl/reference/csimplemap-class.md) třídy.

## <a name="syntax"></a>Syntaxe

```
template <class TKey, class TVal>
class CSimpleMapEqualHelper
```

#### <a name="parameters"></a>Parametry

*TKey*<br/>
Klíčovým prvkem.

*TVal*<br/>
Hodnota elementu.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CSimpleMapEqualHelper::IsEqualKey](#isequalkey)|(Statické) Testuje dva klíče pro rovnost.|
|[CSimpleMapEqualHelper::IsEqualValue](#isequalvalue)|(Statické) Porovná dvě hodnoty na rovnost.|

## <a name="remarks"></a>Poznámky

Tato třída vlastností je dodatek k `CSimpleMap` třídy. Poskytuje metody pro porovnání dvou `CSimpleMap` objektu prvky (konkrétně klíče a hodnoty komponent) pro rovnost. Ve výchozím nastavení, klíče a hodnoty jsou porovnány pomocí **operator==()**, ale pokud mapa obsahuje komplexní datové typy, které nemají vlastní operátor rovnosti, tato třída může být potlačena za účelem poskytují extra požadovanou funkci.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsimpcoll.h

##  <a name="isequalkey"></a>  CSimpleMapEqualHelper::IsEqualKey

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

Vrátí true, pokud klíče jsou stejné, jinak hodnota false.

##  <a name="isequalvalue"></a>  CSimpleMapEqualHelper::IsEqualValue

Porovná dvě hodnoty na rovnost.

```
static bool IsEqualValue(const TVal& v1, const TVal& v2);
```

### <a name="parameters"></a>Parametry

*V1*<br/>
První hodnota.

*v2*<br/>
Druhá hodnota.

### <a name="return-value"></a>Návratová hodnota

Vrátí true, pokud hodnoty jsou stejné, jinak hodnota false.

## <a name="see-also"></a>Viz také

[CSimpleMapEqualHelperFalse – třída](../../atl/reference/csimplemapequalhelperfalse-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
