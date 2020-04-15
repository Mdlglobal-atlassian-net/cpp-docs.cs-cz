---
title: Třída CAutoPtrList
ms.date: 11/04/2016
f1_keywords:
- CAutoPtrList
- ATLCOLL/ATL::CAutoPtrList
- ATLCOLL/ATL::CAutoPtrList::CAutoPtrList
helpviewer_keywords:
- CAutoPtrList class
ms.assetid: 11de4aca-28b0-4ff2-a74a-cb602312ffbd
ms.openlocfilehash: 48c7ad6fe13c5f5fbbe5829c25ce1c27896841be
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318805"
---
# <a name="cautoptrlist-class"></a>Třída CAutoPtrList

Tato třída poskytuje metody užitečné při vytváření seznamu inteligentní ukazatele.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<typename E>
class CAutoPtrList :
   public CAtlList<ATL::CAutoPtr<E>, CAutoPtrElementTraits<E>>
```

#### <a name="parameters"></a>Parametry

*E*<br/>
Typ ukazatele.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CAutoPtrList::CAutoPtrList](#cautoptrlist)|Konstruktor|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje konstruktor a odvozuje metody z [CAtlList](../../atl/reference/catllist-class.md) a [CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md) na pomoc vytvoření seznamu objektu ukládání inteligentní ukazatele. Třída [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) poskytuje podobnou funkci pro objekt pole.

Další informace naleznete v tématu [třídy kolekce klíčů ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Seznam CAtlList](../../atl/reference/catllist-class.md)

`CAutoPtrList`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

## <a name="cautoptrlistcautoptrlist"></a><a name="cautoptrlist"></a>CAutoPtrList::CAutoPtrList

Konstruktor

```
CAutoPtrList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parametry

*nBlockSize*<br/>
Velikost bloku s výchozí hodnotou 10.

### <a name="remarks"></a>Poznámky

Velikost bloku je míra množství paměti přidělené při je požadováno nový prvek. Větší velikosti bloků snižují volání rutiny přidělení paměti, ale používají více prostředků.

## <a name="see-also"></a>Viz také

[Třída CAtlList](../../atl/reference/catllist-class.md)<br/>
[Třída CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
