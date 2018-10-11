---
title: Isessionpropertiesimpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ISessionPropertiesImpl
- ISessionPropertiesImpl::GetProperties
- ISessionPropertiesImpl.GetProperties
- GetProperties
- ISessionPropertiesImpl.SetProperties
- SetProperties
- ISessionPropertiesImpl::SetProperties
dev_langs:
- C++
helpviewer_keywords:
- ISessionPropertiesImpl class
- GetProperties method
- SetProperties method
ms.assetid: ca0ba254-c7dc-4c52-abec-cf895a0c6a63
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 34daf1f1c8624206070c73c9f012192c8b3dec66
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49082628"
---
# <a name="isessionpropertiesimpl-class"></a>ISessionPropertiesImpl – třída

Poskytuje implementaci [ISessionProperties](/previous-versions/windows/desktop/ms713721) rozhraní.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class PropClass = T>  
class ATL_NO_VTABLE ISessionPropertiesImpl :  
   public ISessionProperties,    
   public CUtlProps<PropClass>  
```  
  
### <a name="parameters"></a>Parametry  

*T*<br/>
Vaše třída odvozena od `ISessionPropertiesImpl`.  
  
*PropClass*<br/>
Uživatelská vlastnost třídy, která výchozí hodnota je *T*.  

## <a name="requirements"></a>Požadavky  

**Záhlaví:** atldb.h  
  
## <a name="members"></a>Členové  
  
### <a name="interface-methods"></a>Metody rozhraní  
  
|||  
|-|-|  
|[GetProperties](#getproperties)|Vrátí seznam vlastností ve skupině vlastností relace, které jsou aktuálně nastavená na relaci.|  
|[SetProperties –](#setproperties)|Nastaví vlastnosti ve skupině vlastností relace.|  
  
## <a name="remarks"></a>Poznámky  

Povinné rozhraní na relace. Tato třída implementuje vlastnosti relace voláním statické funkce definované [mapy sady vlastností](../../data/oledb/begin-propset-map.md). Mapa set vlastnosti musí být zadán v třídě relace.  
  
## <a name="getproperties"></a> ISessionPropertiesImpl::GetProperties

Vrátí seznam vlastností v `DBPROPSET_SESSION` skupiny vlastností, které jsou aktuálně nastavená na relaci.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD(GetProperties)(ULONG cPropertyIDSets,   
   const DBPROPIDSET rgPropertyIDSets[],   
   ULONG * pcPropertySets,   
   DBPROPSET ** prgPropertySets);  
```  
  
#### <a name="parameters"></a>Parametry  

Zobrazit [ISessionProperties::GetProperties](/previous-versions/windows/desktop/ms723643) v *referenční informace pro OLE DB programátory*. 

## <a name="setproperties"></a> ISessionPropertiesImpl::SetProperties

Nastaví vlastnosti `DBPROPSET_SESSION` skupiny vlastností.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets,   
   DBPROPSET rgPropertySets[]);  
```  
  
#### <a name="parameters"></a>Parametry  

Zobrazit [ISessionProperties::SetProperties](/previous-versions/windows/desktop/ms714405) v *referenční informace pro OLE DB programátory*.  
  
## <a name="see-also"></a>Viz také  

[Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)