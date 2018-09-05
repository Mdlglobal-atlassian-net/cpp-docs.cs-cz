---
title: Csimplearrayequalhelper – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper::IsEqual
dev_langs:
- C++
helpviewer_keywords:
- CSimpleArrayEqualHelper class
ms.assetid: a2b55d89-78c9-42ef-842c-5304c6d20ad6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 87b23ba46ee4a8e25c15b4d9e51b87c444da67f1
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43758212"
---
# <a name="csimplearrayequalhelper-class"></a>Csimplearrayequalhelper – třída

Tato třída je pomocné rutiny pro [csimplearray –](../../atl/reference/csimplearray-class.md) třídy.

## <a name="syntax"></a>Syntaxe

```
template <class T>  
class CSimpleArrayEqualHelper
```

#### <a name="parameters"></a>Parametry

`T`  
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

*T1*  
Objekt typu T.

*T2.*  
Objekt typu T.

### <a name="return-value"></a>Návratová hodnota

Vrátí true, pokud prvky jsou stejné, jinak hodnota false.

## <a name="see-also"></a>Viz také

[Csimplearray – třída](../../atl/reference/csimplearray-class.md)   
[Csimplearrayequalhelperfalse – třída](../../atl/reference/csimplearrayequalhelperfalse-class.md)   
[Přehled tříd](../../atl/atl-class-overview.md)
