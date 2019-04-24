---
title: CSimpleMapEqualHelperFalse Class
ms.date: 11/04/2016
f1_keywords:
- CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualValue
helpviewer_keywords:
- CSimpleMapEqualHelperFalse class
ms.assetid: a873eea3-e130-45cc-a476-61ee79511c3b
ms.openlocfilehash: 9c4241049ad323047f06c0b29f946521f2c02167
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62277894"
---
# <a name="csimplemapequalhelperfalse-class"></a>CSimpleMapEqualHelperFalse Class

Tato třída je pomocné rutiny pro [csimplemap –](../../atl/reference/csimplemap-class.md) třídy.

## <a name="syntax"></a>Syntaxe

```
template <class TKey, class TVal>
class CSimpleMapEqualHelperFalse
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CSimpleMapEqualHelperFalse::IsEqualKey](#isequalkey)|(Statické) Testuje dva klíče pro rovnost.|
|[CSimpleMapEqualHelperFalse::IsEqualValue](#isequalvalue)|(Statické) Vrátí hodnotu false.|

## <a name="remarks"></a>Poznámky

Tato třída vlastností je dodatek k `CSimpleMap` třídy. Poskytuje metodu pro porovnání dvou elementů obsažených v `CSimpleMap` objektu, konkrétně dvě hodnoty prvků nebo dvě klíčové prvky.

Porovnání hodnoty vždy vrátí hodnotu false a kromě toho bude volat `ATLASSERT` s argumentem false, pokud se na ni stále odkazuje. V situacích, kde není dostatečně definovány test rovnosti, tato třída umožňuje mapování obsahující dvojice klíč/hodnota pro většinu metod správně fungovat, ale selhání způsobem jasně definovaných pro metody, které jsou závislé na porovnání, jako [csimplemap –:: FindVal](../../atl/reference/csimplemap-class.md#findval).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsimpcoll.h

##  <a name="isequalkey"></a>  CSimpleMapEqualHelperFalse::IsEqualKey

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

### <a name="remarks"></a>Poznámky

Tato metoda volá [csimplearrayequalhelper –](../../atl/reference/csimplearrayequalhelper-class.md).

##  <a name="isequalvalue"></a>  CSimpleMapEqualHelperFalse::IsEqualValue

Vrátí hodnotu false.

```
static bool IsEqualValue(const TVal&, const TVal&);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu false.

### <a name="remarks"></a>Poznámky

Tato metoda vždy vrátí hodnotu false a bude volat `ATLASSERT` s argumentem false, pokud se na ni stále odkazuje. Účelem `CSimpleMapEqualHelperFalse::IsEqualValue` metodou je vynutit metod pomocí porovnávání selhání způsobem jasně definované při rovnosti testy nebyly definovány odpovídajícím způsobem.

## <a name="see-also"></a>Viz také:

[CSimpleMapEqualHelper – třída](../../atl/reference/csimplemapequalhelper-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
