---
title: Csimplearrayequalhelperfalse – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse::IsEqual
dev_langs:
- C++
helpviewer_keywords:
- CSimpleArrayEqualHelperFalse class
ms.assetid: 6918af6f-d23d-49eb-8482-c44272f5ffeb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6cc489850ea8e8d2704c92d1c2a671557a4db67a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084325"
---
# <a name="csimplearrayequalhelperfalse-class"></a>Csimplearrayequalhelperfalse – třída

Tato třída je pomocné rutiny pro [csimplearray –](../../atl/reference/csimplearray-class.md) třídy.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class CSimpleArrayEqualHelperFalse
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Odvozené třídy.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CSimpleArrayEqualHelperFalse::IsEqual](#isequal)|(Statické) Vrátí hodnotu false.|

## <a name="remarks"></a>Poznámky

Tato třída vlastností je doplněk k `CSimpleArray` třídy. IT vždy vrátí hodnotu false a kromě toho bude volat `ATLASSERT` s argumentem false, pokud se na ni stále odkazuje. V situacích, kde není dostatečně definovány test rovnosti, tato třída umožňuje pole obsahující prvky, aby správně fungovat pro většinu metod ale selhání způsobem jasně definovaných pro metody, které jsou závislé na porovnání například [csimplearray –:: Najít](../../atl/reference/csimplearray-class.md#find).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsimpcoll.h

##  <a name="isequal"></a>  CSimpleArrayEqualHelperFalse::IsEqual

Vrátí hodnotu false.

```
static bool IsEqual(const T&, const T&);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu false.

### <a name="remarks"></a>Poznámky

Tato metoda vždy vrátí hodnotu false a bude volat `ATLASSERT` s argumentem false, pokud odkazuje. Účelem `CSimpleArrayEqualHelperFalse::IsEqual` metodou je vynutit metod pomocí porovnávání selhání způsobem jasně definované při rovnosti testy nebyly definovány odpovídajícím způsobem.

## <a name="see-also"></a>Viz také

[CSimpleArrayEqualHelper – třída](../../atl/reference/csimplearrayequalhelper-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
