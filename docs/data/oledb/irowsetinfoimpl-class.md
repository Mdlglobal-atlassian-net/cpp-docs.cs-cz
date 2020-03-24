---
title: IRowsetInfoImpl – třída
ms.date: 11/04/2016
f1_keywords:
- ATL.IRowsetInfoImpl
- IRowsetInfoImpl
- ATL::IRowsetInfoImpl
- ATL.IRowsetInfoImpl.GetProperties
- IRowsetInfoImpl.GetProperties
- ATL::IRowsetInfoImpl::GetProperties
- IRowsetInfoImpl::GetProperties
- ATL::IRowsetInfoImpl::GetReferencedRowset
- GetReferencedRowset
- ATL.IRowsetInfoImpl.GetReferencedRowset
- IRowsetInfoImpl.GetReferencedRowset
- IRowsetInfoImpl::GetReferencedRowset
- IRowsetInfoImpl::GetSpecification
- ATL.IRowsetInfoImpl.GetSpecification
- IRowsetInfoImpl.GetSpecification
- GetSpecification
- ATL::IRowsetInfoImpl::GetSpecification
helpviewer_keywords:
- IRowsetInfoImpl class
- GetProperties method
- GetReferencedRowset method
- GetSpecification method
ms.assetid: 9c654155-7727-464e-bd31-143e68391a47
ms.openlocfilehash: cf72aabce58237f470d536c02727f442404db030
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210441"
---
# <a name="irowsetinfoimpl-class"></a>IRowsetInfoImpl – třída

Poskytuje implementaci rozhraní [IRowsetInfo](/previous-versions/windows/desktop/ms724541(v=vs.85)) .

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class PropClass = T>
class ATL_NO_VTABLE IRowsetInfoImpl :
   public IRowsetInfo,
   public CUtlProps<PropClass>
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Vaše třída odvozená od `IRowsetInfoImpl`.

*PropClass*<br/>
Uživatelsky definované třídy vlastností, které mají výchozí hodnotu *T*.

## <a name="requirements"></a>Požadavky

**Záhlaví:** altdb. h

## <a name="members"></a>Členové

### <a name="interface-methods"></a>Metody rozhraní

|||
|-|-|
|[GetProperties](#getproperties)|Vrátí aktuální nastavení všech vlastností podporovaných sadou řádků.|
|[GetReferencedRowset](#getreferencedrowset)|Vrátí ukazatel rozhraní na sadu řádků, na kterou se záložka aplikuje.|
|[Getspecific](#getspecification)|Vrátí ukazatel rozhraní objektu (příkazu nebo relace), který vytvořil tuto sadu řádků.|

## <a name="remarks"></a>Poznámky

Povinné rozhraní pro sady řádků. Tato třída implementuje vlastnosti sady řádků pomocí [mapy sady vlastností](../../data/oledb/begin-propset-map.md) definované ve vaší třídě příkazu. I když se třída sady řádků zdá používat sadu vlastností třídy příkazu, sada řádků je dodávána s vlastní kopií vlastností za běhu, když je vytvořena příkazem nebo objektem relace.

## <a name="irowsetinfoimplgetproperties"></a><a name="getproperties"></a>IRowsetInfoImpl –:: GetProperties

Vrátí aktuální nastavení vlastností ve skupině `DBPROPSET_ROWSET`.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (GetProperties )(const ULONG cPropertyIDSets,
   const DBPROPIDSET rgPropertyIDSets[],
   ULONG* pcPropertySets,
   DBPROPSET** prgPropertySets);
```

#### <a name="parameters"></a>Parametry

Viz [IRowsetInfo:: GetProperties](/previous-versions/windows/desktop/ms719611(v=vs.85)) v *referenci programátora OLE DB*.

## <a name="irowsetinfoimplgetreferencedrowset"></a><a name="getreferencedrowset"></a>IRowsetInfoImpl –:: GetReferencedRowset

Vrátí ukazatel rozhraní na sadu řádků, na kterou se záložka aplikuje.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (GetReferencedRowset )(DBORDINAL iOrdinal,
   REFIID riid,
   IUnknown** ppReferencedRowset);
```

#### <a name="parameters"></a>Parametry

Viz [IRowsetInfo:: GetReferencedRowset](/previous-versions/windows/desktop/ms721145(v=vs.85)) v *referenci programátora OLE DB*. Parametr *iOrdinal* musí být sloupec záložek.

## <a name="irowsetinfoimplgetspecification"></a><a name="getspecification"></a>IRowsetInfoImpl –:: getspecifice

Vrátí ukazatel rozhraní objektu (příkazu nebo relace), který vytvořil tuto sadu řádků.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (GetSpecification )(REFIID riid,
   IUnknown** ppSpecification);
```

#### <a name="parameters"></a>Parametry

Viz [IRowsetInfo:: getspecifičnost](/previous-versions/windows/desktop/ms716746(v=vs.85)) v *referenci programátora OLE DB*.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte s [IGetDataSourceImpl –](../../data/oledb/igetdatasourceimpl-class.md) k načtení vlastností z objektu zdroje dat.

## <a name="see-also"></a>Viz také

[Šablony poskytovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
