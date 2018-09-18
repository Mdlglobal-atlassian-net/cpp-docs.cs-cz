---
title: Irowsetinfoimpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IRowsetInfoImpl
- IRowsetInfoImpl
- ATL::IRowsetInfoImpl
- ATL.IRowsetInfoImpl.GetProperties
- IRowsetInfoImpl.GetProperties
- ATL::IRowsetInfoImpl::GetProperties
- IRowsetInfoImpl::GetProperties
- GetProperties
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
dev_langs:
- C++
helpviewer_keywords:
- IRowsetInfoImpl class
- GetProperties method
- GetReferencedRowset method
- GetSpecification method
ms.assetid: 9c654155-7727-464e-bd31-143e68391a47
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 542c97c1e13d5979290772668b6dccebe1ece9f9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46113159"
---
# <a name="irowsetinfoimpl-class"></a>IRowsetInfoImpl – třída

Poskytuje implementaci pro [IRowsetInfo](/previous-versions/windows/desktop/ms724541\(v=vs.85\)) rozhraní.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class PropClass = T>  
class ATL_NO_VTABLE IRowsetInfoImpl :   
   public IRowsetInfo,    
   public CUtlProps<PropClass>  
```  
  
### <a name="parameters"></a>Parametry  

*T*<br/>
Vaše třída odvozena od `IRowsetInfoImpl`.  
  
*PropClass*<br/>
Uživatelská vlastnost třídy, která výchozí hodnota je *T*. 

## <a name="requirements"></a>Požadavky  

**Záhlaví:** altdb.h   
  
## <a name="members"></a>Členové  
  
### <a name="interface-methods"></a>Metody rozhraní  
  
|||  
|-|-|  
|[GetProperties](#getproperties)|Vrátí aktuální nastavení všech vlastností, které sada řádků podporuje.|  
|[Getreferencedrowset –](#getreferencedrowset)|Vrátí ukazatel rozhraní v sadě řádků, ke kterému se vztahuje na záložku.|  
|[Getspecification –](#getspecification)|Vrátí ukazatel rozhraní na objekt (příkaz nebo relace), který vytvořili této sady řádků.|  
  
## <a name="remarks"></a>Poznámky  

Povinné rozhraní sady řádků. Tato třída implementuje pomocí vlastnosti sady řádků [mapy sady vlastností](../../data/oledb/begin-propset-map.md) definované ve třídě příkazu. I když třídy sady řádků se zobrazí, a používat třídu příkazu vlastnost sady, v sadě řádků je dodán vlastní kopii vlastností za běhu při vytvoření objektu příkazu nebo v jiné relaci.  
  
## <a name="getproperties"></a> IRowsetInfoImpl::GetProperties

Vrátí aktuální nastavení pro vlastnosti v `DBPROPSET_ROWSET` skupiny.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD (GetProperties )(const ULONG cPropertyIDSets,  
   const DBPROPIDSET rgPropertyIDSets[],  
   ULONG* pcPropertySets,  
   DBPROPSET** prgPropertySets);  
```  
  
#### <a name="parameters"></a>Parametry  

Zobrazit [IRowsetInfo::GetProperties](/previous-versions/windows/desktop/ms719611\(v=vs.85\)) v *referenční informace pro OLE DB programátory*. 

## <a name="getreferencedrowset"></a> IRowsetInfoImpl::GetReferencedRowset

Vrátí ukazatel rozhraní v sadě řádků, ke kterému se vztahuje na záložku.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD (GetReferencedRowset )(DBORDINAL iOrdinal,  
   REFIID riid,  
   IUnknown** ppReferencedRowset);  
```  
  
#### <a name="parameters"></a>Parametry  

Zobrazit [IRowsetInfo::GetReferencedRowset](/previous-versions/windows/desktop/ms721145\(v=vs.85\)) v *referenční informace pro OLE DB programátory*. *IOrdinal* parametr musí být sloupec záložky. 

## <a name="getspecification"></a> IRowsetInfoImpl::GetSpecification

Vrátí ukazatel rozhraní na objekt (příkaz nebo relace), který vytvořili této sady řádků.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD (GetSpecification )(REFIID riid,  
   IUnknown** ppSpecification);  
```  
  
#### <a name="parameters"></a>Parametry  

Zobrazit [IRowsetInfo::GetSpecification](/previous-versions/windows/desktop/ms716746\(v=vs.85\)) v *referenční informace pro OLE DB programátory*.  
  
### <a name="remarks"></a>Poznámky  

Pomocí této metody [igetdatasourceimpl –](../../data/oledb/igetdatasourceimpl-class.md) k načtení vlastnosti z objektu zdroje dat.  
  
## <a name="see-also"></a>Viz také  

[Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)