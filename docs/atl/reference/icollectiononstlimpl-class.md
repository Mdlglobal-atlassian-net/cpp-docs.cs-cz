---
title: Třída ICollectionOnSTLimpl
ms.date: 11/04/2016
f1_keywords:
- ICollectionOnSTLImpl
- ATLCOM/ATL::ICollectionOnSTLImpl
- ATLCOM/ATL::ICollectionOnSTLImpl::get__NewEnum
- ATLCOM/ATL::ICollectionOnSTLImpl::getcount
- ATLCOM/ATL::ICollectionOnSTLImpl::get_Item
- ATLCOM/ATL::ICollectionOnSTLImpl::m_coll
helpviewer_keywords:
- ICollectionOnSTLImpl class
ms.assetid: 683c88b0-0d97-4779-a762-e493334ba7f9
ms.openlocfilehash: a8ccab08b89da8c1b8ef56c8932e27a6c74e62aa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329898"
---
# <a name="icollectiononstlimpl-class"></a>Třída ICollectionOnSTLimpl

Tato třída poskytuje metody používané třídou kolekce.

## <a name="syntax"></a>Syntaxe

```
template <class T, class CollType, class ItemType, class CopyItem, class EnumType>
class ICollectionOnSTLImpl : public T
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Rozhraní kolekce COM.

*CollType*<br/>
Třída kontejneru standardní knihovny jazyka C++.

*ItemType*<br/>
Typ položky vystavené rozhraní kontejneru.

*Kopírovat položku*<br/>
Třída [zásad kopírování](../../atl/atl-copy-policy-classes.md).

*EnumType*<br/>
[CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)-kompatibilní enumerator třídy.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[ICollectionOnSTLImpl::get__NewEnum](#newenum)|Vrátí objekt čítače pro kolekci.|
|[ICollectionOnSTLImpl::getcount](#get_count)|Vrátí počet prvků v kolekci.|
|[ICollectionOnSTLImpl::get_Item](#get_item)|Vrátí požadovanou položku z kolekce.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[ICollectionOnSTLImpl::m_coll](#m_coll)|Kolekce|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje implementaci pro tři metody rozhraní kolekce: [getcount](#get_count), [get_Item](#get_item)a [get__NewEnum](#newenum).

Chcete-li použít tuto třídu:

- Definujte (nebo si vypůjčte) rozhraní kolekce, které chcete implementovat.

- Odvodit třídu `ICollectionOnSTLImpl` ze specializace založené na této rozhraní kolekce.

- Odvozené třídy slouží k implementaci všechny metody `ICollectionOnSTLImpl`z rozhraní kolekce není zpracována .

> [!NOTE]
> Pokud je rozhraní kolekce duální rozhraní, odvodit třídu z [IDispatchImpl](../../atl/reference/idispatchimpl-class.md), předávání `ICollectionOnSTLImpl` specializace jako `IDispatch` první parametr šablony, pokud chcete, aby ATL poskytnout implementaci metod.

- Přidejte položky do [m_coll](#m_coll) člen naplnit kolekce.

Další informace a příklady naleznete v tématu [kolekce atl a výčtu](../../atl/atl-collections-and-enumerators.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`T`

`ICollectionOnSTLImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="icollectiononstlimplgetcount"></a><a name="get_count"></a>ICollectionOnSTLImpl::getcount

Tato metoda vrátí počet položek v kolekci.

```
STDMETHOD(getcount)(long* pcount);
```

### <a name="parameters"></a>Parametry

*pcount*<br/>
[out] Počet prvků v kolekci.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="icollectiononstlimplget_item"></a><a name="get_item"></a>ICollectionOnSTLImpl::get_Item

Tato metoda vrátí zadanou položku z kolekce.

```
STDMETHOD(get_Item)(long Index, ItemType* pvar);
```

### <a name="parameters"></a>Parametry

*Index*<br/>
[v] Index na základě 1 položky v kolekci.

*pvar*<br/>
[out] Položka odpovídající *Index*.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Položka je získána zkopírováním dat na zadané pozici v [m_coll](#m_coll) pomocí metody kopírování [třídy zásad kopírování](../../atl/atl-copy-policy-classes.md) předané jako argument šablony ve `ICollectionOnSTLImpl` specializaci.

## <a name="icollectiononstlimplget__newenum"></a><a name="newenum"></a>ICollectionOnSTLImpl::get__NewEnum

Vrátí objekt čítače pro kolekci.

```
STDMETHOD(get__NewEnum)(IUnknown** ppUnk);
```

### <a name="parameters"></a>Parametry

*ppUnk*<br/>
[out] **IUnknown** ukazatel nově vytvořený objekt čítače výčtu.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Nově vytvořený čítač výčtu udržuje iterátor `m_coll`v původní kolekci , (takže je vytvořena žádná kopie) a obsahuje odkaz COM na objekt kolekce, aby bylo zajištěno, že kolekce zůstane naživu, zatímco existují vynikající čítače výčtu.

## <a name="icollectiononstlimplm_coll"></a><a name="m_coll"></a>ICollectionOnSTLImpl::m_coll

Tento člen obsahuje položky reprezentované kolekce.

```
CollType m_coll;
```

## <a name="see-also"></a>Viz také

[Ukázka atlcollections](../../overview/visual-cpp-samples.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
