---
title: Třída CSimpleArrayEqualHelper
ms.date: 11/04/2016
f1_keywords:
- CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper::IsEqual
helpviewer_keywords:
- CSimpleArrayEqualHelper class
ms.assetid: a2b55d89-78c9-42ef-842c-5304c6d20ad6
ms.openlocfilehash: 386b005777b3e31dd74916a41bc5af2ab82df210
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330876"
---
# <a name="csimplearrayequalhelper-class"></a>Třída CSimpleArrayEqualHelper

Tato třída je pomocníkem pro třídu [CSimpleArray.](../../atl/reference/csimplearray-class.md)

## <a name="syntax"></a>Syntaxe

```
template <class T>
class CSimpleArrayEqualHelper
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Odvozená třída.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CSimpleArrayEqualHelper::IsEqual](#isequal)|(Statické) Testuje `CSimpleArray` dva prvky objektu pro rovnost.|

## <a name="remarks"></a>Poznámky

Tato třída vlastností je `CSimpleArray` doplňkem třídy. Poskytuje metodu pro porovnání dvou prvků `CSimpleArray` uložených v objektu. Ve výchozím nastavení jsou prvky porovnány pomocí **operator=()**, ale pokud pole obsahuje komplexní datové typy, které postrádají vlastní operátor rovnosti, budete muset přepsat tuto třídu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsimpcoll.h

## <a name="csimplearrayequalhelperisequal"></a><a name="isequal"></a>CSimpleArrayEqualHelper::IsEqual

Testuje `CSimpleArray` dva prvky objektu pro rovnost.

```
static bool IsEqual(
    const T& t1,
    const T& t2);
```

### <a name="parameters"></a>Parametry

*T1*<br/>
Objekt typu T.

*t2*<br/>
Objekt typu T.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud jsou prvky stejné, false otherwise.

## <a name="see-also"></a>Viz také

[Třída CSimpleArray](../../atl/reference/csimplearray-class.md)<br/>
[Třída CSimpleArrayEqualHelperFalse](../../atl/reference/csimplearrayequalhelperfalse-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
