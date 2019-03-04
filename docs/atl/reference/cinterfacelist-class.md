---
title: Cinterfacelist – třída
ms.date: 11/04/2016
f1_keywords:
- CInterfaceList
- ATLCOLL/ATL::CInterfaceList
- ATLCOLL/ATL::CInterfaceList::CInterfaceList
helpviewer_keywords:
- CInterfaceList class
ms.assetid: 2077764d-25e5-4b3d-96c8-08a287bbcd25
ms.openlocfilehash: e740d891e279bb29eeef898de52698dc3f04fc67
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57282458"
---
# <a name="cinterfacelist-class"></a>Cinterfacelist – třída

Tato třída poskytuje metody, které jsou užitečné při vytváření seznamu ukazatele rozhraní modelu COM.

## <a name="syntax"></a>Syntaxe

```
template<class I, const IID* piid =& __uuidof(I)>
class CInterfaceList
   : public CAtlList<ATL::CComQIPtr<I, piid>,
                     CComQIPtrElementTraits<I, piid>>
```

#### <a name="parameters"></a>Parametry

*I*<br/>
Rozhraní modelu COM zadání typu ukazatel na Uložit.

*piid*<br/>
Ukazatel na IID *můžu*.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CInterfaceList::CInterfaceList](#cinterfacelist)|Konstruktor pro seznamu rozhraní.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje konstruktor a odvozené metody pro vytvoření seznamu ukazatele rozhraní modelu COM. Použití [cinterfacearray –](../../atl/reference/cinterfacearray-class.md) když pole je povinné.

Další informace najdete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CAtlList](../../atl/reference/catllist-class.md)

`CInterfaceList`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

##  <a name="cinterfacelist"></a>  CInterfaceList::CInterfaceList

Konstruktor pro seznamu rozhraní.

```
CInterfaceList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parametry

*nBlockSize*<br/>
Velikost bloku, výchozí hodnota je 10.

### <a name="remarks"></a>Poznámky

Velikost bloku je míra množství paměti přidělené, pokud je nutné použít nový prvek. Bloky o větší velikosti snížit volání rutiny přidělení paměti, ale spotřebovávají více prostředků.

## <a name="see-also"></a>Viz také:

[CAtlList – třída](../../atl/reference/catllist-class.md)<br/>
[CComQIPtr – třída](../../atl/reference/ccomqiptr-class.md)<br/>
[CComQIPtrElementTraits – třída](../../atl/reference/ccomqiptrelementtraits-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
