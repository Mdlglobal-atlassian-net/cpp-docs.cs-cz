---
title: Icollectiononstlimpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ICollectionOnSTLImpl
- ATLCOM/ATL::ICollectionOnSTLImpl
- ATLCOM/ATL::ICollectionOnSTLImpl::get__NewEnum
- ATLCOM/ATL::ICollectionOnSTLImpl::getcount
- ATLCOM/ATL::ICollectionOnSTLImpl::get_Item
- ATLCOM/ATL::ICollectionOnSTLImpl::m_coll
dev_langs:
- C++
helpviewer_keywords:
- ICollectionOnSTLImpl class
ms.assetid: 683c88b0-0d97-4779-a762-e493334ba7f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d2b70e7332c5f0a24af80ddb5cfd14a8ecf146de
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025149"
---
# <a name="icollectiononstlimpl-class"></a>Icollectiononstlimpl – třída

Tato třída poskytuje metody používané třídy kolekce.

## <a name="syntax"></a>Syntaxe

```
template <class T, class CollType, class ItemType, class CopyItem, class EnumType>
class ICollectionOnSTLImpl : public T
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Kolekce rozhraní modelu COM.

*CollType*<br/>
Třída kontejneru standardní knihovny C++.

*Typ položky*<br/>
Typ položky, které jsou vystavené rozhraní kontejneru.

*CopyItem*<br/>
A [třídy zásady kopírování](../../atl/atl-copy-policy-classes.md).

*EnumType*<br/>
A [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)– třída kompatibilní enumerátor.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[ICollectionOnSTLImpl::get__NewEnum](#newenum)|Vrátí objekt enumerátoru pro kolekci.|
|[ICollectionOnSTLImpl::getcount](#get_count)|Vrátí počet prvků v kolekci.|
|[ICollectionOnSTLImpl::get_Item](#get_item)|Vrátí požadovanou položku z kolekce.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[ICollectionOnSTLImpl::m_coll](#m_coll)|Kolekce.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje implementaci pro tři metody rozhraní kolekce: [getcount](#get_count), [get_Item](#get_item), a [get__NewEnum](#newenum).

Chcete-li použít tuto třídu:

- Definovat (nebo si půjčte), který chcete implementovat rozhraní kolekce.

- Odvodit třídu z specializací `ICollectionOnSTLImpl` založené na tomto rozhraní kolekce.

- Použití odvozené třídy pro implementaci jakékoli metody z rozhraní kolekce není zpracována `ICollectionOnSTLImpl`.

> [!NOTE]
>  Pokud kolekce rozhraní je duální rozhraní, odvodit třídu z [třídou IDispatchImpl](../../atl/reference/idispatchimpl-class.md), předejte `ICollectionOnSTLImpl` specializace jako první parametr šablony, pokud chcete, aby ATL poskytnout implementaci `IDispatch` metody.

- Přidat položky do [m_coll](#m_coll) člen k naplnění kolekce.

Další informace a příklady najdete v tématu [ATL – kolekce a enumerátory](../../atl/atl-collections-and-enumerators.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`T`

`ICollectionOnSTLImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom

##  <a name="get_count"></a>  ICollectionOnSTLImpl::getcount

Tato metoda vrátí počet položek v kolekci.

```
STDMETHOD(getcount)(long* pcount);
```

### <a name="parameters"></a>Parametry

*pcount –*<br/>
[out] Počet elementů v kolekci.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

##  <a name="get_item"></a>  ICollectionOnSTLImpl::get_Item

Tato metoda vrátí určenou položku z kolekce.

```
STDMETHOD(get_Item)(long Index, ItemType* pvar);
```

### <a name="parameters"></a>Parametry

*Index*<br/>
[in] Index založený na 1 položka v kolekci.

*pvar*<br/>
[out] Odpovídající položky pro *Index*.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Položka se získá zkopírováním dat na konkrétní pozici v [m_coll](#m_coll) pomocí metody kopie [třídy zásady kopírování](../../atl/atl-copy-policy-classes.md) předán jako argument šablony v `ICollectionOnSTLImpl` specializace.

##  <a name="newenum"></a>  ICollectionOnSTLImpl::get__NewEnum

Vrátí objekt enumerátoru pro kolekci.

```
STDMETHOD(get__NewEnum)(IUnknown** ppUnk);
```

### <a name="parameters"></a>Parametry

*ppUnk*<br/>
[out] **IUnknown** ukazatel nově vytvořený enumerator – objekt.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Nově vytvořený čítač udržuje iterátor v původní kolekci `m_coll`proto (není vytvořena žádná kopie) a obsahuje odkaz modelu COM v objektu kolekce k zajištění, že kolekce zůstane aktivní, i když existují nevyřízené enumerátory.

##  <a name="m_coll"></a>  ICollectionOnSTLImpl::m_coll

Tento člen obsahuje položky reprezentována kolekce.

```
CollType m_coll;
```

## <a name="see-also"></a>Viz také

[Ukázka ATLCollections](../../visual-cpp-samples.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
