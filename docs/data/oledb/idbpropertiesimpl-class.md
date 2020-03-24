---
title: IDBPropertiesImpl – třída
ms.date: 11/04/2016
f1_keywords:
- IDBPropertiesImpl
- ATL.IDBPropertiesImpl
- ATL.IDBPropertiesImpl<T>
- ATL::IDBPropertiesImpl<T>
- ATL::IDBPropertiesImpl
- IDBPropertiesImpl::GetProperties
- IDBPropertiesImpl.GetProperties
- IDBPropertiesImpl::GetPropertyInfo
- IDBPropertiesImpl.GetPropertyInfo
- GetPropertyInfo
- IDBPropertiesImpl.SetProperties
- IDBPropertiesImpl::SetProperties
helpviewer_keywords:
- IDBPropertiesImpl class
- GetProperties method
- GetPropertyInfo method
- SetProperties method
ms.assetid: a7f15a8b-95b2-4316-b944-d5d03f8d74ab
ms.openlocfilehash: f873ec4f4eca434d0eb76df86c0891f1a99c2e2c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210701"
---
# <a name="idbpropertiesimpl-class"></a>IDBPropertiesImpl – třída

Poskytuje implementaci rozhraní `IDBProperties`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
class ATL_NO_VTABLE IDBPropertiesImpl
   : public IDBProperties, public CUtlProps<T>
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Vaše třída odvozená od `IDBPropertiesImpl`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** Atldb. h

## <a name="members"></a>Členové

### <a name="interface-methods"></a>Metody rozhraní

|||
|-|-|
|[GetProperties](#getproperties)|Vrátí hodnoty vlastností ve zdroji dat, v informacích o zdroji dat a skupinách vlastností inicializace, které jsou aktuálně nastaveny pro objekt zdroje dat, nebo na hodnoty vlastností ve skupině vlastností inicializace, které jsou aktuálně nastaveny v čítače.|
|[GetPropertyInfo](#getpropertyinfo)|Vrátí informace o všech vlastnostech podporovaných zprostředkovatelem.|
|[SetProperties](#setproperties)|Nastaví vlastnosti v datových zdrojích a skupinách vlastností inicializace pro objekty zdroje dat nebo skupinu vlastností inicializace pro enumerátory.|

## <a name="remarks"></a>Poznámky

[IDBProperties](/previous-versions/windows/desktop/ms719607(v=vs.85)) je povinné rozhraní pro objekty zdroje dat a volitelné rozhraní pro enumerátory. Nicméně pokud enumerátor zveřejňuje [IDBInitialize](/previous-versions/windows/desktop/ms713706(v=vs.85)), musí zveřejnit `IDBProperties`. `IDBPropertiesImpl` implementuje `IDBProperties` pomocí statické funkce definované [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

## <a name="idbpropertiesimplgetproperties"></a><a name="getproperties"></a>IDBPropertiesImpl –:: GetProperties

Vrátí hodnoty vlastností ve zdroji dat, v informacích o zdroji dat a skupinách vlastností inicializace, které jsou aktuálně nastaveny pro objekt zdroje dat, nebo na hodnoty vlastností ve skupině vlastností inicializace, které jsou aktuálně nastaveny v čítače.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetProperties)(ULONG cPropertySets,
   const DBPROPIDSET rgPropertySets[],
   ULONG * pcProperties,
   DBPROPSET ** prgProperties);
```

#### <a name="parameters"></a>Parametry

Viz [IDBProperties:: GetProperties](/previous-versions/windows/desktop/ms714344(v=vs.85)) v *referenci programátora OLE DB*.

Některé parametry odpovídají *OLE DB referenční parametry programátora* různých názvů, které jsou popsány v `IDBProperties::GetProperties`:

|Parametry šablony OLE DB|*OLE DB referenční parametry programátora*|
|--------------------------------|------------------------------------------------|
|*cPropertySets*|*cPropertyIDSets*|
|*rgPropertySets*|*rgPropertyIDSets*|
|*pcProperties*|*pcPropertySets*|
|*prgProperties*|*prgPropertySets*|

### <a name="remarks"></a>Poznámky

Pokud je poskytovatel inicializován, vrátí tato metoda hodnoty vlastností v DBPROPSET_DATASOURCE, DBPROPSET_DATASOURCEINFO, DBPROPSET_DBINIT skupiny vlastností, které jsou aktuálně nastaveny pro objekt zdroje dat. Pokud zprostředkovatel není inicializován, vrátí pouze DBPROPSET_DBINIT vlastnosti skupiny.

## <a name="idbpropertiesimplgetpropertyinfo"></a><a name="getpropertyinfo"></a>IDBPropertiesImpl –:: GetPropertyInfo

Vrátí informace o vlastnostech podporované zdrojem dat.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetPropertyInfo)(ULONG cPropertySets,
   const DBPROPIDSET rgPropertySets[],
   ULONG * pcPropertyInfoSets,
   DBPROPINFOSET ** prgPropertyInfoSets,
   OLECHAR ** ppDescBuffer);
```

#### <a name="parameters"></a>Parametry

Viz [IDBProperties:: GetPropertyInfo](/previous-versions/windows/desktop/ms718175(v=vs.85)) v *referenci programátora OLE DB*.

Některé parametry odpovídají *OLE DB referenční parametry programátora* různých názvů, které jsou popsány v `IDBProperties::GetPropertyInfo`:

|Parametry šablony OLE DB|*OLE DB referenční parametry programátora*|
|--------------------------------|------------------------------------------------|
|*cPropertySets*|*cPropertyIDSets*|
|*rgPropertySets*|*rgPropertyIDSets*|

### <a name="remarks"></a>Poznámky

K implementaci této funkce používá [IDBInitializeImpl:: m_pCUtlPropInfo](../../data/oledb/idbinitializeimpl-m-pcutlpropinfo.md) .

## <a name="idbpropertiesimplsetproperties"></a><a name="setproperties"></a>IDBPropertiesImpl –:: SetProperties

Nastaví vlastnosti v datových zdrojích a skupinách vlastností inicializace pro objekty zdroje dat nebo skupinu vlastností inicializace pro enumerátory.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets,
   DBPROPSET rgPropertySets[]);
```

#### <a name="parameters"></a>Parametry

Viz [IDBProperties:: SetProperties](/previous-versions/windows/desktop/ms723049(v=vs.85)) v *referenci programátora OLE DB*.

### <a name="remarks"></a>Poznámky

Pokud je poskytovatel inicializován, tato metoda nastaví hodnoty vlastností v DBPROPSET_DATASOURCE, DBPROPSET_DATASOURCEINFO, DBPROPSET_DBINIT skupiny vlastností pro objekt zdroje dat. Pokud zprostředkovatel není inicializován, nastaví pouze DBPROPSET_DBINIT vlastnosti skupiny.

## <a name="see-also"></a>Viz také

[Šablony poskytovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
