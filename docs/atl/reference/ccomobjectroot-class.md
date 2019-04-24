---
title: Ccomobjectroot – třída
ms.date: 11/04/2016
f1_keywords:
- CComObjectRoot
- atlcom/ATL::CComObjectRoot
helpviewer_keywords:
- CComObjectRoot class
ms.assetid: f8797c38-6e73-4f67-85c2-71654cffa8eb
ms.openlocfilehash: 9a9ffa1813fb15297d209894050b6bcce6802df2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62259362"
---
# <a name="ccomobjectroot-class"></a>Ccomobjectroot – třída

Tato definice typu z [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) je založena na výchozí model serveru vláken.

## <a name="syntax"></a>Syntaxe

```
typedef CComObjectRootEx<CComObjectThreadModel> CComObjectRoot;
```

## <a name="remarks"></a>Poznámky

`CComObjectRoot` je `typedef` z [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) založena na výchozí model serveru vláken. Proto [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) bude odkazovat buď [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) nebo [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md).

`CComObjectRootEx` zpracovává správy referenční počet objektů pro neagregovaná a agregované objekty. Obsahuje referenční počet objektů, pokud objekt není agregovaný a drží ukazatel vnější neznámá, pokud je agregovaný objekt. Pro agregované objekty `CComObjectRootEx` metody lze použít k vyřešení selhání vnitřní objekt k vytvoření a odstranění k ochraně vnější objekt před odstraněním vydáním vnitřní rozhraní nebo vnitřní objekt.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom

## <a name="see-also"></a>Viz také:

[CComObjectRootEx – třída](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComAggObject – třída](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject – třída](../../atl/reference/ccomobject-class.md)<br/>
[CComPolyObject – třída](../../atl/reference/ccompolyobject-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
