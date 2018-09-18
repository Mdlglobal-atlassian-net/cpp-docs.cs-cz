---
title: Cautoptrarray – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray::CAutoPtrArray
dev_langs:
- C++
helpviewer_keywords:
- CAutoPtrArray class
ms.assetid: 880a70da-8c81-4427-8ac6-49aa8d424244
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 23cc8e519fc47173efe413cc687ef48c0dc39945
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025162"
---
# <a name="cautoptrarray-class"></a>Cautoptrarray – třída

Tato třída poskytuje metody, které jsou užitečné při vytváření pole inteligentních ukazatelů.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <typename E>
class CAutoPtrArray : public CAtlArray<
                        ATL::CAutoPtr<E>,
                        CAutoPtrElementTraits<E>>
```

#### <a name="parameters"></a>Parametry

*E*<br/>
Typ ukazatele.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAutoPtrArray::CAutoPtrArray](#cautoptrarray)|Konstruktor|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje konstruktor a je odvozena z metody [catlarray –](../../atl/reference/catlarray-class.md) a [cautoptrelementtraits –](../../atl/reference/cautoptrelementtraits-class.md) pro vytvoření objektu třídy kolekce ukládání inteligentní ukazatele.

Další informace najdete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CAtlArray`

`CAutoPtrArray`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

##  <a name="cautoptrarray"></a>  CAutoPtrArray::CAutoPtrArray

Konstruktor

```
CAutoPtrArray() throw();
```

### <a name="remarks"></a>Poznámky

Inicializuje pole inteligentního ukazatele.

## <a name="see-also"></a>Viz také

[CAtlArray – třída](../../atl/reference/catlarray-class.md)<br/>
[CAutoPtrElementTraits – třída](../../atl/reference/cautoptrelementtraits-class.md)<br/>
[CAutoPtrList – třída](../../atl/reference/cautoptrlist-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
