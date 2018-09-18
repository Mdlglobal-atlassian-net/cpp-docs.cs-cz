---
title: Ccomobjectroot – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComObjectRoot
- atlcom/ATL::CComObjectRoot
dev_langs:
- C++
helpviewer_keywords:
- CComObjectRoot class
ms.assetid: f8797c38-6e73-4f67-85c2-71654cffa8eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2647ea3ac46ec3783f584de996c3d988c168980d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054856"
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

## <a name="see-also"></a>Viz také

[CComObjectRootEx – třída](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComAggObject – třída](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject – třída](../../atl/reference/ccomobject-class.md)<br/>
[CComPolyObject – třída](../../atl/reference/ccompolyobject-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
