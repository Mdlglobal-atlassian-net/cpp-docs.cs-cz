---
title: Cheapptrlist – třída
ms.date: 11/04/2016
f1_keywords:
- CHeapPtrList
- ATLCOLL/ATL::CHeapPtrList
- ATLCOLL/ATL::CHeapPtrList::CHeapPtrList
helpviewer_keywords:
- CHeapPtrList class
ms.assetid: cc70e585-362a-4007-81db-c705eb181226
ms.openlocfilehash: ef0224ccb9e2592daecb94204db5e1a8c785c7b7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50676977"
---
# <a name="cheapptrlist-class"></a>Cheapptrlist – třída

Tato třída poskytuje metody, které jsou užitečné při vytváření seznamu haldy ukazatele.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<typename E, class Allocator = ATL::CCRTAllocator>
class CHeapPtrList
   : public CAtlList<ATL::CHeapPtr<E, Allocator>,
                     CHeapPtrElementTraits<E, Allocator>>
```

#### <a name="parameters"></a>Parametry

*E*<br/>
Typ objektu ukládaly ve třídě kolekce.

*Allocator –*<br/>
Třída přidělení paměti pro použití. Výchozí hodnota je [ccrtallocator –](../../atl/reference/ccrtallocator-class.md).

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CHeapPtrList::CHeapPtrList](#cheapptrlist)|Konstruktor|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje konstruktor a je odvozena z metody [catllist –](../../atl/reference/catllist-class.md) a [cheapptrelementtraits –](../../atl/reference/cheapptrelementtraits-class.md) pro vytvoření objektu třídy kolekce ukládání ukazatelů haldy.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Catllist –](../../atl/reference/catllist-class.md)

`CHeapPtrList`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

##  <a name="cheapptrlist"></a>  CHeapPtrList::CHeapPtrList

Konstruktor

```
CHeapPtrList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parametry

*nBlockSize*<br/>
Velikost bloku.

### <a name="remarks"></a>Poznámky

Velikost bloku je míra množství paměti přidělené, pokud je nutné použít nový prvek. Bloky o větší velikosti snížit volání rutiny přidělení paměti, ale spotřebovávají více prostředků.

## <a name="see-also"></a>Viz také

[CAtlList – třída](../../atl/reference/catllist-class.md)<br/>
[CHeapPtr – třída](../../atl/reference/cheapptr-class.md)<br/>
[CHeapPtrElementTraits – třída](../../atl/reference/cheapptrelementtraits-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
