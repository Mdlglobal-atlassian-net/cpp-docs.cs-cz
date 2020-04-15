---
title: Třída CAutoPtrArray
ms.date: 11/04/2016
f1_keywords:
- CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray::CAutoPtrArray
helpviewer_keywords:
- CAutoPtrArray class
ms.assetid: 880a70da-8c81-4427-8ac6-49aa8d424244
ms.openlocfilehash: 93fc5cfea4ea655e57e785ca234df59fe10d6570
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318899"
---
# <a name="cautoptrarray-class"></a>Třída CAutoPtrArray

Tato třída poskytuje metody užitečné při vytváření pole inteligentní ukazatele.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

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

|Name (Název)|Popis|
|----------|-----------------|
|[CAutoPtrArray::CAutoPtrArray](#cautoptrarray)|Konstruktor|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje konstruktor a odvozuje metody z [CAtlArray](../../atl/reference/catlarray-class.md) a [CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md) na podporu vytvoření třídy kolekce objektu ukládání inteligentní ukazatele.

Další informace naleznete v tématu [třídy kolekce klíčů ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CAtlArray`

`CAutoPtrArray`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

## <a name="cautoptrarraycautoptrarray"></a><a name="cautoptrarray"></a>CAutoPtrArray::CAutoPtrArray

Konstruktor

```
CAutoPtrArray() throw();
```

### <a name="remarks"></a>Poznámky

Inicializuje pole inteligentního ukazatele.

## <a name="see-also"></a>Viz také

[Třída CAtlArray](../../atl/reference/catlarray-class.md)<br/>
[Třída CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)<br/>
[Třída CAutoPtrList](../../atl/reference/cautoptrlist-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
