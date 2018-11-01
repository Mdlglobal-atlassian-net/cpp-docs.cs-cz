---
title: Csimplearrayequalhelper – třída
ms.date: 11/04/2016
f1_keywords:
- CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper::IsEqual
helpviewer_keywords:
- CSimpleArrayEqualHelper class
ms.assetid: a2b55d89-78c9-42ef-842c-5304c6d20ad6
ms.openlocfilehash: e677a5d12918649597db9614b965118f8d6b7da6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50656220"
---
# <a name="csimplearrayequalhelper-class"></a>Csimplearrayequalhelper – třída

Tato třída je pomocné rutiny pro [csimplearray –](../../atl/reference/csimplearray-class.md) třídy.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class CSimpleArrayEqualHelper
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Odvozené třídy.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CSimpleArrayEqualHelper::IsEqual](#isequal)|(Statické) Testuje dva `CSimpleArray` objektu prvky pro rovnost.|

## <a name="remarks"></a>Poznámky

Tato třída vlastností je dodatek k `CSimpleArray` třídy. Poskytuje metodu pro porovnání dvou prvků uložených v `CSimpleArray` objektu. Ve výchozím nastavení, prvky jsou porovnány pomocí **operator=()**, ale pokud pole obsahuje komplexní datové typy, které nemají vlastní operátor rovnosti, budete potřebovat k přepsání této třídy.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsimpcoll.h

##  <a name="isequal"></a>  CSimpleArrayEqualHelper::IsEqual

Testuje dva `CSimpleArray` objektu prvky pro rovnost.

```
static bool IsEqual(
    const T& t1,
    const T& t2);
```

### <a name="parameters"></a>Parametry

*T1*<br/>
Objekt typu T.

*T2.*<br/>
Objekt typu T.

### <a name="return-value"></a>Návratová hodnota

Vrátí true, pokud prvky jsou stejné, jinak hodnota false.

## <a name="see-also"></a>Viz také

[CSimpleArray – třída](../../atl/reference/csimplearray-class.md)<br/>
[CSimpleArrayEqualHelperFalse – třída](../../atl/reference/csimplearrayequalhelperfalse-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
