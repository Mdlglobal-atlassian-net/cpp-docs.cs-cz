---
title: Třída CSimpleMapEqualHelperFalse
ms.date: 11/04/2016
f1_keywords:
- CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualValue
helpviewer_keywords:
- CSimpleMapEqualHelperFalse class
ms.assetid: a873eea3-e130-45cc-a476-61ee79511c3b
ms.openlocfilehash: b6bf1d4e3be849004e13e593fb5f4b5cb87f8123
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330733"
---
# <a name="csimplemapequalhelperfalse-class"></a>Třída CSimpleMapEqualHelperFalse

Tato třída je pomocníkem pro [CSimpleMap](../../atl/reference/csimplemap-class.md) třídy.

## <a name="syntax"></a>Syntaxe

```
template <class TKey, class TVal>
class CSimpleMapEqualHelperFalse
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CSimpleMapEqualHelperFalse::IsEqualKey](#isequalkey)|(Statické) Testuje dva klíče pro rovnost.|
|[CSimpleMapEqualHelperFalse::IsEqualValue](#isequalvalue)|(Statické) Vrátí hodnotu false.|

## <a name="remarks"></a>Poznámky

Tato třída vlastností je `CSimpleMap` doplňkem třídy. Poskytuje metodu pro porovnání dvou prvků `CSimpleMap` obsažených v objektu, konkrétně dva prvky hodnoty nebo dva klíčové prvky.

Porovnání hodnot vždy vrátí false a navíc `ATLASSERT` bude volat s argumentem false, pokud je někdy odkazováno. V situacích, kdy test rovnosti není dostatečně definován, tato třída umožňuje mapování obsahující dvojice klíč/hodnota pracovat správně pro většinu metod, ale selhání v dobře definovaným způsobem pro metody, které závisí na porovnání, jako je [CSimpleMap::FindVal](../../atl/reference/csimplemap-class.md#findval).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsimpcoll.h

## <a name="csimplemapequalhelperfalseisequalkey"></a><a name="isequalkey"></a>CSimpleMapEqualHelperFalse::IsEqualKey

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

### <a name="remarks"></a>Poznámky

Tato metoda volá [CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md).

## <a name="csimplemapequalhelperfalseisequalvalue"></a><a name="isequalvalue"></a>CSimpleMapEqualHelperFalse::IsEqualValue

Vrátí hodnotu false.

```
static bool IsEqualValue(const TVal&, const TVal&);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu false.

### <a name="remarks"></a>Poznámky

Tato metoda vždy vrátí false `ATLASSERT` a bude volat s argumentem false, pokud je někdy odkazuje. Účelem `CSimpleMapEqualHelperFalse::IsEqualValue` je vynutit metody pomocí porovnání k selhání v dobře definovaným způsobem, pokud nebyly dostatečně definovány testy rovnosti.

## <a name="see-also"></a>Viz také

[Třída CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
