---
title: Třída CInterfaceList
ms.date: 11/04/2016
f1_keywords:
- CInterfaceList
- ATLCOLL/ATL::CInterfaceList
- ATLCOLL/ATL::CInterfaceList::CInterfaceList
helpviewer_keywords:
- CInterfaceList class
ms.assetid: 2077764d-25e5-4b3d-96c8-08a287bbcd25
ms.openlocfilehash: 0a7fd781c63e4ea084cf078e49fc9efb9cfa2d85
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326782"
---
# <a name="cinterfacelist-class"></a>Třída CInterfaceList

Tato třída poskytuje metody užitečné při vytváření seznamu ukazatelů rozhraní COM.

## <a name="syntax"></a>Syntaxe

```
template<class I, const IID* piid =& __uuidof(I)>
class CInterfaceList
   : public CAtlList<ATL::CComQIPtr<I, piid>,
                     CComQIPtrElementTraits<I, piid>>
```

#### <a name="parameters"></a>Parametry

*I*<br/>
Rozhraní COM určující typ ukazatele, který má být uložen.

*piid*<br/>
Ukazatel na IID *I*.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CInterfaceList::CInterfaceList](#cinterfacelist)|Konstruktor pro seznam rozhraní.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje konstruktor a odvozené metody pro vytvoření seznamu ukazatelů rozhraní COM. [CInterfaceArray](../../atl/reference/cinterfacearray-class.md) použijte v případě, že je vyžadováno pole.

Další informace naleznete v tématu [třídy kolekce klíčů ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Seznam CAtlList](../../atl/reference/catllist-class.md)

`CInterfaceList`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

## <a name="cinterfacelistcinterfacelist"></a><a name="cinterfacelist"></a>CInterfaceList::CInterfaceList

Konstruktor pro seznam rozhraní.

```
CInterfaceList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parametry

*nBlockSize*<br/>
Velikost bloku s výchozí hodnotou 10.

### <a name="remarks"></a>Poznámky

Velikost bloku je míra množství paměti přidělené při je požadováno nový prvek. Větší velikosti bloků snižují volání rutiny přidělení paměti, ale používají více prostředků.

## <a name="see-also"></a>Viz také

[Třída CAtlList](../../atl/reference/catllist-class.md)<br/>
[Třída CComQIPtr](../../atl/reference/ccomqiptr-class.md)<br/>
[Třída CComQIPtrElementTraits](../../atl/reference/ccomqiptrelementtraits-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
