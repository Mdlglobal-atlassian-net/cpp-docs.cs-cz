---
title: Třída CHeapPtrList
ms.date: 11/04/2016
f1_keywords:
- CHeapPtrList
- ATLCOLL/ATL::CHeapPtrList
- ATLCOLL/ATL::CHeapPtrList::CHeapPtrList
helpviewer_keywords:
- CHeapPtrList class
ms.assetid: cc70e585-362a-4007-81db-c705eb181226
ms.openlocfilehash: 0500ab8f76049aeaf1c89355ea5450a93243b734
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326862"
---
# <a name="cheapptrlist-class"></a>Třída CHeapPtrList

Tato třída poskytuje metody užitečné při vytváření seznamu ukazatelů haldy.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<typename E, class Allocator = ATL::CCRTAllocator>
class CHeapPtrList
   : public CAtlList<ATL::CHeapPtr<E, Allocator>,
                     CHeapPtrElementTraits<E, Allocator>>
```

#### <a name="parameters"></a>Parametry

*E*<br/>
Typ objektu, který má být uložen ve třídě kolekce.

*Přidělování*<br/>
Třída přidělení paměti, která má být používána. Výchozí hodnota je [CCRTAllocator](../../atl/reference/ccrtallocator-class.md).

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CHeapPtrList::CHeapPtrList](#cheapptrlist)|Konstruktor|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje konstruktor a odvozuje metody z [CAtlList](../../atl/reference/catllist-class.md) a [CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md) na podporu vytvoření třídy kolekce objektu ukládání haldy ukazatele.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Seznam CAtlList](../../atl/reference/catllist-class.md)

`CHeapPtrList`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

## <a name="cheapptrlistcheapptrlist"></a><a name="cheapptrlist"></a>CHeapPtrList::CHeapPtrList

Konstruktor

```
CHeapPtrList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parametry

*nBlockSize*<br/>
Velikost bloku.

### <a name="remarks"></a>Poznámky

Velikost bloku je míra množství paměti přidělené při je požadováno nový prvek. Větší velikosti bloků snižují volání rutiny přidělení paměti, ale používají více prostředků.

## <a name="see-also"></a>Viz také

[Třída CAtlList](../../atl/reference/catllist-class.md)<br/>
[Třída CHeapPtr](../../atl/reference/cheapptr-class.md)<br/>
[Třída CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
