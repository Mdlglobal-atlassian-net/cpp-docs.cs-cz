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
- GetProperties
- IDBPropertiesImpl::GetPropertyInfo
- IDBPropertiesImpl.GetPropertyInfo
- GetPropertyInfo
- IDBPropertiesImpl.SetProperties
- SetProperties
- IDBPropertiesImpl::SetProperties
helpviewer_keywords:
- IDBPropertiesImpl class
- GetProperties method
- GetPropertyInfo method
- SetProperties method
ms.assetid: a7f15a8b-95b2-4316-b944-d5d03f8d74ab
ms.openlocfilehash: 77385fc8b2869cc59c7a0061951c76a431490efe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638045"
---
# <a name="idbpropertiesimpl-class"></a>IDBPropertiesImpl – třída

Poskytuje implementaci pro `IDBProperties` rozhraní.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
class ATL_NO_VTABLE IDBPropertiesImpl
   : public IDBProperties, public CUtlProps<T>
```

### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída odvozena od `IDBPropertiesImpl`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldb.h

## <a name="members"></a>Členové

### <a name="interface-methods"></a>Metody rozhraní

|||
|-|-|
|[GetProperties](#getproperties)|Vrátí hodnoty vlastností ve zdroji dat, informace o zdroji dat a inicializaci skupiny vlastností, které jsou aktuálně nastaveny na objekt zdroje dat nebo hodnoty vlastností ve skupině vlastností Initialization, které jsou aktuálně nastavená na Enumerátor.|
|[GetPropertyInfo](#getpropertyinfo)|Vrátí informace o všech vlastnostech podporována zprostředkovatelem.|
|[SetProperties –](#setproperties)|Nastaví vlastnosti zdroje dat a inicializační vlastnosti skupiny, pro objekty zdroje dat, nebo skupině vlastností Initialization pro enumerátory.|

## <a name="remarks"></a>Poznámky

[IDBProperties](/previous-versions/windows/desktop/ms719607) je povinné rozhraní pro objekty zdroje dat a volitelné rozhraní pro enumerátory. Nicméně pokud enumerátor zpřístupní [IDBInitialize](/previous-versions/windows/desktop/ms713706), musí vystavit `IDBProperties`. `IDBPropertiesImpl` implementuje `IDBProperties` pomocí statické funkce definované [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

## <a name="getproperties"></a> IDBPropertiesImpl::GetProperties

Vrátí hodnoty vlastností ve zdroji dat, informace o zdroji dat a inicializaci skupiny vlastností, které jsou aktuálně nastaveny na objekt zdroje dat nebo hodnoty vlastností ve skupině vlastností Initialization, které jsou aktuálně nastavená na Enumerátor.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetProperties)(ULONG cPropertySets, 
   const DBPROPIDSET rgPropertySets[], 
   ULONG * pcProperties, 
   DBPROPSET ** prgProperties);
```

#### <a name="parameters"></a>Parametry

Zobrazit [IDBProperties::GetProperties](/previous-versions/windows/desktop/ms714344) v *referenční informace pro OLE DB programátory*.

Některé parametry odpovídají *OLE DB referenční informace pro programátory* parametry jiné názvy, které jsou popsány v `IDBProperties::GetProperties`:

|Parametry šablony technologie OLE DB|*OLE DB referenční informace pro programátory* parametry|
|--------------------------------|------------------------------------------------|
|*cPropertySets*|*cPropertyIDSets*|
|*rgPropertySets*|*rgPropertyIDSets*|
|*pcProperties*|*pcPropertySets*|
|*prgProperties*|*prgPropertySets*|

### <a name="remarks"></a>Poznámky

Pokud zprostředkovatele je inicializován, vrátí tato metoda hodnoty vlastností v DBPROPSET_DATASOURCE DBPROPSET_DATASOURCEINFO, DBPROPSET_DBINIT skupiny vlastností, které jsou aktuálně nastavená na objekt zdroje dat. Pokud zprostředkovatele není inicializován, vrátí pouze vlastnosti DBPROPSET_DBINIT skupiny.

## <a name="getpropertyinfo"></a> IDBPropertiesImpl::GetPropertyInfo

Vrátí informace o vlastnosti zdroje dat podporované.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetPropertyInfo)(ULONG cPropertySets, 
   const DBPROPIDSET rgPropertySets[], 
   ULONG * pcPropertyInfoSets, 
   DBPROPINFOSET ** prgPropertyInfoSets, 
   OLECHAR ** ppDescBuffer);
```

#### <a name="parameters"></a>Parametry

Zobrazit [IDBProperties::GetPropertyInfo](/previous-versions/windows/desktop/ms718175) v *referenční informace pro OLE DB programátory*.

Některé parametry odpovídají *OLE DB referenční informace pro programátory* parametry jiné názvy, které jsou popsány v `IDBProperties::GetPropertyInfo`:

|Parametry šablony technologie OLE DB|*OLE DB referenční informace pro programátory* parametry|
|--------------------------------|------------------------------------------------|
|*cPropertySets*|*cPropertyIDSets*|
|*rgPropertySets*|*rgPropertyIDSets*|

### <a name="remarks"></a>Poznámky

Používá [IDBInitializeImpl::m_pCUtlPropInfo](../../data/oledb/idbinitializeimpl-m-pcutlpropinfo.md) pro implementaci této funkce.

## <a name="setproperties"></a> IDBPropertiesImpl::SetProperties

Nastaví vlastnosti zdroje dat a inicializační vlastnosti skupiny, pro objekty zdroje dat, nebo skupině vlastností Initialization pro enumerátory.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets, 
   DBPROPSET rgPropertySets[]);
```

#### <a name="parameters"></a>Parametry

Zobrazit [IDBProperties::SetProperties](/previous-versions/windows/desktop/ms723049) v *referenční informace pro OLE DB programátory*.

### <a name="remarks"></a>Poznámky

Pokud zprostředkovatele je inicializována, tato metoda nastaví hodnoty vlastností v DBPROPSET_DATASOURCE DBPROPSET_DATASOURCEINFO, DBPROPSET_DBINIT skupiny vlastností pro objekt zdroje dat. Pokud zprostředkovatele není inicializován, nastaví DBPROPSET_DBINIT skupiny pouze vlastnosti.

## <a name="see-also"></a>Viz také

[Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)