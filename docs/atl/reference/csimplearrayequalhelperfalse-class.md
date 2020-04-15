---
title: Třída CSimpleArrayEqualHelperFalse
ms.date: 11/04/2016
f1_keywords:
- CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse::IsEqual
helpviewer_keywords:
- CSimpleArrayEqualHelperFalse class
ms.assetid: 6918af6f-d23d-49eb-8482-c44272f5ffeb
ms.openlocfilehash: 5eca3145d64895e34b599fbf83834af142b65973
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330889"
---
# <a name="csimplearrayequalhelperfalse-class"></a>Třída CSimpleArrayEqualHelperFalse

Tato třída je pomocníkem pro třídu [CSimpleArray.](../../atl/reference/csimplearray-class.md)

## <a name="syntax"></a>Syntaxe

```
template <class T>
class CSimpleArrayEqualHelperFalse
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Odvozená třída.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CSimpleArrayEqualHelperFalse::IsEqual](#isequal)|(Statické) Vrátí hodnotu false.|

## <a name="remarks"></a>Poznámky

Tato třída vlastností je `CSimpleArray` doplňkem třídy. Vždy vrátí false a navíc bude `ATLASSERT` volat s argumentem false, pokud je někdy odkazováno. V situacích, kdy test rovnosti není dostatečně definován, tato třída umožňuje pole obsahující prvky pracovat správně pro většinu metod, ale selhat v dobře definovaným způsobem pro metody, které závisí na porovnání, jako je [Například CSimpleArray::Find](../../atl/reference/csimplearray-class.md#find).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsimpcoll.h

## <a name="csimplearrayequalhelperfalseisequal"></a><a name="isequal"></a>CSimpleArrayEqualHelperFalse::IsEqual

Vrátí hodnotu false.

```
static bool IsEqual(const T&, const T&);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu false.

### <a name="remarks"></a>Poznámky

Tato metoda vždy vrátí false `ATLASSERT` a bude volat s argumentem false,pokud odkazuje. Účelem `CSimpleArrayEqualHelperFalse::IsEqual` je vynutit metody pomocí porovnání k selhání v dobře definovaným způsobem, pokud nebyly dostatečně definovány testy rovnosti.

## <a name="see-also"></a>Viz také

[Třída CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
